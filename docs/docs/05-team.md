---
id: team
sidebar_position: 5
---

# Glows.ai Team Edition Tutorial

Glows.ai's Team Edition builds a team collaboration system with centralized resource management, flexible quota allocation, and a secure sharing mechanism, meeting the cloud resource sharing needs of enterprise-level users.

This tutorial is divided into three parts:

- [Owner Tutorial](#owner-tutorial)
- [Admin Tutorial](#admin-tutorial)
- [Member Tutorial](#member-tutorial)

------

## Owner Tutorial

### Creating a Team

After logging into the Glows.ai platform, click your profile info in the top-right corner, click `Teams` in the popup, and then click `Create Teams` to enter the team creation process.

![Create Team Menu](../docs-images/p05team/01.png)

There are currently three plans: Free, Basic, and Premium. Choose the plan that best fits your team's project needs. If you have more advanced requirements, click `Contact us` to get in touch about custom development.

![Select Team Plan](../docs-images/p05team/02.png)

After choosing a team plan type, you can continue setting the team name and description.

![Set Team Name](../docs-images/p05team/03.png)

Choose the plan duration to purchase — you can manually renew later — then click `Next`.

![Choose Plan Duration](../docs-images/p05team/04.png)


Once you've confirmed the information is correct, click `Create Team` to finish creating the team.

![Confirm Team Creation](../docs-images/p05team/05.png)


Once created, you'll see the team's basic information, and you'll become the team's **Owner**. This identity is automatically bound to your personal account, so you can access the team page from your personal account in the future.

Click `Enter Team` to go directly to the team page.

![Team Created](../docs-images/p05team/06.png)


### Switching to the Team Interface

You can switch to the Team Edition directly from your Glows.ai personal account page. As shown, click your profile info in the top-right corner, click `Teams` in the popup, and then click the team you want to enter.

![Switch To Team](../docs-images/p05team/07.png)


### Member Management

After logging in as the owner or an admin, click the `Member` tab in the left sidebar to manage members. Currently supported: **adding members**, **assigning credits**, **reclaiming member credits**, **resource visibility control**, **editing member basic information**, **member instance management**, and more.

#### Adding a Member

Click the `Add Members` button on the `Member` page to start adding a member.

![Add Team Member](../docs-images/p05team/08.png)


You can set the new member's **login account**, **login password**, **role**, **initial credit allocation (Assign Credit)**, **alias**, and **note**. Once done, click the `Add Member` button on the page to finish creating the member.

The **Role** currently supports **Admin** or **Member**.

**Assign Credits** sets the initial number of credits a member receives upon joining the team, which can be used to rent machines or purchase a **Storage Space** plan. Credits can also be assigned after the member is created.

![New Member Form](../docs-images/p05team/09.png)


Once created, click `Copy Login Details` to get the new member's information, then send it to them. For how new members log in, see [Joining a Team](#joining-a-team).

![Copy Login Details](../docs-images/p05team/10.png)


#### Recharging Credits

Any credits used by team members must first be recharged into the team by the **Owner**, then assigned to members.
On the Team Edition page, the **Owner** first clicks the **Credits info** in the top right, then clicks `Recharge` to start recharging.

![Recharge Credits](../docs-images/p05team/11.png)

In addition to supporting the same credit recharge methods as the personal edition, in the Team Edition the **Owner** can also recharge credits from their personal account into the team account.

Select or enter the **credit amount**, choose `USD`, then select `Glows.ai Balance` and click `Recharge` to complete the recharge.
![Recharge From Balance](../docs-images/p05team/12.png)


#### Assigning Credits

On the `Member` page, click the Action button next to a member and select `Assign Credits` to open the assign credits page.

![Assign Credits](../docs-images/p05team/13.png)


Enter the amount to assign and click `Assign` to complete the assignment.

![Confirm Assign Credits](../docs-images/p05team/14.png)

#### Reclaiming Credits

On the same page, select `Reclaim Credits` to reclaim a member's credits. The process is the same as assigning credits.

![Reclaim Credits](../docs-images/p05team/15.png)


#### Resource Visibility Control

In `Permissions & Quota`, you can set which GPUs, images, total available instances, and total storage space team members can see.

Click `Permissions & Quota` to open the permission settings page. First, you can control which machine resources are visible to team members, including: **Region**, **Type**, and **Accelerator**.

The example shown sets team members to only be able to use **GPU** type machines in the **TW-03** and **TW-04** regions, and only the **NVIDIA GeForce RTX 4090** spec.

![Machine Permissions](../docs-images/p05team/16.png)


Scroll down to continue setting which official base images members can use. The example shown restricts members to creating instances only with the **Gemma4 31B Q8** and **Qwen3.5-27B-Claude-4.6-Opus-Q8** images.

![Image Permissions](../docs-images/p05team/17.png)


Finally, you can also set team members' instance data, number of **Snapshots**, available **Storage Space**, and more.

![Resource Quota Settings](../docs-images/p05team/18.png)


Once done, click `Save` in the top right to save the settings. Going forward, the machines a team member can choose from when clicking `Create New` will be limited to the machine types and environments configured in `Permissions & Quota`.

![Save Permissions](../docs-images/p05team/19.png)



#### Editing Member Basic Information

On the `Member` page, click the `Details` button next to a member to open the member details panel.

![Member Details Panel](../docs-images/p05team/20.png)


Currently you can edit a member's **Name**, **Role** (e.g., **Admin** or **Member**), **Account Balance**, **Note**, and **Login Password**. The details panel also shows other usage information for the member, such as remaining credits, total spending, number of instances, and storage usage.

![Edit Member Info](../docs-images/p05team/21.png)


Click `Edit Permission` in the top right of this page to set the resource visibility for a single member, allowing different members to see different machine and image resources.

![Edit Permission](../docs-images/p05team/22.png)

Switch **Use Team Default Permission** from `On` to `Off` to configure it.

![Individual Permission](../docs-images/p05team/23.png)


#### Member Instance Management

Click `Admin View` on the `Instances` page to see the instance records and running status of all members.

![Admin View Instances](../docs-images/p05team/24.png)



Click `Action` on the instance row of the member instance you want to shut down, then click `Release` to release that member's instance directly.

![Release Instance](../docs-images/p05team/25.png)


### Storage Space Management

#### Subscribing to a Shared Team Storage Space Plan

On the `Storage Space` page, select `Admin View`, then click `Upgrade` to choose the plan you need, and click `Recharge` to complete the Storage Space purchase.

**Note**: When subscribing to a shared team Storage Space plan, follow the steps shown and click `Admin View` first. If you're in `Member View`, you'll instead be subscribing to a personal Storage Space plan within the team.

![Upgrade Storage Plan](../docs-images/p05team/26.png)


#### Allocating Shared Team Storage Space

On the `Storage Space` page, select `Admin View` to see the usage of the team's shared Storage Space, as well as each member's personal Storage Space usage within the team.

![Storage Usage Overview](../docs-images/p05team/27.png)


On the `Storage Space` page, after selecting `Admin View`, click `Manage` under **Team Storage Space**,

![Manage Team Storage](../docs-images/p05team/28.png)

then, on the shared team Storage Space allocation page, click `Modify` to set the **Datadrive** and **Snapshot** space quotas, and finally click `Update` to complete the allocation. The allocation process is the same as in the personal edition.

![Allocate Storage Quota](../docs-images/p05team/29.png)


### Shared Datadrive Management

Click `Datadrive` in the sidebar, then select `Admin View` on the page to see the usage of the team's shared Datadrive as well as each team member's personal Datadrive usage.

![Datadrive Usage Overview](../docs-images/p05team/30.png)


Click `Manage` under `Team Datadrive` to open the team Datadrive management page.

![Manage Team Datadrive](../docs-images/p05team/31.png)

Here you can see an overview of files in the shared Datadrive across different **regions**. Only the team's **Owner** and **Admins** have permission to upload and delete files in the shared team Datadrive; all members can **download** files.

![Datadrive File List](../docs-images/p05team/32.png)



When creating an instance, other members can choose to mount the shared team Datadrive, which appears at the path `/team_data` inside the instance. Regular members have read-only access, while the team owner and admins have read/write access.

![Mount Team Datadrive](../docs-images/p05team/33.png)


### Snapshot Management

On the `Snapshots` page, select `Admin View` to see snapshots created by the team as well as by each individual team member.

![Snapshots Overview](../docs-images/p05team/34.png)


#### Setting a Shared Team Snapshot

Click `Details` next to the snapshot you want to convert to a shared team snapshot, then select `Share to team` to turn a member-created snapshot into a shared team snapshot.

![Share Snapshot](../docs-images/p05team/35.png)


#### Using a Shared Team Snapshot

When other members create an instance and select a snapshot, they'll be able to see shared team snapshots, which are marked with a **Team** badge in the top right corner.

![Use Shared Snapshot](../docs-images/p05team/36.png)


#### Managing Team Snapshots

On the `Snapshots` page, after selecting `Admin View`, click `Manage` in the top right of the `Team Shared Snapshots` module to open the team snapshot management page.

![Manage Shared Snapshots](../docs-images/p05team/37.png)


Here you can see all team snapshots. Currently only deletion is supported — select the snapshot you no longer need and click `Delete` under `Action` to delete it.

**Note**: Once a team snapshot is deleted, it is permanently removed and cannot be recovered. Please proceed with caution.

![Delete Snapshot](../docs-images/p05team/38.png)


### Billing Management

On the `Billing` page, select `Admin View` to see billing data for all team members.

![Team Billing Overview](../docs-images/p05team/39.png)

Billing lookups support filtering by member and by billing type.

![Filter By Member](../docs-images/p05team/40.png)
![Filter By Type](../docs-images/p05team/41.png)






### Editing Team Information

On the `Team Setting` page, click `Edit` in the top right to edit the team's name and description.

![Edit Team Info](../docs-images/p05team/42.png)
![Team Info Saved](../docs-images/p05team/43.png)


## Admin Tutorial

Aside from not being able to create a team or recharge credits, admins have the same permissions as the team owner. Please refer to [the Owner Tutorial](#owner-tutorial).

## Member Tutorial

Regular members only have access to the following features: creating instances (Create New), instance management (Instances), Datadrive management (Datadrive), Snapshot management (Snapshots), Storage management (Storage Space), billing lookups (Billing), and editing personal information (Profile). These work the same as on the main Glows.ai site — see the [Glows.ai User Guide](https://docs.glows.ai/docs/create-new) for details.

![Member Feature List](../docs-images/p05team/44.png)

### Joining a Team

Once a regular member receives a member account created by the team owner or an admin, they can join the team through two entry points.

#### 1> Log in via the Team Edition link

Visit the team login page below in your browser and enter the team account credentials.

```bash
https://platform.glows.ai/team/login
```

![Team Login Page](../docs-images/p05team/45.png)



#### 2> Enter from the Glows.ai personal page

After logging into the main Glows.ai site, click your profile avatar in the top right and select **`Teams` -> `Join Team`**.

![Join Team Menu](../docs-images/p05team/46.png)

On the Join Team page, enter the team account credentials to bind your Glows.ai personal account to the team. After that, you can switch to the team page directly from your personal page without logging in with the team account credentials again.

![Join Team Form](../docs-images/p05team/47.png)



Regardless of which method you use to log in, you'll be required to reset your password the first time you log in.

![Reset Password](../docs-images/p05team/48.png)

### Getting Credits

If a team member needs credits, please request them from the team owner or an admin.

### Creating an Instance

Click `Create New` and choose the GPU and environment you want to rent.

![Create Instance](../docs-images/p05team/49.png)

Scroll down to see the instance configuration. Aside from **Mount Team Datadrive**, the rest of the settings are the same as in the personal edition. Once configured, click `Complete Checkout` to finish creating the instance.

- **Unit Qty**: The number of GPUs to rent. Setting this to 2 means renting 2 GPUs.
- **Mount Personal Datadrive**: Choose whether to mount your personal Datadrive.
- **Mount Team Datadrive**: Choose whether to mount the shared team Datadrive to the `/team_data` directory inside the instance. The team **Owner** and **Admins** have read/write access, while regular members only have read access.
- **Bind Public IP Address**: Bind a static IP.

![Instance Configuration](../docs-images/p05team/50.png)

Regular team members only have **read-only** access when mounting the Team Datadrive, while the team **Owner** and **Admins** have **read & write** access.

![Datadrive Read Only](../docs-images/p05team/51.png)


### Instance Management

Once an instance has started successfully, you can see the newly started instance on the Instances page. Click the instance to see more detailed information and additional actions.

- **Access:** Access information for the instance — the most commonly used are SSH (Port 22) and JupyterLab (Port 8888).
- **Monitor:** CPU and GPU resource monitoring for the instance.
- **Billing:** Billing details for the instance.
- **Config:** A description of the instance's configuration (details about the software in the instance's boot image).
- **Hardware:** A description of the instance's hardware configuration.

Once you're done using it, you can choose `Release` under `Action` to release the instance, or `Take Snapshot` to create a snapshot.

![Release Or Snapshot](../docs-images/p05team/52.png)

### Other Features

Personal **Storage Space** within the Team Edition, along with **Datadrive** management, **Snapshots** management, billing lookups (Billing), and editing personal information (Profile), all work the same as on the personal edition page. Please refer to the [Glows.ai User Guide](https://docs.glows.ai/docs/create-new) for details.

## Contact Us

If you have any questions or suggestions while using Glows.ai, feel free to reach out to us via email, Discord, or Line.

**Email:** [support@glows.ai](mailto:support@glows.ai)

**Discord:** [https://discord.com/invite/glowsai](https://discord.com/invite/glowsai)

**Line:** [https://lin.ee/fHcoDgG](https://lin.ee/fHcoDgG)
