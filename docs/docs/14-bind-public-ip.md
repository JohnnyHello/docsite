---
id: bind-public-ip
sidebar_position: 14
---

# Bind Public IP

**Bind Public IP** is a public IP management feature provided by **Glows.ai** that lets you create a standalone **Public IP** resource and bind it to a specific instance, allowing that instance to serve external requests or be accessed from outside. You can also use **IP ACL** rules to further control the inbound and outbound traffic of this **Public IP**, ensuring only authorized sources and ports can access your service.

This guide covers, in order:
1. How to create a **Public IP**
2. How to bind a **Public IP** to an instance
3. How to configure **IP ACL** rules to control access

---

## Creating a Public IP

First, click `Network Endpoint` in the left sidebar, then click `Create New` to start creating a **Public IP**.
![](../docs-images/bind-public-ip/01.png)

After choosing the **Region** and **IP Bandwidth Type**, click `Create` to create the **Public IP**.

Note that the **Public IP**'s Region must match the Region of the instance you plan to bind it to later, so please double-check before selecting.
![](../docs-images/bind-public-ip/02.png)

Once created, the **Public IP** will appear in the list, indicating it's ready and available to bind when creating an instance.
Note that a **Public IP** is a dedicated resource — once created, it will keep consuming Credit even if it isn't attached to an instance, so please confirm your needs before creating one.

Each **Public IP** in the list includes the following fields:
- **ID**: The unique identifier of each **Public IP**.
- **Address**: The **Public IP** address.
- **Region**: The region it's located in (e.g., TW-03).
- **Bandwidth**: The bandwidth type (e.g., Shared, Custom).
- **Status**: The status (e.g., Available).
- **Cost**: The Credit this **Public IP** has consumed so far.
- **Action**: The operations available for this **Public IP**.
![](../docs-images/bind-public-ip/03.png)

---

## Binding a Public IP

Once created, you can bind it when creating an instance.
Note that when creating the instance, choose the same Region as the **Public IP** you want to bind.
![](../docs-images/bind-public-ip/04.png)

When creating the instance, click `Bind` next to **Public IP Address** below the menu.
![](../docs-images/bind-public-ip/05.png)

In the popup, choose the **Public IP** you want to bind, select the `Protocol`, fill in the `Port`, then click `Bind` to complete the binding.
If you've created multiple **Public IPs**, the ones in the same Region as the instance will appear in this list for you to choose from.
![](../docs-images/bind-public-ip/06.png)

Once bound successfully, the **Public IP**'s information will be displayed. After confirming everything is correct, you can create the instance with the **Public IP** bound.
![](../docs-images/bind-public-ip/07.png)

After creating the instance, you can see the IP address successfully bound to it in the instance list.
![](../docs-images/bind-public-ip/08.png)

---

## IP ACL Configuration

Every **Public IP** can have **ACL** rules bound to it, used to control external access permissions and the direction of network traffic for that IP.

### Creating an L3 Rule

1. Click `Network Endpoint`, then select the **Public IP** you want to configure.
2. Click `IP ACL`.
3. Click `Add ACL Resource`.
![](../docs-images/bind-public-ip/09.png)

After clicking `Add ACL Resource`, an **IP ACL** will be created — click `Manage Rules` to begin configuring it.
![](../docs-images/bind-public-ip/10.png)

#### L3 Rule Explanation and Default Rule

After clicking `Manage Rules` in the previous step, you'll see a default set of L3 rules with the IP `0.0.0.0/0`.

This page shows a list of all current **ACL** rules for this **Public IP**. **ACL** rules are split into two directions:
  > **Inbound**: Controls which external sources can access this IP, restricting the range of sources allowed to connect to this service.

  > **Outbound**: Defines the range of destination IPs this IP is allowed to connect to, controlling the range of outbound connections this service can make.

The ACL rule fields are as follows:
- **Remote CIDR**: The source or destination IP range, expressed in **CIDR** format (e.g., `0.0.0.0/0` represents all IPs).
- **Direction**: The direction of this rule, either `Inbound` or `Outbound`.
- **Default Policy**: The action applied to the **Remote CIDR** — `Deny` to reject, `Allow` to permit.
- **Status**: Whether the rule is in effect (e.g., `Pending` means not yet applied, `Applied` means it's active).
- **Description**: A description written by the user for this **ACL**.
- **Created Time**: When this **ACL** rule was created.
- **Action**: The operations available for this **ACL**.
![](../docs-images/bind-public-ip/11.png)

By default, the system creates one `Inbound` rule: **Remote CIDR** `0.0.0.0/0` (representing all source IPs), with a **Default Policy** of `Deny`, meaning all external sources are denied access to this IP by default.

#### Adding an L3 Rule

Besides the default `0.0.0.0/0` rule, you can also add additional IPs to your L3 rules.
Click `Add Rule` to start adding one.
![](../docs-images/bind-public-ip/12.png)

- **Rule Direction**: The direction of this rule, either `Inbound` or `Outbound`.
- **Action**: `Allow` permits this IP, `Deny` blocks it.
- **Source IP Address**: The IP address the rule should apply to.
- **Description**: A description for this rule.
- Once configured, click `Create L3 Rule` to add the rule.
![](../docs-images/bind-public-ip/13.png)

Once created, you'll see the new L3 rule.
![](../docs-images/bind-public-ip/14.png)

### Creating an L4 Rule

To allow access from a specific source, click `New L4 Rule` to add an exception rule.
![](../docs-images/bind-public-ip/15.png)

Configuring the **L4 Rule**:
1. The system will indicate that the **L4** rule you're setting up belongs under the L3 rule `0.0.0.0/0`, so its **L4 Policy** can only be set to `Allow`. In this case, since the `Default Policy` is `Deny`, the IP address `0.0.0.0/0` denies access from all IPs, so we need an L4 rule to whitelist the connections we want to allow.
2. **Destination Port**: Enter the destination port range you want to open, e.g., 8000 to 8888. If you only need to open a single port, enter the same value in both fields, e.g., `8000` to `8000`.
3. Once you've confirmed the port range is correct, click `Add` to add this setting to the rule list.
4. Click `Create L4 Rule` to finish creating the rule.
![](../docs-images/bind-public-ip/16.png)

Once the **L4 Rule** has been created, it will appear as an exception rule under the L3 rule `0.0.0.0/0`. This rule's Policy will be `Allow`, meaning that while all connections are denied by default (the L3 Deny rule), connections on ports 8000 to 8888 are allowed.

Information shown in the L4 Rule list:
- **Policy**: The action for this **L4** rule — since it belongs to an L3 rule with `Deny`, it can only be `Allow`.
- **Protocol**: The protocol this rule applies to (e.g., Custom TCP).
- **Port Range**: The destination port range this rule opens, e.g., 8000-8888.
- **Description**: A description written by the user for this **L4** rule.
- **Created Time**: When this **L4** rule was created.
- **Action**: The operations available for this rule, such as Edit.
![](../docs-images/bind-public-ip/17.png)

---

## Multiple Instances Bound to the Same Public IP

Each instance that was bound to this **Public IP** at creation time will appear in the list below.
![](../docs-images/bind-public-ip/18.png)

---

## Contact Us

If you have any questions or suggestions while using **Glows.ai**, please reach out via email, Discord, or Line.

**Email:** [support@glows.ai](mailto:support@glows.ai)

**Discord:** [https://discord.com/invite/glowsai](https://discord.com/invite/glowsai)

**Line:** [https://lin.ee/fHcoDgG](https://lin.ee/fHcoDgG)
