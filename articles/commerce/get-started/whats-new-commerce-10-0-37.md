---
title: What's new or changed in Dynamics 365 Commerce 10.0.37 (November 2023)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.37. 
author: josaw1
ms.date: 04/12/2024
ms.topic: article
audience: Application User
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2023-09-01
ms.dyn365.ops.version: 10.0.37

---

# What's new or changed in Dynamics 365 Commerce 10.0.37 (November 2023)

[!include [banner](../includes/banner.md)]


This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce version 10.0.37. This version has a build number of 10.0.1725 and is available on the following schedule:

- **Preview of release:** September 2023
- **General availability of release (self-update):** October 2023
- **General availability of release (auto-update):** November 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Payments | Aggregated payments workspace in Commerce headquarters | An aggregated **Payments** workspace was added to headquarters workspaces to simplify analysis of payment configurations and comparison of settings across your legal entity. The new workspace provides options to review all call centers, online stores, and retail stores, and provides a view of various payment connector settings. You can adjust and save columns in the grid per saved view, and you can print from the workspace. Payment-related quick links were also added so you can quickly navigate to key configuration pages in Commerce headquarters. | Default |
| B2B | Order template and reorder from order history enhancement to support B2B catalog | Order templates now support catalogs. When the catalog feature is enabled, each order template line saves the corresponding catalog information. When users add one or more lines from the order template to their shopping cart, the cart lines get the correct catalog information from the order template lines. Also, the **Synchronize order templates** batch job that syncs order template information from the channel database to headquarters is available to use. | Default |

## Additional resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.37 includes platform updates. To learn more, see [Platform updates for version 10.0.37 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-37.md). 
  

### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.37, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=838613).

### Dynamics 365 and industry clouds: 2023 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2023 release wave 2 plan](/dynamics365/release-plan/2023wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.


For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
