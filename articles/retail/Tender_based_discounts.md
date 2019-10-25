---
# required metadata

title: Tender based discounts
description: This topic provides an overview of functionality that enables retailers to configure discounts for certain tender types.
author: bebeale
manager: AnnBe
ms.date: 10/25/19
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailTenderDiscount
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: Version 10.0.7

---

# Tender based discounts

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

It is common practice for retailers to release private branded credit cards. Retailers benefit from getting preferred rates from the banks, and the credits cards can result in an increase in the frequency that customers visit the store, thus directly improving the bottom line of the retailer. Because of these benefits, retailers are motivated to increase the usage frequency of their branded credit cards. To achieve this goal, retailers often provide additional discounts for using the cards. 

Alternatively, retailers who don't provide branded cards may want to motivate customers to pay by alternate means such as cash, gift card, or loyalty, thereby reducing the expense in credit card processing fees. Those retailers provide discounts for these alternate tender types.

With Dynamics 365 Retail, retailers can configure a discount percentage to be applied on qualified lines if the user pays using the preferred tender. The customer can choose to do partial payment or a full payment, and Retail determines the appropriate discount amount. It's important to note that the discount is given on the pre-tax amount of the qualified items. These discounts do not compete with item-based discounts such as periodic/manual discounts and they are always compounded over the item discounts. This means that even if an exclusive periodic discount is applied on the item, the tender-based discount will still be applied on top of the exclusive discount. Similarly, if a threshold discount is applied on the transaction and the tender-based discount reduces the total below the threshold, the threshold discount will remain on the transaction. Even though tender discounts reduce the subtotal of the transaction, the auto-charges applied on the transaction are not affected. For example, if the the delivery charges are calculated to be $5 because the subtotal was above $100, and tender-based discounts reduce the amount to below $100, the delivery charge amount will still be $5 for the order.

> [!NOTE]
> The tender-based discount is proportionally distributed on the qualified sales lines and reduces the pre-tax amount of the individual lines. In case multiple tender-based discounts are configured for a tender type (for exampple, cash), then the best tender-based discount will apply.

The tender-based discount can only be applied to sales lines for which the prices are not locked. If an order is modified and new sales lines are added to the order, the tender-based discount will only be applicable to the new sales lines during payment. While placing a customer order for pickup or shipping, the discount will only be applied to the deposit amount, because once the order is placed, during fulfillment, the prices of the sales lines are locked and any balance paid during pickup or authorized during shipping won't result in a tender-based discount. To provide the tender-based discount on the entire amount of customer orders, the retailer must collect the entire amount as a deposit up front.

> [!NOTE]
> Currently in Retail, these discounts are restricted to two payment types; credit cards and cash. 

## Point of sale (POS) user experience
If the tender-based discount is set up for cash and the cashier hits a button that is mapped to the pay cash operation, the tender-based discount will automatically get applied to the transaction and the reduced amount will be shown as the balance. However, if the cashier hits the back button on the payment screen, the discount will be removed and the cashier will see the original amount on the transaction screen. The tender-based discount gets removed if the payment line is voided.

For cards payments, the retailer may set the discount on one or more types of credit cards but unlike cash payments, the system can't verify the type of card used unless the card is authorized. If the discount gets applied after authorization, the payment authorization wwill be for a higher amount, but the payment capture will be for a lower amount. To avoid this situation, if a customer chooses to pay with a card, a dialog is displayed to the user listing the cards which will result in additional savings. The cashier could then ask the customer if he wants to use one of the preferred cards to get additional discount. If the cashier chooses the preferred card, then the tender-based discount will be applied on the transaction and the reduced amount will be shown on the payment screen and the authorization will be also be for the reduced amount. If the user inserts a different card than the one selected by the cashier, then the system will throw an error message and the authorization will be voided.

## Call center user experience
When the user selects **Complete** during a call center order, the **Totals** screen is displayed. The totals on this screen initially don't include any tender-based discounts because the payment method has not been selected. On the **Add payment** screen, if the user chooses the payment method for which the tender-based discount is configured, the payment amount is adjusted automatically to show the discounted amount. As on POS, the user can choose to pay the full payment or partial payment. Based on the paid amount, the tender-based discount will be applied to the sales order.

> [!NOTE]
> Card validation is not performed for call center orders. For example, if the call center user selected Visa card, but Master card is used, the system will still apply the discount.

## Exclude items from discounts 
The **Prevent all discounts** configuration setting for products will, when turned on, exclude the item from all types of discounts. This setting is generally used for new or in-demand items to maximize profits. However, tender-based discounts are still applied on the items. If the retailer wants to prevent all product-specific discounts, for example, if the retailer wants to prevent periodic and manual discounts but still tender-based discounts enabled, they need to turn off the **Prevent all discounts** and **Prevent tender-based discounts** configurations, and turn on **Prevent retail discounts** and **Prevent manual discounts** configurations. 

> [!NOTE]
> When **Prevent all discounts** is turned on, no discounts, including tender-based discounts, will be applied to the product. 

