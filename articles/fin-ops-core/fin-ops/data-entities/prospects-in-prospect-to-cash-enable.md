---
title: Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales
description: This article describes how to enable, set up, and configure the latest enhancements in prospect-to-cash with Microsoft Dynamics 365 Sales.
author: AditiPattanaik
ms.author: adpattanaik
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

Microsoft Dynamics 365 Supply Chain Management uses dual-write to integrate with Dynamics 365 Sales. In Supply Chain Management version 10.0.34, several enhancements were released that provide a more seamless quotation process flow across the two systems. As of Supply Chain Management version 10.0.39, you can also use prospects in the sales quotation process. Several other enhancements are also supported, such as delivery date control in quotation revision and quotation winning scenarios.

For a conceptual overview that describes how the improved prospect-to-cash system works and how the integrated system behaves, see [Work with prospects in prospect-to-cash with Dynamics 365 Sales](prospects-in-prospect-to-cash-use.md).

To add *Enable prospect in prospect-to-cash with Dynamics 365 Sales* functionality to your system, you must install the required solution in your dual-write environment, enable mappings in Supply Chain Management, and turn on the feature that you want to use. This article describes how to set up and configure the features that you want to use.

## Prerequisites

Before you can follow the procedures in this article, your system must meet the prerequisites that are listed in the following subsections.

### Version requirements

To use the features described in this topic, your system must meet the following version requirements:

- You must be running Supply Chain Management version 10.0.39 or later.
- You must be running [Dual-write Supply Chain solution](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.dwscm) version 2.3.4.312 or later.
- If you've deployed the dual-write global address book (GAB) solution, you must be running version 3.5.2.72 or later of the GAB solution.

### Number sequence requirements

The integration design of prospects between Sales and Supply Chain Management *requires* that account numbers for prospects are the same in Sales and Supply Chain Management. Number sequences for prospects and the number sequence for customer accounts in Supply Chain Management *must not* overlap. Otherwise, conflicts can occur when a prospect is converted to a customer account. These conflicts prevent the conversion from being done.

## Step 1: Add the dual-write Supply Chain solution to your Power Platform environment

> [!IMPORTANT]
> Don't update the Dual-write Supply Chain solution, as described in this section, unless you're running Supply Chain Management version 10.0.34 or later. To fully benefit from this update and the other improvements that are described in this article, you must be running Supply Chain Management version 10.0.39 or later.

Follow these steps to add the Dual-write Supply Chain solution to your Power Platform environment.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. On the navigation pane, select **Environments**.
1. Open the environment that you want to integrate with Supply Chain Management.
1. On the **Resources** tile, select **Dynamics 365 apps**.
1. On the toolbar, select **Install app**.
1. In the **Install Dynamics 365 apps** dialog box, find the row where the **Name** field is set to *Dual-write Supply Chain solution*. Then follow one of these steps:

    - If the **Status** field for the row indicates that the app isn't installed, or that an update is available, select the row, and then select **Next** to open an installation wizard. Follow the on-screen instructions to install the app.
    - If the **Status** field for the row indicates that the app is installed, enabled, and up to date, select **Cancel**.

1. On the **Dynamics 365 apps** page, find the row where the **Name** field is set to *Dual-write Supply Chain solution*. The **Status** field for the row should now indicate that this app is installed.
1. Select the ellipsis button (**&hellip;**) for the row, and then select **Details** on the menu.
1. In the **Details** dialog box for the solution, confirm that the **Version** value fulfills the [prerequisites](#prerequisites) at the beginning of this article. Then close the dialog box.

## Step 2: Enable mappings in Supply Chain Management

The maps that you must enable depend on the version of Supply Chain Management that you're running and whether you've deployed the dual-write global address book (GAB) solution. The following permutations exist:

- Supply Chain Management version 10.0.39 or later with the dual-write GAB solution
- Supply Chain Management version 10.0.39 or later without the dual-write GAB solution
- Supply Chain Management version 10.0.38 or older, either with or without the dual-write GAB solution

Each of the following subsections describes how to set up one of the preceding types of systems. Follow the procedure that matches your environment.

For more information about the dual-write GAB solution, see [Party and global address book](../../dev-itpro/data-entities/dual-write/party-gab.md).

### Step 2, option 1: For Supply Chain Management version 10.0.39 or later with the dual-write GAB solution

Follow these steps if you're running Supply Chain Management version 10.0.39 or later, and you've deployed the dual-write GAB solution.

1. Sign in to Supply Chain Management.
1. Go to **System administration** \> **Workspaces** \> **Data management**.
1. In the **Data management** workspace, select **Dual-write**.
1. On the **Dual-write** page, on the Action Pane, select **Apply solution**.
1. In the **Apply solution** dialog box, select the maps to apply. At minimum, you must select the map where the **Display name** field is set to *Dynamics 365 Supply Chain Management extended entity maps*. However, we recommend that you select all the maps that are listed. After you finish selecting maps, select **Apply**.
1. Stop the following maps, because they're no longer required:

    - Dynamics 365 Sales feature management states (msdyn\_supplychainfeaturestates)
    - CDS sales order headers (salesorders)
    - CDS sales order lines (salesorderdetails)
    - CDS sales order lines V2 (salesorderdetails)
    - CDS sales quotation header (quotes)
    - CDS sales quotation lines (quotedetails)

1. The entity maps in the following table are required and might have to be updated. Update each of these maps to the latest version, and make sure that it's running.

    | Map | Update to this version | Details |
    |---|---|---|
    | Dynamics 365 Sales feature parameters (msdyn\_supplychainfeaturestates) | 1.0.0.0 | New map for the setup parameters for Sales integration. |
    | Dynamics 365 Sales order headers (salesorders) | 1.0.2.1 | New map with discount customer groups and delivery date control. |
    | Dynamics 365 Sales order lines (salesorderdetails) | 1.0.1.0 | New map with delivery date control. |
    | Dynamics 365 Sales quotation header (quotes) | 1.0.4.1 | New map for the quotation revision feature with ownership change capability, prospect integration, discount customer groups, and delivery date control. |
    | Dynamics 365 Sales quotation lines (quotedetails) | 1.0.1.0 | Existing map for quotation lines. |
    | Dynamics 365 Sales prospects (accounts) | 1.0.0.1 | New map for prospects of the *Organization* type. |
    | Dynamics 365 Sales prospects (contacts) | 1.0.0.1 | New map for prospects of the *Person* type. |
    | Customers V3 (accounts) | 1.0.1.5 | New map for setting the relationship type when the *Dynamics 365 Sales prospects* map is running. This map removes **PartyNumber** and other party-related fields, such as fields for the name, personal details, postal address, and electronic contact address. |
    | Customers V3 (contacts) | 1.0.1.5 | New map for setting the relationship type when the *Dynamics 365 Sales prospects* map is running. This map removes **PartyNumber** and other party-related fields, such as fields for the name, personal details, postal address, and electronic contact address. |
    | Total discount customer groups | 1.0.0.0 | New map for Total discount customer groups. |
    | Line discount customer groups | 1.0.0.0 | New map for Line discount customer groups. |
    | Multiline discount customer groups | 1.0.0.0 | New map for Multiline discount customer groups. |

    > [!IMPORTANT]
    > Don't run the CDS Contacts V2 map in Supply Chain Management. You must instead run this map in the GAB solution.

1. On the **Dual-write** page, make sure that all the maps in the previous table show a **Status** value of *Running*. If any of them show a **Status** value of *Not running*, select them, and then select **Run** on the Action Pane.

### Step 2, option 2: For Supply Chain Management version 10.0.39 or later without the dual-write GAB solution

Follow these steps if you're running Supply Chain Management version 10.0.39 or later, and you haven't deployed the dual-write GAB solution.

1. Sign in to Supply Chain Management.
1. Go to **System administration** \> **Workspaces** \> **Data management**.
1. In the **Data management** workspace, select **Dual-write**.
1. On the **Dual-write** page, on the Action Pane, select **Apply solution**.
1. In the **Apply solution** dialog box, select the maps to apply. At a minimum, you must select the map where the **Display name** field is set to *Dynamics 365 Supply Chain Management extended entity maps*. However, we recommend that you select all the maps that are listed. After you finish selecting maps, select **Apply**.
1. Stop the following maps, because they're no longer required:

    - Dynamics 365 Sales feature management states (msdyn\_supplychainfeaturestates)
    - CDS sales order headers (salesorders)
    - CDS sales order lines (salesorderdetails)
    - CDS sales order lines V2 (salesorderdetails)
    - CDS sales quotation header (quotes)
    - CDS sales quotation lines (quotedetails)

1. The entity maps in the following table are required and might have to be updated. Update each of these maps to the latest version, and make sure that it's running.

    | Map | Update to this version | Details |
    |---|---|---|
    | Dynamics 365 Sales feature parameters (msdyn\_supplychainfeaturestates) | 1.0.0.0 | New map for the setup parameters for Sales integration. |
    | Dynamics 365 Sales order headers (salesorders) | 1.0.2.0 | New map with discount customer groups and delivery date control. |
    | Dynamics 365 Sales order lines (salesorderdetails) | 1.0.1.0 | New map with delivery date control. |
    | Dynamics 365 Sales quotation header (quotes) | 1.0.4.0 | New map for the quotation revision feature with ownership change capability, prospect integration, discount customer groups, and delivery date control. |
    | Dynamics 365 Sales quotation lines (quotedetails) | 1.0.1.0 | Existing map for quotation lines. |
    | Dynamics 365 Sales prospects (accounts) | 1.0.0.0 | New map for prospects of the *Organization* type. |
    | Dynamics 365 Sales prospects (contacts) | 1.0.0.0 | New map for prospects of the *Person* type. |
    | CDS Contacts V2 (contacts) | 1.0.0.0 | New map for prospect contact persons. |
    | Customers V3 (accounts) | 1.0.1.1 | New map for setting the relationship type when the *Dynamics 365 Sales prospects* map is running. |
    | Customers V3 (contacts) | 1.0.1.1 | New map for setting the relationship type when the *Dynamics 365 Sales prospects* map is running. |
    | Total discount customer groups | 1.0.0.0 | New map for Total discount customer groups. |
    | Line discount customer groups | 1.0.0.0 | New map for Line discount customer groups. |
    | Multiline discount customer groups | 1.0.0.0 | New map for Multiline discount customer groups. |

1. On the **Dual-write** page, make sure that all the maps in the previous table show a **Status** value of *Running*. If any of them show a **Status** value of *Not running*, select them, and then select **Run** on the Action Pane.

### Step 2, option 3: For Supply Chain Management version 10.0.38 or older, either with or without the dual-write GAB solution

Follow these steps if you're running Supply Chain Management version 10.0.38 or older, regardless of whether you've deployed the dual-write GAB solution.

1. Sign in to Supply Chain Management.
1. Go to **System administration** \> **Workspaces** \> **Data management**.
1. In the **Data management** workspace, select **Dual-write**.
1. On the **Dual-write** page, on the Action Pane, select **Apply solution**.
1. In the **Apply solution** dialog box, select the maps to apply. At a minimum, you must select the map where the **Display name** field is set to *Dynamics 365 Supply Chain Management extended entity maps*. However, we recommend that you select all the maps that are listed. After you finish selecting maps, select **Apply**.
1. Stop the following maps, because they're no longer required:

    - CDS sales order headers (salesorders)
    - CDS sales order lines (salesorderdetails)
    - CDS sales order lines V2 (salesorderdetails)
    - CDS sales quotation header (quotes)
    - CDS sales quotation lines (quotedetails)

1. The entity maps in the following table are required and might have to be updated. Update each of these maps to the latest version, and make sure that it's running.

    | Map | Update to this version | Details |
    |---|---|---|
    | Dynamics 365 Sales feature management states (msdyn\_supplychainfeaturestates) | 1.0.0.0 | New map for Sales integration features. |
    | Dynamics 365 Sales order headers (salesorders) | 1.0.0.0 | Existing map for sales orders. |
    | Dynamics 365 Sales order lines (salesorderdetails) | 1.0.0.0 | Existing map for sales order lines. |
    | Dynamics 365 Sales quotation header (quotes) | 1.0.1.0 | New map for the quotation revision feature with ownership change capability. |
    | Dynamics 365 Sales quotation lines (quotedetails) | 1.0.1.0 | Existing map for quotation lines. |
    | Total discount customer groups | 1.0.0.0 | New map for Total discount customer groups. |
    | Line discount customer groups | 1.0.0.0 | New map for Line discount customer groups. |
    | Multiline discount customer groups | 1.0.0.0 | New map for Multiline discount customer groups. |

1. On the **Dual-write** page, make sure that all the maps in the previous table show a **Status** value of *Running*. If any of them show a **Status** value of *Not running*, select them, and then select **Run** on the Action Pane.

## Step 3: Turn on the feature in Feature management

Use the [Feature management](../get-started/feature-management/feature-management-overview.md) workspace to turn on the features in the following table. Then use the workspace to turn on the other quote-to-cash features that you want to use. For more information about each of the other quote-to-cash features, see [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md).

| Feature | Required or optional | Description |
|---|---|---|
| *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | Required | This feature changes the way that sales quotations in Sales are integrated with sales quotations in Supply Chain Management through dual-write. After it's enabled, state and status transitions throughout the lifecycle of a sales quotation are mapped between the two apps, and a policy of ownership is applied to control the actions that are available for a sales quotation while it's in either Sales or Supply Chain Management. |
| *Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales* | Required to enable prospect integration | This feature can be enabled only when the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is enabled. It enables the integration of prospects between Sales and Supply Chain Management through dual-write. Prospects in Supply Chain Management are integrated with the *Prospect* account type in Sales. The lifecycle of a prospect, from creation through conversion to a customer, is supported in both Sales and Supply Chain Management, and is seamlessly integrated into the quotation winning process. This feature enables a prospect to be used on a quotation in Supply Chain Management and as a potential customer in Sales. |

After you complete the initial setup, follow these steps to configure the features that you enabled.

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Dynamics 365 Sales integration** tab, on the **General** FastTab, set the following values:

    - **Integrate quotation lifecycles:** *Yes*
    - **Integrate prospects:** *Yes*

    The other fields on this tab affect different aspects of the integrated prospect-to-cash functionality. For more information about the other fields, see [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md). Tooltips are also provided for each field on the page.

1. On the **Prospect** FastTab, set the **Default relation type** field to the default prospect type that you'll also set on the **Sales and marketing parameters** page for prospects.
1. Go to **Sales and marketing** \> **Setup** \> **Sales and marketing parameters**.
1. On the **Prospects** tab, set the **Type** field to *Prospect*, and ensure that the **Table source** field is set to *Relation table*. In addition, we recommend that you select a default customer group to allow for a seamless prospect-to-customer conversion process.

<!--KFM: Follow up on the **Table source** setting. I didn't see it here in the UI. -->

## Next steps

- [Add efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-concept.md)
- [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md)
- [Work with prospects in prospect-to-cash with Dynamics 365 Sales](prospects-in-prospect-to-cash-use.md)
