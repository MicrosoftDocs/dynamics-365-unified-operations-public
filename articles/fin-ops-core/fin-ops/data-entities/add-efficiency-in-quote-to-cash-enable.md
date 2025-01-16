---
title: Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales
description: Learn about how to enable extra efficiency in quote-to-cash with Microsoft Dynamics 365 Sales, with outlines on prerequisites and initial setup.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: DataManagementWorkspace, CustParameters
ms.topic: how-to
ms.date: 01/07/2025
ms.custom: 
  - bap-template
---

# Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales

[!include [banner](../../../finance/includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management uses dual-write to integrate with Dynamics 365 Sales. In Supply Chain Management version 10.0.34 and later, this capability has been improved to provide a more seamless quotation process flow across the two systems. Therefore, it allows for fewer touch points, better efficiency, and improved transparency. To take advantage of these improvements, you must enable several new features in Supply Chain Management and make sure that you're using a qualifying version of the Dual-write Supply chain solution.

For a conceptual overview that describes how the improved quote-to-cash system works and how the integrated system will behave, depending on the features that you enable, see [Add efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-concept.md).

> [!NOTE]
> By default, all sales quotations that were created before the feature is enabled will have an **Origin** value of *Dynamics 365 Sales* in Dataverse and *Supply Chain Management* in Supply Chain Management. This initial misalignment of **Origin** values and the resulting ownership will be aligned when the sales quotation header is synced for the first time. If the first post-uptake synchronization is invoked from an update in Supply Chain Management, *Supply Chain Management* will be synced as the **Origin** value. If the first post-uptake synchronization is invoked from an update in Sales, *Dynamics 365 Sales* will be synced as the **Origin** value.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.34 or later.
- You must be running [Dual-write Supply Chain solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwscm) version 2.3.4.203.

> [!IMPORTANT]
> Before you enable the functionality that's described in this article, we strongly recommend that you complete (that is, win or cancel) any existing sales quotations that are in progress. Then, after you enable the functionality, re-create the quotations as required. This approach allows for a clean switch to the new integrated functionality.

## Initial setup

To add *Extra efficiency in quote-to-cash with Dynamics 365 Sales* functionality to your system, you must install the required solution in your dual-write environment, enable mappings in Supply Chain Management, and turn on the features that you want to use.

### Step 1: Add the Dual-write Supply Chain solution to your Power Platform environment

> [!IMPORTANT]
> Don't update your Dual-write Supply Chain solution, as described in this section, unless you're running Supply Chain Management version 10.0.32 or later. To fully benefit from this update and the other improvements that are described in this article, you must be running Supply Chain Management version 10.0.34 or later.

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

Follow these steps to enable the required mappings in Supply Chain Management.

1. Sign in to Supply Chain Management.
1. Go to **System administration** \> **Workspaces** \> **Data management**.
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
    - *1.0.1.0* – Select this version if you're running Supply Chain Management version 10.0.34 or later. This version of the table map provides more features, but you'll receive an error if you enable it for an unsupported version of Supply Chain Management.

1. On the **Dual-write** page, find the following rows, and make sure that they show a **Status** value of *Running*. If any of them show a **Status** value of *Not running*, select them, and then select **Run** on the Action Pane.

    - *Dynamics 365 Sales order headers (salesorders)*
    - *Dynamics 365 Sales order lines (salesorderdetails)*
    - *Dynamics 365 Sales quotation header (quotes)*
    - *Dynamics 365 Sales quotation lines (quotedetails)*

### Step 3: Turn on the features you need in Feature management

Use the [Feature management](../get-started/feature-management/feature-management-overview.md) workspace to turn on the feature that's listed as required in the following table. Then use the workspace to turn on each optional feature that you want to use. For more information about what each feature does and how to work with it, see [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md).

| Feature | Required or optional | Description |
|---|---|---|
| *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | Required | <p>This feature changes the way that sales quotations in Sales are integrated with sales quotations in Supply Chain Management through dual-write. After it's enabled, state and status transitions throughout the lifecycle of a sales quotation are mapped between the two apps, and a policy of ownership is applied to control the actions that are available for a sales quotation while it's in either Sales or Supply Chain Management.</p><p>In Supply Chain Management version 10.0.37 and later, after you enable this feature, you can turn the functionality on or off by using the **Integrate quotation lifecycles** option on the **Accounts receivable parameters** page (as described in the next section).</p><p>As of Supply Chain Management version 10.0.41, this feature is turned on by default.</p>  |
| *Set default ownership for sales quotations when integrated with Dynamics 365 Sales* | Optional | <p>This feature adds a field for setting default ownership to the **Accounts receivable parameters** page. This field can be set to *Based on origin*, *Dynamics 365 Sales*, or *Supply Chain Management*. If this feature is disabled, ownership is always based on the origin.</p><p>As of Supply Chain Management version 10.0.41, this feature is turned on by default.</p> |
| *Make Supply Chain Management price master when integrated with Dynamics 365 Sales* | Optional | <p>When this feature is enabled, calculations for extended amounts, summary amounts, subtotals, and totals for sales quotations and sales orders aren't done in Sales. When quotations or sales orders are created in Sales, if a price list exists in Sales, the price from that price list is used, but no other calculations are done. All calculated monetary fields are calculated in and synced from Supply Chain Management.</p><p>The following changes are made in the Sales user interface (UI) for sales quotation and sales order lines: the **Volume discount** field is hidden, and the **Manual discount** field becomes read-only and is relabeled **Discount**. Manual discounts can then be entered in the **Line discount amount** field.</p><p>In Supply Chain Management version 10.0.37 and later, after you enable this feature, you can turn the functionality on or off by using the **Make Supply Chain Management price master** option on the **Accounts receivable parameters** page (as described in the next section).</p><p>As of Supply Chain Management version 10.0.41, this feature is turned on by default.</p>  |
| *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated with Dynamics 365 Sales* | Optional | <p>This feature enables the system to calculate and push line prices, discounts, charges, taxes, and totals for a single sales order and sales quotation to Sales.</p><p>This feature adds a new menu item to the sales order and sales quotation list and details pages in Supply Chain Management. When this menu item is selected, it enables the calculation and pushes to Sales. The feature also adds two new pages that complement the existing **Calculate sales totals** page: **Calculate sales order totals for Sales** and **Calculate sales quotation totals for Sales**. Each of these pages lets you specify a range of sales orders or sales quotations that the calculation should consider.</p><p>In Supply Chain Management version 10.0.37 and later, after you enable this feature, you can turn the functionality on or off by using the **Calculate and push prices** option on the **Accounts receivable parameters** page (as described in the next section).</p><p>As of Supply Chain Management version 10.0.41, this feature is turned on by default.</p> |
| *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales* | Optional | <p>This feature helps ensure data consistency between sales orders and related sales quotations in Supply Chain Management when sales orders are created from sales quotations in Sales and synced through dual-write. As a result, sales orders in Supply Chain Management contain the information from the sales quotation in Supply Chain Management.</p><p>This feature adds a field to the **Dynamics 365 Sales integration** tab of the **Accounts receivable parameters** page. Admins can use this field to specify whether quotation information is copied upon order creation or through the message processor.</p><p>In Supply Chain Management version 10.0.37 and later, after you enable this feature, you can turn the functionality on or off by using the **Copy quotation data to sales orders** option on the **Accounts receivable parameters** page (as described in the next section).<p>As of Supply Chain Management version 10.0.41, this feature is turned on by default.</p> |
| *Process Dynamics 365 Sales integration related events* | Optional | <p>This feature enables Sales integration-related events to be processed asynchronously via the message processor framework. This capability can improve performance in some scenarios, such as a scenario where the status of a sales quotation is transitioned when a quotation journal or quotation confirmation journal must be created.</p><p>In Supply Chain Management version 10.0.37 and later, after you enable this feature, you can turn the functionality on or off by using the **Use message processor** option on the **Accounts receivable parameters** page (as described in the next section).</p><p>As of Supply Chain Management version 10.0.41, this feature is turned on by default.</p> |

> [!NOTE]
> The status of these features in Supply Chain Management is exposed to Dataverse and will be consumed by business logic that's run in Sales. If **Integrate quotation lifecycles** and **Calculate and push prices** functionalities are enabled, they affect the process for working with sales quotations in both Sales and Supply Chain Management, and price calculations for sales orders and sales quotations in Sales. The exposure of feature statuses to Dataverse helps ensure consistency of feature statuses between the two apps. In Supply Chain Management version 10.0.37 and later, after you enable the features in Feature management, you can turn both functionalities on or off by using the **Accounts receivable parameters** page (as described in the next section).

## <a name="config-parameters"></a>Configure extra efficiency in quote-to-cash with Dynamics 365 Sales

After you've completed the initial setup, you can configure the features that you enabled in the previous section. The configuration settings that are available depend both on which features you've enabled in Feature management and which version of Supply Chain Management you're running. In Supply Chain Management versions 10.0.34 through 10.0.36, several features are managed by using Feature management only. However, as of version 10.0.37, these features can also be managed by using the **Accounts receivable parameters** page (after they're enabled in Feature management).

To open the configuration settings, follow these steps.

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Dynamics 365 Sales integration** tab, set the fields that are described in the following table. A tooltip is also provided for each field on the page.

    | FastTab | Field | Required features | Description |
    |---|---|---|---|
    | **General** | **Integrate quotation lifecycles** | *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | <p>Enable or disable the functionality that's added by the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature. All other fields on the **General** FastTab require that this option is enabled.</p><p>For more information about this functionality, see [Add efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-concept.md).</p><p>This option requires Supply Chain Management version 10.0.37 or later. In previous versions, use Feature management to turn this feature on or off.</p> |
    | **General** | **Copy quotation data to sales orders** | <p>*Integrate Sales Quotation lifecycle with Dynamics 365 Sales*</p><p>*Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales*</p> | <p>Enable or disable the functionality that's added by the *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales* feature.</p><p>For more information about this functionality, see [Copy Supply Chain Management sales quotation data to sales orders synced from Sales](add-efficiency-in-quote-to-cash-use.md#copy-quotation-data).</p><p>This option requires Supply Chain Management version 10.0.37 or later. In previous versions, use Feature management to turn this feature on or off.</p> |
    | **General** | **Make Supply Chain Management price master** | <p>*Integrate Sales Quotation lifecycle with Dynamics 365 Sales*</p><p>*Make Supply Chain Management price master when integrated with Dynamics 365 Sales*</p> | <p>Enable or disable the functionality that's added by the *Make Supply Chain Management price master when integrated with Dynamics 365 Sales* feature.</p><p>For more information about this functionality, see [Make Supply Chain Management the price master](add-efficiency-in-quote-to-cash-use.md#scm-price-master).</p><p>This option requires Supply Chain Management version 10.0.37 or later. In previous versions, use Feature management to turn this feature on or off.</p> |
    | **General** | **Use message processor** | <p>*Integrate Sales Quotation lifecycle with Dynamics 365 Sales*</p><p>*Process Dynamics 365 Sales integration related events*</p> | <p>Enable or disable the functionality that's added by the *Process Dynamics 365 Sales integration related events* feature.</p><p>For more information about this functionality, see [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md).</p><p>This option requires Supply Chain Management version 10.0.37 or later. In previous versions, use Feature management to turn this feature on or off.</p> |
    | **General** | **Calculate and push prices** | <p>*Integrate Sales Quotation lifecycle with Dynamics 365 Sales*</p><p>*Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales*</p> | <p>Enable or disable the functionality that's added by the *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* feature.</p><p>For more information about this functionality, see [Calculate and push prices, discounts, and totals from Supply Chain Management to Sales](add-efficiency-in-quote-to-cash-use.md#push-to-sales).</p><p>This option requires Supply Chain Management version 10.0.37 or later. In previous versions, use Feature management to turn this feature on or off.</p> |
    | **Message processor** | **Messages per task** | *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | <p>Set the maximum number of messages from the *Dynamics 365 Sales integration* queue that the message processor can process in a single batch task.</p><p>For more information about this field, see [Set message processor options](add-efficiency-in-quote-to-cash-use.md#processor-options).</p> |
    | **Message processor** | **Create quotation journal in batch** | *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | <p>Specify whether the message processor creates quotation journals asynchronously. Asynchronous creation improves performance when a quotation is activated in Sales.</p><p>For more information about this option, see [Set message processor options](add-efficiency-in-quote-to-cash-use.md#processor-options).</p> |
    | **Message processor** | **Create quotation confirmation journal in batch** | *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | <p>Specify whether the message processor creates quotation confirmation journals asynchronously. Asynchronous creation improves performance when a quotation is won in Sales.</p><p>For more information about this option, see [Set message processor options](add-efficiency-in-quote-to-cash-use.md#processor-options).</p> |
    | **Message processor** | **Copy quotation data to sales order in batch** | *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | <p>Specify whether the message processor copies quotation data to sales orders asynchronously. Asynchronous copying improves performance when a quotation is won in Sales.</p><p>For more information about this functionality, see [Copy Supply Chain Management sales quotation data to sales orders synced from Sales](add-efficiency-in-quote-to-cash-use.md#copy-quotation-data).</p> |
    | **Message processor** | **Calculate and push prices and totals in batch** | *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* | <p>Specify whether the message processor runs the *Push price and totals*, *Calculate sales order totals for Sales*, and *Calculate sales quotation totals for Sales* processes asynchronously. Asynchronous runs improve performance.</p><p>For more information about this functionality, see [Choose whether to process and push totals synchronously or asynchronously](add-efficiency-in-quote-to-cash-use.md#synch-async).</p> |
    | **Sales quotation** | **Default ownership** | <p>*Integrate Sales Quotation lifecycle with Dynamics 365 Sales*</p><p>*Set default ownership for sales quotations when integrated with Dynamics 365 Sales*</p> | <p>Set the owner of the sales quotations (Supply Chain Management or Sales).</p><p>For more information about this functionality, see [Set the default ownership for all sales quotations](add-efficiency-in-quote-to-cash-use.md#default-ownership).</p> |

## Troubleshooting

After you enable the **Integrate quotation lifecycles** functionality, if the sales quotation lifecycle flow doesn't work as expected for newly created sales quotations, follow these steps. For more information about each step, see the [Step 2: Enable mappings in Supply Chain Management](#enable-mappings) section.

1. In Supply Chain Management, go to **System administration** \> **Workspaces** \> **Data management**.
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
