---
title: WHat's new and changed in Dynamics 365 Commerce 10.0.29 (October 2022)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.29. 
author: josaw1
ms.date: 09/29/2022
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29
---

# What's new or changed in Dynamics 365 Commerce 10.0.29 (October 2022)

[!include [banner](../includes/banner.md)]


This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce version 10.0.29. This version has a build number of 10.0.1326 and is available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** September 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---------|------------------|----------------|--------------| 
| B2B | [Enable support for sales agreement across channels](/dynamics365-release-plan/2022wave2/commerce/dynamics365-commerce/enable-b2b-sales-agreement-contract-based-pricing) | This feature enables business-to-business (B2B) seller organizations to use sales agreements in Commerce headquarters to define contract-based pricing for their buyers. When a B2B buyer shops on the e-commerce website, the contract-based pricing that is configured for the B2B buyer organization is automatically applied to the whole product discovery, purchase, and checkout experience. | Feature management<p>*Support for sales agreement across commerce channels* |
| Customer Service | [Enable Customer Service with Dynamics 365 Omnichannel for Customer Service](/dynamics365-release-plan/2022wave2/commerce/dynamics365-commerce/chat-dynamics-365-commerce-omnichannel-customer-service) | A first-class customer support experience is key to providing a personalized and delightful commerce experience for consumers. Multiple commerce touchpoints currently exist, such as physical stores, online channels, and social channels. Consumers expect a personalized support experience in all these touchpoints. This feature helps you increase cart conversions to sales, increase personalized engagement with consumers, and enhance customer service by integrating with Dynamics 365 Omnichannel for Customer Service. | Enabled by admin/makers |
| E-commerce | Support for product comparison in e-commerce | Enable shoppers to compare products across a wide range of categories so that they can make the correct purchase decision for themselves. This feature is available for both business-to-consumer (B2C) and B2B sites. | Site builder | 
| Gift cards | Support for retail gift card tables for cross-company data sharing | Dynamics headquarters supports the ability to enable cross-company data sharing for specific tables in the Dynamics architecture. In this feature, Dynamics 365 Commerce adds support for cross-company data sharing for the retail gift card tables. Therefore, a gift card in one company can now have its data duplicated to another company in the environment. Changes that are made to the originating company gift card table will be shared to the duplicated company gift card table. | Developers |
| Globalization | [Enable Commerce localization features for new Commerce SDK](/dynamics365-release-plan/2022wave2/commerce/dynamics365-commerce/enable-commerce-localization-features-new-commerce-sdk) | The new feature provides the possibility to enable Commerce localization features from Commerce headquarters by using the feature management framework or parameters. Fiscal integration samples are now included in the new Commerce SDK and support independent packaging. This feature also enables the adoption of the Store Commerce app by global Commerce customers.<p><p>This release includes Commerce localization features and fiscal integration samples for [Austria](../localizations/emea-aut-fi-sample.md), [the Czech Republic](../localizations/emea-cze-fi-sample.md), [France](../localizations/emea-fra-cash-registers.md), [Germany](../localizations/emea-deu-fi-sample.md), [Italy](../localizations/emea-ita-fpi-sample.md), [Norway](../localizations/emea-nor-cash-registers.md), and [Poland](../localizations/emea-pol-fpi-sample.md). | Enabled by admin/makers |
| Offline | [POS offline database compression](../dev-itpro/implementation-considerations-offline.md#important-offline-features) | This new feature reduces offline database sizes by enabling automated index compression outside of channel [store hours](../dev-itpro/store-hours.md). | Feature management<p>*POS offline database compression* |
| Performance | Remove RTS dependency for "edit customer" scenarios | High availability and high performance are default expectations for point of sale (POS) and e-commerce channels. To help meet these expectations, Dynamics 365 Commerce channels no longer have to rely on real-time communication with Commerce headquarters when customer information is edited. The ability to edit customer information asynchronously for asynchronous and non-asynchronous customers can help reduce real-time calls to Commerce headquarters. | Enabled by admin/makers |

## Feature state changes in this release

The following table lists features that became mandatory or on by default in version 10.0.29. All these features will automatically be turned on for your system as soon as you update to version 10.0.29. Mandatory features can't be turned off, but features that are on by default can still be turned off by using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The table also lists features that were previously in public preview but have changed to become generally available in version 10.0.29. This change indicates that the features are now recommended for use in production environments. These features are turned off by default unless otherwise noted. Therefore, you must use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable them if you want to use them.

| Feature | Title | New feature state |
| --- | --- | --- |
| BrazilRetailLocalizationFeature_BR |(Brazil) Commerce functionality that is specific to Brazil | On by default |
| RetailAdvancedGTETaxAdjustmentFeature | (India) Apply GST calculated for retail transactions in Retail POS to retail statements | On by default |
| RetailChronologicalInvoicePostingFeature_IT | (Italy) Enable retail invoices posted without chronological order | On by default |
| RetailDiscountWithoutTaxAdjustingFeature_MX | (Mexico) Discount adjusting in Retail CFDI Global | On by default |
| RetailFiscalIntegrationConfigurationEnhancementFeature | Fiscal integration technical profile overrides | On by default |
| RetailFiscalIntegrationConnectorLocationFeature | Direct fiscal integration from POS registers | On by default |
| RetailFiscalIntegrationLocalStorageBackupEnableFeature | Fiscal integration local storage backup | On by default |
| RetailFiscalIntegrationPostponeFiscalRegistrationFeature | Postponed registration of documents | On by default |
| RetailFiscalIntegrationRegistrationProcessTerminalExceptionFeature | Fiscal Registration State of POS Registers | On by default |
| RetailGSTInvoiceAddressTaxCalculationFeature_IN | (India) Calculate GST based on invoice address for e-commerce orders | On by default |
| RetailInvoicesDefaultSalesDocumentStatusFeature_PL | (Poland) Default sales document status for retail invoices | On by default |
| RetailRecalculateRoundingOfTaxBaseAmountsFeature_MX | (Mexico) Rounding recalculation for tax base amounts in Retail CFDI Global. | On by default |
| RetailSupplementaryInvoiceFeature | Enable supplementary invoices for cash and carry transactions completed in retail stores | On by default |
| RetailInventoryBufferAndInventoryLevelEnableFeature	|  Enable inventory buffers and inventory levels	|  On by default|
|RetailInboundOutboundInventoryValidationFeature|	Enable validation in POS inbound and outbound inventory operation	|   On by default   |
|  RetailInventoryChannelCalculationConsolidationFeature	|  Enhanced e-Commerce channel-side inventory calculation logic	|   On by default   |
|RetailInventoryAdjustmentsInPointOfSaleFeature| 	Inventory adjustments in point of sale	 |  On by default  |
| RetailMultiplePickupDeliveryModeFeature |	 Support for multiple pickup delivery modes	    |   Mandatory    |
|  RetailProductAvailabilityOptimizationFeature	|   Optimized product availability calculation	|  Mandatory |
|   RetailPricingDataManagerV2Feature	|   Improve performance for Commerce pricing engine	|   Mandatory |
|  RetailPricingPreventUnintendedRecalculationFeature	| Prevent unintentional price calculation for commerce orders	 |  Mandatory  |
| RetailTeamsIntegration 	|   Enable Microsoft Teams integration|	Mandatory   |  
| ConsumerEFDSyncProcessFeature_BR | (Brazil) NFC-e synchronous processing | On by default |
| RetailFiscalIntegrationInternalAndExternalServicesEnableFeature | Support for internal and external connectors in the fiscal integration framework | Mandatory |
| RetailTaxRegistrationIdEnableFeature_BR | (Brazil) Search customers in Retail POS by tax registration numbers | Mandatory |
| RetailTaxRegistrationIdEnableFeature_IN | (India) Search customers in Retail POS by tax registration numbers | Mandatory |
| RetailTaxRegistrationIdEnableFeature_IT | (Italy) Customer information management in Retail POS | Mandatory |
| RetailTaxRegistrationIdEnableFeature_PL | (Poland) Customer information management in Retail POS | Mandatory |
| RetailUpdateReturnOriginalTransactionIdGlobalEnableFeature_IN | (Retail GST for India) Update credit notes with references to original invoices | Mandatory |
| RetailUserDefinedCertificateProfileFeature | User-defined certificate profiles for retail stores | Mandatory |
  

## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Commerce 10.0.29 includes platform updates. To learn more, see [Platform updates for version 10.0.29 of Finance and Operations apps (October 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-29.md). 

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.29, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=726559&dbType=3&qc=ec3e3846199f5d3a27a0c4949e3902ffdbc87560f0cf928c4838b3bdd421633c). 

### Dynamics 365 and industry clouds: 2022 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
