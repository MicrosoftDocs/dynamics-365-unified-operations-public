---
title: Sync on-demand with the Supply Chain Management pricing engine
description: This topic describes how to use the pricing engine in Microsoft Dynamics 365 Supply Chain Management from Dynamics 365 Sales.
author: RamaKrishnamoorthy
ms.date: 03/10/2019
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: rhaertle
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2020-01-06
---

# Sync on-demand with the Supply Chain Management pricing engine

[!include [banner](../../includes/banner.md)]



Microsoft Dynamics 365 Supply Chain Management includes a pricing engine that handles trade agreements, price lists, customer loyalty programs, promotions, and discounts. The pricing engine uses complex rules to determine the best price for a given quotation or order. When you use dual-write, you use either static pricing or the pricing engine from Dynamics 365 Supply Chain Management on the Quote and Order pages in Dynamics 365 Sales.

## Use the pricing engine from Supply Chain Management in Sales

1. In Sales, go to **Sales \> Orders**.
2. Select **New** to create a new order, or select an existing order in the **My Orders** list.
3. Add a new order line.
4. If you're creating a new order, select **Price Order** on the Action Pane. If you're updating an existing order, select **Recalculate** on the Action Pane.

    The following columns are automatically filled in:

    + Detail Amount
    + Discount %
    + Discount
    + Pre-Freight Amount
    + Freight Amount
    + Total Tax
    + Total Amount
    
5. To ensure that the system considers trade agreements to calculate the price:
    1. Navigate to your Supply Chain Management environment.
    2. Navigate to **Accounts receivable \> Setup \> Accounts receivable parameters**.
    3. Select the **Prices** tab in the side navigation bar.
    4. Under the **Trade agreement evaluation** fastab, uncheck the **Manual entry** option.

## How it works

When you select **Price Order** in Sales, the **Totals** function on the **Sales Order \> View** tab in Supply Chain Management is called for the associated sales order. The values in the order total in Sales are used to fill in the corresponding columns in Supply Chain Management.

When the sales order total is calculated in Supply Chain Management, the calculation evaluates the existing trade agreements for the customer and the products that are listed in the sales order. This information is used to calculate the totals. When **Price Order** is selected, Sales automatically reflects all the setup that has been done in Supply Chain Management.

## Limitations

When the columns in Sales are filled in, the following limitations apply:

+ The setup of charges and charge allocations in Supply Chain Management isn't replicated in Sales.
+ Pricing doesn't consider special retail pricing that is specified in the **Retail Channel** column on the sales order line page in Supply Chain Management.
+ Discounts that are defined in the **Trade Allowance Management** section of Supply Chain Management aren't considered.
+ Pricing doesn't consider sales agreements.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
