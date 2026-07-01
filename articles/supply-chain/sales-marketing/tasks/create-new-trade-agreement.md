---
title: Create a new trade agreement
description: Learn how to create a trade agreement where you register a new product sales price that you've agreed with a specific customer.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: TradeNonStockedConversion, TradeNonStockedConversionChangeWizard, TradeNonStockedConversionCheckWorksheet, TradeNonStockedConversionWizard, TradeNonStockedRegister
ms.topic: how-to
ms.date: 04/22/2026
ms.custom: 
  - bap-template
---

# Create a new trade agreement

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a trade agreement where you register a new product sales price that you agreed on with a specific customer. You can run this procedure in demo data company USMF or on your own data. If you're using your own data, before you start this guide, make sure that a trade agreement journal name exists where the **Default relation** is set to *Price (sales)*.

## Create and post a new trade agreement journal

1. Go to **Sales and marketing > Prices and discounts > Trade agreement journals**.
1. Select **New**.
1. In the **Name** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. On Action Pane, select **Lines**.
1. In the **Party code type** field, select *Table*. In this example, you're updating the price for a specific customer, which means you must choose *Table*. If you were updating the product's list price, you would select *All*, so that the new price is valid for all customers. If you were differentiating prices among different customer segments, then you would select *Group*. To select *Group*, you must have set up customer price groups.  
1. In the **Account selection** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the **Product code type** field, select *Table*. When you're entering a trade agreement of type *Price (sales)*, you must select *Table* in the **Product code type** field. This requirement exists because a price is an absolute value and can't be the same for all products or a group of products.
1. In the **Item relation** field, select the drop-down button to open the lookup.
1. In the list, select the product you want to include in the agreement. Make a note of which product you selected.  
1. In the **From** field, enter a minimum quantity.
    - If the customer has to order a minimum quantity before they can qualify for the new price, specify that quantity here.  
    - Enter a value in the **To** field to specify the maximum quantity above which the agreement's price isn't valid. If you offer prices and discounts based on multiple quantity breaks, specify each quantity bracket as a pair of minimum and maximum quantity in the **From** and **To** fields respectively.
1. In the **Amount in currency field**, enter a price.
1. Under the **Details** section, in the **From date** field, enter a date from which this agreement is valid.
1. Select **Save**.
1. Select **Validate**.
1. Select **Validate selected lines**.
1. Select **OK**.
1. Select **Post**.
1. Select **OK**.

## View trade agreements for a product

1. Go to **Product information management > Products > Released products**.
1. In the list, find and select the product whose price you just updated.
1. On the Action Pane, select **Sell**.
1. Select **View trade agreements**. Review the details of the price trade agreement you just created.
1. Close the page.

## Related information

### White paper

For more information, download the following white paper (written to support AX2012, but still applies for Dynamics 365 Supply Chain Management).

- [Trade agreements](https://download.microsoft.com/download/0/2/9/02972c8b-0159-4936-a3ef-1e64252b2d2f/TradeAgreementsInAX.pdf)

### Community blogs

- [Sales prices in finance and operations](https://financefunction.tech/2018/11/14/sales-prices-in-dynamics-365-for-finance-and-operations/#sales_price_in_trade_agreements)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
