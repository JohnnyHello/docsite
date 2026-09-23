---
id: my-instance
sidebar_position: 4
---

# My Instance

On the **My Instance** page, you can view and manage the status and configuration of all your instances. Below is a detailed feature introduction:

---

## **Instance Status**

On the **My Instance** page, you can see four instance statuses:

1. **Pending**: The instance is starting up.
1. **Running**: The instance is running, and you can access or manage it. ⚠️ **Billing only occurs while the instance is in this state**, so please manage your usage time accordingly.
2. **Suspending**: The instance is performing a Take Snapshot operation and other management operations are temporarily unavailable. **No additional billing occurs** in this state.
3. **Terminated**: The instance has been released and its resources reclaimed. An instance in this state cannot be started again, and **no further billing occurs**.
![](../docs-images/p04/01.png)
![](../docs-images/p04/02.png)
![](../docs-images/p04/03.png)
![](../docs-images/p04/04.png)




**Each status has an instance list with the following fields**:

- **ID**: The unique identifier of each instance.
- **Name**: The instance name, for easy identification.
- **Region**: The region where the instance is located (e.g., TW-03, TW-04).
- **Status**: The current status of the instance (e.g., Running, Pending).
- **Billing Method**: The billing method. Currently available as pay-as-you-go or subscription.
- **Cost**: The total cost accumulated by the instance so far.
- **Action**: The operations available for the instance (see below for details).

![](../docs-images/p04/05.png)


## **Tabs**

Click a row in the instance list to view the corresponding instance and manage the following tabs:

### **1. Access**

Retrieve and configure the access methods for connecting to the instance.

![](../docs-images/p04/06.png)

- **SSH Port 22**

  - View the information needed for an SSH connection:
    - **SSH Command**: `ssh -p <Service Port> root@<Access URL>`
    - **Service Port**: The service port of the instance.
    - **User**: The default username is `root`.
    - **Password**: The initial password (displayed encrypted).
    - **SSH Key**: You can use a key instead of a password to log in. Go to `Profile` in the left sidebar and click `SSH keys` to set it up.
    ![](../docs-images/p04/07.png)

- **HTTP Port 8888**
  This port has JupyterLab deployed by default. Click Open to access the instance directly.

  - Available operations:
    - **Open**: Open the link in a new tab.
    - **Copy**: Copy the HTTP address.
    ![](../docs-images/p04/08.png)

- **New Port Forwarding**: Click this button to add a new port forwarding rule.
  ![](../docs-images/p04/09.png)
  Fill in the following information:
  - **Service Port**: Set the service port.
  - **Protocol**: Choose the protocol type for the service; TCP is the default. If you are forwarding a web-based service (such as JupyterLab or a dashboard), check `HTTPS` to enable encrypted access and ensure the security of your browser connection.
  ![](../docs-images/p04/10.png)

### **2. Monitor**

View the instance's performance and resource usage in real time.

   - **CPU Usage**: The instance's current CPU usage.
    - **Memory Usage**: Current memory usage / total allocated memory capacity.
    - **Disk Usage**: Current disk usage / total allocated storage capacity.
![](../docs-images/p04/11.png)

### **3. Billing**

Shows all billing details related to the instance.

   - **Start Time**: The time the instance was started.
    - **End Time**: The time the instance ended (shows the current status, such as `Running`, if it is still running).
    - **Price/Hour**: The hourly billing rate for the instance.
    - **Cost**: The total cost accumulated so far.
    - **Duration**: How long the instance has been running.
    - **Billing Method**: The billing method, either `Pay-as-you-go` or subscription.
    - **Discount**: The discount currently applied.
![](../docs-images/p04/12.png)

### **4. Config**

View the instance's configuration, such as image-related parameter settings.

   - **Image**: The name of the image used by the instance.
    - **Image Description**: Detailed information about the image, including required hardware resources, operating system, and pre-installed package versions.
    - **Ports**: The service ports exposed by default in the image.
![](../docs-images/p04/13.png)

### **5. Datadrive**

View the instance's configuration, such as image-related parameter settings.

   - **Mount Path**: The path where the Datadrive is mounted inside the instance.
   - **Permissions**: The read/write permissions for the Datadrive.
![](../docs-images/p04/14.png)

### **6. Hardware**

Check the instance's hardware configuration, including GPU or CPU model, memory, storage, and more.

   - **GPU Model**: The GPU model configured for the instance.
    - **GPUs**: The number of GPUs allocated.
    - **GPU RAM**: The video memory capacity of a single GPU.
    - **CPU Model**: The CPU model configured for the instance.
    - **vCPUs**: The number of virtual CPU cores allocated.
    - **RAM**: The system memory capacity.
    - **Storage**: The disk storage capacity.
![](../docs-images/p04/15.png)

### **7. Network Group**

View the instance's cluster network information. Glows.ai supports multi-node, multi-GPU operation — you can add multiple instances to the same cluster in Mesh so that instances within the cluster can communicate with each other via internal IPs, enabling more efficient computing collaboration.

![](../docs-images/p04/16.png)

---

## **Actions Available While an Instance Is Running**

The Action column has two buttons: `Take Snapshot` and `Release`.

### **1. Take Snapshot**

- **Function**: Creates a snapshot of the current instance, saving all state and file changes in the instance except `/datadrive`, including installed packages, system settings, and modifications in other directories.
- **Use cases**:
  - You've made extensive custom configurations to the instance environment (such as installing Python packages or Ubuntu software) and want to save the current state so you can quickly reproduce it later.
  - As a base template for creating new instances in the future, avoiding repeated configuration.

#### **Detailed Take Snapshot Workflow**

1. **Click the `Take Snapshot` button in the Action column to open the snapshot creation window.**

   ![](../docs-images/p04/17.png)

2. **Fill in the snapshot information**:

   - **Name**: Enter a name for the snapshot.
   - **The instance will be automatically released after the process is completed**:
      If checked, the instance will be automatically released once the snapshot is complete;
     if unchecked, the instance will automatically return to the Running state once the snapshot is complete, and you can continue using it.
        ![](../docs-images/p04/18.jpg)


3. **View the snapshot progress**:

   - While the snapshot is being saved, the instance will move from the `Running` tab to the `Snapshotting` tab:

      ![](../docs-images/p04/19.png)

4. **Effects once complete**:

   - While the snapshot is being saved, the instance will be paused, and it will automatically resume running or be released once the snapshot is complete (depending on whether auto-release is checked).
      ![](../docs-images/p04/20.png)


#### **Notes**

- The instance will be temporarily unavailable during the save process, and can only be used again once the connection automatically resumes.
- Saving a snapshot requires sufficient personal storage space, so please confirm this in advance.

---

### **2. Release**

- **Function**: Releases the instance's resources and changes the instance to the **Released** state.
- **Use case**: When you no longer need an instance, you can release it to reclaim resources and stop billing.

#### **Detailed Release Workflow**

1. **Click the `Release` button in the Action column** to open a confirmation window.

   ![](../docs-images/p04/21.png)

2. **Confirm the release**:

   ![](../docs-images/p04/22.jpg)
   - The system will show relevant notices, such as data deletion and irreversibility.
   - Click `Stop & Release` to confirm the release.

3. **Status update during the release process**:

   - The released instance will appear in the `Released` area. Its status will change to **Terminated**.
   ![](../docs-images/p04/23.png)


4. **How to start a new instance from a Snapshot:**

   - When creating an instance, select the Snapshot and start the instance.
   ![](../docs-images/p04/24.png)


   - Once the instance snapshot has been created: if you did not check the option to release the instance after saving, you can find the instance under Running in the My Instance interface; otherwise, the instance will continue running after the snapshot finishes.
   ![](../docs-images/p04/25.png)

#### **Note**: The instance cannot be accessed while a snapshot is being created, and any running processes inside the instance will be interrupted. It is generally recommended to take a snapshot before releasing a machine once you are done using it.

---

## **Summary of Notes**

1. **Snapshotting and Released Restrictions**:

   - In these two states, only the **Config** and **Hardware** tabs can be viewed; no other operations are available.

2. **Recommendations for Release and Snapshots**:

   - Before choosing to release an instance, be sure to confirm whether you need to keep the current data.
   - Creating snapshots regularly can help preserve important data.

3. **Impact of Operations**:

   - Certain operations (such as taking a snapshot or releasing an instance) may interrupt normal use of the instance, so please plan accordingly.

This is a complete guide to instance management. For more detailed information, please refer to the following sections.
