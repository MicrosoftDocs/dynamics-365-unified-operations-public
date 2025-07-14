---
title: Platform updates for version 10.0.42 of finance and operations apps (December 2024)
description: This article lists the features and enhancements that are included in the platform updates for version 10.0.42 of finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.date: 03/11/2025
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
---
# Platform updates for version 10.0.42 of finance and operations apps (December 2024)

[!include [banner](../includes/banner.md)]

This article lists the features that are included in the platform updates for version 10.0.42 of finance and operations apps. This version has a build number of 7.0.7452.15 and is available on the following schedule:

- **Preview of release:** October 2024
- **General availability of release (self-update):** December 2024
- **General availability of release (auto-update):** February 2025

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| User interface development | Add Adaptive Card controls to your forms in finance and operations apps | [Adaptive Card controls](../../dev-itpro/user-interface/adaptive-cards.md) | Default |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Data Management | Automatic retry support for DMF batch jobs | Data management batch jobs failed sometimes without completing the import/export operations due to batch node restarts. To address this issue, retry support was implemented to allow automatic retries if a batch restarts. Learn more in [Data import and export jobs overview](../data-entities/data-import-export-job.md). | Default |
 

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=968512).

### Dynamics 365: 2024 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2024 release wave 2 plan](/dynamics365/release-plan/2024wave2/). All of the details, end to end, top to bottom, are captured in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article describes removed features or features that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices are added to the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
