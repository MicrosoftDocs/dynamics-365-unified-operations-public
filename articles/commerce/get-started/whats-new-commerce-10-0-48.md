---
title: Preview features in Dynamics 365 Commerce 10.0.48 (April 2026)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.48. 
author: johnmichalak
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.date: 04/24/2026
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.search.region: Global
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.48

---

# What's new or changed in Dynamics 365 Commerce 10.0.48 (April 2026)

[!include [banner](../includes/banner.md)]

This article lists features that are new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.48. This version has a build number of nnnnnnn and is available on the following schedule:

- **Preview of release:** April 2026
- **General availability of release (self-update):** June 2026
- **General availability of release (auto-update):** July 2026

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that are added to the build after this article is originally published.

| Feature area | Feature | More information | Enabled by |
| --- | --- | --- | --- |

| eCommerce | Customize the default branding of EEID sign-in page | In addition to replacing Azure AD B2C for new deployments, Entra External ID as next-gen CIAM introduces enhanced support for customizing the sign‑in and sign‑up experience, allowing sellers to brand and tailor login pages to match their storefront identity and customer journeys | Feature management |

| eCommerce | Prevent indexing of internal URL(s) | The eCommerce platform now supports preventing search engines from indexing internal or non‑public URLs, helping ensure that only intended, customer‑facing pages appear in search results. This reduces the risk of exposing internal flows (such as preview, authoring, testing, or system-generated URLs), improves SEO quality, and avoids duplicate or low‑value pages being indexed by search engines.
This capability helps customers maintain clean search visibility, protect internal site structures, and improve overall search ranking signals by indexing only relevant, production‑ready content | Feature management |

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.48. You can still disable these features in **Feature management**, if necessary.

| Module | Feature name | More information |
| --- | --- | --- |


## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.48 includes platform updates. For more information, see [Platform updates for version 10.0.48 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-48.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.48, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=nnnnnn).

### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). It captures all the details, end-to-end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Before Microsoft removes any feature from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that you need to make to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
