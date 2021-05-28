---
# required metadata

title: Preview features in Dynamics 365 Commerce 10.0.20 (July 2021)
description: This topic describes features that are either new or changed in Dynamics 365 Commerce 10.0.20. 
author: josaw1
ms.date: 05/27/2021
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
ms.search.validFrom: 2021-04-30 
ms.dyn365.ops.version: 10.0.209

---
# What's new and changed in Dynamics 365 Commerce 10.0.20 (July 2021)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.20. This version has a build number of 10.0.886 and is available on the following schedule:

- **Preview of release:** May 2021
- **General availability of release (self-update):** June 2021
- **General availability of release (auto-update):** July 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature.

Most of these features must be enabled using [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them. Some of the listed features are still in preview, while others may already be generally available.

| Feature area   | Feature                                                  | More information                                                                    |
|----------------|----------------------------------------------------------|-------------------------------------------------------------------------------------|
| Site builder  | Global configuration properties in Commerce site builder can be made visible, hidden, or disabled when specific Commerce features are turned on.  | [Configure site builder global configuration settings based on enabled features](../e-commerce-extensibility/config-settings-for-features.md) |
| Product dimensions |  Configure product dimension values as swatches in Commerce headquarters.  |  [Configure product dimension values to display as swatches](../dev-itpro/dimensions-swatch.md) |
| Product dimensions |  Configure display settings in Commerce headquarters. |  [Apply display settings for product dimensions](../dimension-settings.md) |
| Point of sale (POS) | Validate serialized items as part of the return process. | [Return serial number-controlled products in point of sale (POS)](../pos-serial-returns.md) |
| Point of sale (POS) | Initiate returns for cash and carry or customer orders in the POS application. | [Create returns in point of sale (POS)](../pos-returns.md)  |
| Point of sale (POS) | Store Commerce app released for preview. | <ul><li>[Store commerce app with Chromium rendering engine and integrated hardware support](/dynamics365/commerce/dev-itpro/store-commerce.md)</br></li></br><li>[Store Commerce app in Microsoft Dynamics 365 Commerce (Preview)](../dev-itpro/store-commerce.md)  |

## Additional resources

### Platform updates for Finance and Operations apps

Dynamics 365 Commerce 10.0.20 includes platform updates. To learn more, see [Platform updates for version 10.0.20 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-20.md).

### Bug fixes 
For information about the bug fixes that are included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=575415&dbType=3&qc=762ace311d670d27275cb0b6e11d811e4222643ffccdc5681a42a580780b8337).

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) topic describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
