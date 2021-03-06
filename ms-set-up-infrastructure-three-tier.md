---

copyright:
  years: 2017, 2020
lastupdated: "2020-05-05"

keywords: SAP NetWeaver, bring your own license, BYOL, VLAN, application server, database server, three-tier, SAP certified servers

subcollection: sap-netweaver-ms-qrg

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 1. Ordering  192 GB and 32 GB servers for a three-tier setup
{: #install_three_tier}

Follow the steps in [Ordering your 32 GB server](/docs/sap-netweaver-ms-qrg?topic=sap-netweaver-ms-qrg-install_32GB) to order the SAP NetWeaver application server. The following steps guide you through ordering the database server. External storage is provisioned in a later step as backup space for the database for both archived log files and online full backups.

## Ordering your database server
{: #order_db_servers}

Use the following steps to order an SAP-certified server as your database server.

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com){: external} with your unique credentials.
2. Click **Create resource** > **Compute** > **Infrastructure** > **Bare Metal Server**.
3. Click **Continue**. If you can't click **Continue**, you don't have the correct permissions to create a server. Check with your system administrator about your permissions.
4. Leave **1** in the **Quantity** field.
5. Enter `sdb192` in the **Hostname** field. Hostname is a permanent or temporary name for your servers. Click **Information** for formatting specifics.
6. Enter `mycloud.com` in the **Domain** field. Domain is the identification string that defines administrative control within the internet. Click **Information** for formatting specifics.
7. **Billing** defaults to **Monthly**. At this time, 1-year contract and 3-year contract are not available for SAP-certified servers.
8. The data centers displayed under **Location** depend on product availability within a particular data center. Leave the default Location of **NA South DAL10-Dallas**.
9. Click **All servers** > **SAP certified**.

## Configuring your database server
{: #configure_server-192GB}

Use the following steps to configure your database server and its OS.

1. Select **CPU Model BI.S3.NW192 (OS Options)**. For information on how to decipher the server names, see [Provisioning your {{site.data.keyword.baremetal_short}} using the {{site.data.keyword.cloud_notm}} console](/docs/sap-netweaver?topic=sap-netweaver-set_up_infrastructure#order-server).
2. **RAM** defaults to a predefined value based on your server selection and cannot be changed.
3. Enter an optional public key for your **SSH key**, which you can use to log in to your server after it's provisioned. The default is **None**.
4. Choose **Microsoft** as your **Image** (OS), and select **2016 Standard (64 bit)-HVM**.

  If you're bringing your own license (BYOL) for your OS, select **No OS**. For more information, see [Bring your own license](#byol-192GB).
  {: note}

## Adding storage disks
{: #adding-storage-disks-192GB}

Use the following steps to add a 2 TB SATA drive for your database server.

1. For **Disk 1**, click the Menu icon ![Menu icon](../../icons/action-menu-icon.svg) > **Advanced configuration** and verify that **Primary disk partition** is set to the default of **Windows Basic**. Click **OK**.
2. Click **Add new**.
3. **Disks**, **Hot Spare**, and **Disk Media** have default values. Select a **Disk Size** that covers the total amount of storage you need.

## Setting up the network interface
{: #network-options-192GB}

Use the following steps to set up the network interface for your database server.

1. Select **1 Gbps Redundant Public and Private Network Uplinks** for **Uplink Port Speed**.
2. Select the values in Table 1 for the following fields:

  Make sure the network interface values for your database server match those of your application server.
  {: note}

|              Field               |      Value              |
| -------------------------------- | ------------------------|
| Private VLAN                     | `dal10.bcr01a.981`      |
| Public VLAN                      | `dal10.fcr01a.926`      |
| Private Subnet                   | `10.177.119.192/26`     |
| Public Subnet                    | `169.46.15.96/27`       |
{: caption="Table 1. 192 GB network interface values" caption-side="top"}  

3. Leave the default values for all other fields.                  
4. Review your Order Summary.
5. Select **I read and agree to the following Third-Party Service Agreements**.

  You can create your server, save the order as a quote to provision at a later time, or add the order an estimate, which may include multiple services.
  {: note}

6. Click **Create** to be redirected to the Checkout page after your order has been verified.

You are redirected to a page with your order number. You can print the page, because it's your receipt. In addition, you receive a confirmation email with the subject *Your IBM Cloud Order ## has been approved* with ## being your order number.

After the order is submitted, the server, depending on your order, is available for use within one to four hours. You can check Device Details from the {{site.data.keyword.cloud_notm}} console (Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > Resource List > Devices) for a status of the provisioning steps. Click the **Device Name** that matches your given Hostname and Domain to see its status.

## Bring your own license
{: #byol-192GB}

When you have your own operating system license, you install it on your {{site.data.keyword.baremetal_short}} based on the vendor's instructions. For more information, see [The no OS option](/docs/bare-metal?topic=bare-metal-bm-no-os#bm-no-os).

## Next Steps
{: #three-tier-set-up-next-steps}

[2. Preparing your server for your SAP installation](/docs/sap-netweaver-ms-qrg?topic=sap-netweaver-ms-qrg-prepare_256GB)

[3. Partitioning and filesystems](/docs/sap-netweaver-ms-qrg?topic=sap-netweaver-ms-qrg-3-partitioning-and-file-systems)

[4. Preparing your network](/docs/sap-netweaver-ms-qrg?topic=sap-netweaver-ms-qrg-network)
