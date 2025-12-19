[---
title: Platform updates for version 10.0.47 of finance and operations apps (January 2026)
description: This article lists the features and enhancements that are included in the platform updates for version 10.0.47 of finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.date: 01/24/2026
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
---

# Platform updates for version 10.0.47 of finance and operations apps (January 2026)

[!include [banner](../includes/banner.md)]

This article lists the features in the platform updates for version 10.0.47 of finance and operations apps. This version uses build number 7.0.XXXXX and is available on the following schedule:

- **Preview of release:** January 2026
- **General availability of release (self-update):** XXXXX 2026
- **General availability of release (auto-update):** XXXXX 2026

## Features included in this release

This section lists the features included in this release when available. We might update this article to add features that are added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| No changes reported at this time |---|---|---|

## Feature enhancements included in this release

This section has a table that lists enhancements included in this release when available. We update this article to include features added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Platform | Change to query timeout settings | The default timeout settings are updated so that interactive workloads that previously had a 30-minute timeout now has five-minute timeout, and other workloads except OData & Batch reduce to 10 minutes. This update helps reduce resource usage, minimize blocking, and prevent batch throttling, ensuring your operations remains responsive and reliable. Phased production rollout is planned to start by 01/20/2026.| On by default |
| System administration | Dynamics 365 ERP Model Context Protocol server | In this release the capabilities of the Dynamics 365 ERP MCP server are enhanced by increasing the number of functions the server can perform, and enabling the server to work with extensions and personalization in the environment. For more information, see [Use Model Context Protocol for finance and operations apps](../../dev-itpro/copilot/copilot-mcp.md) | System administrator |
| System Administration | DMF Telemetry integrates with Application Insights| We’re enhancing the Monitoring and Telemetry feature by introducing **DMF telemetry integration** with Application Insights. This capability is currently behind feature flights. While you may notice additional events in the UI, the underlying telemetry is **planned for preview in January 2026**. Additional details will be shared as soon as the feature becomes available. | Feature Management |


### Bug fixes

To see bug fixes in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=XXXXX).

### Dynamics 365: 2025 release wave 2 plan

Want to know about upcoming and recently released capabilities in our business apps or platform?

See the [Dynamics 365: 2025 release wave 2 plan](/dynamics365/release-plan/2026wave1/). This document has all the details you need for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article describes features that are removed or planned for removal in platform updates for finance and operations apps.

- A *removed* feature isn't available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices appear in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before any feature is removed.

For breaking changes that affect only compilation time, but are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. These changes are functional updates that must be made to the compiler.
](https://successhub.crm.dynamics.com/main.aspx?appid=0fe9f79a-a1f6-4064-af95-ded6c5e7bd5c&pagetype=entityrecord&etn=rn_releasenote&id=ee25d2dc-5946-f011-877a-7c1e52585ca6)
