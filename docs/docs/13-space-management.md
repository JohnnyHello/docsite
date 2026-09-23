---
id: space-management
sidebar_position: 13
---

# Space Management

On the **Space Management** page, you have full control over your storage resources, allowing for flexible plan adjustments and space allocation to ensure optimal resource utilization. Below is an introduction and operation guide for these features:

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

## **Space Storage**

At the top of the page, the **Space Storage** bar shows your current usage clearly. Your total **Storage Space** can be allocated across three uses: **Snapshot**, **Datadrive**, and **Image**.

For example:

- **Using 17.1GB of 50GB**
- **Expires on 2026-09-28**

The bar shows how much space your **Snapshot**, **Datadrive**, and **Image** usage adds up to — in this case, 17.1GB.
  ![Space storage](../docs-images/p10/01.png)

## **Quota**

Below the main dashboard, you can see the individual storage usage for **Snapshot**, **Datadrive**, and **Image**.

For example:

- **Image**: **Using 3.79 GB of 20 GB**.
- **Snapshot**: **Using 13.30 GB of 18 GB**.
- **Datadrive**: **Using 0 GB of 4 GB**.
![Space storage](../docs-images/p10/02.png)


### **Subscribing to a Storage Plan**

Click the `Upgrade` button to enter the **Select Storage Plan** page.
 ![Space storage](../docs-images/p10/03.png)

You can choose from different capacity plans, each corresponding to a required amount of **Credit**, and all plans are valid for **30 Days**. After selecting a plan, a **Summary** will be displayed below, including:
- **Storage**: The size of the selected storage plan.
- **Expire**: The expiration date of the plan.
- **Total Price**: The total price.
![Space storage](../docs-images/p10/04.png)

## **Changing Your Subscription Plan**

For example, if your currently subscribed plan is `50GB`, you can change plans during your subscription period, such as: `subscribing to a plan smaller than 50GB`, `resubscribing to the 50GB plan`, or `subscribing to a plan larger than 50GB`.
1. **Downgrading a plan**: The expiration date stays the same, and no refund is issued for the price difference. Note that before downgrading, your used **Storage Space** must be smaller than the capacity of the downgrade option, or you won't be able to select it. Please clear out any data you no longer need before downgrading.
2. **Choosing a plan of the same size**: This extends the same plan by another **30 Days**. You'll be charged the full subscription price again.
3. **Upgrading a plan**: The expiration date stays the same after upgrading. Billing method: the price difference between the current and new plan, multiplied by the number of days remaining in the plan.
![Space storage](../docs-images/p10/05.png)

## **Modify**

Click the `Modify` button to freely adjust how much storage space is available to **Snapshot**, **Datadrive**, and **Image**.
![Modify](../docs-images/p10/06.png)

After clicking `Modify`, you'll see the individual storage usage for **Snapshot**, **Datadrive**, and **Image** on the page.
- You can freely allocate how much space each of **Snapshot**, **Datadrive**, and **Image** can use.
- **Datadrive** requires further allocation across its different regions, such as how much space is available for each region like **TW-03**, **TW-04**, etc.
- Any space not used by **Snapshot** and **Datadrive** will be allocated to **Image**.
![Quota list](../docs-images/p10/07.png)
