---
# required metadata

title: Platform updates for version 10.0.35 of finance and operations apps (July 2023)
description: This article lists the features that are included in the platform updates for version 10.0.35 of finance and operations apps.
author: johnmichalak
ms.date: 05/25/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2022-10-14

---
# Platform updates for version 10.0.35 of finance and operations apps (July 2023)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are included in the platform updates for version 10.0.35 of finance and operations apps. This version has a build number of 7.0.6972 and is available on the following schedule:

- **Preview of release:** May 2023
- **General availability of release (self-update):** July 2023
- **General availability of release (auto-update):** July 2023

## Features included in this release

This section will contain a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.


## Feature enhancements included in this release

This section lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Data integration: User-based service protection API limits are disabled by default. | User-based service protection API limits are no longer mandatory and are disabled by default. The limits may optionally be enabled with the **User-based service protection API limits** feature in **Feature management**. However, the limits will be disabled for all environments and the option removed from **Feature management** in a future release. | [Service protection API limits](../data-entities/service-protection-api-limits.md) | Optional |


### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=817204&dbType=3&qc=31515199fa35fbda929b42fcfa31225e2c30e55eef262c4f917d98d8cc57d42d).

### Dynamics 365: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2023 release wave 1 plan](/dynamics365/release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
