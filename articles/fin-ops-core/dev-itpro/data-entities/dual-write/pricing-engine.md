---
title: Sync on-demand with the Supply Chain Management pricing engine
description: This topic describes how to use the pricing engine in Microsoft Dynamics 365 Supply Chain Management from Microsoft Dynamics 365 Sales.
author: RamaKrishnamoorthy
ms.date: 03/10/2019
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: tfehr
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2020-01-06
---

# Sync on-demand with the Supply Chain Management pricing engine

[!include [banner](../../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management includes a pricing engine that handles trade agreements, price lists, customer loyalty programs, promotions, and discounts. The pricing engine uses complex rules to determine the best price for a given quotation or order. When you use dual-write, you use either static pricing or the pricing engine from Supply Chain Management on the **Quote** and **Order** pages in Microsoft Dynamics 365 Sales.

## Use the pricing engine from Supply Chain Management in Sales

1. In Sales, go to **Sales \> Orders**.
1. Select **New** to create a new order, or select an existing order in the **My Orders** list.
1. Add a new order line.
1. If you're creating a new order, select **Price Order** on the Action Pane. If you're updating an existing order, select **Recalculate** on the Action Pane.
1. The following columns are automatically filled in:

    - Detail Amount
    - Discount %
    - Discount
    - Pre-Freight Amount
    - Freight Amount
    - Total Tax
    - Total Amount

## How it works

When you select **Price Order** in Sales, the *Totals* function is called for the associated sales order in Supply Chain Management (this is the same function that is available on the **All sales orders** page in Supply Chain Management by opening the **Sales order** tab on the Action Pane and, from the **View** menu, selecting **Totals**). The values in the order total in Sales are used to fill in the corresponding columns in Supply Chain Management.

When the sales order total is calculated in Supply Chain Management, the calculation evaluates the existing trade agreements for the customer and the products that are listed in the sales order. This information is used to calculate the totals. When **Price order** is selected, Sales automatically reflects all the setup that has been done in Supply Chain Management.

## Set trade agreement evaluation options in Supply Chain Management

You can configure Supply Chain Management to either respect or ignore trade agreements when calculating the price of an order created in Sales. Do the following steps to set up this option: <!-- KFM: It's unclear whether this option only affects trade agreements, or whether it might also affect other types of calculations (e.g., discounts, rebates, other?) -->

1. Sign in to your Supply Chain Management environment.
1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
1. On the **Trade agreement evaluation** FastTab, add or remove the **Manual entry** entry as needed. The presence or absence of this entry controls whether or not the sales price entered in Sales will be automatically overruled by the Supply Chain Management pricing engine. Based on this setting, the system will work as follows:

    - When **Manual entry** *is not* present in the **Trade agreement evaluation** setup, then Supply Chain Management is the price master. When a user selects **Price order** or **Price quote** on the Action Pane in Sales, the Supply Chain Management pricing engine is called and the sales price entered in Sales is overwritten unless it is equal to what is calculated in Supply Chain Management.
    - When **Manual entry** *is* present in the **Trade agreement evaluation** setup, then Sales is the price master. <!-- KFM: Please confirm this first sentence --> This prevents the sales price entered in Sales from being automatically overwritten when a user selects **Price order** or **Price quote** on the Action Pane in Sales. <!-- KFM: Liu Qi has this comment for this point: "I am not very clear about this, how come the **Manual entry** must be present?" (KFM: I may have clarified this...) -->
    - Orders for items that have a sales price of zero in Sales are treated as a special case. Supply Chain Management will always apply the relevant trade agreement price to these items (if available), regardless of the **Trade agreement evaluation** setup. <!-- KFM: I reworded this to match the examples. Please confirm -->  <!-- KFM: Liu Qi has this comment for this point: "Maybe after “A zero sales price in Dynamics 365 is considered no sales price”, we can add “then Microsoft Dynamics 365 Supply Chain Management is the price master”" (KFM: I rewrote this point, so I think that comment doesn't apply anymore, but please confirm.) -->

### Example scenario 1: Trade agreement evaluation without the Manual entry option

In this scenario, the **Trade agreement evaluation** setup in Supply Chain Management *does not* include the **Manual entry** entry. A Sales user enters an order for an item with a non-zero sales price in Sales and there is no sales price defined for the item in Supply Chain Management. <!-- KFM: Here we have no price in SCM; is this related to a trade agreement, or is this coming from somewhere else? -->

<!-- KFM: Are "sales price", "sales unit price", and "sales line price" all the same, or are these different things? We must take care to use each of these terms accurately, or use just one term if they we mean the same thing with each of them. All three terms appeared in the original, but it didn't seem intentional, so I changed these to "sales price" everywhere, which may be incorrect. -->

1. In Sales, a user creates an order line for an item with a sales price of 1 USD.
1. The order line is synched to Supply Chain Management with a sales price of 1 USD.
1. In Sales, the user selects **Price Order** on the Action Pane.
1. Supply Chain Management runs its *Totals* function on the order line, which updates the line to have a sales price of 0 USD. This is because the item has no sales price in Supply Chain Management.
1. The new line sales price is synched back to Sales.
1. The end result is an order line in Sales with a sales price of 0 USD.

### Example scenario 2: Trade agreement evaluation with the Manual entry option

In this scenario, the **Trade agreement evaluation** setup in Supply Chain Management *does* include the **Manual entry** entry. A Sales user enters an order for an item with a non-zero sales price in Sales. Supply Chain Management includes a trade agreement that sets a sales price of 2 USD for the ordered item.

1. In Sales, a user creates an order line for an item with a sales price of 1 USD.
1. The order line is synched to Supply Chain Management with a sales price of 1 USD.
1. Because the **Trade agreement evaluation** setup in Supply Chain Management includes the **Manual entry** entry, the sales price isn't changed (even though an applicable trade agreement specifies another sales price).
1. In Sales, the user selects **Price Order** on the Action Pane.
1. The sales price remains unchanged in Sales and in Supply Chain Management.

### Example scenario 3: Trade agreement evaluation for an item with a sales price of zero in Sales

In this scenario, the **Trade agreement evaluation** setup in Supply Chain Management *does* include the **Manual entry** entry. The Sales user enters an order for an item with a sales price of zero in Sales. Supply Chain Management includes a trade agreement that sets a sales price of 2 USD for an ordered item.

1. In Sales, a user creates an order line for an item with a sales price of 0 USD.
1. The order line is synched to Supply Chain Management with a sales price of 0 USD.
1. Because it received an order line with a sales price of 0, Supply Chain Management calls its pricing engine (even though the **Manual entry** option is enabled). The pricing engine returns the sales price of 2 USD (as established by the trade agreement) and updates the order line in Supply Chain Management.
1. The updated sales price is not yet synched to the order line in Sales.
1. In Sales, the user selects **Price Order** on the Action Pane.
1. The order line in Supply Chain Management keeps its sales price of 2 USD, which is now synched back to Sales. The sales price of the order line in Sales is therefore updated from 0 USD to 2 USD.

## Limitations

When the columns in Sales are filled in, the following limitations apply:

- The setup of charges and charge allocations in Supply Chain Management isn't replicated in Sales.
- Pricing doesn't consider special retail pricing that is specified in the **Retail Channel** column on the sales order line page in Supply Chain Management.
- Discounts that are defined in the **Trade Allowance Management** section of Supply Chain Management aren't considered.
- Pricing doesn't consider sales agreements.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
