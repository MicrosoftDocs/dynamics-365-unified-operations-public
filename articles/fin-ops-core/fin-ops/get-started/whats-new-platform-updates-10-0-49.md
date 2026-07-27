---
title: Platform updates for version 10.0.49 of finance and operations apps (July 2026)
description: This article lists the features and enhancements that are included in the platform updates for version 10.0.49 of finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.date: 07/27/2026
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.search.region: Global
---

# Platform updates for version 10.0.49 of finance and operations apps (July 2026)

[!include [banner](../includes/banner.md)]

This article lists the features in the platform updates for version 10.0.49 of finance and operations apps. This version uses build number 10.0.2790 and is available on the following schedule:

- **Preview of release:** July 2026
- **General availability of release (self-update):** September 2026
- **General availability of release (auto-update):** October 2026

## Features included in this release

This section lists the features included in this release when available. The article might be updated to add features that are added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
| Nothing at this time |  |  |  |


## Feature enhancements included in this release

This section has a table that lists enhancements included in this release when available. The article might be updated to include features added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
| Developer tools | X++ | Starting with PU74 , Microsoft no longer supports Microsoft Visual Studio 2022 for X++ development. Only Visual Studio 2026 is supported. | &nbsp; |
| Batch telemetry to Application Insights | Batch job occurrence telemetry | Microsoft introduced Batch job occurrence telemetry as an enhancement to the existing Microsoft Dynamics 365 Finance and Operations batch telemetry. The additional telemetry provides visibility into the lifecycle of individual batch job executions, enabling administrators to monitor job progress, completion status, and execution outcomes. Previously, telemetry was available only at the batch task level, making it difficult to track end-to-end job execution. Batch job occurrence telemetry addresses this gap by providing execution-level insights. The telemetry is available in **PU74/10.0.50 (build >= 7.0.8219.0)** and is backported to **PU73/10.0.49 (build >= 7.0.8199.5)** and **PU72/10.0.48 (build >= 7.0.7996.85)**. Contact Microsoft support if the required flight (BatchJobOccurrenceTelemetryFlight) isn't enabled in your environments. - [Learn more](../../dev-itpro/monitoring-telemetry/monitoring-available-telemetry.md#batch-telemetry) | System admin |


### Bug fixes

To see bug fixes in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1156136).

### Dynamics 365: 2026 release wave 1 plan

Want to know about upcoming and recently released capabilities in our business apps or platform?

Check out the [Dynamics 365: 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). This document has all the details you need for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article describes features that are removed or planned for removal in platform updates for finance and operations apps.

- A *removed* feature isn't available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices appear in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before any feature is removed.

For breaking changes that affect only compilation time but are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. These changes are functional updates that you must make to the compiler.
](https://successhub.crm.dynamics.com/main.aspx?appid=0fe9f79a-a1f6-4064-af95-ded6c5e7bd5c&pagetype=entityrecord&etn=rn_releasenote&id=11112222-bbbb-3333-cccc-4444dddd5555)
