---
# required metadata

title: Omni-channel credit card payments overview
description: This topic provides an overview of omni-channel payments for Dynamics 365 for Retail.
author: rubendel
manager: AnnBe
ms.date: 03/21/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Omni-channel payments overview

[!include [banner](../includes/banner.md)]

This topic provides an overview of omni-channel payments support in Microsoft Dynamics 365 for Retail. It includes a comprehensive list of supported features and functionality, setup, troubleshooting information, and descriptions of some common issues.

the Microsoft Dynamics 365 Payment Connector for Adyen. 

## Key terms

> [!NOTE]
> The terms 'token' and 'reference' can be used interchangeably.

| Term | Description |
|---|---|
| Token | A string of data that is provided by payment processors to be used as a reference. Tokens can represent payment card numbers, payment authorizations and previous payment captures. Tokens are important because they help to keep sensitive data out of the point of sale system.   |
| Card token | A token that is provided by the payment processor for storage in the point of sale system. This card token can only be used by the merchant receiving the token and is generally harmless outside of the system. May also be referred to as 'Card reference'. Recurring card token |
| Auth(orization) token | When a point of sale system makes an authorization request to a payment processor, the payment processor will provide a unique ID back to the point of sale system as part of the response to that request. This authorization token, or authorization reference, can later be used when calling the processor to perform actions such as reversing or voiding the authorization. Most commonly the authorization token is used to capture funds when an order is fulfilled or a transaciton is being finalized. |
| Capture token | When a payment is finalized, or captured, the processor provides a reference to that capture back to the point of sale. That capture can be referenced in subsequent operations such as refund requests. | 
| Card not present | Refers to payment transactions where a physical card is presented and used on a payment terminal connector to the Dynamics 365 Point of Sale. |
| Card present | Refers to payment transactions where a physical card is not present, such as E-Commerce or Call Center scenarios. In these scenarios the payment related information is entered manyally either on an E-Commerce website, a Call Center flow, or on the point-of-sale or payment terminal. |

## Overview

This topic provides an overview of omni-channel payment support within Dynamics 365 for Retail. In general, "omni-channel payments" describes the ability to create an order in one channel and fulfill it in another channel. The  key to omni-channel payment support is to preserve payment details with the rest of the order details and to utilize those payments when the order is recalled or processed in another channel.   A classic example of this is "Buy online, pickup in store". In that case, the payment details are added when the order is created online and can be recalled at the point of sale to charge the customer's payment card at the time of pickup. 

All scenarios described in this article can be implemented using the standard payments SDK provided with Microsoft Dynamcis 365 for Retail. The [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3) provides an out of box implementation of each of the scenarios described in this document. 

### Prerequisites

Each of the scenarios described in this document requires a payment connector that supports omni-channel payments. The out of box Adyen connector may also be used as it supports each of the scenarios enabled through the SDK. For more information about implementing payment connectors and the retail SDK in general visit the [Retail for IT pros and developers home page](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/dev-retail-home-page#payment-connectors).

#### Card present and card not present connectors

The retail payment SDK relies on two sets of payment APIs. The first, is called iPayment processor. This set of APIs is used to implement card not present payment connectors for use in call center and e-commerce. More information about the iPaymentProcessor interface can be found in this [whitepaper](http://download.microsoft.com/download/4/D/7/4D7C6B05-0C23-4C6C-BA13-AB62ED08AA61/The%20Guide%20to%20Implementing%20Payment%20Connector%20and%20Payment%20Device.docx) covering payments. 

The second set of APIs is called iNamedRequestHandler. This set of APIs is the supported method of implementing card present payment integrations that utilize a payment terminal. This set of APIs is documented in the [Create a payment intgration for a payment terminal](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension) document. 

### Setup

This capability requires the following components and setup steps:

**E-commerce integration:** An online storefront integration to Microsoft Dynamics 365 for Retail. For more information related to the Retail e-commerce SDK, visit the [e-Commerce platform software development kit (SDK)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/ecommerce-platform-sdk) topic.

**Online payments configuration:** Out of box, List PI is supported by the Dynamics 365 Payment Connector for Adyen. To configure payments for online stores, visit the [Adyen payment connector topic](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce). 

In addition to the e-commerce setup steps, provided in the link above, set the "Allow saving payment information in e-commerce" parameter to 'Yes'. 

**Omni-channel payments configuration:** In the back office, navigate to Retail --> Headquarters setup --> Parameters --> Retail shared parameters. Select the "Omni-channel payments tab and set "Use omni-channel payments" to 'Yes'. 

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

---

# [Buy online, pickup in store](#tab/8-1-3)
### Dynamics 365 for Retail POS version 8.1.3
| Minimum Adyen Firmware Version | Maximum Adyen Firmware Version |
| --- | --- |
| adyen_v1_35p15 | adyen_v1_35p15 |

# [10.0](#tab/10-0)
### Dynamics 365 for Retail POS version 10.0
| Minimum Adyen Firmware Version | Maximum Adyen Firmware Version |
| --- | --- |
| adyen_v1_35p15 | adyen_v1_35p15 |

# [10.0.1](#tab/10-0-1)
### Dynamics 365 for Retail POS version 10.0.1
| Minimum Adyen Firmware Version | Maximum Adyen Firmware Version |
| --- | --- |
| adyen_v1_35p15 | adyen_v1_35p15 |

---

#### Table with checks

| Brand | Variant | Card present | E-Commerce | Call Center |
|---|---|:-:|:-:|:-:|
| MasterCard | Credit | ✔ | ✔ | ✔ |
