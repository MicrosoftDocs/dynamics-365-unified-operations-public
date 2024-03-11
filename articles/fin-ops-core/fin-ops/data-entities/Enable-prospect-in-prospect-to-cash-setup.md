---
title: Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales
description: This article describes how to enable setup and configure the latest enhancements in prospect-to-cash with Microsoft Dynamics 365 Sales.
author: henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: DataManagementWorkspace, CustParameters
ms.topic: how-to
ms.date: 03/15/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales

[!include [banner](../../../finance/includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management uses dual-write to integrate with Dynamics 365 Sales. In Supply Chain Management version 10.0.34 a number of enhancements were released providing a more seamless quotation process flow across the two systems. In Supply Chain Management version 10.0.39 or later, it is supported to use a prospect in the sales quotation process while a number of additional enhancements such as delivery date control support in quote revision and quote winning scenarioes are supported.

To take advantage of these improvements, you must enable the *Enable prospect in prospect-to-cash with Dynamics 365 Sales* feature in Supply Chain Management and make sure that you're using a qualifying version of the Dual-write Supply chain solution.

For a conceptual overview that describes how the improved prospect-to-cash system works and how the integrated system will behave, see [Enable-prospect-in-prospect-to-cash with Dynamics 365 Sales](Enable prospect-in-prospect-to-cash-concept.md). <!--KFM: Correct link to be added by Karl -->

## Prerequisites

Before you can use the feature that is described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.39 or later.
- You must be running [Dual-write Supply Chain solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwscm) version 2.3.4.XXX <!--KFM: Update when solution ID is provided by HenrikJ-->.

## Initial setup

To add **Enable prospect in prospect-to-cash with Dynamics 365 Sales** functionality to your system, you must install the required solution in your dual-write environment, enable mappings in Supply Chain Management, and turn on the feature that you want to use.

### Step 1: Add the Dual-write Supply Chain solution to your Power Platform environment

> [!IMPORTANT]
> Do not update your Dual-write Supply Chain solution, as described in this section, unless you are running Supply Chain Management version 10.0.34 or later. To fully benefit from this update and the other improvements that are described in this article, you must be running Supply Chain Management version 10.0.39 or later.

Follow these steps to add the Dual-write Supply Chain solution to your Power Platform environment.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. On the navigation pane, select **Environments**.
1. Open the environment that you want to integrate with Supply Chain Management.
1. On the **Resources** tile, select **Dynamics 365 apps**.
1. On the toolbar, select **Install app**.
1. In the **Install Dynamics 365 apps** dialog box, find the row where the **Name** field is set to *Dual-write Supply Chain solution*, and follow one of these steps:

    - If the **Status** field for the row indicates that the app isn't installed, or that an update is available, select the row, and then select **Next** to open an installation wizard. Follow the on-screen instructions to install the app.
    - If the **Status** field for the row indicates that the app is installed, enabled, and up to date, select **Cancel**.

1. On the **Dynamics 365 apps** page, find the row where the **Name** field is set to *Dual-write Supply Chain solution*. The **Status** field for the row should now indicate that this app is installed. 
1. Select the ellipsis button (**&hellip;**) for the row, and then select **Details** on the menu.
1. In the **Details** dialog box for the solution, confirm that the **Version** value fulfills the [prerequisites](#prerequisites) at the beginning of this article. Then close the dialog box.

### <a name="enable-mappings"></a>Step 2: Enable mappings in Supply Chain Management
Maps to enable depend on whether your Supply Chain Management version is 10.0.38 or older and on whether you have deployed the GAB dual-write solution.The following permutations exist and are described in the following: 
A. **Supply Chain Management version 10.0.39 or later with GAB dual-write solution**
B. **Supply Chain Management version 10.0.39 or later without GAB dual-write solution**
C. **Supply Chain Management version 10.0.38 or older irrespective of GAB dual-write solution**

Follow these common steps to enable the required mappings in Supply Chain Management.
1. Sign in to Supply Chain Management.
2. Go to **System administration \> Workspaces \> Data management**.
3. In the **Data management** workspace, select **Dual-write**.
4. On the **Dual-write** page, on the Action Pane, select **Apply solution**.
5. In the **Apply solution** dialog box, select the maps to apply. At a minimum, you must select the map where the **Display name** field is set to *Dynamics 365 Supply Chain Management extended entity maps*. However, we recommend that you select all the maps that are listed. When you've finished selecting maps, select **Apply**.

Proceed with the setup below that matches your environment.

#### Setup (With GAB solution – FnO version 10.0.39 or later) ####
For GAB dual-write solution see https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/party-gab

6.	Stop the following maps, since they are no longer required.

| Map | 
|---|
|Dynamics 365 Sales feature management states (msdyn_supplychainfeaturestates)|
|CDS sales order headers (salesorders)|
|CDS sales order lines (salesorderdetails)|
|CDS sales order lines V2 (salesorderdetails)|
|CDS sales quotation header (quotes)|
|CDS sales quotation lines (quotedetails)|

7. The following entity maps are updated for Gobal Address Book Party functionality, so the latest version must be applied to these maps and running.

| Map | Update to this version | Details |
|---|---|---|
|Dynamics 365 Sales feature parameters (msdyn_supplychainfeaturestates)|	1.0.0.0|<p>	New map for set up parameters for Dynamics 365 Sales integration<p>|
|Dynamics 365 Sales order headers (salesorders)| 1.0.2.1 | <p>New map with discount customer groups and delivery date control.</p> |
|Dynamics 365 Sales order lines (salesorderdetails)| 1.0.1.0 | <p>New map with delivery date control.</p> |
|Dynamics 365 Sales quotation header (quotes)| 1.0.4.1	 | <p>New map for quotation revision feature with ownership change capability, prospect integration, discount customer groups and delivery date control.</p> |
|Dynamics 365 Sales quotation lines (quotedetails)| 1.0.0.0 | <p>Existing map for quotation lines.</p> |
|Dynamics 365 Sales prospects (accounts)|	1.0.0.1	| <p>New map for prospects of type organization.</p> |
|Dynamics 365 Sales prospects (contacts)|	1.0.0.1	| <p>New map for prospects of type person.</p> |
|CDS Contacts V2 (contacts)|	1.0.0.0	| <p>New map for prospect contact persons.</p> |
|Customers V3 (accounts)|	1.0.1.5	| <p>New map for setting relationship type when Dynamics 365 Sales prospects map is running. Removed PartyNumber and other party-related fields like name, personal details, postal address fields, and electronic contact address.</p> |
|Customers V3 (contacts)|	1.0.1.5	| <p>New map for setting relationship type when Dynamics 365 Sales prospects map is running. Removed PartyNumber and other party-related fields like name, personal details, postal address fields, and electronic contact address.</p> |
|Total discount customer groups| 1.0.0.0|<p>New map for Total discount customer groups.</p> | 
|Line discount customer groups| 1.0.0.0|<p>New map for Line discount customer groups.</p> | 
|Multiline discount customer groups| 1.0.0.0|<p>New map for Multiline discount customer groups.</p> | 

On the **Dual-write** page, make sure that all the above maps in the table show a **Status** value of *Running*. If any of them show a **Status** value of *Not running*, select them, and then select **Run** on the Action Pane.

#### Setup (Without GAB solution – FnO version 10.0.39 or later) ####
6.	Stop the following maps, since they are no longer required.

| Map | 
|---|
|Dynamics 365 Sales feature management states (msdyn_supplychainfeaturestates)|
|CDS sales order headers (salesorders)|
|CDS sales order lines (salesorderdetails)|
|CDS sales order lines V2 (salesorderdetails)|
|CDS sales quotation header (quotes)|
|CDS sales quotation lines (quotedetails)|

7. The following entity maps are updated, so the latest version must be applied to these maps and be running.

| Map | Update to this version | Details |
|---|---|---|
|Dynamics 365 Sales feature parameters (msdyn_supplychainfeaturestates)|	1.0.0.0|<p>	New map for set up parameters for Dynamics 365 Sales integration<p>|
|Dynamics 365 Sales order headers (salesorders)| 1.0.2.0 | <p>New map with discount customer groups and delivery date control.</p> |
|Dynamics 365 Sales order lines (salesorderdetails)| 1.0.1.0 | <p>New map with delivery date control.</p> |
|Dynamics 365 Sales quotation header (quotes)| 1.0.4.0	 | <p>New map for quotation revision feature with ownership change capability, prospect integration, discount customer groups and delivery date control.</p> |
|Dynamics 365 Sales quotation lines (quotedetails)| 1.0.0.0 | <p>Existing map for quotation lines.</p> |
|Dynamics 365 Sales prospects (accounts)|	1.0.0.0	| <p>New map for prospects of type organization.</p> |
|Dynamics 365 Sales prospects (contacts)|	1.0.0.0	| <p>New map for prospects of type person.</p> |
|CDS Contacts V2 (contacts)|	1.0.0.0	| <p>New map for prospect contact persons.</p> |
|Customers V3 (accounts)|	1.0.1.1	| <p>New map for setting relationship type when Dynamics 365 Sales prospects map is running.</p> |
|Customers V3 (contacts)|	1.0.1.1	| <p>New map for setting relationship type when Dynamics 365 Sales prospects map is running.</p> |
|Total discount customer groups| 1.0.0.0|<p>New map for Total discount customer groups.</p> | 
|Line discount customer groups| 1.0.0.0|<p>New map for Line discount customer groups.</p> | 
|Multiline discount customer groups| 1.0.0.0|<p>New map for Multiline discount customer groups.</p> | 

On the **Dual-write** page, make sure that all the above maps in the table show a **Status** value of *Running*. If any of them show a **Status** value of *Not running*, select them, and then select **Run** on the Action Pane.

#### Setup (FnO version 10.0.38 or earlier) ####
6.	Stop the following maps, since they are no longer required.

| Map | 
|---|
|CDS sales order headers (salesorders)|
|CDS sales order lines (salesorderdetails)|
|CDS sales order lines V2 (salesorderdetails)|
|CDS sales quotation header (quotes)|
|CDS sales quotation lines (quotedetails)|

7. The following entity maps are updated, so the latest version must be applied to these maps and be running.

| Map | Update to this version | Details |
|---|---|---|
|Dynamics 365 Sales feature management states (msdyn_supplychainfeaturestates)| 1.0.0.0 | <p>New map for Dynamics 365 Sales integration features.</p> |
|Dynamics 365 Sales order headers (salesorders)| 1.0.0.0 | <p>Existing map for sales orders.</p> |
|Dynamics 365 Sales order lines (salesorderdetails)| 1.0.0.0 | <p>Existing map for sales order lines.</p> |
|Dynamics 365 Sales quotation header (quotes)| 1.0.1.0	 | <p>New map for quotation revision feature with ownership change capability.</p> |
|Dynamics 365 Sales quotation lines (quotedetails)| 1.0.0.0 | <p>Existing map for quotation lines.</p> |
|Total discount customer groups| 1.0.0.0|<p>New map for Total discount customer groups.</p> | 
|Line discount customer groups| 1.0.0.0|<p>New map for Line discount customer groups.</p> | 
|Multiline discount customer groups| 1.0.0.0|<p>New map for Multiline discount customer groups.</p> | 

On the **Dual-write** page, make sure that all the above maps in the table show a **Status** value of *Running*. If any of them show a **Status** value of *Not running*, select them, and then select **Run** on the Action Pane.

### Step 3: Turn on the feature you need in Feature management

Use the [Feature management](../get-started/feature-management/feature-management-overview.md) workspace to turn on the feature that's listed in the following table. Then use the workspace to turn on the feature that you want to use. For more information about what each of the features released in 10.0.34 and 10.0.39 does and how to work with it, see [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md) and 
[Enable-prospect-in-prospect-to-cash with Dynamics 365 Sales](Enable prospect-in-prospect-to-cash-concept.md). <!--KFM: Correct link to be added by Karl -->

| Feature | Required or optional | Description |
|---|---|---|
| *Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales* | Required to enable prospect integration | <p>This feature can only be enabled when *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* is enabled. The feature enables the integration of prospects between Dynamics 365 Sales and Supply Chain management over dual-write. Prospects in Supply Chain Management integrate with account type "prospect" in Dynamics 365 Sales. The lifecycle of a prospect from creation to converting into a customer is supported from both Dynamics 365 Sales and Supply Chain Management and is seamlessly integrated into the quotation winning process. With this feature, it is possible to use the prospect on a quotation in Supply Chain Management and as a potential customer in Dynamics 365 Sales. After you enable this feature, you can turn the functionality on or off by using the **Integrate quotation lifecycles** option on the **Accounts receivable parameters** page.</p> |

After you've completed the initial setup, you can configure the feature that you enabled. To open the configuration settings, follow these steps.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Dynamics 365 Sales integration** tab, set the fields that are described in the following table. A tooltip is also provided for each field on the page.

    | FastTab | Field | Required features | Description |
    |---|---|---|---|
    | **General** | **Integrate prospect** | *Integrate prospect with Dynamics 365 Sales* | <p>This feature can only be turned on when *Integrate quotation lifecycles* is turned on. Enable or disable the functionality that's added by the *Enable prospect integration with Dynamics 365 Sales* feature. </p> |
