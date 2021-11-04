---
# required metadata

title: Tender-based discounts
description: This topic provides an overview of functionality that lets retailers configure discounts for specific tender types.
author: bebeale
ms.date: 10/30/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailTenderDiscount
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: Version 10.0.7

---

# Tender-based discounts

[!include [banner](includes/banner.md)]


It's a common practice among retailers to release private, branded credit cards. The retailers benefit because they get preferred rates from the banks. Additionally, because these credits cards can encourage customers to visit the store more often, they help improve the retailer's bottom line. Therefore, retailers have an incentive to increase customer use of their branded credit cards. To achieve this goal, they often provide additional discounts to customers who use these credit cards.

Alternatively, retailers who don't provide branded credit cards might want to encourage customers to pay by using other tender types, such as cash, gift cards, or loyalty points. In this way, they can help reduce the expense of credit card processing fees. Therefore, retailers might provide discounts to customers who use these alternative tender types.

In Microsoft Dynamics 365 Commerce, retailers can configure a discount percentage that is applied to qualified lines if the customer pays by using the preferred tender type. The customer can decide whether to do a partial payment or a full payment, and Commerce determines the appropriate discount amount. Note that the discount is always given on the pre-tax amount of the qualified items.

Tender-based discounts don't compete with item-based discounts, such as periodic or manual discounts. They are always compounded over the item discounts. Therefore, even if an exclusive periodic discount is applied to an item, the tender-based discount is still applied on top of the exclusive periodic discount. Likewise, if a threshold discount is applied to the transaction, and the tender-based discount reduces the total below the threshold, the threshold discount is still applied to the transaction.

Even though tender-based discounts reduce the subtotal of the transaction, automatic charges that are applied to the transaction aren't affected. For example, if the delivery charges are calculated as $5 because the subtotal was more than $100, and the tender-based discount reduces the amount so that it's less than $100, the delivery charges are still $5 for the order.


> [!NOTE]
> Tender-based discounts are proportionally distributed to the qualified sales lines and reduce the pre-tax amount of the individual lines. If multiple tender-based discounts are configured for a tender type (for example, cash), only the best tender-based discount is applied.

Tender-based discounts can be applied only to sales lines where the prices aren't locked. If new sales lines are added to an order, the tender-based discount is applied to the new sales lines only during payment. While a customer order for pickup or shipment is being placed, the tender-based discount is applied only to the deposit amount. After the order is placed, during fulfillment, the prices of the sales lines are locked. Therefore, no tender-based discount is applied to any balance that is paid during pickup or authorized during shipment. The tender-based discount can be applied to the whole amount of a customer order only if the retailer collects the whole amount as a deposit while the order is being placed.

> [!IMPORTANT]
> In Commerce, tender-based discounts are currently limited to two payment types: credit cards and cash.

## POS user experience

If the tender-based discount is set up for cash, and the cashier at the point of sale (POS) selects a button that is mapped to the Pay cash operation, the tender-based discount is automatically applied to the transaction. The reduced amount is then shown as the balance. However, if the cashier selects the **Back** button on the payment screen, the discount is removed, and the original amount is shown on the transaction screen. The tender-based discount is removed if the payment line is voided.

For cards payments, retailers can set the tender-based discount on one or more types of credit cards. However, the system can't verify the type of credit card that is used unless the card is authorized. If the discount is applied after authorization, the payment authorization will be for a larger amount, but the payment capture will be for a smaller amount.

To help prevent this situation, if a customer pays with a credit card, the cashier sees a dialog box that lists credit cards that will bring the customer additional savings. The cashier can then ask whether the customer wants to use one of the preferred cards to get an additional discount. If the cashier uses a preferred card, the tender-based discount is applied to the transaction, and the reduced amount is shown on the payment screen. The authorization will be for the reduced amount. If the customer inserts a card that differs from the card that the cashier selected, an error message is shown, and the authorization is voided.


## Call center user experience

When the user selects **Complete** during a call center order, the **Totals** screen is shown. At first, the totals on this screen don't include tender-based discounts, because the payment method hasn't yet been selected. On the **Add payment** screen, if the user selects the payment method that the tender-based discount is configured for, the payment amount is automatically adjusted so that it reflects the discounted amount. Like the customer at the POS, the call center customer can decide whether to pay the full payment or a partial payment. Based on the amount that is paid, the tender-based discount is applied to the sales order.

> [!NOTE]
> Card validation isn't done for call center orders. For example, if the call center user selects Visa as the credit card, but the customer uses Mastercard, the system still applies the discount.

## Exclude items from discounts

Retailers often choose to exclude some products, such as new items or in-demand items, from discounts. However, they might still want to apply tender-based discounts. For example, a retailer configures Commerce so that it doesn't allow item-based discounts or manual discounts. However, if the customer pays by using the preferred tender, Commerce still applies the tender-based discount. To set up Commerce in this manner, retailers must go to **Product information management > Products > Released products**, select the item, and then, on the **Commerce** FastTab, set the **Prevent all discounts** and **Prevent tender based discounts** options to **No**, and the **Prevent discounts** and **Prevent manual discounts** options to **Yes**.

> [!NOTE]
> When the **Prevent all discounts** configuration is set to **Yes**, no discounts will be applied to the product. Not even tender-based discounts will be applied.


[!INCLUDE[footer-include](../includes/footer-banner.md)]