---
# required metadata

title: What's new or changed in Dynamics 365 Commerce 10.0.25 (April 2022)
description: This topic describes features that are either new or changed in Dynamics 365 Commerce 10.0.25. 
author: josaw1
ms.date: 04/22/2022
ms.topic: article
ms.prod: 
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
ms.search.validFrom: 2021-01-31 
ms.dyn365.ops.version: 10.0.25

---

# What's new or changed in Dynamics 365 Commerce 10.0.25 (April 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.25. This version has a build number of 10.0.1149 and is available on the following schedule:

- **Preview of release**: January 2022
- **General availability of release (self-update)**: March 2022
- **General availability of release (auto-update)**: April 2022

## Features included in this release

The following table lists the features that are included in this release. The *Feature* column provides links to the [release plan](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/planned-features), where you can see the official release dates for each feature. The *More information* column provides more details and/or links to related documentation. To determine how to turn on a feature, see the *Enabled by* column. For more information about how to use feature management, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). We might update this topic to include features that made it into the build after this topic was initially published.

| Feature area   | Feature                                                  | More information                                          |  Enabled by             |
|----------------|----------------------------------------------------------|-----------------------------------------------------------|-------------------------|
| POS | [Store Commerce app](/dynamics365-release-plan/2021wave1/commerce/dynamics365-commerce/store-commerce-app-chromium-rendering-engine-integrated-hardware-support) | The Store Commerce app in Commerce is the next-generation offering for physical stores. It unifies Modern Point of Sale (MPOS) and Cloud Point of Sale (CPOS) into a single application, provides deployment choices to retailers, helps improve performance, and offers superior application lifecycle management (ALM). It also retains all the functionality of MPOS and CPOS, including extensibility. See [Store Commerce app](../dev-itpro/store-commerce.md). |Opt-in | 
| POS  | [Support additional filter options in POS inventory operations](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/additional-filter-options-pos-inventory-operations) |  This feature provides support for additional filter options that are commonly requested across POS inventory operations, thereby eliminating the need for unnecessary extensions and significantly improving the efficiency of the store inventory operation. | Feature management<p>*Additional filter options in POS inventory operations* |
| B2B | Mock a signed-in B2B user | [Mock the signed-in state during local development](../e-commerce-extensibility/mock-sign-in.md) | Developer opt-in | 
| E-commerce | [Integration with Sitecore Content Hub](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/integration-sitecore-content-hub) | A data connector will automatically push the Dynamics 365 Commerce product and category data into your Sitecore Content Hub instance allowing additional digital asset management and product enrichment options for your Commerce channels. | Site builder |
| E-commerce | [PayPal Cart Checkout support in e-commerce](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/paypal-cart-checkout-support-e-commerce) | [Dynamics 365 Payment Connector for PayPal](../paypal.md)| Developer opt-in |
| E-commerce | [Show or hide tax breakdown in e-commerce when prices include sales tax](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/show-or-hide-tax-breakdown-e-commerce-when-prices-include-sales-tax) |  Businesses can display or hide tax information explicitly in the order summary on cart, checkout, confirmation, and order details pages in the e-commerce channel. | Site builder |
| E-commerce    | Rename multiple content item types | Site builder now supports renaming multiple content item types including sites, templates, fragments and layouts. For more information, see [Rename a site](../create-ecommerce-site.md#rename-your-site), [Rename a template](../work-with-templates.md#rename-a-template), [Rename a fragment](../work-with-fragments.md#rename-a-fragment), [Rename a page](../add-new-page.md#specify-the-page-name), [Rename a layout](../work-with-layouts.md#rename-a-preset-layout), [Rename an audience](../targeting-overview.md#rename-an-audience-in-site-builder).  |  Site builder   |
| Globalization | [Direct fiscal integration from POS](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/direct-fiscal-integration-pos) | The feature extends the fiscal integration framework by adding a capability to create fiscal connectors that will be executed in POS. This type of connector will communicate with a fiscal device or service that provides an HTTP API and will not require a dedicated physical machine in the store to be plugged in or deployed on. For more information, see [Overview of fiscal integration for Commerce channels](../localizations/fiscal-integration-for-retail-channel.md#fiscal-registration-is-done-via-a-device-or-service-in-the-local-network) and [Create connector technical profiles](../localizations/setting-up-fiscal-integration-for-retail-channel.md#create-connector-technical-profiles). | Feature management<p>*Direct fiscal integration from POS registers*| 
| Globalization | [Enhanced fiscal connector configuration](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/enhanced-fiscal-connector-configuration) | The feature extends the fiscal integration framework by adding an option to define connection settings for a fiscal connector on the individual POS register level, in addition to the hardware profile level. This will provide the ability to configure different connection settings for individual fiscal devices or service instances used by different POS registers in the store. For more information, see [Create connector technical profiles](../localizations/setting-up-fiscal-integration-for-retail-channel.md#create-connector-technical-profiles). |  Feature management<p>*Fiscal integration technical profile overrides* | 
|Statements |  Improvements to statement posting functionality  | [Improvements to statement posting functionality](../statement-posting-EOD.md) | Commerce parameters |



## Additional resources

### Modernizing the Commerce in-store technology stack

The [Modernizing the Dynamics 365 Commerce In-Store Technology Stack](https://download.microsoft.com/download/2/2/3/22310579-4b89-4703-becb-9c48aac3cd9c/Modernizing-the-Dynamics-365-Commerce-In-Store-Technology-Stack.pdf) white paper describes the evolution of the Commerce in-store solution, the motivation for new modernization work, and a detailed release timeline to help customers and partners plan their adoption of the new Store Commerce app and Commerce SDK. 

### Platform updates for Finance and Operations apps

Dynamics 365 Commerce 10.0.25 includes platform updates. To learn more, see [Platform updates for version 10.0.25 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-25.md).

### Bug fixes 
For information about the bug fixes that are included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=654580).

For Commerce-specific breaking changes, view the [Dynamics 365 Commerce online SDK FAQ](../e-commerce-extensibility/sdk-faq.md).

### Dynamics 365: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) topic describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
