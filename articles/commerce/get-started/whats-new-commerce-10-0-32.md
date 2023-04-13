---
title: What's new or changed in Dynamics 365 Commerce 10.0.32 (March 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.32. 
author: josaw1
ms.date: 03/17/2023
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2023-01-31
ms.dyn365.ops.version: 10.0.32
---

# What's new or changed in Dynamics 365 Commerce 10.0.32 (March 2023)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.32. This version has a build number of 10.0.1515 and is available on the following schedule:

- **Preview of release:** January 2023
- **General availability of release (self-update):** February 2023
- **General availability of release (auto-update):** March 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Extensibility  | Enable OpenAPI (Swagger) specification for local self-hosted Commerce Scale Unit (CSU) | OpenAPI specification is a widely accepted standard used to provide API descriptions for REST APIs. A [local self-hosted Commerce Scale Unit (CSU)](../dev-itpro/setup-local-dev-env.md#local-self-hosted-csu) now has OpenAPI specification enabled by default. The API specification can be accessed via the "/swagger" endpoint. | On by default |
| Payments | Include shipping address in Adyen authorizations for additional fraud protection. | The Dynamics 365 Payment Connector for Adyen adds support for sending the user's values for the **Shipping Address** and **Shopper Email** fields with transactions where shipping to the customer is involved. These fields can be used by Adyen's Fraud Protection rules to help identify fraudulent purchase attempts. These fields will be included for online channels, Call Center, or Point of Sale (POS) when a customer is selecting the ship-to address. Fields that exist in the checkout process are newly included at the time of transactional interaction with the Adyen Payment Gateway. |  On by default |
| Point of sale  | New network and connectivity health checks | New tests in the POS health check operation provide key information during troubleshooting of network or performance-related issues on a POS terminal. In addition, the health check operation can now be accessed directly from the **POS Settings** page. | On by default |
| Self-service installers (Sealed)  | Store Commerce token capture and automated uninstallation of Modern POS. | By using new installer parameters, the Store Commerce installer can capture the device token that's used by Modern POS and then uninstall Modern POS. Therefore, Store Commerce can be used without requiring Azure Active Directory (Azure AD) credentials during device activation. | On by default |
| Self-service installers (Sealed)  | .NET 6 is now a prerequisite. | .NET 6 is now a required installation for all sealed installers. Store Commerce has gained various performance improvements through the uptake of requirement. | On by default |
| Pricing and discounts | [Improved pricing computation performance by using flattened discount tables](https://learn.microsoft.com/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/improved-pricing-computation-performance-using-flattened-discount-tables) | <p>This feature optimizes the discount publishing and lookup procedures of the Dynamics 365 Commerce pricing engine by leveraging flattened data schema. With this feature enabled, discount data configured in Commerce headquarters is denormalized before it's sent to channel databases. The publishing of flattened discount data occurs automatically when a discount is enabled. This process helps achieve faster discount lookup and computation at runtime.<p>This feature is initially introduced in version 10.0.23 and is enabled by default in version 10.0.32 and above. For customers who have not enabled this feature and now upgrade to 10.0.32 or above, please ensure you run **Initialize commerce scheduler** and **1020 (Prices and discounts)** distribution schedule after system upgrade. | On by default |


## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Commerce version 10.0.32 includes platform updates. To learn more, see [Platform updates for version 10.0.32 of finance and operations apps (January 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-32.md). 
  

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.32, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=787268).

### Dynamics 365 and industry clouds: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2023 release wave 1 plan](/dynamics365/release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.


For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
