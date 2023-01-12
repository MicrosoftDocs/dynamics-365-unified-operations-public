---
title: Preview of Dynamics 365 Commerce 10.0.32 (March 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.32. 
author: josaw1
ms.date: 01/06/2023
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2023-01-31
ms.dyn365.ops.version: 10.0.32
---

# Preview of Dynamics 365 Commerce 10.0.32 (March 2023)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.32. This version has a build number of xxx and is available on the following schedule:

- **Preview of release:** January 2023
- **General availability of release (self-update):** February 2023
- **General availability of release (auto-update):** March 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Self-service installers (Sealed)  | Store Commerce token capture and automated uninstallation of Modern POS. | Using new installer parameters, the Store Commerce installer can capture the device token in use by Modern POS and then uninstall Modern POS. This allows the use of Store Commerce without requiring Azure Active Directory credentials during device activation. | On by default |
| Self-service installers (Sealed)  | .NET 6 is now a prerequisite. | .NET 6 is now a required installation for all sealed installers. Store Commerce has gained a variety of performance improvements through the uptake of this. | On by default |


## Additional resources

### Platform updates for Finance and Operations apps

Microsoft Dynamics 365 Commerce 10.0.32 includes platform updates. To learn more, see [Platform updates for version 10.0.32 of finance and operations apps (February 2023)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-31.md). 
  

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.32, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=758525).

### Dynamics 365 and industry clouds: 2022 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.


For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
