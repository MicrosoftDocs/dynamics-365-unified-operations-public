---
# required metadata

title: Preview features in Dynamics 365 Commerce 10.0.21 (October 2021)
description: This topic describes features that are either new or changed in the preview release of Dynamics 365 Commerce 10.0.21. 
author: josaw1
ms.date: 08/02/2021
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
ms.search.validFrom: 2021-08-31 
ms.dyn365.ops.version: 10.0.21

---
# Preview features in in Dynamics 365 Commerce 10.0.21 (October 2021)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.21. This version has a build number of 10.0.960 and is available on the following schedule:

- **Preview of release:** August 2021
- **General availability of release (self-update):** September 2021
- **General availability of release (auto-update):** October 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature.

Most of these features must be enabled using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them.

| Feature area   | Feature                                                  | More information                                                                    |
|----------------|----------------------------------------------------------|-------------------------------------------------------------------------------------|
|  B2B           |   [Grant and revoke B2B e-commerce business partner user admin privileges](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/grant-revoke-b2b-e-commerce-business-partner-user-admin-privileges.md)    |   [Manage business partner users on B2B e-commerce websites](../b2b/manage-b2b-users.md)   |
|  B2B          |  [Support for catalogs in e-commerce channel](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/support-catalogs-e-commerce-channel.md)   |  Create partner-specific catalogs that reflect the products and special pricing that have been negotiated with the partner.   |
|  Deployment   |   Apply updates and extensions to Commerce Scale Unit (cloud)  |  [Apply updates and extensions to Commerce Scale Unit (cloud)](/../fin-ops-core/dev-itpro/deployment/Update-retail-channel.md)     |
|  Extensibility  |  Remove Cloud Scale Unit extensions   |  [Remove Cloud Scale Unit extensions](../dev-itpro/retail-sdk/remove-csu-package.md)      |
|  Point of sale (POS)  |  Prevent unintentional price calculation for commerce orders     |  [Customer orders in point of sale (POS)](../customer-orders-overview.md)           |
|  Point of sale (POS)  |   [Support inventory movement between in-store locations from POS](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/support-inventory-movement-between-in-store-locations-pos.md)   |  Enable inventory movements between in-store locations directly from the POS.   |
|  Localizations        |   Prepayments in Dynamics 365 Commerce for Russia            |  [Prepayments in Dynamics 365 Commerce for Russia](../localizations/rus-commerce-prepayments.md)   |
|  Localizations  |   Set up the Dynamics 365 Commerce localization for Russia       |   [Set up the Dynamics 365 Commerce localization for Russia](../localizations/rus-commerce-setup.md)  |
|   Merchandizing   |  Inventory awareness on swatches  |  [Configure product dimension values to appear as swatches](../dev-itpro/dimensions-swatch.md)    |
|   Targeting   |  [Customer segmentation and targeting](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/customer-segmentation-targeting.md)  |  [Device, market, and geolocation targeting](../targeting-overview.md)    |
|  Performance  | [Enforce custom query change tracking configurations on retail transaction tables due to performance impacts](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/enforce-custom-query-change-tracking-configurations-retail-transaction-tables-due-performance-impacts.md)   | This feature will improve Commerce performance when using the Data Management export framework combined with change tracking capabilities on retail transaction tables.  |
| E-commerce   |   [Enhanced reordering experience in e-commerce](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/enhanced-reordering-experience-e-commerce.md)  |   This feature introduces enhancements to the existing reordering ("buy it again") function for e-commerce sites.   |


## Additional resources

### Platform updates for Finance and Operations apps

Dynamics 365 Commerce 10.0.21 includes platform updates. To learn more, see [Platform updates for version 10.0.21 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-21.md).

### Bug fixes 
For information about the bug fixes that are included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/).

For Commerce-specific breaking changes, view the [Dynamics 365 Commerce online SDK FAQ](../e-commerce-extensibility/sdk-faq.md).

### Dynamics 365: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) topic describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
