---
# required metadata

title: What's new or changed in Dynamics 365 Commerce 10.0.26 (May 2022)
description: This article describes features that are either new or changed in Dynamics 365 Commerce 10.0.26. 
author: josaw1
ms.date: 04/22/2022
ms.topic: article
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2022-03-31 
ms.dyn365.ops.version: 10.0.26

---

# What's new or changed in Dynamics 365 Commerce 10.0.26 (May 2022)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.26. This version has a build number of 10.0.1192 and is available on the following schedule:

- **Preview of release:** March 2022
- **General availability of release (self-update):** April 2022
- **General availability of release (auto-update):** April 2022


## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area   | Feature                                                  | More information                                          |  Enabled by             |
|----------------|----------------------------------------------------------|-----------------------------------------------------------|-------------------------|
|   Globalization      |    [Payments in installments with the Dynamics 365 Payment Connector for Adyen for Brazil](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/payments-installments-dynamics-365-payment-connector-adyen-brazil)    |   This feature extends the out-of-the-box Dynamics 365 Payment Connector for Adyen to support paying in installments for Brazil. For more information, see [Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil](../localizations/latam-bra-adyen.md).       | For more information, see [Set up the Adyen payment connector for Dynamics 365](https://docs.adyen.com/plugins/microsoft-dynamics). |
|   Globalization      |    [Sample of direct fiscal integration from POS with EFR](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/direct-fiscal-integration-pos)    |     The feature extends the fiscal integration framework by adding a capability to create fiscal connectors that will be executed in POS. This type of connector will communicate with a fiscal device or service that provides an HTTP API and will not require a dedicated physical machine in the store to be plugged in or deployed on. This release provides a sample of the direct fiscal integration from POS with the Electronic Fiscal Register service (EFR) for [Austria](../localizations/emea-aut-fi-sample.md), [the Czech Republic](../localizations/emea-cze-fi-sample.md), and [Germany](../localizations/emea-deu-fi-sample.md).   | Feature management<p>*Direct fiscal integration from POS registers*<p>Configuration of fiscal registration process |
|   Globalization      |    [Disable fiscal registration for selected POS registers](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/enhanced-fiscal-connector-configuration)    |   The feature extends the fiscal integration framework by adding an option to disable fiscal registration for selected POS registers in a fiscal registration-enabled store. Store associates will be able to use the registers for non-sales operations (such as inventory management operations), and to create sales that can then be completed on fiscal registration-enabled registers. For more information, see [Set up registers with fiscal registration restrictions](../localizations/setting-up-fiscal-integration-for-retail-channel.md#set-up-registers-with-fiscal-registration-restrictions). | Feature management<p>*Fiscal Registration State of POS Registers* |
|  Payments  |   [PayPal Cart Checkout support in e-commerce](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/paypal-cart-checkout-support-e-commerce) | [Dynamics 365 Payment Connector for PayPal](../paypal.md)| Developer opt-in |
| Store Commerce |  [Store Commerce supports dual display to show cart-related information](../retail-peripherals-overview.md) | Dual display shows cart-related information to the customer-facing display and [dual display can be extended to show custom information](../dev-itpro/pos-dual-display-extension.md).| Opt-in |



## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Commerce 10.0.26 includes platform updates. To learn more, see [Platform updates for version 10.0.26 of finance and operations apps (May 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-26.md).

### Bug fixes 
For information about the bug fixes that are included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=662864).

For Commerce-specific breaking changes, view the [Dynamics 365 Commerce online SDK FAQ](../e-commerce-extensibility/sdk-faq.md).

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

