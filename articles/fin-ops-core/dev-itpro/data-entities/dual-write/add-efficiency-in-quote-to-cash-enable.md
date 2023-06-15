---
title: Enable extra efficiency in quote-to-cash with Dynamics 365 Sales
description: This article describes how to enable extra efficiency in quote-to-cash with Microsoft Dynamics 365 Sales.
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

Microsoft Dynamics 365 Supply Chain Management uses dual-write to integrate with Dynamics 365 Sales. In Supply Chain Management version 10.0.34 and later, this capability has been improved to provide a more seamless quotation process flow across the two systems. Therefore, it allows for fewer touch points, better efficiency, and improved transparency. To take advantage of these improvements, you must enable several new features in Supply Chain Management and make sure that you're using a qualifying version of the Dual-write Supply chain solution.

For a conceptual overview that describes how the improved quote-to-cash system works and how the integrated system will behave, depending on the features that you enable, see [Add efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash.md).

> [!NOTE]
> By default, all sales quotations that were created before the feature is enabled will have an **Origin** value of *Dynamics 365 Sales* in Dataverse and *Supply Chain Management* in Supply Chain Management. This initial misalignment of **Origin** values and the resulting ownership will be aligned when the sales quotation header is synced for the first time. If the first post-uptake synchronization is invoked from an update in Supply Chain Management, *Supply Chain Management* will be synced as the **Origin** value. If the first post-uptake synchronization is invoked from an update in Sales, *Dynamics 365 Sales* will be synced as the **Origin** value.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.34 or later.
- You must be running [Dual-write Supply Chain solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwscm) version XX.XX.XX.<!--KFM: Version needed -->

> [!IMPORTANT]
> Before you enable the features that are described in this article, we strongly recommend that you complete (that is, win or cancel) any existing sales quotations that are in progress. Then, after you enable the features, re-create the quotations as required. This approach allows for a clean switch to the new integrated functionality.

## Step 1: Add the Dual-write Supply Chain solution to your Power Platform environment

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

## <a name="enable-mappings"></a>Step 2: Enable mappings in Supply Chain Management

Follow these steps to enable the required mappings in Supply Chain Management.

1. Sign in to Supply Chain Management.
1. Go to **System administration \> Workspaces \> Data management**.
1. In the **Data management** workspace, select **Dual-write**.
1. On the **Dual-write** page, on the Action Pane, select **Apply solution**.
1. In the **Apply solution** dialog box, select the maps to apply. At a minimum, you must select the map where the **Display name** field is set to *Dynamics 365 Supply Chain Management extended entity maps*. However, we recommend that you select all the maps that are listed. When you've finished selecting maps, select **Apply**.
1. On the **Dual-write** page, in the grid, find the row where the **Table map** field is set to *Dynamics 365 Sales feature management states (msdyn\_supplychainfeaturestates)*. Select the row, and then select **Run** on the Action Pane.
1. The **Initial writes and related table map(s)** dialog box shows a single row, for the table map that you selected in the previous step. Set the following fields for this row:

    - **Initial sync** – Select this checkbox.
    - **Master for initial sync** – Select *Finance and operations apps*.

    > [!IMPORTANT]
    > The solution won't work correctly unless you run the initial synchronization as described in this step.

1. Select **Run** to apply your settings and close the dialog box.
1. On the **Dual-write** page, find the following rows, and make sure that they show a **Status** value of *Not running*. If any of them show a **Status** value of *Running*, select them, and then select **Stop** on the Action Pane.

    - *CDS Sales order headers (salesorders)*
    - *CDS Sales order lines (salesorderdetails)*
    - *CDS sales quotation header (quotes)*
    - *CDS sales quotation lines (quotedetails)*

1. On the **Dual-write** page, find the row for the *Dynamics 365 Sales quotation header (quotes)* table map. Select the link in the **Version** column for this row.
1. In the **Table map version** dialog box, select one of the following versions, and then select **Save**:

    - *1.0.0.0* – Select this version if you're running Supply Chain Management version 10.0.32 or 10.0.33.
    - *1.0.1.0* – Select this version if you're running Supply Chain Management version 10.0.34 or later. This version of the table map provides more features, but you will receive an error if you enable it for an unsupported version of Supply Chain Management.

1. On the **Dual-write** page, find the following rows, and make sure that they show a **Status** value of *Running*. If any of them show a **Status** value of *Not running*, select them, and then select **Run** on the Action Pane.

    - *Dynamics 365 Sales order headers (salesorders)*
    - *Dynamics 365 Sales order lines (salesorderdetails)*
    - *Dynamics 365 Sales quotation header (quotes)*
    - *Dynamics 365 Sales quotation lines (quotedetails)*

## Step 3: Enable the features you need in Feature management

Use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to turn on the feature that's listed as required in the following table. Then use the workspace to turn on each optional feature that you want to use. For more information about what each feature does and how to work with it, see [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md).

| Feature | Required or optional | Description |
|---|---|---|
| *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | Required | This feature changes the way that sales quotations in Sales integrate with sales quotations in Supply Chain Management through dual-write. After it's enabled, state and status transitions throughout the lifecycle of a sales quotation are mapped between the two apps, and a policy of ownership is applied to control the actions that are available for a sales quotation while it's in either Sales or Supply Chain Management. |
| *Set default ownership for sales quotations when integrated with Dynamics 365 Sales* | Optional | This feature adds a field for setting a default ownership to the **Accounts receivables parameters** page. This field can be set to *Based on origin*, *Dynamics 365 Sales*, or *Supply Chain Management*. If this feature is disabled, ownership is always based on the origin. |
| *Make Supply Chain Management price master when integrated with Dynamics 365 Sales* | Optional | <p>When this feature is enabled, calculations for extended amounts, summary amounts, subtotals, and totals for sales quotations and sales orders aren't done in Sales. When quotations or sales orders are created in Sales, if a price list exists in Sales, the price from that price list is used, but no other calculations are done. All calculated monetary fields are calculated in and synced from Supply Chain Management.</p><p>When this feature is enabled, it sets the **Use system price calculation** option to *No* and the **Discount calculation method** field to *Per unit* in Sales. The following changes are also made in the Sales user interface (UI) for sales quotation and sales order lines: the **Volume discount** field is hidden, the value of the **Discount** field is expressed as a per-unit discount amount, and the **Manual discount** field becomes read-only and is relabeled. Manual discounts can then be entered in the **Line discount amount** field.</p> |
| *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | Optional | <p>This feature enables the system to calculate and push line prices, discounts, charges, taxes, and totals for a single sales order and sales quotation to Sales.</p><p>This feature adds a new menu item to the sales order and sales quotation list and details pages in Supply Chain Management. When this menu item is selected, it enables the calculation and push to Sales. The feature also adds two new pages that complement the existing **Calculate sales totals** page: **Calculate sales order totals for Sales** and **Calculate sales quotation totals for Sales**. Each of these pages lets you specify a range of sales orders or sales quotations that the calculation should consider.</p> |
| *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales* | Optional | This feature helps ensure data consistency between sales orders and related sales quotations in Supply Chain Management when sales orders are created from sales quotations in Sales and synced through dual-write. As a result, sales orders in Supply Chain Management will contain the information from the sales quotation in Supply Chain Management. This feature adds a field to the **Dynamics 365 Sales integration** tab of the **Accounts receivable parameters** page, so that admins can specify whether quotation information is copied upon order creation or through the message processor. |
| *Process Dynamics 365 Sales integration related events* | Optional | This feature enables Sales integration-related events to be processed asynchronously via the message processor framework. This capability can improve performance in some scenarios, such as a scenario where the status of a sales quotation is transitioned when a quotation journal or quotation confirmation journal must be created. |

> [!NOTE]
> The status of these features in Supply Chain Management is exposed to Dataverse and will be consumed by business logic that's run in Sales. If the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is enabled, it affects the process for working with sales quotations in both Sales and Supply Chain Management. The nature of the impact depends on the ownership of the sales quotation. Exposing feature statuses to Dataverse helps ensure consistency of feature statuses between the two apps.

## Troubleshooting

After you enable the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature, if the sales quotation lifecycle flow doesn't work as expected for newly created sales quotations, follow these steps. For more information about each step, see the [Step 2: Enable mappings in Supply Chain Management](#enable-mappings) section.

1. In Supply Chain Management, go to **System administration \> Workspaces \> Data management**.
1. In the **Data management** workspace, select **Dual-write**.
1. Run an initial synchronization for the table map that's named *Dynamics 365 Sales feature management states (msdyn\_supplychainfeaturestates)*.
1. Make sure that the following maps are running:

    - *Dynamics 365 Sales order headers (salesorders)*
    - *Dynamics 365 Sales order lines (salesorderdetails)*
    - *Dynamics 365 Sales quotation header (quotes)*
    - *Dynamics 365 Sales quotation lines (quotedetails)*

1. Make sure that the following table maps have been stopped:

    - *CDS Sales order headers (salesorders)*
    - *CDS Sales order lines (salesorderdetails)*
    - *CDS Sales quotation header (quotes)*
    - *CDS Sales quotation lines (quotedetails)*
