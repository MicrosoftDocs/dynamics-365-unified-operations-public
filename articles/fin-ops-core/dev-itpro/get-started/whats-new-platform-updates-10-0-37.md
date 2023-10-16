---
# required metadata

title: Platform updates for version 10.0.37 of finance and operations apps (November 2023)
description: This article lists the features that are included in the platform updates for version 10.0.37 of finance and operations apps.
author: johnmichalak
ms.date: 09/01/2023
ms.topic: article
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2022-10-14

---
# Platform updates for version 10.0.37 of finance and operations apps (November 2023)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are included in the platform updates for version 10.0.37 of finance and operations apps. This version has a build number of 7.0.7068 and is available on the following schedule:

- **Preview of release:** September 2023
- **General availability of release (self-update):** October 2023
- **General availability of release (auto-update):** November 2023

## Features included in this release

This section will contain a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|

## Feature enhancements included in this release

This section will contain a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Data Management|Job history cleanup| By default, job history entries and related staging table data that are older than 90 days will be automatically deleted. The Job history cleanup feature in Data management can be used to create a Job history cleanup batch job with a lower value configured for job history retention.|On by default|

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=838613).

### Dynamics 365: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2023 release wave 1 plan](/dynamics365/release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and 
operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are 
functional updates that must be made to the compiler.
