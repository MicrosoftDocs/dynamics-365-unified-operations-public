---
title: Platform updates for version 10.0.38 of finance and operations apps (February 2024)
description: Learn about the features that are included in the platform updates for version 10.0.38 of finance and operations apps released in February 2024.
author: johnmichalak
ms.author: johnmichalak
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.date: 04/12/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-10-14
---

# Platform updates for version 10.0.38 of finance and operations apps (February 2024)

[!include [banner](../includes/banner.md)]

This article lists the features that are included in the platform updates for version 10.0.38 of finance and operations apps. This version has a build number of 7.0.7120 and is available on the following schedule:

- **Preview of release:** October 2023
- **General availability of release (self-update):** December 2023
- **General availability of release (auto-update):** February 2024

## Features included in this release

This section will contain a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Client | Bulk editing for grids | [Grid capabilities](grid-capabilities.md) | Feature management | 
| Data Management | Clean up staging tables from Data Management menu | This [feature](/dynamics365/fin-ops-core/dev-itpro/data-entities/staging-tables) allows Data Management Administrators to directly truncate the staging table associated with a data entity. The option is available in the Data Entities menu within the Data Management workspace. This action will remove all records from the staging table for the selected entity and should be used with caution. Currently running data import/export jobs involving the selected staging table (imports or exports through staging) is impacted if the staging table is truncated. Ensure there aren't any currently running jobs that involve this staging table before using this feature. | On by default|

## Feature enhancements included in this release

This section will contain a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=857683).

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
