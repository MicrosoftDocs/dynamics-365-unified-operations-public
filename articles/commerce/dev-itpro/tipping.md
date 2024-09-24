---
title: Support for tipping in the payments SDK
description: This article describes the support for accepting tips on payment terminals in the payments software development kit (SDK).
author: BrianShook
ms.date: 11/18/2020
ms.topic: how-to
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2020-10-31
ms.custom: 
  - bap-template
---

# Support for tipping in the payments SDK

[!include [banner](../includes/banner.md)]

This article describes how the payments software development kit (SDK) for Microsoft Dynamics 365 Commerce supports tip amounts that are entered through a payment terminal. The purpose of this feature is to add first-class support to the payments SDK by including a separate field for the tip amount in authorization responses.

This feature doesn't add support for tipping or tip reporting at the point of sale (POS). Implementation of full tipping capabilities requires POS extensions.

## Key terms

| Term | Description |
|---|---|
| Tips | Tips, which are also known as gratuities, are common in the quick service and hospitality industries. They enable a payment to be given directly to the store or restaurant employee who provides services. |
| Header-level charge | A charge that can be applied to a purchase, but that isn't for a specific line item. |

## Overview of the tipping feature

Tipping is common in some locales and industries. For example, in the quick service and hospitality industries, tipping is now done almost everywhere in the United States. For many businesses, the ability to support tipping through payment terminals is becoming an important factor that helps attract employees. This feature adds a separate **TipAmount** field to the payments SDK, so that tip amounts that are selected on the payment terminal can be sent back to the POS as part of the authorization response.

Although this feature adds support for tipping at the level of the payments SDK, it doesn't include support for other important aspects of tipping functionality. For example, the feature doesn't support reporting of tip payouts at the end of shifts, the ability to pool tips, or the ability to report tips for payroll. To enable full tipping support, you must implement those capabilities through extensions.

For more information about how to create the payment terminal integrations and SDK references that are mentioned in this article, see [Create an end-to-end payment integration for a payment terminal](end-to-end-payment-extension.md).

### Prerequisites

| Prerequisite | Description |
|---|---|
| Tip support on devices | Customers must be able to select a tip amount on the payment terminal. |
| **isTippingEnabled** support | Payment connectors must support the **isTippingEnabled** variable for payment initialization. |
| **TipAmount** field | The tip amount must be returned from the payment connector in the **TipAmount** field of the authorization response. |
| POS tip support through extension | The tip amount that is returned from the payment connector should be added to the sale as a header-level charge. Tip reporting and management aren't provided out of the box. |

### Tipping support by payment processors

This feature adds a new **isTippingEnabled** variable to the **AuthorizePaymentTerminalDeviceRequest** request. When a payment is requested from the POS, this variable indicates whether the authorization request is eligible to have a tip added. Payment connectors that receive this request can then request a tip-eligible authorization from the connected payment service or terminal.

When the **isTippingEnabled** variable is set to **True**, if a customer selects a tip amount on the payment terminal, that amount should be returned in the **TipAmount** field of the **AuthorizePaymentCardPaymentResponse** response that is returned from the payment connector. The tip amount is also included in the **ApprovedAmount** field of the authorization response.

### Tipping support for the Adyen connector

The Adyen connector includes tip support. Customization is required to set the **isTippingEnabled** variable to **True** when the authorization response is passed to the connector. When the **isTippingEnabled** variable is set to **True**, if a customer selects a tip amount on the device, that amount should be returned in the **TipAmount** field of the authorization response.

Before a customer can be prompted to select a tip amount on the Adyen terminal, the terminal must be configured for tipping. This configuration is done through the Adyen customer area. To enable tipping, select the **Point of Sale** tab in the Adyen portal. Tipping can be enabled by terminal or through the fleet-wide **Terminal settings** option. In both the settings for individual terminals and the fleet-wide terminal settings, tipping is enabled on the **Payment features** tab. After tipping is enabled on your Adyen device, settings on the device must be updated. The change won't take effect until this update is done.

### Suggested implementation

We recommend that a header-level charge be used to add the tip amount to the transaction after the authorization response is returned from the payment connector. To support this functionality, an extension should be created for the **PaymentTerminalAuthorizePaymentRequestHandler** handler. That extension should include logic to add a header-level charge to the transaction if a **TipAmount** value is returned in the authorization response.

## Additional resources

- [Adyen connector overview](adyen-connector.md?tabs=10-0-14.md)
- [Create an end-to-end payment integration for a payment terminal](end-to-end-payment-extension.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
