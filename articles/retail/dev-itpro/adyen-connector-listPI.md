---
# required metadata

title: Saving online payment instruments with the Adyen connector
description: This topic describes how to save payment instruments using the Adyen connector for ecommerce.
author: rubendel
manager: AnnBe
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
ms.reviewer: rubendel
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

# Saving online payments with the Adyen connector

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topics describes the setup and functionality related to saving payment instruments when using the Adyen "card not present" payment connector for ecommerce. 

## Key terms

| Term | Description |
|---|---|
| Token | A string of data that is provided by payment processors to be used as a reference. Tokens can represent payment card numbers, payment authorizations, and previous payment captures. Tokens are important because they help to keep sensitive data out of the point of sale system.   |
| Card token | A token that is provided by the payment processor for storage in the point of sale system. This card token can only be used by the merchant receiving the token and is generally harmless outside of the system. May also be referred to as "Card reference". Recurring card token |
| Authorization (Auth) token | When a point of sale system makes an authorization request to a payment processor, the payment processor will provide a unique ID back to the point of sale system as part of the response to that request. This authorization token, or authorization reference, can later be used when calling the processor to perform actions such as reversing or voiding the authorization. Most commonly the authorization token is used to capture funds when an order is fulfilled or a transaciton is being finalized. |
| List PI | The capability described in this document is often generically referred to as "List PI". List PI refers to the ability to save payment instruments and list previously used payment instruments during subesquent checkouts in through the same ecommerce website. |
| Named user | An ecommerce customer who is logged into the online storefront at the time of checkout. Named users have a unique customer ID and their online purchases are always mapped to the same customer ID when they are signed into the online storefront. |

## Overview

When creating an ecommerce order, it is common for retailers to offer to save a customer's payment card information for future transactions. This topic describes how that capability is delivered through the Dynamics 365 Payment Connector for Adyen. While supported out of box by the Adyen payment connector, 3rd party payment connectors will require customization to uptake this support. In addition, not all payment processors may support the same method of saving payment card information. 

The out of box implementation of this feature relies on the payment processor to retain a mapping of an online customer's unique ID to payment instruments that have previously processed through the same payment connector. In order for a customer to have the option to save their payment card information for the next online visit, the customer must be signed into the website as a "named user". Customers who use a "guest checkout" option when creating an online order will not be able to save payments for subsequent transactions. 

## Prerequisites

This capability requires an ecommerce integration to Microsoft Dynamics 365 for Retail, a payment conenector that is compatible with the capability, and a payment processor that maps customer unique IDs to the payment instruments that they wish to save with that payment processor. 

For more information about implementing payment connectors and the retail SDK in general, visit the [Retail for IT pros and developers home page](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/dev-retail-home-page#payment-connectors).

## Setup

This capability requires the following components and setup steps.

**E-commerce integration:** An online storefront integration to Microsoft Dynamics 365 for Retail is required. For more information related to the Retail ecommerce SDK, visit the [eCommerce platform software development kit (SDK)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/ecommerce-platform-sdk) topic.

**Online payments configuration:** Out of box, List PI is supported by the Dynamics 365 Payment Connector for Adyen. To configure payments for online stores, visit the [Adyen payment connector topic](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce). 

In addition to the ecommerce setup steps provided in the link above, set the **Allow saving payment information in e-commerce** parameter to **Yes**. 

**Omni-channel payments configuration:** In the back office, navigate to **Retail > Headquarters setup > Parameters > Retail shared parameters**. Select the **Omni-channel payments** tab and set **Use omni-channel payments** to **Yes**. 

## Functional experience

### Checkout as guest

When an ecommerce visitor opts for guest checkout, a customer record will not be created during checkout and the customer will not be able to  save payments for their next visit. 

### Named customer checkout

When a named customer navigates to the payments section of the checkout, they will experience List PI. If it is the first checkout for a signed in customer, they will see as part of the credit card entry form an option to "Save for my next payment". 

![Save payment option](../media/Payments/Save_PI.png)

When this box is checked, and a new card is submitted for payment, the currently logged in customer's unique ID will be sent to the payment processor and that card will be saved securely and mapped to the customer's unique ID. 

During subsequent visits, if the same customer is logged into the storefront, they will be able to select that same card for payment at checkout. 

![Previously saved payment](../media/Payments/Saved_PI.jpg)

### Order fulfillment and processing

eCommerce orders with a tender line that was applied by a customer using the List PI capability will function in the same way as orders that were created without a saved card payment. From an order processing and fulfillment standpoint, the two types of payments will be indistinguishable. 

## eCommerce payment card tokenization details

### Standard flow

In Microsoft Dynamics 365 for Retail eCommerce integrations, the payment card is typically entered as part of checkout and saved with the order prior to finalization. When the card is entered, the card details are entered directly into a payment acceptance page provided by a payment processor. When the customer proceeds to the next step after payment card entry, the processor creates a token that is used later in the order creation process. 

When the customer finalizes their online order, the payment card token is sent to the payment processor as part of an authorization request. If the payment authorization request is successful, the payment processor will reply with an authorization token. This auth token is saved with the customer's order and referenced when that order is fulfilled from the back office. 

### List PI flow

The key difference between the standard flow and the List PI flow is that, rather than having to enter the full credit card number, the customer is only required to select a previously saved card and provide the card verification value, or CVV. If the customer provides the correct CVV and proceeds to the next step in the checkout process, the payment processor will provide a payment card token that will included in the authorization request. 

## Related articles

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)


