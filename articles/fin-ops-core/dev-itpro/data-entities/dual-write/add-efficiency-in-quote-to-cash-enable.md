---
title: Enable extra efficiency in quote-to-cash with Dynamics 365 Sales
description: This article describes how to enable extra efficiency in quote-to-cash with Dynamics 365 Sales
author: henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 05/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Enable extra efficiency in quote-to-cash with Dynamics 365 Sales

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

<!-- KFM: Preview until 10.0.34 GA -->

Dynamics 365 Supply Chain Management uses dual-write to integrate with Dynamics 365 Sales. In Supply Chain Management version 10.0.34 and higher, this capability has been improved to provide a more seamless quotation process flow across the two systems, allowing for fewer touch points, higher efficiency, and improved transparency. To take advantage of these improvements, you must enable several new features in Supply Chain Management and make sure you are using a qualifying version of the Dual-write Supply chain solution.

For a conceptual overview of how the improved quote-to-cash system works and how the integrated system will behave based on which features you choose to enable, see [Add efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash.md).

> [!NOTE]
> All sales quotations created prior to the feature being enabled will have Dynamics 365 Sales as default origin in Dataverse while the same sales quotations have Supply Chain Management as default origin in Supply Chain Management. This initial misalignment of origin and resulting ownership will align upon the first sales quotation header synchronization. Once the first synchronization of a sales quotation header update is done, then the origin values will be aligned. If the first post-uptake synchronization is invoked from an update in Supply Chain Management, then Supply Chain Management will be synched as origin. If the first post-uptake synchronization is invoked from an update in Dynamics 365 Sales, then Dynamics 365 Sales will be synced as origin.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.34 or later.
- You must be running [Dual-write Supply Chain solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwscm) version XX.XX.XX.<!--KFM: Version needed -->

> [!IMPORTANT]
> Before you enable the features described in this article, we strongly recommend that you complete (win or cancel) any existing sales quotations that are in progress. After you're done enabling the feature, go back and recreate them if needed. This will allow for a clean switch to the new integrated functionality.

## Step 1: Add the Dual-write Supply Chain solution to your Power Platform environment

Follow these steps to add the Dual-write Supply Chain solution to your Power Platform environment:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. In the navigation pane, select **Environments**.
1. Open the environment that you want to integrate with Supply Chain Management.
1. In the **Resources** tile, select **Dynamics 365 apps**.
1. From the toolbar, select **Install app** to open **Install Dynamics 365 apps** dialog.
1. Scroll down to find the row where **Name** is *Dual-write Supply Chain solution*. Do one of the following steps:
    - If the **Status** for this row indicates that the app isn't installed or that there is an update available, then select the row and then select **Next** to launch an installation wizard. Follow the instructions on your screen to install the app.
    - If the **Status** for this row indicates that the app is installed, enabled, and up to date, select **Cancel**.
1. You now return to the **Dynamics 365 apps** page. Scroll down to find the row where **Name** is *Dual-write Supply Chain solution*. The **Status** column should now indicate that this app is installed. 
1. Select the ellipsis button for this row to open a drop-down list and then select **Details** to open the **Details** dialog for the solution. Make sure the **Version** shown fulfils the [prerequisites](#prerequisites) listed at the start of this article. Then close the dialog.

## <a name="enable-mappings"></a>Step 2: Enable mappings in Supply Chain Management

Follow these steps to enable the required mappings in Supply Chain Management:

1. Sign in to Supply Chain Management.
1. Go to **System administration \> Workspaces \> Data management**.
1. The **Data management** workspace opens. Select the **Dual-write** button.
1. The **Dual-write** page opens. On the Action Pane, select **Apply solution**.
1. The **Apply solution** dialog opens. Here, you can choose to apply one or more of the listed maps. You must at least select the map with a **Display name** of *Dynamics 365 Supply Chain Management extended entity maps*, but we recommend that you select all of the listed maps. Then select **Apply**.
1. You now return to the **Dual-write** page. In the grid, find the row where **Table map** is *Dynamics 365 Sales feature management states (msdyn_supplychainfeaturestates)*. Select the row and then select **Run** on the Action Pane.
1. The **Initial writes and related table map(s)** dialog opens, showing a single row with the table map you selected before opening the dialog. Make the following settings for this row:
    - **Initial sync** – Select this check box.
    - **Master for initial sync** – Select *Finance and operations apps*.

    > [!IMPORTANT]
    > The solution won't work correctly unless you run the initial sync as described in this step.

1. Select **Run** to apply your settings and close the dialog.
1. On the **Dual-write** page, scroll down to the following rows and make sure they show a **Status** of *Not running*. If one or both are running, then select them and then select **Stop** on the Action Pane.
    - *CDS sales quotation header (quotes)*
    - *CDS sales quotation lines (quotedetails)*
1. On the **Dual-write** page, scroll down to the *Dynamics 365 Sales quotation header (quotes)* table map. Select the link in the **Version** column for this row to open the **Table map version** dialog. Select one of the following versions and then select **Save**:
    - *1.0.0.0* – Select this version if you are running Supply Chain Management version 10.0.32 or 10.0.33.
    - *1.0.1.0* – Select this version if you are running Supply Chain Management version 10.0.34 or later. This version provides more features, but will generate an error if you enable it for an unsupported version of Supply Chain Management.
1. On the **Dual-write** page, scroll down to the following rows and make sure they show a **Status** of *Running*. If one or both aren't running, then select them and then select **Run** on the Action Pane.
    - *Dynamics 365 Sales quotation header (quotes)*
    - *Dynamics 365 Sales quotation lines (quotedetails)*

## Step 3: Enable the features you need in feature management

Use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to turn on the feature listed as required in the following table. Then use the workspace turn on each of the optional features as you would like to use.

| Feature | Required or optional | Description |
|---|---|---|
| *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | Required | This feature changes the way sales quotations in the Dynamics 365 Sales application integrate with sales quotations in Supply Chain management over dual-write. Once enabled, state and status transitions throughout the lifecycle of a sales quotation are mapped between the two applications while applying a policy of ownership to control the available actions for a sales quotation when in either Dynamics 365 Sales or in Supply Chain Management. |
| *Set default ownership for sales quotations when integrated with Dynamics 365 Sales* | Optional | Adds a setting to the **Accounts receivables parameters** page, where the default ownership can be set. Default ownership can be set to *Based on origin*, *Dynamics 365 Sales*, or *Supply Chain Management*. When this feature is disabled, ownership is always based on origin. |
| *Make Supply Chain Management price master when integrated with Dynamics 365 Sales* | Optional | When enabled, calculations for extended amounts, summary amounts, subtotals, and totals for sales quotations and sales orders will not be performed in Dynamics 365 Sales. When quotations or sales orders are created in Sales, and a price list exists in Sales, then that price will be used, but no other calculations will be made. All calculated monetary fields are calculated in and synchronized from Supply Chain Management.<br><br>When enabled, this feature sets **Use system price calculation** to *No* and **Discount calculation method** to *Per unit* in Sales. The following changes are also made in the Sales user interface for sales quotation and sales order lines: the **Volume discount** field is hidden, the **Discount** field is expressed as per-unit discount amount, and the **Manual discount** field is made read-only and relabeled. Manual discounts can henceforth be entered in the **Line discount amount** field. |
| *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | Optional | Enables the system to calculate and push line prices, discounts, charges, taxes and totals for a single sales order and sales quotation to Dynamics 365 Sales.<br><br>This feature adds a new menu item <!-- KFM: Name the menu here -->to the sales order and sales quotation list and details pages in Supply Chain Management; when selected, will enable the calculation and push to Dynamics 365 Sales. The feature also adds two new pages that complement the existing **Calculate sales totals** page: **Calculate sales order totals for Sales** and **Calculate sales quotation totals for Sales**. Each of these pages let you specify a range of sales orders or sales quotations to be considered in the calculation. |
| *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales* | Optional | This feature ensures data consistency between sales orders and related sales quotations in Supply Chain Management when sales orders are created from sales quotations in Dynamics 365 Sales and synchronized over dual-write. As a result, sales orders in Supply Chain Management will contain the information from the sales quotation in Supply Chain Management. This feature adds a setting <!-- KFM: Name the setting here --> on the **Dynamics 365 Sales integration** tab of the **Accounts receivable parameters** page, which lets admins choose whether to copy quotation information on order creation or through the message processor. |
| *Process Dynamics 365 Sales integration related events* | Optional | Enables Dynamics 365 Sales integration-related events to be processed asynchronously using the message processor framework. This can improve performance in various scenarios, such as transitioning the status of a sales quotation when a quotation journal or quotation confirmation journal needs to be created. |

> [!NOTE]
> The status of these features in Supply Chain Management is exposed to Dataverse and will be consumed by business logic executed in Dynamics 365 Sales. If the feature *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* is enabled, the process for working with sales quotations will be impacted in both Dynamics 365 Sales and Supply Chain Management. The nature of the impact will depend on ownership of the sales quotation. Exposing feature statuses to Dataverse ensures feature status consistency between the two applications.

## Troubleshooting

If the sales quotation lifecycle flow isn't working as expected for newly created sales quotations after you enable the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales*, do the following steps. See also [Step 2: Enable mappings in Supply Chain Management](#enable-mappings) for more information about each of these steps.

1. In Supply Chain Management, go to **System administration \> Workspaces \> Data management** and select the **Dual-write** button.
1. Run an initial sync for the table map called *Dynamics 365 Sales feature management states (msdyn_supplychainfeaturestates)*.
1. Make sure that that following maps are running:

    - Dynamics 365 Sales order headers (salesorders) <!-- KFM: Not mentioned in the procedure. Add this there? -->
    - Dynamics 365 Sales order lines (salesorderdetails) <!-- KFM: Not mentioned in the procedure. Add this there? -->
    - Dynamics 365 Sales quotation header (quotes)
    - Dynamics 365 Sales quotation lines (quotedetails)

1. Make sure that these table maps have been stopped:

    - CDS Sales order headers (salesorders) <!-- KFM: Not mentioned in the procedure. Add this there? -->
    - CDS Sales order lines (salesorderdetails) <!-- KFM: Not mentioned in the procedure. Add this there? -->
    - CDS Sales quotation header (quotes)
    - CDS Sales quotation lines (quotedetails)
