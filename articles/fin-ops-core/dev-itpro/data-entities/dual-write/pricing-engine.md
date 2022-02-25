---
title: Sync on-demand with the Supply Chain Management pricing engine
description: This topic describes how to use the pricing engine in Microsoft Dynamics 365 Supply Chain Management from Dynamics 365 Sales.
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
    4. Under the **Trade agreement evaluation** fastab, remove the **Manual entry** entry.

## How it works

When you select **Price Order** in Sales, the **Totals** function on the **Sales Order \> View** tab in Supply Chain Management is called for the associated sales order. The values in the order total in Sales are used to fill in the corresponding columns in Supply Chain Management.

When the sales order total is calculated in Supply Chain Management, the calculation evaluates the existing trade agreements for the customer and the products that are listed in the sales order. This information is used to calculate the totals. When **Price Order** is selected, Sales automatically reflects all the setup that has been done in Supply Chain Management.

## Trade agreement evaluation

Trade agreement evaluation Manual entry controls whether or not the sales price  entered in Dynamics 365 Sales is allowed to be automatically overruled by the Microsoft Dynamics 365 Supply Chain Management pricing engine. When Manual entry is not present in the Trade agreement evaluation setup, then Microsoft Dynamics 365 Supply Chain Management is the price master. When **Price Order** or **Price Quote** is selected on the Action Pane in Dynamics 365 Sales,  the Microsoft Dynamics 365 Supply Chain Management pricing engine is called and the sales price entered in Dynamics 365 Sales is overwritten; unless it is equal to what is calculated in Microsoft Dynamics 365 Supply Chain Management. In the case, where the sales price entered in Dynamics 365 Sales is required to not be automatically overwritten, when **Price Order** or **Price Quote** is selected in Dynamics 365 Sales, then Manual entry must be present in the Trade agreement evaluation setup. Zero sales price in Dynamics 365 Sales is however treated as an exception. A zero sales price in Dynamics 365 Sales is considered no sales price. This regardless of the setup of Trade agreement evaluation, whereas a sales price different from zero is respected depending on the Trade agreement evaluation setup. 

Consider the following scenarios: 
In Microsoft Dynamics 365 Supply Chain Management, Trade agreement evaluation setup does not include Manual entry. In Microsoft Dynamics 365 Supply Chain Management there is no sales price.
In Dynamics 365 Sales, a user create an order line with the sales unit price of 1 USD. 
The order line is created with a sales unit price of 1 in Dynamics 365 Sales and synched to Microsoft Dynamics 365 Supply Chain Management with a sales price of 1.
In Dynamics 365 Sales, the user select **Price Order** on the Action Pane. 
The order line in Microsoft Dynamics 365 Supply Chain Management is updated with a sales unit price of 0 and synched to Dynamics 365 Sales. The end result is a order line in Dynamics 365 Sales with a sales price of zero. 

In Microsoft Dynamics 365 Supply Chain Management, Trade agreement evaluation setup includes Manual entry. In Microsoft Dynamics 365 Supply Chain Management there is a sales price in trade agreements of 2 USD.
In Dynamics 365 Sales, Orders, a user create an order line with the sales unit price of zero. 
The order line is created with a sales unit price of 0 in Dynamics 365 Sales. When synched to Microsoft Dynamics 365 Supply Chain Management the pricing engine is called since a zero sales price is input. The pricing engine returns a sales price of 2 and updates the order line in Microsoft Dynamics 365 Supply Chain Management. It is not yet synched to the order line in Dynamics 365 Sales.
In Dynamics 365 Sales, the user select **Price Order** on the Action Pane. 
The order line in Microsoft Dynamics 365 Supply Chain Management sales line price remains at 2 and is synched to Dynamics 365 Sales. The order line sales price in Dynamics 365 Sales is updated from zero to 2. 
Had the user in Dynamics 365 Sales entered a sales price of 1 instead of zero, then the sales price on the order line in Microsoft Dynamics 365 Supply Chain Management would have been created with sales price 1. When in Dynamics 365 Sales, the user selects **Price Order** on the Action Pane, the price would not change. 

## Limitations

When the columns in Sales are filled in, the following limitations apply:

+ The setup of charges and charge allocations in Supply Chain Management isn't replicated in Sales.
+ Pricing doesn't consider special retail pricing that is specified in the **Retail Channel** column on the sales order line page in Supply Chain Management.
+ Discounts that are defined in the **Trade Allowance Management** section of Supply Chain Management aren't considered.
+ Pricing doesn't consider sales agreements.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
