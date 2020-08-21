---
# required metadata

title: Process credit cards without a hardware station
description: This topic describes how to configure the point of sale (POS) to process "card not present" transactions in POS clients that don't include a hardware station. 
author: rubendel
manager: AnnBe
ms.date: 08/21/2020
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
ms.author: rubendel
ms.search.validFrom: 2020-08-31
ms.dyn365.ops.version: AX 7.0.1

---

# Process credit cards without a hardware station

[!include [banner](../includes/banner.md)]

This topic describes how to configure point of sale (POS) clients to process "card not present" transactions without a hardware station. This functionality specifically targets emerging scenarios such as curbside pickup. When enabled, clients such as the Cloud POS and Modern POS for iOS can make credit card processing calls through Commerce Scale Unit, rather than depending on a standalone hardware station deployed on the local network. The result is that curbside pickup can be supported on any POS client, and with fewer setup steps. 

> [!NOTE]
> This feature shouldn't be enabled for registers that support offline mode. It routes all "card not present" payment requests through the Commerce Scale Unit, which isn't available when the register goes offline.  

## Key terms

| Term | Description |
|---|---|
| BOPIS | BOPIS is the common abbreviation for "buy online, pick up in store." |
| Curbside pickup | This scenario is similar to BOPIS, but rather than picking the item up in the store, the customer generally doesn't enter the store and in many cases doesn't leave their vehicle. |
| Card not present | Sometimes abbreviated as CNP, "card not present" describes scenarios where the credit card or other form of electronic payment is not phyically present. In  BOPIS and curbside pickup scenarios, the customer makes their payment online or over the phone, and the payment is then captured from the POS at the time of pick up. 
| Hardware station | This term is used to describe the business logic that drives interactions between the POS and payment terminals or retail peripherals such as receipt printers. The hardware station is built into the Modern POS for Windows and Modern POS for Android. Modern POS for iOS and Cloud POS require a standalone deployed hardware station to interact with physical devices. |

## Overview

If this feature isn't enabled, "card not present" credit card requests can't be processed by the Cloud POS or Modern POS for iOS by themselves because they don't have a built-in hardware station. By enabling the feature, the Commerce Scale Unit can be used to facilitate these requests for those clients. Aside from Cloud POS and Modern POS for iOS, this feature can also be used for Modern POS for Windows and Android clients, but it isn't suported for offline mode. For scenarios where a Windows client is using offline mode, this feature shouldn't be used.  

## Supported scenarios

The following scenarios are supported for POS clients that don't have a built-in hardware station. 

| Scenario | Description |
| --- | --- |
| Payment capture | Recall of orders for pickup and capture of the credit card payment associated with the order. |
| Linked refund | Linked refund to the original payment instrument for return orders and cash and carry transactions. |
| Order editing | Orders can be recalled and edited in the POS with the same payment card being authorized to support the new order total. | 
| Order cancellation | Orders that are cancelled can have the balance that is due back to the customer refunded to the original payment card. |

## Unsupported scenarios

Creation of credit card authorizations isn't supported. Only exisitng card payments can be captured, refunded, or edited. 

| Scenario | Description |
| --- | --- |
| Creating payment | Creation of new customer orders and authorization of payments for fulfillment isn't supported by this feature. Creating new payments will continue to require a hardware station. |
| Changing payment card | If an order is recalled in the POS, the same payment method must be used for pickup. If the store associate chooses not to use the card associated with the order, they won't be able to replace it with a different card unless a hardware station is available. |
| Offline | When this feature is enabled, "card not present" requests will always be sent to the Commerce Scale Unit. If a register goes offline, the Commerce Scale Unit is no longer available, so "card not present" requests will fail. This feature shouldn't be enabled for registers that are configured to support offline mode. |

## Set up POS to process "card not present" transactions without a hardware station

The configuration to enable this feature is completed at the register level. In the back office, go to **Retail and Commerce \> Channel setup \> POS setup \> Registers**. Select the relevant register and then select **Edit**. Select the dropdown for **Card not present processing**, select **Use retail server**, and then select **Save**.

![Previously saved payment instrument](../media/Payments/CNP-POS.png)

After the change is saved, run the **1090** distribution schedule to sync the changes to the POS. 

The **Card not present processing** configuration option is set to **Use hardware station** by default. 

## Related articles

- [Omni-channel payments overview](https://docs.microsoft.com/en-us/dynamics365/commerce/omni-channel-payments)
