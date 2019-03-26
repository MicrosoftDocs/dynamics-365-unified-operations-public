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

## Overview

This topic provides an overview of omni-channel payment support within Dynamics 365 for Retail. In general, "omni-channel payments" describes the ability to create an order in one channel and fulfill it in another channel. The  key to omni-channel payment support is to preserve payment details with the rest of the order details and to utilize those payments when the order is recalled or processed in another channel.   A classic example of this is "Buy online, pickup in store". In that case, the payment details are added when the order is created online and can be recalled at the point of sale to charge the customer's payment card at the time of pickup. 

All scenarios described in this article can be implemented using the standard payments SDK provided with Microsoft Dynamcis 365 for Retail. The [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3) provides an out of box implementation of each of the scenarios described in this document. 

### Prerequisites

Each of the scenarios described in this document requires a payment connector that supports omni-channel payments. The out of box Adyen connector may also be used as it supports each of the scenarios enabled through the SDK. For more information about implementing payment connectors and the retail SDK in general visit the [Retail for IT pros and developers home page](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/dev-retail-home-page#payment-connectors).


- **[Section name](#Section name)** – This section is a section.

## Supported scenario

The out-of-box Dynamics 365 Payment Connector for Adyen uses the standard payments SDK. Therefore, it doesn't have special capabilities that aren't also available to other payment connectors. 

### Supported Versions

#### Microsoft Dynamics 365 Supported Versions

---

# [8.1.3](#tab/8-1-3)
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
