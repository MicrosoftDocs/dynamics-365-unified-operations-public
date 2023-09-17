---
title: Restrict payment methods for returns without a receipt
description: This article describes how certain payment types can be restricted for refund if the returns are made without a receipt.
author: josaw1
ms.date: 03/05/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2019-02-01
ms.dyn365.ops.version: AX 10.0.0, Retail Feb 2019 update
ms.assetid: 465893a5-6b4f-4c5f-b305-db071df2d33f
ms.search.industry: Retail
ms.search.form: RetailTenderTypeTable
---

# Restrict payment methods for returns without a receipt


[!include [banner](includes/banner.md)]

Each payment type that a retailer accepts must be configured when the system is set up. This article describes how certain payment types can be restricted for refund if the returns are made without a receipt.

## Set up payment methods

To set up payment methods, the following tasks must be completed.
1. Create the payment methods that are accepted by the entire organization.
2. Create organization-wide card types and card numbers. If credit cards or debit cards are accepted, you must create one payment method for cards, and then create the organization-wide card types and card numbers.
3. Set up store payment methods. Associate payment methods with each store, and then enter the store-specific settings for each payment method.
4. Set up card payment methods for stores. For any card payment methods that the store accepts, complete the card setup.

![Store Setup.](media/NoReceiptReturns1.png "Retail Store Setup") 


## Restrict payment methods for returns without a receipt

For each store payment method, on the **Store management** page, under **Non receipt returns**, set **Restrict for refunds without receipt** to **Yes**. 

The default value of the toggle is **No**, which ensures that the payment method is allowed for refunds. 

When **Restrict for refunds without receipt** is set to **Yes**, the selected payment method will not be allowed for refunds. 

![Store payment method.](media/NoReceiptReturns3.png "Retail Store Payment Method") 

> [!NOTE]
> When a cashier selects a payment method that is restricted for refund without a receipt, a message displays to verify the acceptable payment methods.

![Acceptable payment methods.](media/NoReceiptReturns4.png "Acceptable payment methods") 

If a transaction has both a receipted return and a return without a receipt, the restriction conditions will not be enforced because the transaction will be a return workflow with a receipt. 



[!INCLUDE[footer-include](../includes/footer-banner.md)]
