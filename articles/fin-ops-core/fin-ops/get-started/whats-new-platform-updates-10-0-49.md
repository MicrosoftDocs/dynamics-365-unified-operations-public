---
title: Platform updates for version 10.0.49 of finance and operations apps (July 2026)
description: This article lists the features and enhancements that are included in the platform updates for version 10.0.49 of finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.date: 08/28/2026
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
| Agent foundation | ERP MCP data tool enhancements | Enhancements to the data tools in the Dynamics 365 ERP MCP server include: <br><ul><li>SQL `SELECT` now supports arithmetic between aggregates, for example `SUM(a) - SUM(b)`. <li>Field name validation returns an explicit error for an invalid field instead of failing opaquely or silently returning an unexpected shape. <li>Actions return their full parameter set, including inherited parameters. <li>Added `queryTimeout` support added to the underlying **SysDA** framework for protocol data path requirements. </li></ul><br><p>These enhancements are available in **PU73/10.0.49 PQU-1** (version 7.0.8199.29 and up), and are backported to **PU72/10.0.48 PQU-5** (version 7.0.7996.107 and up) and **PU71/10.0.47 PQU-11** (version 7.0.7858.166 and up). | By default |
| Agent foundation | ERP MCP form tool enhancements | Enhancements to the form tools in the Dynamics 365 ERP MCP server include: <br><ul><li>Support for **Group Option Button controls** (`FrameOptionButton = Radio` and `Check`), a control family that previously couldn't be read or set. <li>Control resolution hardening: find-by-name, grid group resolution, and a preference for non-lookup controls when setting values, which removes a class of ambiguous-target failures. <li>Menu item label resolution, including resolution via search. <li>Document upload and document viewer control support. </li></ul><br><p>These enhancements are available in **PU73/10.0.49 PQU-1** (version 7.0.8199.29 and up), and are backported to **PU72/10.0.48 PQU-5** (version 7.0.7996.107 and up) and **PU71/10.0.47 PQU-11** (version 7.0.7858.166 and up). | By default |
| Agent foundation | ERP MCP human-in-the-loop (HITL) tool annotations | Each tool in the Dynamics 365 ERP MCP server is marked with its behavioral contract - whether the tool is read-only, destructive, idempotent, or open-world -- so a calling agent can decide when to stop and ask a human before acting. <br><br><p>This enhancement is available in **PU73/10.0.49 PQU-1** (version 7.0.8199.29 and up), and is backported to **PU72/10.0.48 PQU-5** (version 7.0.7996.107 and up) and **PU71/10.0.47 PQU-11** (version 7.0.7858.166 and up). | By default | 
| Developer tools | Assemblies | The following assemblies were removed in this release. Packages with dependencies on these assemblies need to be updated to specifically include them. <br><ul><li> Microsoft.CortanaIntelligence.RecommendationsServiceClient.dll <li> Microsoft.Azure.Management.DataFactories.dll <li> Microsoft.Azure.Management.Resource.dll <li> Microsoft.Azure.Management.Storage.dll </li></ul> |  |

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
