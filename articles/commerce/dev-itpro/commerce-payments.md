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

## Key terms

| Term | Description |
|---|---|
| Commerce payment | A string of data that a payment processor provides as a reference. Tokens can represent payment card numbers, payment authorizations, and previous payment captures. Tokens are important because they help keep sensitive data out of the point of sale (POS) system. |
| Order completion | **Enable order completion** is a setting that forces orders to go thgrough a set of validation rules before they can be cofirmed. For more details, visit the [Enable order completion](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-order-processing-options#enable-order-completion) section of the [Set up call center channels](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-order-processing-options) topic. 
| Call Center order | An order created in the back office by a Call Center user. |

## Overview

Dynamics 365 Commerce consists of 3 main channels: Point of Sale, e-Commerce, and Call Center. Until now, management of payment lines for orders created in those channels has not been uniform. For example, when creating and editing orders the Call Center there is an order completion flow that ensures payments are designated for those orders prior to fulfillment. Alternatively, POS and e-commerce orders have not supported Call Center order completion. The primary way to observe this lack of parity is by observing orders on the **Customer service** form in the back office and observing which orders have an active link to the **Payments** form. 

Order created in Call Center:

COP_CC_PAY

Order created in the point of sale:

COP_NONCC_PAY

This feature essentially enables access to the payments form for orders created in e-commerce and the point of sale. In addition, with this feature enabled, those orders can be edited using the order completion function that was previously only available to Call Center orders. When order completion is enabled, business logic enforces that those order have payments available prior to submittal for processing. 

Order completion:

COP_ORDERCOMPLETION

## Key scenarios enabled by Omni-channel order payments

### Editing order payments

When this feature is enabled, e-commerce order payments can easily be managed through order completion. If a customer places an online order, then calls into the Call Center to request a change to the order, the order completion function will allow for the payments on that order to be adjusted to support the new balance due.

### Cancelling order payments

Support cancellation of uncaptured payments for non-Call Center orders through order completion.

### Linked refund 

Return orders for non-Call Center orders generated in the back office can execute linked refunds against the credit card used to pay for the original order.

### Unlinked refund

Return orders can be refunded to a credit card other than the one used to pay for the original order. 



recall a customer that has orders created in the POS and in the Call CenterThe result is that non-Call Center orders have not had the same back office payment management capabilities as orders created in Call Center. 

This feature enables back office management of payments applied to orders originating from the e-commerce storefront and point of sale by leveraging Call Center order completion capabilities.



## Prerequisite features

To enable Omni-Channel order payments, you first must enable several other features. These features should be enabled as a best practice because they address functional gaps related to orders. After OCOP has been enabled, some these features may be disabled, but that is discouraged because all testing for OCOP has been done with these features enabled.

| Feature name | Description | May be disabled later |
| --- | --- | --- |
| Omni-channel payments | Enables omni-channel payment scenarios such as buy online, pick up in store. For more information, visit the [Omni-channel payments overview](https://docs.microsoft.com/en-us/dynamics365/commerce/omni-channel-payments) topic. | No | 
| Unified payment posting journal defaults for Commerce | When this feature is enabled, business logic will be changed in regards to how customer payment and customer refund payment journals are created for orders created through Call Center, POS or e-Commerce channels. For more information, visit the [Unified payment posting journal defaults for Commerce](TBD) topic. | Yes |
| Duplicate payment protection on invoicing | This feature will enable duplicate payment protection for invoicing scenarios. It may affect customizations in invoicing scenarios. If your organization has customizations in this feature area, please ensure these customizations are refactored prior to enabling this option on production environments. | Yes |
| Enable refunds over multiple captures | This feature addresses an issue with performing multiple linked refunds against an order. | Yes |

## Prerequisite configurations

map operations to payment methods

Need a call center

Need to be call center user

Need to enable order completion. https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-order-processing-options#enable-order-completion

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
