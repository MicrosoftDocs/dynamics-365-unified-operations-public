---
# required metadata

title: What's new and changed in Dynamics 365 Commerce 10.0.20 (August 2021)
description: This article describes features that are either new or changed in Dynamics 365 Commerce 10.0.20. 
author: josaw1
ms.date: 04/12/2024
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.custom:
  - bap-template
  - evergreen
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2021-04-30 
ms.dyn365.ops.version: 10.0.20

---
# What's new and changed in Dynamics 365 Commerce 10.0.20 (August 2021)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.20. This version has a build number of 10.0.886 and is available on the following schedule:

- **Preview of release:** May 2021
- **General availability of release (self-update):** July 2021
- **General availability of release (auto-update):** July 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature.

Most of these features must be enabled using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them.

| Feature area   | Feature                                                  | More information                                                                    |
|----------------|----------------------------------------------------------|-------------------------------------------------------------------------------------|
| Product dimensions |  Configure product dimension values as swatches in Commerce headquarters.  |  [Configure product dimension values to display as swatches](../dev-itpro/dimensions-swatch.md)|
| Product dimensions |  Configure display settings in Commerce headquarters. |  [Apply display settings for product dimensions](../dimension-settings.md) |
| Point of sale (POS) | Return serial number-controlled products in point of sale (POS) | [Return serial number-controlled products in point of sale (POS)](../pos-serial-returns.md)|
| Point of sale (POS) | Create returns in point of sale (POS) | [Create returns in point of sale (POS)](../pos-returns.md) |
| Point of sale (POS) | [Store commerce app with Chromium rendering engine and integrated hardware support](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/store-commerce-app-chromium-rendering-engine-integrated-hardware-support)  |  [Store Commerce app in Microsoft Dynamics 365 Commerce (Preview)](../dev-itpro/store-commerce.md)  |
| Point of sale (POS)  | [Support inventory adjustments from POS](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/support-inventory-adjustments-pos)  |   Use POS to adjust inventory in or out. |
| Payments  | [Out-of-the-box support for wallet-style payment methods](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/out-of-box-support-wallet-style-payment-methods)  | [Wallet payment support](../wallets.md) |
|  Payments |  [Refactored payment processing in storefront checkout](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/refactored-payment-processing-storefront-checkout)  | This feature reduces the number of authorization requests to the payments processor and adds better support for Strong Customer Authentication (SCA) in the European Union. |
| E-commerce  |  [Enable order lookup for guest customers](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/enable-order-lookup-guest-customers)   | This feature enables look up orders for guest checkouts. |
|   E-commerce|  [Enhanced e-commerce product discovery to be inventory-aware](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/enhanced-e-commerce-product-discovery-be-inventory-aware)  | [Apply inventory settings](../inventory-settings.md)<br>[Search results module](../search-result-module.md) | 
| E-commerce  |  [Enhancements to the e-commerce inventory availability lookup APIs](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/enhancements-e-commerce-inventory-availability-lookup-apis)  |  This feature provides enhancements to the GetEstimatedAvailability and GetEstimatedProductWarehouseAvailability APIs.  |
|  E-commerce   |   [Immersive theme to showcase modern e-commerce site](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/immersive-theme-showcase-modern-e-commerce-site)   | Use this new theme to build modern, immersive experiences on your e-commerce site. |
| Globalization |  [Adyen payment connector for Brazil](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/adyen-payment-connector-brazil)    |  Use the Dynamics 365 Payment Connector for Adyen to support payment operations in stores that are located in Brazil. | 
|  Globalization |   [SAT integration for Brazil](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/sat-integration-brazil)  |  This feature enables fiscal registration of retail sales in a SAT (Sistema Autenticador e Transmissor de Cupons Fiscais Eletrônicos) device connected to a hardware station. | 
| Globalization | Global configuration properties in Commerce site builder can be made visible, hidden, or disabled when specific Commerce features are turned on.  | [Configure site builder global configuration settings based on enabled features](../e-commerce-extensibility/config-settings-for-features.md) |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Commerce 10.0.20 includes platform updates. To learn more, see [Platform updates for version 10.0.20 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-20.md).

### Bug fixes 
For information about the bug fixes that are included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=586707&dbType=3&qc=d0dad8eee2af234e8c288e2a7df14c579004518673d014be511f900cfed008f8).

For Commerce-specific breaking changes, view the [Dynamics 365 Commerce online SDK FAQ](../e-commerce-extensibility/sdk-faq.md).

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

