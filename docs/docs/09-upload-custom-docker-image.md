---
id: upload-custom-docker-image
title: 'Images'
date: '2025-09-28 19:00'
sidebar_position: 9
description: 'This tutorial demonstrates how to upload a local Docker image to Glows.ai, including image creation, tar packaging, uploading, and instance setup.'
---

# Uploading Custom Docker Images on Glows.ai

This tutorial will guide you step by step on how to upload a local Docker image to Glows.ai, covering image preparation, packaging, uploading, and instance creation.

## **Notice of Snapshot and Image Billing Policy Update**

To provide users with a more flexible and efficient way to manage environments and data, the platform will update the quota and billing mechanism for Snapshot and Image services effective December 1, 2026, at 00:00 (UTC+8).
After the update, Storage package quotas will apply exclusively to Datadrive storage. Snapshot and Image resources will no longer consume Storage quotas and will instead be billed based on their actual storage usage with hourly billing.
The updated billing rules are as follows:
- Billing rate: 0.0001 credits/hour/GB
- Billing starts once a Snapshot or Image is successfully created
- Billing stops once the corresponding Snapshot or Image is deleted
This adjustment is designed to provide greater flexibility in resource management and allow users to optimize costs based on actual usage.

If you have any questions, please contact us here: [Click here to contact us](/docs/contact-us)

## Creating a Docker Image Tar Package

To ensure your image runs properly on Glows.ai, pay attention to the following:

- The image **ENTRYPOINT** must keep running (otherwise the container will exit automatically).
- Install and start the SSH service (for convenient instance access).

### Setup Instructions

It is recommended to create a separate `.sh` script as the ENTRYPOINT, for example `run_glowsai.sh`, containing startup commands for the container (SSH service or custom services). Example:

```bash
#!/bin/bash
# Start SSH service
echo "Starting SSH service..."
/usr/sbin/sshd -E /root/.ssh/sshd_running.log

# Custom Command
echo "hello glowsai" > /hello.txt

# Keep the container running
echo "Container running..."
tail -f /dev/null
```

Also, in your Dockerfile, include SSH installation and configuration, and set the ENTRYPOINT:

```bash
# Install and configure SSH server
RUN apt-get update && apt-get install -y openssh-server && \
    mkdir /var/run/sshd /root/.ssh && sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Copy and set permissions for the start script
COPY run_glowsai.sh /usr/bin/
RUN chmod +x /usr/bin/run_glowsai.sh
EXPOSE 22
# Set entrypoint
ENTRYPOINT ["/usr/bin/run_glowsai.sh"]
```

### Practical Steps

Before uploading your local image, ensure SSH is installed and running inside the image and that the ENTRYPOINT keeps running. Otherwise, follow these steps.

![set run_glowsai.sh](../docs-images/upload-docker-image/01.png)

1. Create a directory `new_images` and inside it, create `run_glowsai.sh` with the following content:

```bash
#!/bin/bash
# Start SSH service
echo "Starting SSH service..."
/usr/sbin/sshd -E /root/.ssh/sshd_running.log

# Custom Command
echo "hello glowsai" > /hello.txt

# Keep the container running
echo "Container running..."
tail -f /dev/null
```

> Note: The `# Custom Command` section is where you can add any commands to run on container startup. Do not modify other parts to avoid startup failure.

2. Create a `Dockerfile` with the following content:

```bash
# Set the base image
FROM oldwatch/tmp-images:huggingface-text-embeddings-inference_1_8

# Install and configure SSH server
RUN apt-get update && apt-get install -y openssh-server && \
    mkdir /var/run/sshd /root/.ssh && sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Copy and set permissions for the start script
COPY run_glowsai.sh /usr/bin/
RUN chmod +x /usr/bin/run_glowsai.sh
EXPOSE 22
# Set entrypoint
ENTRYPOINT ["/usr/bin/run_glowsai.sh"]
```

3. Build the new image in the directory:

```bash
docker build -t new_images:huggingface-text-embeddings-inference_1_8 .
```

![Build successfully](../docs-images/upload-docker-image/02.png)

4. After a successful build, use `docker save` to package the image as a tar file:

```bash
docker save -o <output_file_path> <image_name_or_id>
```

![Pack tar ](../docs-images/upload-docker-image/03.png)

## Uploading the Docker Image Tar Package

1. Open Glows.ai’s **Images** interface and click `Upload Image`.
2. Enter an image description and click **Select Image** to upload the tar package.

![Choose image](../docs-images/upload-docker-image/04.png)

3. During upload, progress will be displayed. Once completed, the image can be used in Glows.ai.

![Upload successfully](../docs-images/upload-docker-image/05.png)

## Creating an Instance

1. When creating an instance, select **My Images**. You will see the uploaded image. Choose it, and if a Datadrive Mount is needed, complete the instance creation process.

![Create instance](../docs-images/upload-docker-image/06.png)

2. After the instance starts, manually set the ports you want to expose, e.g., SSH on port 22:

   - Click `New Port Forwarding`
   - Set **Service Port** to 22
   - **Do not check HTTPS**
   - Click `Create` to finish port forwarding

![Set port](../docs-images/upload-docker-image/07.png)

3. After about 10–20 seconds, port mapping will be established. The interface will show SSH connection info and password for local access.

![SSH connection](../docs-images/upload-docker-image/08.png)

4. If the instance runs other services that need public access, you can add additional port mappings. For HTTP services, check **HTTPS**.

![Public port](../docs-images/upload-docker-image/09.png)

5. For example, to run an HTTP service on port 8080, use the corresponding link from the instance interface to access it.

![Run an HTTP service](../docs-images/upload-docker-image/10.png)

6. After modifying the environment or files, you can create a **Snapshot** or release the instance when no longer needed.

![Create a Snapshot or Release](../docs-images/upload-docker-image/11.png)

---

# Contact Us

If you have any questions or suggestions while using **Glows.ai**, please reach out via email, Discord, or Line.

**Email:** [support@glows.ai](mailto:support@glows.ai)

**Discord:** [https://discord.com/invite/glowsai](https://discord.com/invite/glowsai)

**Line:** [https://lin.ee/fHcoDgG](https://lin.ee/fHcoDgG)
