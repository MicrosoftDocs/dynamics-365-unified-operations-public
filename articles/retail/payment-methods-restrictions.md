---
# required metadata

title: Restrict payment methods for returns without a receipt
description: This topic describes how certain payment types can be restricted for refund if the returns are made without a receipt.
author: rapraj
manager: AnnBe
ms.date: 03/05/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailTenderTypeTable
# ROBOTS: NOINDEX, NOFOLLOW
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 15831
ms.assetid: 465893a5-6b4f-4c5f-b305-db071df2d33f
ms.search.region: global
ms.search.industry: Retail
ms.author: yabinl
ms.search.validFrom: 2019-02-01
ms.dyn365.ops.version: AX 10.0.0, Retail Feb 2019 update


---

# Restrict payment methods for returns without a receipt


[!include [banner](includes/banner.md)]

Each payment type that a retailer accepts must be configured when the system is set up. This topic describes how certain payment types can be restricted for refund if the returns are made without a receipt.

## Set up payment methods

To set up payment methods, the following tasks must be completed.
1. Create the payment methods that are accepted by the entire organization.
2. Create organization-wide card types and card numbers. If credit cards or debit cards are accepted, you must create one payment method for cards, and then create the organization-wide card types and card numbers.
3. Set up store payment methods. Associate payment methods with each store, and then enter the store-specific settings for each payment method.
4. Set up card payment methods for stores. For any card payment methods that the store accepts, complete the card setup.

![Retail Store Setup](media/NoReceiptReturns1.png "Retail Store Setup") 


## Restrict payment methods for returns without a receipt

For each store payment method, on the **Retail store management** page, under **Non receipt returns**, set **Restrict for refunds without receipt** to **Yes**. 

The default value of the toggle is **No**, which ensures that the payment method is allowed for refunds. 

When **Restrict for refunds without receipt** is set to **Yes**, the selected payment method will not be allowed for refunds. 

![Retail Store payment method](media/NoReceiptReturns3.png "Retail Store Payment Method") 

> [!NOTE]
> When a cashier selects a payment method that is restricted for refund without a receipt, a message displays to verify the acceptable payment methods.

![Acceptable payment methods](media/NoReceiptReturns4.png "Acceptable payment methods") 

If a transaction has both a receipted return and a return without a receipt, the restriction conditions will not be enforced because the transaction will be a return workflow with a receipt. 

