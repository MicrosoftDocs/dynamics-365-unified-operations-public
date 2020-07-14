---
# required metadata

title: Omni-channel Commerce order payments
description: This topic describes the Omni-channel Commerce order payments feature.
author: rubendel
manager: Tonya.Fehr
ms.date: 05/13/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Omni-channel Commerce order payments

[!include [banner](../includes/banner.md)]

This topic describes the Omni-channel Commerce order payments feature that enables editing of e-Commerce and POS order payments from the back office.

## Availability

This feature is available starting with the 10.0.13 monthly update.

## Key terms

| Term | Description |
|---|---|
| Commerce payment | A payment associated with a customer order generated at the point of sale or in the e-commerce storefront after this feature has been enabled. |
| Order completion | Order completinn is the business logic in the Call Center that ensures payments have been collector before the order is submitted. The **Enable order completion** setting in call center parameters is used to enable this business logic in Call Center. For more details, visit the [Enable order completion](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-order-processing-options#enable-order-completion) section of the [Set up call center channels](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-order-processing-options) topic. 
| Call Center order | An order created in the back office by a Call Center user. |

## Overview

Dynamics 365 Commerce consists of 3 main channels: Point of Sale, e-Commerce, and Call Center. Until now, management of payment lines for orders created in those channels has not been uniform. For example, when creating and editing orders the Call Center there is an order completion flow that ensures payments are designated for those orders prior to fulfillment. Alternatively, POS and e-commerce orders have not supported Call Center order completion. The primary way to observe this lack of parity is by observing orders on the **Customer service** form in the back office and observing which orders have an active link to the **Payments** form. 

Order created in Call Center:

COP_CC_PAY

Order created in the point of sale:

COP_NONCC_PAY

This feature enables access to the payments form for orders created in e-commerce and the point of sale. In addition, with this feature enabled, those orders can be edited using the order completion function that was previously only available to Call Center orders.  

Order completion:

COP_ORDERCOMPLETION

## Key scenarios

When this feature is enabled, e-commerce and POS order credit card payments can easily be managed through order completion. For example, if a customer places an online order, then calls into the Call Center to request a change to the order, the order completion function will allow for the payments on that order to be adjusted to support the new balance due.

Properties on order line that can be edited prior to payment capture:
- Card type
- Card number
- Payment amount
- Percent amount

For orders that were created in POS or the e-Commerce Storefront, the following scenarios are enabled by this feature: 

### Editing order payments

####Uncaptured card payments

| Scenario | Description | Supported |
| --- | --- |
| **Editing to specify a higher amount** | For card payments which have been authorized, but not yet captured, the payment amount may be increased. When this is done, a new authorization will be created for the new amount and the old authorization will be voided. |
| **Editing to speciry a lower amount** | Card payments which have been authorized, but not yet captured, may be reduced. When a payment line amount is reduced, the previous authorization is cancelled and a new authorization is created for the lower amount. |
| **Removing an old card and adding a new one** | Uncaptured card payment authorizations may be removed from orders and be replaced by a payment on a different card. When this is done, the authorization for the first card is cancelled and an authorization for the new card will be obtained when the order is submitted. |

####Editing partially and fully captured card payments

| Scenario | Description | Supported |
| --- | --- |
| **Editing a payment that has already been used to invoice part of the order** | When an order with Commerce payments has already been partially invoiced, the card payment amount for the existing card may be edited through call center order completion down to the amount that has already been captured. A new card may then be applied to cover the balance due for the order.  |
| **Editing amount when the car payment is fully captured** | If a card payment has already been fully captured, but the amount for that card payment is increased through call center order completion, upon submittal a new authorization for the card will be created for the amount that the payment was increased. |

###Removing order payments

| Scenario | Description |
| --- | --- |
| **Authorized payments** | |
| **Voided** | |
| **Partially captured payments** | If the payment is in a 'Paid' state, but has not been fully captured, then the payment cannot be removed. However, the payment amount can be reduced to the already posted amount and the uncaptured amount will be voided from the authorization. | 
| **Fully captured credit card payments and prepayments** | Cannot be removed from the order. |

### Order and sales line cancellation

**Order cancellation for credit card payments that have not been captured**
Voided

**Order cancellation for credit card payments that have been captured**
Refunded

**Line cancellation**
If an order is modified to cancel an order line, then order completion must be used to complete the process. During order cancellation, the payment amount should be reduced to reflect the new order total. 

### Linked refund 

Return orders for non-Call Center orders generated in the back office can execute linked refunds against the credit card used to pay for the original order.

### Unlinked refund

Return orders can be refunded to a credit card other than the one used to pay for the original order. 

### Orders with prepayments

Prepayments already have payment vouchers associated with them.That meass

## Prerequisite features

To enable Omni-Channel order payments, you first must enable several other features. These features should be enabled as a best practice because they address functional gaps related to orders. After OCOP has been enabled, some these features may be disabled, but that is discouraged because all testing for OCOP has been done with these features enabled.

| Feature name | Description | May be disabled later |
| --- | --- | --- |
| Omni-channel payments | Enables omni-channel payment scenarios such as buy online, pick up in store. For more information, visit the [Omni-channel payments overview](https://docs.microsoft.com/en-us/dynamics365/commerce/omni-channel-payments) topic. | No | 
| Unified payment posting journal defaults for Commerce | When this feature is enabled, business logic will be changed in regards to how customer payment and customer refund payment journals are created for orders created through Call Center, POS or e-Commerce channels. For more information, visit the [Unified payment posting journal defaults for Commerce](TBD) topic. | Yes |
| Duplicate payment protection on invoicing | This feature will enable duplicate payment protection for invoicing scenarios. It may affect customizations in invoicing scenarios. If your organization has customizations in this feature area, please ensure these customizations are refactored prior to enabling this option on production environments. | Yes |
| Enable refunds over multiple captures | This feature addresses an issue with performing multiple linked refunds against an order. | Yes |

## Prerequisite configurations

### Map payment methods to operations to payment methods

This feature requires that payment methods in all channels are mapped to a corresponding operation. This was not previously required, but is neccesary to support management of order payments in the back office. .

Example from Call Center:

COP_OPERATION



Need a call center

Need to be call center user

Need to enable order completion. https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-order-processing-options#enable-order-completion

Disable pay later

## Setup

The List PI capability requires the following components and setup steps:

- **E-commerce integration** – An online storefront integration with Commerce is required. For more information about the e-Commerce SDK, see [e-Commerce platform software development kit (SDK)](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/ecommerce-platform-sdk).
- **Online payments configuration** – The Dynamics 365 Payment Connector for Adyen supports List PI out of the box. For information about how to configure payments for online stores, see [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce). 

    In addition to completing the ecommerce setup steps that are described in that topic, you must set the **Allow saving payment information in e-commerce** option in the Payment accounts fasttab of the **Online store** form to **Yes**. 

- **Omni-channel payments configuration** – In the back office, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. Then, on the **Omni-channel payments** tab, set the **Use omni-channel payments** option to **Yes**. 

## Functional experience

### Guest checkout

When e-commerce visitors choose to check out as guests, customer records aren't created during checkout, and the customers can't save payment instruments for their next visit. 

### Named user checkout

When named users (signed-in customers) go to the payment step of the checkout process, they will experience the List PI capability. The first time that a named user checks out, a **Save for my next payment** check box appears in the section where credit card information is entered. 

![Save for my next payment option](../media/Payments/Save_PI.png)

If this check box is selected, when a new credit card is submitted for payment, the named user's unique customer ID is sent to the payment processor, and the credit card is securely saved and mapped to the that unique customer ID. 

If the same customer signs in during future visits to the storefront, he or she will be able to select the same credit card for payment at checkout. 

![Previously saved payment instrument](../media/Payments/Saved_PI.jpg)

### Order fulfillment and processing

E-Commerce orders where the customer applied a tender line by using the List PI capability work in the same way as orders that were created without using a saved card payment. From the standpoint of order processing and fulfillment, the two types of payment are indistinguishable. 

## Details of eCommerce payment card tokenization

### Standard flow

In e-Commerce integrations, the payment card is typically entered as part of the checkout process and is saved together with the order before finalization. The card details are entered directly on a payment acceptance page that a payment processor provides. After card details are entered and the customer moves on to the next step of the checkout process, the processor creates a token that is used later in the order creation process. 

When the customer finalizes the online order, the payment card token is sent to the payment processor as part of an authorization request. If the payment authorization request is successful, the payment processor replies by sending an authorization token. This authorization token is saved together with the customer's order and is referenced when that order is fulfilled from the back office. 

### List PI flow

The main difference between the standard flow and the List PI flow is that the customer doesn't have to enter the full credit card number. Instead, the customer just has to select a previously saved credit card and provide the Card Verification Value (CVV number). If the customer provides the correct CVV number and moves on to the next step of the checkout process, the payment processor provides a payment card token that will be included in the authorization request. 

## Related articles

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
