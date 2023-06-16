---
title: Sync on-demand with the Supply Chain Management pricing engine
description: This article describes how to use the pricing engine in Microsoft Dynamics 365 Supply Chain Management from Microsoft Dynamics 365 Sales.
author: RamaKrishnamoorthy
ms.date: 03/10/2019
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: sericks
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2020-01-06
---

# Sync on-demand with the Supply Chain Management pricing engine

[!include [banner](../../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management includes a pricing engine that handles trade agreements, price lists, customer loyalty programs, promotions, and discounts. This pricing engine uses complex rules to determine the best price for a given quotation or order. When it's integrated with Dynamics 365 Sales, you can choose whether all price-related calculations are done in Supply Chain Management and then synced to Sales, or whether Sales does selective price-related calculations for quotations and sales orders. You control the behavior by setting the **Use system pricing calculation** option in Sales, at **Settings \> Administration \> System settings \> Sales**. When this option is set to *No*, Supply Chain Management is responsible for all pricing calculations. When it's set to *Yes*, part of the Sales pricing calculation logic is also applied. In the examples later in this article, the **Use system pricing calculation** option is set to *Yes*.

> [!NOTE]
> In Supply Chain Management version 10.0.34, an alternative approach to pricing for sales quotations and sales orders is available. In this approach, Supply Chain Management becomes the price master, and no price-related calculations are done in Sales. This approach goes into effect when the *Make Supply Chain Management price master when integrated with Dynamics 365 Sales* feature is enabled. Note that, per the Microsoft lifecycle policy, the plan is for this feature to become enabled by default six months after it's released, and then mandatory six months after it's enabled by default. For more information about this feature, see [Add efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-concept).

## Use the pricing engine from Supply Chain Management in Sales with Use system pricing calculation equal Yes

1. In Sales, go to **Sales \> Orders**.
1. Select **New** to create a new order, or select an existing order in the **My Orders** list.
1. Add a new order line.
1. If you're creating a new order, select **Price order** on the Action Pane. If you're updating an existing order, select **Recalculate** on the Action Pane.
1. The following columns are automatically filled in:

    - Detail Amount
    - Discount %
    - Discount
    - Pre-Freight Amount
    - Freight Amount
    - Total Tax
    - Total Amount

> [!NOTE]
> A similar process applies when you create quotations.

## How it works

When you create an order in Sales, that order is immediately synced to Supply Chain Management by using the values that you entered in Sales. When you select **Price order** or **Price quote** in Sales, Supply Chain Management calculates the price for each order line, and the total order, based on trade agreement rules that are defined in Supply Chain Management. The new calculated values are then synced back to Sales.

## Set trade agreement evaluation options in Supply Chain Management

You can configure Supply Chain Management to either respect or ignore trade agreements when it calculates the price of an order that was created in Sales. Follow these steps to set up this option.

1. Sign in to your Supply Chain Management environment.
1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Prices** tab, on the **Trade agreement evaluation** FastTab, add or remove the row for the **Manual entry** policy as you require. The presence or absence of this policy controls whether the Supply Chain Management pricing engine will automatically overrule the sales price that was entered in Sales.

    - If the **Manual entry** policy *is not* present in the **Trade agreement evaluation** setup, Supply Chain Management is the price master. When a user selects **Price order** or **Price quote** on the Action Pane in Sales, the Supply Chain Management pricing engine is called, and the sales price that was entered in Sales is overwritten, unless it equals the sales price that is calculated in Supply Chain Management.
    - If the **Manual entry** policy *is* present in the **Trade agreement evaluation** setup, Sales is the price master. The sales price that was entered in Sales is prevented from being automatically overwritten when a user selects **Price order** or **Price quote** on the Action Pane in Sales.
    - Order lines and quotation lines that have a **Price per unit** and/or **Discount** value of *0* (zero) in Sales are treated as a special case. If a relevant trade agreement price is available, Supply Chain Management will *always* apply it to these fields, regardless of the **Trade agreement evaluation** setup.

    For an example of each of these cases, see the scenarios that follow.

## Example scenario 1: Trade agreement evaluation without the Manual entry option

In this scenario, the **Trade agreement evaluation** setup in Supply Chain Management *does not* include the **Manual entry** policy. A Sales user enters an order line that has a non-zero sales price in Sales, and no sales price is defined for the item in Supply Chain Management.

1. In Sales, a user creates an order line that has a **Price per unit** value of 1 US dollar (USD).
1. The order line is synced to Supply Chain Management with a sales price of 1 USD.
1. In Sales, the user selects **Price order** on the Action Pane.
1. Supply Chain Management searches for relevant prices and discounts, and then calculates totals. Because the item has no sales price in Supply Chain Management, the calculation updates the line so that it has a sales price of 0 USD.
1. The new sales price of the line is synced back to Sales.
1. The result is an order line in Sales that has a sales price of 0 USD.

## Example scenario 2: Trade agreement evaluation with the Manual entry option

In this scenario, the **Trade agreement evaluation** setup in Supply Chain Management *does* include the **Manual entry** policy. A Sales user enters an order line that has a non-zero sales price in Sales. Supply Chain Management includes a trade agreement that sets a sales price of 2 USD for the ordered item.

1. In Sales, a user creates an order line for an item that has a **Price per unit** value of 1 USD.
1. The order line is synced to Supply Chain Management with a sales price of 1 USD.
1. In Sales, the user selects **Price order** on the Action Pane.
1. Because the **Trade agreement evaluation** setup in Supply Chain Management includes the **Manual entry** policy, the sales price isn't changed, even though an applicable trade agreement specifies another sales price.
1. The sales price remains unchanged in Sales and in Supply Chain Management.

## Example scenario 3: Trade agreement evaluation for an item that has a sales price of zero in Sales

In this scenario, the **Trade agreement evaluation** setup in Supply Chain Management *does* include the **Manual entry** policy. The Sales user enters an order line that has a sales price of 0 (zero) in Sales. Supply Chain Management includes a trade agreement that sets a sales price of 2 USD for an ordered item.

1. In Sales, a user creates an order line that has a **Price per unit** value of 0 USD and a **Line discount** value of 0 USD.
1. The order line is synced to Supply Chain Management with a sales price of 0 USD.
1. Because it received an order line that has a sales price of 0 (zero), Supply Chain Management calls its pricing engine, even though the **Manual entry** option is enabled. The pricing engine returns the sales price of 2 USD that is established by the trade agreement and updates the order line in Supply Chain Management.
1. The updated sales price isn't yet synced to the order line in Sales.
1. In Sales, the user selects **Price order** on the Action Pane.
1. The order line in Supply Chain Management keeps its sales price of 2 USD, which is now synced back to Sales. Therefore, the **Price per unit** value of the order line in Sales is updated from 0 USD to 2 USD.
1. In Sales, the user enters a new **Line discount** value of 0.50 USD. Sales now calculates that the **Extended amount** value for the line is 1.50 USD.
1. The order line is synced to Supply Chain Management with a **Line discount** value of 0.50 USD.
1. In Sales, the user selects **Price order** on the Action Pane.
1. No prices or discounts change for the order line in Sales.

## Limitations

When the columns in Sales are filled in, the following limitations apply:

- The setup of charges and charge allocations in Supply Chain Management isn't replicated in Sales.
- Pricing doesn't consider special retail pricing that is specified in the **Retail Channel** column on the sales order line page in Supply Chain Management.
- Discounts that are defined in the **Trade Allowance Management** section of Supply Chain Management aren't considered.
- Pricing doesn't consider sales agreements.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
