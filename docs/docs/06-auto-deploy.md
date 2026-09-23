---
id: auto-deploy
sidebar_position: 6
---

# Auto Deploy

On the **Auto Deploy** page, you can configure and automate the deployment process so your application runs efficiently and securely.

When deploying a GPU service, you usually need to manually create an instance and then manually release it once you're done; when usage is irregular or requests are sparse, this becomes tedious.

Glows.ai's Auto Deploy service solves this problem. Once configured, the system provides a fixed service link; whenever a request is sent to this URL, Glows.ai processes the request according to your configuration, automatically creating an instance and executing the start command. If no new requests arrive within n consecutive minutes, Glows.ai will automatically release the instance.

In other words, Auto Deploy turns "create instance → process request → release instance" into an automated loop. You only need to maintain a single fixed service link, which you can integrate directly into your code or automated workflows — no need to manually manage the instance lifecycle, and no risk of ongoing charges from forgetting to release an instance, helping you save on costs.

Below is a detailed feature introduction:

---
## **Creating an Auto Deploy**

### **Configuring Auto Deploy**
Go to the Auto Deploy page and click `New Deploy` in the top right to create a new configuration and get started.

---
![](../docs-images/autodeploy/01.png)

- **Deploy Name**: The name of this Auto Deploy.
- **Deploy Description**: A description for this Auto Deploy.
- **Access Method**: The access method, either `Public` or `Private`.
- **Instance & Image**: The machine type and image to launch through Auto Deploy. You can choose a Snapshot you've configured yourself, or a system preset image.
![](../docs-images/autodeploy/02.png)

---
- **Port (HTTP/HTTPS)**: The port used for the external-facing service.
- **Start Command**: The command automatically executed when the instance starts.
- **Instance Idle Retention Period**: How long an instance launched via Auto Deploy can sit idle before being automatically released.
- **Maximum Number of Instances**: The maximum number of instances this Auto Deploy can open.
- Once configured, click `Confirm`.
![](../docs-images/autodeploy/03.png)

### **Confirming the Deployment**

1. Once you've finished filling out the form, click `Confirm`.
2. The system will begin deploying your Auto Deploy configuration. Once deployed successfully, the application status will show under the **Activated** list, meaning your Auto Deploy configuration is standing by, ready for you to call.
4. **Instance Status**: `Standby` means this Auto Deploy is waiting for you to call it; `Running` means an instance has currently been started through this Auto Deploy.
![](../docs-images/autodeploy/04.png)
![](../docs-images/autodeploy/05.png)



---

## **Auto Deploy Status**

### **Auto Deploy Basic Information**

On the **Auto Deploy** page, you can see two deployment statuses:

1. **Activated**: The Auto Deploy is enabled and standing by.
2. **Suspended**: The Auto Deploy service is paused and not running.
![](../docs-images/autodeploy/06.png)

**Each deployment task list includes the following fields**:

- **ID**: The unique identifier for each deployment task.
- **Name**: The deployment task name.
- **Status**: The current deployment status (Activated, Suspended).
- **Instance Status**: The current running status of the instance (e.g., Standby, Running).
- **Cost**: The resource cost consumed by this deployment.
- **Last Running Time**: The time it was last run.
- **Action**: The operations available for the deployment (see below for details).
![](../docs-images/autodeploy/07.png)
---

### **Auto Deploy Details**

**Click the arrow on the right to show more details**:

1. **ID / Auto Deploy Name / Auto Deploy Description**: Basic information about this deployment — the name and description entered when it was created.
2. **Instance Preview**: A preview of the machine type and image configured for this deployment, including the Image, GPU/CPU specs, RAM, Storage, etc. — the same as configured at creation time.
3. **Service & Start Command**:
    - **Access Method**: The access method for this Auto Deploy.
    - **URL**: The URL used to access this service — the actual endpoint used to connect to or call the service.
    - **Port**: The service port corresponding to the URL.
    - **Start Command**: The command automatically executed when the Auto Deploy instance starts (if configured).
4. **Deployment Control**: Deployment control settings such as the idle release time and maximum number of instances — the same as configured at creation time.
![](../docs-images/autodeploy/08.png)


---

## **Available Auto Deploy Actions**

The **Action** column provides the following operations:

### **1. Edit**

- **Function**: Edit the deployment configuration.
- **Use case**: Use this when you need to change the deployment name, environment variables, or other settings.

### **2. Suspend**

- **Function**: Suspend the deployment, stopping the application from running.
- **Use case**: When you no longer need the application running, you can suspend the deployment to save on resource costs.

### **3. Deploy**

- **Function**: Start or redeploy the application.
- **Use case**: Start an instance through a configured Auto Deploy — this is equivalent to using the URL provided by Auto Deploy (see the `Glows.ai Auto Deploy Usage` chapter in the user tutorial for URL details).
![](../docs-images/autodeploy/09.png)


### **4. Delete**

- **Function**: Delete the deployment task.
- **Use case**: When you no longer need this Auto Deploy, you can delete the deployment task. **This cannot be undone once deleted.**

### **5. Resume**

- **Function**: Resume a suspended Auto Deploy configuration.
- **Use case**: When an Auto Deploy configuration is in the Suspended state and you need to restart it, use this action to return it to the Activated state, after which you can click `Deploy` to deploy an instance.
![](../docs-images/autodeploy/10.png)


### **6. Release**

- **Function**: Release an instance launched via Auto Deploy, changing it to the Released state.
- **Use case**: When you no longer need a deployed instance, click `Release` to free up resources and stop billing.
![](../docs-images/autodeploy/11.png)


---

## **Basic Usage of Auto Deploy**

1. On the Auto Deploy page, copy the service URL of the Auto Deploy you want to use — this URL is the fixed entry point that triggers the service.
![](../docs-images/autodeploy/12.png)

2. Open this URL in a browser, or send a request to it using curl.
![](../docs-images/autodeploy/13.png)

3. Once the request has been processed, go back to the My Instances page to see that a machine has been successfully triggered and started via Auto Deploy.
![](../docs-images/autodeploy/14.png)

4. If you set an Instance Idle Retention Period when creating this Auto Deploy, the instance will be automatically released once it has been idle without receiving requests for longer than that period, with no manual action needed.
![](../docs-images/autodeploy/15.png)

---

## **Notes**

- **Deleting an application is irreversible**: Once an application is deleted, it cannot be recovered.

- **Suspending saves resources**: If you want to temporarily disable an Auto Deploy configuration, choose `Suspend`.

- **Confirm your settings before deploying**: Make sure your settings are correct to avoid deployment errors.

---

**This is a complete guide to Auto Deploy. For more detailed steps and use cases, please refer to [Glows.ai Auto Deploy Usage](https://docs.glows.ai/docs/auto-deploy-usage).**
