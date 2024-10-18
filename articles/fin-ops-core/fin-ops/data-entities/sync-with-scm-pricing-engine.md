---
title: Seamless sync with the Supply Chain Management pricing engine (preview)
description: Learn how to use seamless sync when integrating the pricing engine in Microsoft Dynamics 365 Supply Chain Management with Microsoft Dynamics 365 Sales.
author: henrikan
ms.author: Henrikan
ms.reviewer: kamaybac
ms.search.form: CustParameters
ms.topic: how-to
ms.date: 10/25/2025
ms.custom: 
  - bap-template
---

# Seamless sync with the Supply Chain Management pricing engine (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Microsoft Dynamics 365 Supply Chain Management includes a sophisticated pricing engine that handles trade agreements for prices and discounts. This pricing engine uses complex rules to determine the best price for a given quotation or order. When Supply Chain Management is integrated with Dynamics 365 Sales, you can choose either to [sync on demand with Supply Chain Management pricing engine](pricing-engine.md) or to apply *seamless sync*, as described in this article.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Seamless sync allows users working on sales orders and quotations in Dynamics 365 Sales to see the results of calculations made by the Supply Chain Management pricing engine without needing to take any extra steps to get prices, discounts, and totals. All the required data and calculation results are seamlessly synced between systems as needed while the user is working in Sales.

This capability significantly improves scenarios where front-end staff predominantly work in Dynamics 365 Sales creating and updating sales quotations and sales orders. As sales quotation/order lines are added or updated in Dynamics 365 Sales, updated line prices, discounts, and totals calculated in Supply Chain Management are immediately reflected in the Dynamics 365 Sales UI without requiring any additional clicks. In most cases, users won't need to select **Price quote** or **Price order** buttons in Dynamics 365 Sales to see line prices, discounts, and totals updated to show calculation results made in Supply Chain Management.

## Prerequisites

To use seamless sync, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.42 or later.
- You must be running Dual-write Supply Chain solution version 2.3.X.XXX or later. <!--KFM: Version number needed  -->
- You must turn on and set up the basic Dynamics 365 Sales integration, as described in [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md).
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)
    - *Make Supply Chain Management price master when integrated with Dynamics 365 Sales* – This is a prerequisite feature. You can learn more about it in [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md).
    - *Automatically synchronize line data and totals with Dynamics 365 Sales* – This feature adds the capabilities described in this topic.

## Turn on and set up seamless sync

To turn on and configure seamless sync, follow these steps:

1. Go to **Accounts receivable** \> **Accounts receivable setup** \> **Accounts receivable parameters**.
1. Open the **Dynamics 365 Sales Integration** tab.
1. Use the settings here to turn on and set up the basic Dynamics 365 Sales integration, as described in [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md) and [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md).
1. On the **General** FastTab, make the following additional settings:
    - **Make Supply Chain Management price master** – You must set this to *Yes* before you can enable either of the auto-sync options. You can learn more about this option in [Make Supply Chain Management the price master](add-efficiency-in-quote-to-cash-use.md#scm-price-master).
    - **Auto sync line data to Sales** – Set to *Yes* to automatically sync sales quotation/order line data (including line prices and discounts) from sales quotation/order lines in Supply Chain Management to Dynamics 365 Sales when a line is created or updated in Dynamics 365 Sales. Synchronized data includes more than just monetary data (such as unit price, line discounts, and net amounts). It also includes all mapped line data in the respective quote/order lines mapping set to sync from Supply Chain Management to Dynamics 365 Sales. This also includes data such as requested ship and requested receipt dates, which are potentially recalculated upon line entry. The benefit of this is that the user creating and updating a sales quotation/order line in Dynamics 365 Sales  will, after saving the line, see the same line values in Dynamics 365 Sales as in Supply Chain Management. This functionality ensures full transparency and no misalignment between the data across systems, removing the need to trigger additional synchronization from Supply Chain Management.
    - **Auto sync totals to Sales** – Set to *Yes* to automatically calculate and sync sales quotation/order subtotals and totals between systems when lines are added, deleted, or changed in Dynamics 365 Sales. You can only set this option to *Yes* when **Auto sync line data to Sales** is also set to *Yes*.

We recommend setting both auto-sync options to *Yes*. This configuration provides the best user experience when working in the Dynamics 365 Sales user interface on sales quotations/orders, ensuring that line monetary data, subtotals, and totals are updated in both systems whenever a user changes a relevant value (such as a line quantity) in Dynamics 365 Sales. If you disable these options, then users must manually select a **Price quote** and/or **Price order** button after creating or editing quotations or orders in Dynamics 365 Sales to trigger the calculation and synchronization.

You might choose to set one or both of these option to *No* if you are using custom pricing logic in Dynamics 365 Sales, or if your front-end staff working in Dynamics 365 Sales only work with line unit prices (not discounts, charges, sales taxes, totals, and subtotals).

## Non-zero unit prices entered in Dynamics 365 Sales

If a user enters a unit price other than 0 (zero) for a quotation/order line in Dynamics 365 Sales, then that unit price is synced and applied to the sales quotation line in Supply Chain Management. Seamless sync won't apply additional calculations to the line data in Supply Chain Management. <!--KFM: This isn't clear. -->

## Manual line discounts

If you want to allow users to add manual line discount amounts to quotation/order lines in Dynamics 365 Sales, then be sure to set the **Copy quotation data to sales orders** option to *Yes* on the **Dynamics 365 Sales Integration** FastTab on the **Accounts receivable parameters** page. Otherwise manual line discounts won't be synchronized to Supply Chain Management when the quotation is won in in Dynamics 365 Sales. Learn more in [Copy Supply Chain Management sales quotation data to sales orders synced from Sales](add-efficiency-in-quote-to-cash-use.md#copy-quotation-data).

## Example scenarios of working with seamless sync

The following subsections present examples of the seamless sync user experience.

### Example scenario 1: Create a sales quotation in Dynamics 365 Sales with full seamless sync

#### Prerequisites for scenario 1

This scenario assumes the system is set up as follows.

- **Auto sync line data to Sales** is set to *Yes* on the **Accounts receivable parameters** page.
- **Auto sync totals to Sales** is set to *Yes* on the **Accounts receivable parameters** page.
- Dynamics 365 Sales isn't using price lists. (Alternatively, price lists are used in Dynamics 365 Sales and the base sales price for released products in Supply Chain Management is 0 (zero).)

#### Scenario 1 user story

Sarah is a salesperson at Contoso, where she works daily in Dynamics 365 Sales. On Monday, Sarah uses Sales to create a sales quotation. She saves the quotation and adds more lines.

After adding and saving lines to the sales quotation, Sarah sees the **Summary** tab of the **Quote** page, which shows the message *Syncing from F&O*. This message indicates that a matching sales quotation is being created in Supply Chain Management and that data is being synchronized between the two systems. When synchronization is complete, the *Syncing from F&O* message disappears.

Sarah inspects the sales quotation in Dynamics 365 Sales and can see that the price per unit, discount, and extended amounts have been correctly updated to show the results of calculations made by Supply Chain Management. All line discounts are included, including multi-line discounts applied by Supply Chain Management. Other line data is also synchronized from Supply Chain Management, including requested ship and receipt dates. Sarah can see this information on the **Integration** tab for the sales quotation line on the **Quote** page in Dynamics 365 Sales

In Dynamics 365 Sales, Sarah can see subtotals and totals for the detail amount, discount (total discount), freight amount (the sum of line and header charges added automatically in Supply Chain Management), total tax (the sum of line and header taxes added automatically in Supply Chain Management), and total amount. All of this information was calculated by and automatically synchronized from the sales quotation in Supply Chain Management.

In this scenario, there is no need for Sarah to select **Price Quote** in Dynamics 365 Sales. The quotation in Sales is current and aligned with the values from the sales quotation in Supply Chain Management.

> [!NOTE]
> The scenario of creating sales orders and order lines works similarly.

### Example scenario 2: Edit sales quotation lines in Dynamics 365 Sales with full seamless sync

#### Prerequisites for scenario 2

This scenario assumes the same system setup as scenario 1.

#### Scenario 2 user story

On Tuesday, Sarah (from the previous scenario) finds out that her customer wants to increase the quantity of items in the sales quotation she made for them on Monday. She opens the quotation in Dynamics 365 Sales and edits quantity for the relevant line and saves the change. The system synchronizes the updated line to Supply Chain Management, which triggers relevant recalculations. As before, Dynamics 365 Sales displays the *Syncing from F&O* message during this process and Sarah doesn't to select the **Price quote** button to trigger it.

When you create an order in Sales, that order is immediately synced to Supply Chain Management by using the values that you entered in Sales. When you select **Price order** or **Price quote** in Sales, Supply Chain Management calculates the price for each order line, and the total order, based on trade agreement rules that are defined in Supply Chain Management. The new calculated values are then synced back to Sales. <!--KFM: Is this right? We just said that the user doesn't need to press those buttons. -->

> [!NOTE]
> The scenario of updating sales orders and order lines works similarly.

### Example scenario 3: Create a sales quotation in Dynamics 365 Sales without auto-sync totals

#### Prerequisites for scenario 3

This scenario assumes the same system setup as scenario 1 except that **Auto sync totals to Sales** is set to *No* on the **Accounts receivable parameters** page.

#### Scenario 3 user story

Fabrikam use seamless sync without the **Auto sync totals to Sales** option. Charlie is a salesperson at Fabrikam, where he works daily in Dynamics 365 Sales. On Wednesday, Charlie creates a sales quotation and adds lines to it.

After adding and saving lines to the sales quotation, Charlie sees the **Summary** tab of the **Quote** page, which shows the message *Syncing from F&O*. This message indicates that a matching sales quotation is being created in Supply Chain Management and that data is being synchronized between the two systems. When synchronization is complete, the *Syncing from F&O* message disappears.

Charlie inspects the sales quotation in Dynamics 365 Sales and can see that the price per unit and extended amounts have been correctly updated to show the results of calculations made by Supply Chain Management. However the line discount fields in Dynamics 365 Sales haven't been updated automatically because that option is disabled for his system. Instead, these fields are blank. The extended amounts presented in Dynamics 365 Sales may therefore not be aligned with the actual value in Supply Chain Management. In addition, Charlie only sees subtotal and total values for detail amount, pre-freight amount, and total amount. He doesn't see subtotals or totals data for discount (total discount), freight amount, or total tax. The detail amount is the sum of the line extended amounts. In cases where the extended amounts in Dynamics 365 Sales aren't aligned with Supply Chain Management, the offset for all subtotal and totals calculations presented in Dynamics 365 Sales are incorrect compared with Supply Chain Management.

To get the line discounts, subtotals, and total amounts calculated in Supply Chain Management and synced to Dynamics 365 Sales, the Charlie must select **Price Quote**. Only then are the monetary amounts in Dynamics 365 Sales be aligned and current with Supply Chain Management.

> [!NOTE]
> The scenario of creating sales orders and order lines works similarly.

## Cases when manual sync is required even when using seamless sync

A few cases exist where Dynamics 365 Sales users will be required to select **Price Quote** or **Price Order** to get line prices and discounts recalculated and synced between systems. Those are cases where suggested prices are applied in Dynamics 365 Sales, but actual prices are stored in trade agreements in Supply Chain Management or where the date type used to retrieve the sales price is *Today*. Each cases is illustrated in the following subsections.

### Case 1: Price data type is Today

Consider a setup where a sales price exists with price USD 20, effective from August 28, and a sales price of USD 19 exists, effective from September 1. (Price lists are not applied in Dynamics 365 Sales.)

- Trade agreement price for August 28: USD 20
- Trade agreement price for September 1: USD 19

A sales order is created in Dynamics 365 Sales on August 28 with a line showing a line unit price of USD 20. A second order line for the same item is added on September 1, but it has a line unit price of USD 19 because the new trade agreement price has come into effect.

Following standard Supply Chain Management behavior, the line price of USD 19 only applies for the second line. It doesn't automatically change the price of the first line. However, if the user in Dynamics 365 Sales selects **Price order** on or after September 1, both lines are repriced in accordance with the trade agreement evaluation policy. Therefore, both lines will show a unit price USD 19.

> [!NOTE]
> This case applies equally to sales quotations.

### Case 2: Dynamics 365 Sales price lists coexists with Supply Chain Management trade agreements

In this case, suggested sales prices are stored in a Dynamics 365 Sales price list, whereas actual agreed-upon and customer-specific prices are stored in trade agreements in Supply Chain Management. The following prices are defined for the same item:

- Dynamics 365 Sales price list price: USD 25
- Supply Chain Management trade agreement price: USD 19

The trade agreement evaluation policy in Supply Chain Management excludes manual entry.

A salesperson creates a sales order in Dynamics 365 Sales and adds a line for the item. The line unit price for this line is USD 25 (representing the suggested sales price from the price list). The sales order line is then saved and synced to Supply Chain Management.

If the salesperson opens the order in Dynamics 365 Sales and select the **Price order** button, then this line is repriced in accordance with the Supply Chain Management trade agreement evaluation policy. The line unit price in Supply Chain Management is therefore updated to USD 19 and synced back to Dynamics 365 Sales.

If your company requires the system to show suggested prices (as stored in price lists in Dynamics 365 Sales) when creating a sales order/quotation, while applying customer-specific prices (stored in trade agreements Supply Chain Management and possibly different from the suggested prices) to the final order, then salespeople must be trained to use the **Price order** button after creating a new order. <!--KFM: Please review this paragraph. -->

> [!NOTE]
> This case equally applies to sales quotation.

## Limitations

The limitations presented in [Sync on-demand with the Supply Chain Management pricing engine](pricing-engine.md) still apply when using seamless sync.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
