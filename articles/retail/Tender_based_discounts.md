---
# required metadata

title: Tender based discounts for Retail
description: This topic provides an overview of new capability which will allow the retailers to configure discounts for certain tender types.
author: bebeale
manager: AnnBe
ms.date: 10/17/19
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
ms.custom: 260624
ms.assetid: a4f9d315-9951-451c-8ee6-37f9b3b15ef0
ms.search.region: global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: Version 10.0.7

---

# Tender based discounts

[!include [banner](includes/banner.md)]

It has now become a common practice for retailers to release private branded credit cards. Retailers benefit from getting preferred rates from the banks, and according to a study, such credits cards result in an increase in the store visit frequency, thus directly improving the bottom line of the retailer. So, retailers are motivated to increase the usage frequency of such credit cards. To achieve this goal, retailers often provide additional discounts for using these cards. Alternatively, some retailers, who do not provide such cards, want to motivate the customers to pay by alternate means e.g. Cash, Gift card, loyalty etc. and thus reduce the expense in credit card processing fees. Such retailers provide discounts for these alternate tender types.
With this feature, the retailers can configure a discount percentage that would be applied on the qualified lines if the user pays using the preferred tender. The customer can choose to do partial payment, or a full payment and the system determines the appropriate discount amount. It is important to note that the discount is given on the pre-tax amount of the qualified items. These discounts do not compete with the item-based discounts i.e. Periodic/Manual discounts and are always compounded over the item discounts. This means that even if an Exclusive periodic discount is applied on the item, the Tender based discount will still be applied on top of the Exclusive discount. Similarly, if a threshold discount is applied on the transaction and the tender based discount reduces the total below the threshold, the threshold discount will remain on the transaction. Additionally, even though the tender discounts reduce the sub total of the transaction/sales order, this does not affect the auto charges applied on the transaction/sales order. So, if the system calculates the delivery charges to be $5, because the sub total was above $100, but tender based discounts reduces the amount to below 100, the delivery charge amount will still be $5 for the order.
> [!NOTE]
> The tender based discount is proportionally distributed on the qualified sales lines and thus reduce the pre-tax amount of the individual lines. In case multiple tender based discounts are configured for a tender type e.g. cash, then the best tender based discount will apply.

The tender based discount can only be applied to sales lines for which the prices are not locked. This means if an order is modified and new sales lines are added to the order, then, during payment, the tender based discount will only be applicable to the new sales lines. This also means that while placing a customer order for pickup or shipping, the discount will only be applied to the deposit amount because, once the order is placed, then during fulfillment, the prices of the sales lines are locked and thus any balance paid during pickup or authorized during shipping will not result in tender based discount. To provide the tender based discount on the entire amount of customer orders, the retailer would have to collect the entire amount as a deposit upfront.
> [!NOTE]
> With the first release, these discounts are restricted to two payment types namely credit cards and cash. 

## POS user experience
If the tender based discount is set up for Cash and the cashier hits a button that is mapped to Pay cash operation, then the tender based discount will automatically get applied to the transaction and the reduced amount will be shown as the balance. However, if the cashier hits the back button on the payment screen, the discount will be removed, and the cashier will see the original amount on the transaction screen. The tender based discount gets removed if the payment line is voided.
For Cards payment type, the retailer might set the discount on one or more types of credit cards but, unlike cash payments, the system cannot verify the type of card used unless the card is authorized. If the discount gets applied after authorization, then this result in payment authorization for a higher amount, but the payment capture for a lower amount. Thus, to avoid this situation, if a customer chooses to pay with a card, a new dialog is displayed to the user listing the cards which will result in additional savings. The cashier could then ask the customer if he wants to use one of the preferred cards to get additional discount. Based on customer’s response, if the cashier chooses the preferred card, then the tender based discount will be applied on the transaction and the reduced amount will be shown on the payment screen. Thus, the authorization will be also be for the reduced amount. If the user inserts a different card than the one selected by the cashier, then the system will throw an error message and the authorization will be voided.

## Call center user experience
For the call center orders, once the user presses the ‘Complete’ button, the system shows the totals screen. The totals on this screen initially do not include any tender based discounts as the payment method/s have not been selected. On add payment screen, if the user chooses the payment method for which the tender based discount is configured, then the Payment amount is adjusted automatically to show the discounted amount. Like POS, the user can choose to pay the full payment or partial payment. Based on the paid amount, the tender based discount will be applied to the sales order. 
> [!NOTE]
> The card validation is not performed for Call center orders i.e. if the call center user selected Visa card, but Master card is used, then the system will still apply the discount.

## Exclude items from discounts 
There is an existing configuration at the product level named “Prevent all discounts” which, if turned on, excludes the item from all types of discounts. This is generally used for new or in-demand items to maximize the profits. However, the tender based discounts are still applicable on such new/in-demand items. To achieve this, we have now added two more configurations titled “Prevent retail discounts” and “Prevent tender based discounts”. So, if the retailer wants to prevent all the product specific discounts e.g. periodic and manual discounts but want to enable the tender based discounts, so they can turn off the “Prevent all discounts and “Prevent tender based discounts” configurations, and turn on the “Prevent retail discounts” and “Prevent manual discounts” configurations. 
> [!NOTE]
> If the configuration “Prevent all discounts” is turned on, then none of the discounts, including tender based discounts, will be applied to the product. 

