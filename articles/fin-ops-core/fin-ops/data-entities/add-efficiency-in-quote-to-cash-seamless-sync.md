---
title: Enable and configure seamless sync with Dynamics 365 Sales (preview)
description: Learn how to enable, configure, and use seamless sync when Microsoft Dynamics 365 Sales is integrated with the pricing engine in Dynamics 365 Supply Chain Management. 
author: adpattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: CustParameters
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Enable and configure seamless sync with Dynamics 365 Sales (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.42 GA -->

Microsoft Dynamics 365 Supply Chain Management includes a sophisticated pricing engine that handles trade agreements for prices and discounts. This pricing engine uses complex rules to determine the best price for a given order or quotation. When Supply Chain Management is integrated with Dynamics 365 Sales, you can either [sync on demand by using the Supply Chain Management pricing engine](pricing-engine.md) or use *seamless sync*, as described in this article.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

With seamless sync, users who work on sales orders and sales quotations in Sales can view the results of calculations that the Supply Chain Management pricing engine does, without having to take any extra steps to get prices, discounts, and totals. As the users work in Sales, all the necessary data and calculation results are seamlessly synced between systems as required.

Seamless sync significantly improves scenarios where front-end staff mainly work in Sales to create and update sales orders and sales quotations. As users add or update order and quotation lines in Sales, updated line prices, discounts, and totals are calculated in Supply Chain Management and immediately reflected in the Sales user interface (UI), without requiring any extra taps or clicks. In most cases, users don't have to manually select **Price quote** or **Price order** in Sales to get updated line prices, discounts, and totals that show the results of calculations that are done in Supply Chain Management.

## Prerequisites

Before you can use seamless sync, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.42 or later.
- You must be running [Dual-write Supply Chain solution](https://appsource.microsoft.com/product/dynamics-365/mscrm.dwscm) version  2.3.4.367 or later.
- You must enable and configure the basic Sales integration as described in [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md) and [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md).
- The following features must be turned on in [Feature management](../get-started/feature-management/feature-management-overview.md):

    - *Make Supply Chain Management price master when integrated with Dynamics 365 Sales* – This feature is a prerequisite for the next feature. Learn more about it in [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md).
    - *Automatically synchronize line data and totals with Dynamics 365 Sales* – This feature adds the capabilities that are described in this article.

## Turn on and configure seamless sync

To turn on and configure seamless sync, follow these steps.

1. Go to **Accounts receivable** \> **Accounts receivable setup** \> **Accounts receivable parameters**.
1. On the **General** FastTab, set the following fields:

    - **Make Supply Chain Management price master** – You must set this option to *Yes* before you can enable either of the auto-sync options. Learn more about this option in [Make Supply Chain Management the price master](add-efficiency-in-quote-to-cash-use.md#scm-price-master).
    - **Auto sync line data to Sales** – Set this option to *Yes* if data (including line prices and discounts) from sales order and sales quotation lines in Supply Chain Management should automatically be synced to Sales when a line is created or updated in Sales. The data that is synced includes more than just monetary data, such as unit prices, line discounts, and net amounts. It also includes all mapped line data on the appropriate order and quotation lines that are set up for synchronization from Supply Chain Management to Sales. Additionally, it includes data such as requested ship and requested receipt dates, which might be recalculated when lines are entered.

        The benefit of this functionality is that, when users who create and update sales order or sales quotation lines in Sales save those lines, the same line values that are shown in Supply Chain Management are also shown in Sales. Therefore, this functionality ensures full transparency and alignment of data across systems, and removes the need to trigger additional synchronization from Supply Chain Management.

    - **Auto sync totals to Sales** – Set this option to *Yes* if sales order and sales quotation subtotals and totals should automatically be calculated and synced between systems when lines are added, deleted, or changed in Sales. You can set this option to *Yes* only if the **Auto sync line data to Sales** is also set to *Yes*.

We recommend that you set both auto-sync options to *Yes*. This configuration provides the best experience to users who work on sales orders and sales quotations in Sales. It ensures that line monetary data, subtotals, and totals are updated in both systems whenever a user changes a relevant value (such as a line quantity) in Sales. If you set these options to *No*, users must manually select **Price quote** and/or **Price order** after they create or edit orders or quotations in Sales to trigger the calculation and synchronization.

You might choose to set one or both options to *No* if you're using custom pricing logic in Sales, or if your front-end staff who work in Sales work only with line unit prices, not with discounts, charges, sales taxes, totals, and subtotals.

## Nonzero unit prices entered in Sales

If a user enters a unit price other than 0 (zero) for a sales order or sales quotation line in Sales, that unit price is also synced and applied to the sales quotation line in Supply Chain Management. In this case, Supply Chain Management doesn't apply additional calculations to the line data.

## Manual line discounts

If users should be able to add manual line discount amounts to sales order and quotation lines in Sales, be sure to set the **Copy quotation data to sales orders** option to *Yes* on the **Dynamics 365 Sales Integration** FastTab of the **Accounts receivable parameters** page. Otherwise, when the quotation is won in in Sales, manual line discounts aren't synced to Supply Chain Management. Learn more in [Copy Supply Chain Management sales quotation data to sales orders synced from Sales](add-efficiency-in-quote-to-cash-use.md#copy-quotation-data).

## Cases where manual synchronization is required even when seamless sync is used

In two cases, users in Sales must select **Price Quote** or **Price Order** before line prices and discounts are recalculated and synced between systems:

- The date type that is used to retrieve the sales price is *Today*.
- Suggested prices are applied in Sales, but actual prices are stored in trade agreements in Supply Chain Management.

The following subsections explain these cases through examples.

### Case 1: Price data type is Today

In this case, your setup has one sales price of 20 US dollars (USD20) that is effective from August 28 and another sales price of USD19 that is effective from September 1. Price lists aren't applied in Sales.

- **Trade agreement price for August 28:** USD20
- **Trade agreement price for September 1:** USD19

On August 28, a sales order is created in Sales. It has one line that has a line unit price of USD20. On September 1, a second order line for the same item is added. It has a line unit price of USD19, because the new trade agreement price has gone into effect.

According to standard Supply Chain Management behavior, the line price of USD19 applies only to the second line. The price of the first line isn't automatically changed. However, if the user in Sales selects **Price order** on or after September 1, both lines are repriced according to the trade agreement evaluation policy. Therefore, both lines show a unit price of USD19.

> [!NOTE]
> This case also applies to sales quotations.

### Case 2: Sales price lists coexist with Supply Chain Management trade agreements

In this case, suggested sales prices are stored in a Sales price list, whereas actual agreed-on and customer-specific prices are stored in trade agreements in Supply Chain Management. The following prices are defined for the same item:

- **Sales price list price:** USD25
- **Supply Chain Management trade agreement price:** USD19

The trade agreement evaluation policy in Supply Chain Management excludes manual entry.

A salesperson creates a sales order in Sales and adds a line for the item. The line unit price for this line is USD25, which represents the suggested sales price from the price list. The sales order line is then saved and synced to Supply Chain Management.

If the salesperson opens the order in Sales and selects **Price order**, the line is repriced according to the trade agreement evaluation policy in Supply Chain Management. Therefore, the line unit price in Supply Chain Management is updated to USD19 and synced back to Sales.

In general, when Supply Chain Management is the price master, we don't recommend that you use suggested prices that are defined in Sales price lists. However, if your company uses a process like the one that is described in this subsection, salespeople must be trained to select **Price order** after they create a sales order.

> [!NOTE]
> This case also applies to sales quotations.

## Example scenarios for working with seamless sync

The following subsections provide examples of the user experience for seamless sync.

### Example scenario 1: Create a sales quotation in Sales with full seamless sync

#### Prerequisites for scenario 1

This scenario is based on the following system setup:

- The **Auto sync line data to Sales** option is set to *Yes* on the **Accounts receivable parameters** page.
- The **Auto sync totals to Sales** option is set to *Yes* on the **Accounts receivable parameters** page.
- Price lists aren't used in Sales. (Alternatively, price lists are used in Sales, and the base sales price for released products in Supply Chain Management is 0 \[zero\].)

#### User story for scenario 1

Sarah is a salesperson at Contoso, where she works in Sales every day. On Monday, Sarah uses Sales to create a sales quotation. She saves the quotation and adds more lines.

After Sarah finishes adding lines to the sales quotation and saving them, Sales shows the following message on the **Summary** tab of the **Quote** page: "Syncing from F&O." This message indicates that a matching sales quotation is being created in Supply Chain Management, and that data is being synced between the two systems. When synchronization is completed, the "Syncing from F&O" message disappears.

Sarah inspects the sales quotation in Sales and sees that the price per unit, discount, and extended amounts were correctly updated and show the results of the calculations that Supply Chain Management did. All line discounts are included, including multiline discounts that Supply Chain Management applied. Other line data is also synced from Supply Chain Management, such as requested ship and requested receipt dates. Sarah can view this information on the **Integration** tab for the sales quotation line on the **Quote** page in Sales.

In Sales, Sarah can view subtotals and totals for the detail amount, discount (total discount), freight amount (the sum of line and header charges that are automatically added in Supply Chain Management), total tax (the sum of line and header taxes that are automatically added in Supply Chain Management), and total amount. All this information was calculated by and automatically synced from the sales quotation in Supply Chain Management.

In this scenario, Sarah doesn't have to select **Price Quote** in Sales. The sales quotation in Sales is up to date and aligned with the values from the sales quotation in Supply Chain Management.

> [!NOTE]
> The scenario for creating sales orders and sales order lines works in a similar way.

### Example scenario 2: Edit sales quotation lines in Sales with full seamless sync

#### Prerequisites for scenario 2

This scenario is based on the same system setup as scenario 1.

#### User story for scenario 2

On Tuesday, Sarah from the previous scenario learns that her customer wants to increase the quantity of items on the sales quotation that she created for them on Monday. She opens the quotation in Sales, edits the quantity for the relevant line, and saves the change. The system syncs the updated line to Supply Chain Management, which triggers the relevant recalculations. As in scenario 1, Sales shows the "Syncing from F&O" message during this process. Sarah doesn't have to select **Price quote** to trigger the process.

> [!NOTE]
> The scenario for updating sales orders and sales order lines works in a similar way.

### Example scenario 3: Create a sales quotation in Sales without automatic synchronization of totals

#### Prerequisites for scenario 3

This scenario is based on the same system setup as scenario 1, except the **Auto sync totals to Sales** option is set to *No* on the **Accounts receivable parameters** page.

#### User story for scenario 3

Fabrikam use seamless sync without the **Auto sync totals to Sales** option. Charlie is a salesperson at Fabrikam, where he works in Sales every day. On Wednesday, Charlie creates a sales quotation and adds lines to it.

After Charlie finishes adding lines to the sales quotation and saving them, Sales shows the following message on the **Summary** tab of the **Quote** page: "Syncing from F&O." This message indicates that a matching sales quotation is being created in Supply Chain Management, and that data is being synced between the two systems. When synchronization is completed, the "Syncing from F&O" message disappears.

Charlie inspects the sales quotation in Sales and sees that the price per unit and extended amounts were correctly updated and show the results of the calculations that Supply Chain Management did. However, the line discount fields in Sales weren't automatically updated, because that option is disabled in his system. Instead, those fields are blank. Therefore, the extended amounts that are shown in Sales might not be aligned with the actual values in Supply Chain Management. Additionally, Charlie sees subtotals and totals only for the detail amount, pre-freight amount, and total amount, not for the discount (total discount), freight amount, and total tax. The detail amount is the sum of the line extended amounts. In cases where the extended amounts in Sales aren't aligned with Supply Chain Management, the offsets for all subtotal and total calculations that are presented in Sales are incorrect in comparison to Supply Chain Management.

To have the line discounts, subtotals, and totals calculated in Supply Chain Management and synced to Sales, Charlie must select **Price Quote**. The monetary amounts in Sales are then aligned and current with Supply Chain Management.

> [!NOTE]
> The scenario for creating sales orders and sales order lines works in a similar way.

## Limitations

The limitations that are described in [Sync on-demand with the Supply Chain Management pricing engine](pricing-engine.md) still apply when seamless sync is used.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
