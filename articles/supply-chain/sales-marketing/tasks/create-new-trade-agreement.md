---
title: Create a new trade agreement
description: This procedure shows you how to create a trade agreement where you register a new product sales price that you've agreed with a specific customer. 
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: TradeNonStockedConversion, TradeNonStockedConversionChangeWizard, TradeNonStockedConversionCheckWorksheet, TradeNonStockedConversionWizard, TradeNonStockedRegister
ms.topic: how-to
ms.date: 03/06/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---
# Create a new trade agreement

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a trade agreement where you register a new product sales price that you've agreed with a specific customer. You can run this procedure in demo data company USMF or on your own data. If you're using your own data, before you start this guide you need to make sure that a Trade agreement journal name exists where the Default relation is set to "Price (sales)".

## Create and post a new trade agreement journal

1. Go to **Sales and marketing > Prices and discounts > Trade agreement journals**.
2. Select **New**.
3. In the **Name** field, select the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. On **Action Pane**, select **Lines**.
6. In the **Account code** field, select *Table*. In this example, you're updating the price for a specific customer, which means you need to choose *Table*. If you were updating the product's list price, you would select *All*, so that the new price is valid for all customers. If you were differentiating prices among different customer segments, then you would select *Group*. To select *Group*, you must have set up customer price groups.  
7. In the **Account selection** field, select the drop-down button to open the lookup.
8. In the list, find and select the desired record.
9. In the **Item code** field, select *Table*. When you're entering a trade agreement of type 'Price (sales)', you must only select 'Table' in the **Item code** field. This is because a price is an absolute value and can't be same for all products or a group of products.
10. In the **Item relation** field, select the drop-down button to open the lookup.
11. In the list, select the product you want to include in the agreement. Make a note of which product you've selected.  
12. In the **From** field, enter a minimum quantity.
    - If the customer has to order a minimum quantity before they can qualify for the new price, then you need to specify that quantity here.  
    - Enter a value in the **To** field to specify the maximum quantity above which the agreement's price won't be valid. If you offer prices and discounts based on multiple quantity breaks, then specify each quantity bracket as a pair of minimum and maximum quantity in the **From** and **To** fields respectively.
13. In the **Amount in currency field**, enter a price.
14. Under the **Details** section, in the **From date** field, enter a date from which this agreement will be valid.
15. Select **Save**.
16. Select **Validate**.
17. Select **Validate selected lines**.
18. Select **OK**.
19. Select **Post**.
20. Select **OK**.

## View trade agreements for a product

1. Go to **Product information management > Products > Released products**.
2. In the list, find and select the product whose price you have just updated.
3. On the **Action Pane**, select **Sell**.
4. Select **View trade agreements**. Review the details of the price trade agreement you have just created.
5. Close the page.

## Additional resources

### Whitepaper

For more information, download the following white paper (written to support AX2012, but still applies for Dynamics 365 Supply Chain Management)

- [Trade agreements](https://download.microsoft.com/download/0/2/9/02972c8b-0159-4936-a3ef-1e64252b2d2f/TradeAgreementsInAX.pdf)

### Community blogs

- [Sales prices in finance and operations](https://financefunction.tech/2018/11/14/sales-prices-in-dynamics-365-for-finance-and-operations/#sales_price_in_trade_agreements)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
