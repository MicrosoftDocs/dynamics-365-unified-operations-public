---
# required metadata

title: Saving online payment instruments with the Adyen connector
description: This topic describes how to save payment instruments using the Adyen connector for e-commerce.
author: rubendel
manager: AnnBe
ms.date: 04/07/2019
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

[!include [banner](../includes/banner.md)]

This topics describes the setup and capabilities related to saving payment instruments when using the Adyen card not present payment connector for e-commerce. 

## Key terms

| Term | Description |
|---|---|
| Token | A string of data that is provided by payment processors to be used as a reference. Tokens can represent payment card numbers, payment authorizations and previous payment captures. Tokens are important because they help to keep sensitive data out of the point of sale system.   |
| Card token | A token that is provided by the payment processor for storage in the point of sale system. This card token can only be used by the merchant receiving the token and is generally harmless outside of the system. May also be referred to as 'Card reference'. Recurring card token |
| Auth(orization) token | When a point of sale system makes an authorization request to a payment processor, the payment processor will provide a unique ID back to the point of sale system as part of the response to that request. This authorization token, or authorization reference, can later be used when calling the processor to perform actions such as reversing or voiding the authorization. Most commonly the authorization token is used to capture funds when an order is fulfilled or a transaciton is being finalized. |
| List PI | The capability described in this document is often generically referred to as "List PI". List PI refers to the ability to save payment instruments and list previously used payment instruments during subesquent checkouts in through the same e-commerce website.
| Named user | An e-commerce customer who is logged into the online storefront at the time of checkout. Named users have a unique customer ID and their online purchases are always mapped to the same customer ID when they are signed into the online storefront. 

## Overview

When creating an e-commerce order, it is common for retailers to offer to save a customer's payment card information for future transactions. This topic describes how that capabiliy is delivered through the Dynamics 365 Payment Connector for Adyen. While supoprted out of box by the Adyen payment connector, 3rd party payment connectors will require customization to uptake this support. In addition, not all payment processors may support the same method of saving payment card information. 

The out of box implementation of this feature relies on the payment processor to retain a mapping of an online customer's unique ID to payment instruments that have previously processed through the same payment connector. In order for a customer to have the option to save their payment card information for the next online visit, the customer must be signed into the website as a "named user". Customers who use a "guest checkout" option when creating an online order will not be able to save payments for subsequent transactions. 

### Prerequisites

This capability requires an e-commerce integration to Microsoft Dynamics 365 for Retail, a payment conenector that is compatible with the capability, and a payment processor that maps customer unique IDs to the payment instruments that they wish to save with that payment processor. 

For more information about implementing payment connectors and the retail SDK in general visit the [Retail for IT pros and developers home page](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/dev-retail-home-page#payment-connectors).

### Setup

This capability requires the following components and setup steps:

**E-commerce integration:** An online storefront integration to Microsoft Dynamics 365 for Retail. For more information related to the Retail e-commerce SDK, visit the [e-Commerce platform software development kit (SDK)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/ecommerce-platform-sdk) topic.

**Online payments configuration:** Out of box, List PI is supported by the Dynamics 365 Payment Connector for Adyen. To configure payments for online stores, visit the [Adyen payment connector topic](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce). 

In addition to the e-commerce setup steps, provided in the link above, set the "Allow saving payment information in e-commerce" parameter to 'Yes'. 

**Omni-channel payments configuration:** In the back office, navigate to Retail --> Headquarters setup --> Parameters --> Retail shared parameters. Select the "Omni-channel payments tab and set "Use omni-channel payments" to 'Yes'. 

### Functional experience

#### Checkout as guest

When an e-commerce visitor opts for guest checkout, a customer record will not be created during checkout and they will not be able to to save payments for their next visit. 

#### Named customer checkout

When a named customer navigates to the payments section of the checkout, they will experience List PI. If it is the first checkout for a signed in customer, they will see as part of the credit card entry form an option to "Save for my next visit

![Save payment option](media/PAYMENTS/DUPLICATE-PAYMENT-PROTECTION/Save-PI.png)

The retail payment SDK relies on two sets of payment APIs. The first, is called iPayment processor. This set of APIs is used to implement card not present payment connectors for use in call center and e-commerce. More information about the iPaymentProcessor interface can be found in this [whitepaper](http://download.microsoft.com/download/4/D/7/4D7C6B05-0C23-4C6C-BA13-AB62ED08AA61/The%20Guide%20to%20Implementing%20Payment%20Connector%20and%20Payment%20Device.docx) covering payments. 

The second set of APIs is called iNamedRequestHandler. This set of APIs is the supported method of implementing card present payment integrations that utilize a payment terminal. This set of APIs is documented in the [Create a payment intgration for a payment terminal](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension) document. 

### Basic priciple supporting omni-channel payments

Payment connectors and payment processors utilize references, or tokens, to reference interactions related to card payments. For example, when a payment authorization is requested, a reference to that authorization is provided so that authorization can be used later. This authorization is unique to the merchant, payment connector, and processor. 

When and authorization is created in a channel, the details related to that authorization are created in the context of that channel. When that authorization is refernced later, that same context must be presented for the payment processor to map the requested action to the previous authorization. 

In practice, this means that if an order that was created online is being picked up in the store, the same payment details for that order must also be recalled and used. When those original details are provided as part of the request to capture a payment against the original authorization, the payment processor will understand the request and be able to to capture the payment. 

On order to properly reference the online order, a card not present payment connector which supports the same processor must also be available. Using the same example, the point of sale might have one processor for card present payments, but also have access to other payment connectors in order to fulfill orders created in different channnels using different payment processors. 

#### Deployed payment connectors example

| Channel | Action | Payment connector in use |
| --- | --- | --- |
| Online | Order is created and authorization is saved | Payment connector 'A' implemented using iPaymentProcessor |
| Point of sale | Online order is recalled along with details instructing Payment connector 'A' to be used | Payment connector 'A' implemented using iPaymentProcessor | 
| Point of sale | Card present payments for point of sale transactions | Payment connector 'B' implemented using iNamedRequestHandler |



- **[Section name](#Section name)** – This section is a section.

## Supported scenarios

The out-of-box Dynamics 365 Payment Connector for Adyen uses the standard payments SDK. Therefore, it doesn't have special capabilities that aren't also available to other payment connectors. 

### Supported Versions

#### Microsoft Dynamics 365 Supported Versions
