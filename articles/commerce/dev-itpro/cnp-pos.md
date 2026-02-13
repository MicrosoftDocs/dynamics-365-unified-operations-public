---
title: Process credit cards without a hardware station
description: Learn how to configure the Microsoft Dynamics 365 Commerce point of sale (POS) to process "card not present" transactions in POS clients that don't include a hardware station.
author: BrianShook
ms.date: 02/12/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: shajain
ms.custom: 
  - bap-template
---

# Process credit cards without a hardware station

[!include [banner](../includes/banner.md)]

This article describes how to configure the Microsoft Dynamics 365 Commerce point of sale (POS) to process "card not present" transactions in POS clients that don't include a hardware station. This feature specifically targets emerging scenarios such as curbside pickup.

When you turn on this feature, Store Commerce for web can make credit card processing calls through Commerce Scale Unit because it doesn't require a standalone hardware station that is deployed on the local network. Any POS client can support curbside pickup, and fewer setup steps are required.

> [!NOTE]
> Don't turn on this feature for registers that support offline mode. The feature routes all "card not present" payment requests through the Commerce Scale Unit, but the Commerce Scale Unit isn't available when the register goes offline.

## Key terms

| Term | Description |
|---|---|
| BOPIS | This abbreviation is short for "buy online, pick up in store." |
| Curbside pickup | This scenario resembles BOPIS. However, instead of picking up items in the store, customers don't usually enter the store and often don't even leave their vehicle. |
| Card not present | This term is sometimes abbreviated CNP. It describes scenarios where the credit card or other form of electronic payment isn't physically present. In BOPIS and curbside pickup scenarios, customers make a payment online or over the phone, and the payment is then captured from the POS at the time of pickup. |
| Hardware station | This term describes the business logic that drives interactions between the POS and payment terminals or retail peripherals such as receipt printers. The hardware station is built into the Store Commerce app for Windows, Android and iOS. Store Commerce for web requires a standalone deployed hardware station to interact with physical devices. |

## Overview

When you turn off this feature, Store Commerce for web can't process "card not present" credit card requests by itself because it doesn't have a built-in hardware station. When you turn on the feature, the Commerce Scale Unit can be used to facilitate the requests for Store Commerce for web.

Although this feature can also be used for the Store Commerce app for Windows and Store Commerce app for Android, in addition to Store Commerce for web and Store Commerce app for iOS, it isn't supported for offline mode. Therefore, the feature shouldn't be used in scenarios where a Windows client uses offline mode.

## Supported scenarios

The following scenarios are supported for POS clients that don't have a built-in hardware station.

| Scenario | Description |
|---|---|
| Payment capture | An order can be recalled for pickup, and the credit card payment that is associated with the order can be captured. |
| Linked refund | A refund can be linked to the original payment instrument for return orders and cash-and-carry transactions. |
| Order editing | Orders can be recalled and edited in the POS, and the same payment card can be authorized to support the new order total. |
| Order cancellation | For orders that are canceled, the balance due back to the customer can be refunded to the original payment card. |

## Unsupported scenarios

Creation of credit card authorizations isn't supported. You can only capture, refund, or edit existing card payments.

| Scenario | Description |
|---|---|
| Creating a payment | This feature doesn't support the creation of new customer orders or the authorization of payments for fulfillment. Creation of new payments continue to require a hardware station. |
| Changing the payment card | If you recall an order in the POS, you must use the same payment method for pickup. Store associates can substitute a different card for the card associated with an order only if a hardware station is available. |
| Offline mode | When this feature is turned on, "card not present" requests are always sent to the Commerce Scale Unit. If a register goes offline, "card not present" requests fail, because the Commerce Scale Unit is no longer available. Don't turn on the feature for registers that are configured to support offline mode. |

## Set up the POS to process "card not present" transactions without a hardware station

Complete the configuration to turn on this feature at the register level.

1. In Commerce headquarters, go to **Retail and Commerce > Channel setup > POS setup > Registers**.
1. Select the relevant register, and then select **Edit**.
1. On the **General** FastTab, in the **Card not present processing** field, select **Use retail server**. (By default, this field is set to **Use hardware station**.)

    :::image type="content" source="media/PAYMENTS/CNP-POS.png" alt-text="Screenshot of the Card not present processing field on the register General FastTab.":::

1. Select **Save**.
1. After you save the change, run the **1090** distribution schedule to sync the changes to the POS.

## Additional resources

[Omni-channel payments overview](../omni-channel-payments.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
