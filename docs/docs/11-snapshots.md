---
id: snapshots
sidebar_position: 11
---

# Snapshots

A **Snapshot** is used to save the current environment configuration of an instance, such as installed packages and development environment settings. Once you've set up your development environment, you can create a Snapshot as a save point to back up the instance's current state, so that later, when creating an instance, you can use the Snapshot to quickly restore that state without having to set everything up again.

Below is a feature introduction and operation guide:

---

## **Notice of Snapshot and Image Billing Policy Update**

To provide users with a more flexible and efficient way to manage environments and data, the platform will update the quota and billing mechanism for Snapshot and Image services effective December 1, 2026, at 00:00 (UTC+8).
After the update, Storage package quotas will apply exclusively to Datadrive storage. Snapshot and Image resources will no longer consume Storage quotas and will instead be billed based on their actual storage usage with hourly billing.
The updated billing rules are as follows:
- Billing rate: 0.0001 credits/hour/GB
- Billing starts once a Snapshot or Image is successfully created
- Billing stops once the corresponding Snapshot or Image is deleted

This adjustment is designed to provide greater flexibility in resource management and allow users to optimize costs based on actual usage.

If you have any questions, please contact us here: [Click here to contact us](/docs/contact-us)


## Creating a Snapshot

  - While a machine is running, click the menu on the right of the machine and click `Take Snapshot` to start creating a Snapshot.
    > Note that the instance will be paused while the Snapshot is being created.

  ![](../docs-images/p08/01.png)


   1. **Name**: Enter a name for the Snapshot.
   2. **The instance will be automatically released after the process is completed**:
      If checked, the instance will be automatically released once the Snapshot is complete;
      if unchecked, the instance will automatically return to the Running state once the Snapshot is complete, and you can continue using it.
   3. Once filled in, click Take Snapshot to start creating it.
![](../docs-images/p08/02.png)


  - While saving, the instance will move from the `Running` tab to the `Snapshotting` tab, and the instance's status will change to `Suspending`.
![](../docs-images/p08/03.png)


   - Once the Snapshot has been created, the instance will either:
    1. Continue running.
    2. Be automatically released (if you checked **The instance will be automatically released after the process is completed** when clicking Take Snapshot).
  ![](../docs-images/p08/04.png)

---

## Using a Snapshot

  - When creating a machine, click the Snapshot tab to see your Snapshots, and you can create an instance from a Snapshot — the instance will be restored to the state it was in when the Snapshot was created.
    > **Note**: Snapshots can be used across regions — for example, a Snapshot created from an instance in `TW-03` can be used when creating an instance in another region (e.g., `TW-04`). Note: the first launch using a Snapshot across regions will be slower; subsequent launches will be faster due to caching.

![](../docs-images/p08/05.png)


---

## Snapshot List

On the main page, click Snapshot in the left-side menu to see a list of all your Snapshots.
![](../docs-images/p08/06.png)

---

### Snapshot Status

  1. The **Available** tab shows all available Snapshots, which you can view and manage.
  2. The **Restorable** tab shows Snapshots that have been deleted or are unavailable due to insufficient Storage Space; these Snapshots can still be restored within a certain period of time.
  ![](../docs-images/p08/07.png)

  ### Available
    **Snapshot information fields**:
    - **ID**: The unique identifier of the Snapshot.
    - **Name**: The Snapshot name, for easy identification.
    - **Size**: The storage space occupied by the Snapshot.
    - **Status**: The current status of the Snapshot (e.g., `Available`).
    - **Create Time**: The creation time of the Snapshot.
    - **Action**: The available action (`Delete` only).
      > Using `Delete` will move the Snapshot to the **Restorable** tab.

    ![](../docs-images/p08/08.png)
  ### Restorable
    **Snapshot information fields**:
    - **Same fields as the Available tab, except for Action**.
    - **Action**: The available actions (`Restore` or `Delete`).
      > Note: Using `Delete` on a Snapshot in Restorable will permanently delete it.

    ![](../docs-images/p08/09.png)

    **Restoring a Snapshot from Restorable**:

      Once restored, the Snapshot will move from `Restorable` to `Available`, becoming usable again.

    1. Click the `Restorable` tab.
    2. Click `Restore`.
    3. Restoring will consume one of your remaining `Snapshot restores left`.
          ![](../docs-images/p08/10.png)



---

## **Notes**

- **Deletion and Restoration**:
  After deleting a Snapshot, it will move to the **Restorable** tab, where you can choose to restore or permanently delete it.

- **Renaming**:
  You can rename a Snapshot at any time for easier management and identification.

- **Storage Management**:
  Regularly cleaning up unnecessary Snapshots can free up storage space and ensure effective resource utilization.

With these features, you can easily manage and protect your data, ensuring you can quickly restore to a specific state when needed.
