---
# required metadata

title: Tender-based discounts
description: This article describes tender-based discount functionality that lets retailers configure discounts for specific tender types in Microsoft Dynamics 365 Commerce.
author: bebeale
ms.date: 08/19/2022
ms.topic: article
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2018-10-31

---

# Tender-based discount

[!include [banner](includes/banner.md)]

This article describes tender-based discount functionality that lets retailers configure discounts for specific tender types in Microsoft Dynamics 365 Commerce.

It's a common practice among retailers to release private, branded credit cards. The retailers benefit because they get preferred rates from the banks. Additionally, because these credits cards can encourage customers to visit the store more often, they help improve the retailer's bottom line. Therefore, retailers have an incentive to increase customer use of their branded credit cards. To achieve this goal, they often provide additional discounts to customers who use these credit cards.

Alternatively, retailers who don't provide branded credit cards might want to encourage customers to pay by using other tender types, such as cash, gift cards, or loyalty points. In this way, they can help reduce the expense of credit card processing fees. Therefore, retailers might provide discounts to customers who use these alternative tender types.

## Tender-based discount

Commerce supports a *tender-based discount* that lets retailers configure a discount percentage that is applied to a transaction if the transaction total exceeds a specific amount and the customer pays by using the preferred payment type. The tender-based discount is tier-based, so that different discount percentages can be associated with different amount thresholds. The customer can decide whether to do a partial payment or a full payment, and the pricing engine determines the appropriate discount amount. The tender-based discount is always given on the pre-tax amount of the sales lines.

The tender-based discount can be applied only to sales lines where the prices aren't locked, and it's proportionally distributed to the qualified lines. If new sales lines are added to an order, the tender-based discount is applied only to the new sales lines during payment. When a customer order for pickup or delivery is being placed, the tender-based discount is applied only to the deposit amount. After the order is placed, during fulfillment, the prices of the sales lines are locked. No tender-based discount is applied to any balance that is paid during pickup or authorized during shipment. The tender-based discount can be applied to the whole amount of a customer order only if the retailer collects the whole amount as a deposit while the order is being placed.

Tender-based discounts don't compete with item-based discounts such as simple discounts, quantity discounts, threshold discounts, mix and match discounts, and manual discounts. Tender-based discounts are always compounded over the item-based discounts. Therefore, even if an exclusive discount is applied to an item, the tender-based discount can still be applied on top of the exclusive discount. Likewise, if a threshold discount is applied to the transaction, and the tender-based discount reduces the total below the threshold, the threshold discount is still applied to the transaction.

Even though tender-based discounts reduce the subtotal of a transaction, automatic charges that are applied to the transaction aren't affected. For example, if the delivery charges are calculated as $5 because the subtotal was more than $100, and the tender-based discount reduces the amount so that it's less than $100, the delivery charges remain $5 for the order.

The tender-based discount is currently limited to two payment types: credit cards and cash. If multiple tender-based discounts are configured for a payment type, only the best tender-based discount is applied.

## POS user experience

If a tender-based discount is set up for cash, and a cashier at the point of sale (POS) selects the **Pay cash** button to check out a cash and carry transaction, the tender-based discount is automatically applied to the transaction. The reduced amount is then shown as the balance. However, if the cashier selects the **Back** button on the payment screen, the discount is removed, and the original amount is shown on the transaction screen. The tender-based discount is removed if the payment line is voided.

For credit card payments, retailers can set the tender-based discount on one or more types of credit cards. However, the system can't verify the type of credit card that is used unless the card is authorized. If the discount is applied after authorization, the payment authorization will be for a larger amount, but the payment capture will be for a smaller amount. To help prevent this situation, if a customer pays with a credit card, the cashier is prompted by a dialog box that lists any preferred credit cards that will give the customer an additional discount. The cashier can then ask whether the customer wants to use one of the preferred cards to get an additional discount. If the cashier selects a preferred card, the tender-based discount is applied to the transaction, and the reduced amount is shown on the payment screen. The authorization will be for the reduced amount. If the customer inserts a card that differs from the card that the cashier selected, an error message is shown, and the authorization is voided.

## Call center user experience

If a call center user selects **Complete** during a call center order, the **Totals** screen appears. At first, the totals on this screen don't include tender-based discounts, because the payment method hasn't yet been selected. On the **Add payment** screen, if the user selects the payment method that the tender-based discount is configured for, the payment amount is automatically adjusted so that it reflects the discounted amount. Like a customer at the POS, the call center customer can decide whether to pay the full payment or a partial payment. Based on the amount that is paid, the tender-based discount is applied to the sales order.

> [!NOTE]
> Card validation isn't done for call center orders. For example, if the call center user selects Visa as the credit card, but the customer uses Mastercard, the system still applies the discount.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
