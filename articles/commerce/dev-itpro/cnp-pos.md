---
# required metadata

title: Processing credit cards without hardware station
description: This topic describes how to configure the point of sale to process card not present transactions in POS clients that do not include a hardware station. 
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

# Processing credit cards without hardware station


[!include [banner](../includes/banner.md)]

This topic describes how to configure all POS clients to process card not present transactions without the need for a hardware station. Specifically targeting emerging scenarios such as curbside pickup, this feature removes the need for a hardware station when performing curbside pickup. When enabled, this feature allows clients such as the Cloud POS and Modern POS for iOS make credit card processing calls through Commerce scale unit, rather than depending on a standalone hardware station deployed on the local network. The result is that curbside pickup can be supported with many fewer setup steps. 

> [!NOTE]
> This feature should not be enabled for registers that support offline mode. It routes all card not present payment requests through the Commerce Scale Unit, which is not available when the register goes offline.  

## Key terms

| Term | Description |
|---|---|
| BOPIS | BOPIS is the common abbreviation for buy online, pick up in store. |
| Curbside pickup | This scenario is similar to BOPIS, but rather than picking up in store, the customer generally does not enter the store and in many cases does not leave their car. |
| Card not present | Sometimes abbreviated as CNP, card not present describes scenarios where the credit card or other form of electronic payment is not phyically present. In the case of BOPIS and curbside pickup, the customer makes their payment online or over the phone and the payment is then captured from the point of sale at the time of pick up. 
| Hardware station | Used to describe the business logic that drives interactions between the point of sale and payment terminals or retail peripherals such as receipt printers. The hardware station is built into the Modern POS for Windows and Modern POS for Android. Modern POS for iOS and Cloud POS require standalone deployed hardware station to interact with physical devices. |

## Overview

When this feature is not enabled, card not present credit card requests cannot be processed by the Cloud POS or Modern POS for iOS by themselves due to the fact that they do not have a built-in hardware station. By enabling this feature, the Commerce Scale unit can be used to facilitate these clients for those clients. Aside from Cloud POS and Modern POS for iOS, this feature can also be used for Modern POS for Windows and Android clients, but it is not suported for offline mode, so for cases in which a Windows client with offline mode is used, this feature should not be used.  

## Supported scenarios

This feature enables the following scenarios for point of sale clients that do not have a built-in hardware station. Most of these scenarios are partially supported by these point of sale clients today, but step required to finalize the transaction with the payment processor was not supported prior to this feature.

| Scenario | Description |
| --- | --- |
| Payment capture | Recall of orders for pickup and capture of the credit card payment associate with the order. |
| Linked refund | Linked refund to the original payment instrument for return orders and cash and carry transactions. |
| Order editing | Orders can be recalled and edited in the point of sale with the same payment card being authorized to support the new order total. | 
| Order cancellation | Orders that are cancelled can have the balance due back to the customer refunded to the original payment card. |

## Unsupported scenarios

This feature does not add support for creating credit card authorizations. Only exisitng card payments can be captured, refunded or edited. 

| Scenario | Description |
| --- | --- |
| Creating payment | Creating new customer orders and authorizing payments for fulfillment is not supported by this feature. Creating new payments will continue to require a hardware station. |
| Changing payment card | If an order is recalled in the point of sale, the same payment method must be used for pickup. If the store associate chooses not to use the card associated with the order, they will not be able to replace it with a different card unless a hardware station is available. |
| Offline | When this feature is enabled, card not present requests will always be sent to the Commerce Scale Unit. If a register goes offline, the Commerce Scale Unit is no longer available, so card not present requests will fail. This feature should not be enabled for registers that are configured to support offline mode. |

## Setup

The configuration to enable this feature is at the register level. In the back office, navigate to **Retail and Commerce /> Channel setup \> \> POS setup \> Registers** 

## Related articles

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
