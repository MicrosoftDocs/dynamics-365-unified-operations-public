---
title: Restrict payment methods for returns without a receipt
description: Learn how certain payment types can be restricted for refund if the returns are made without a receipt in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2019-02-01
ms.assetid: 465893a5-6b4f-4c5f-b305-db071df2d33f
ms.search.form: RetailTenderTypeTable
ms.custom: 
  - bap-template
---

# Restrict payment methods for returns without a receipt

[!include [banner](includes/banner.md)]

This article explains how to restrict certain payment types for refunds when customers return items without a receipt in Microsoft Dynamics 365 Commerce.

You configure each payment type that a retailer accepts during system setup. This article describes how to restrict certain payment types for refunds when customers return items without a receipt.

## Set up payment methods

To set up payment methods, follow these steps:
1. Create the payment methods that the entire organization accepts.
1. Create organization-wide card types and card numbers. If you accept credit or debit cards, you must create one payment method for cards, and then create the organization-wide card types and card numbers.
1. Set up store payment methods. Associate payment methods with each store, and then enter the store-specific settings for each payment method.
1. Set up card payment methods for stores. For any card payment methods that the store accepts, complete the card setup.

:::image type="content" source="media/NoReceiptReturns1.png" alt-text="Screenshot of retail store setup.":::

## Restrict payment methods for returns without a receipt

For each store payment method, on the **Store management** page, under **Non receipt returns**, set **Restrict for refunds without receipt** to **Yes**.

The default value of the toggle is **No**, which ensures that the payment method is allowed for refunds.

When you set **Restrict for refunds without receipt** to **Yes**, the selected payment method isn't available for refunds.

:::image type="content" source="media/NoReceiptReturns3.png" alt-text="Screenshot of retail store payment method.":::

> [!NOTE]
> When a cashier selects a payment method that is restricted for refund without a receipt, a message displays to verify the acceptable payment methods.

:::image type="content" source="media/NoReceiptReturns4.png" alt-text="Screenshot of acceptable payment methods.":::

If a transaction has both a receipted return and a return without a receipt, the restriction conditions aren't enforced because the transaction is a return workflow with a receipt.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
