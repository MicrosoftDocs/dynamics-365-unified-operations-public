---
title: Platform updates for version 10.0.46 of finance and operations apps (October 2025)
description: This article lists the features and enhancements that are included in the platform updates for version 10.0.46 of finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.date: 10/24/2025
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
---

# Platform updates for version 10.0.46 of finance and operations apps (October 2025)

[!include [banner](../includes/banner.md)]

This article lists the features in the platform updates for version 10.0.46 of finance and operations apps. This version uses build number 7.0.7778.8 and is available on the following schedule:

- **Preview of release:** October 2025
- **General availability of release (self-update):** November 2025
- **General availability of release (auto-update):** December 2025

## Features included in this release

This section lists the features included in this release when available. We might update this article to add features that are added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| No changes reported at this time |---|---|---|

## Feature enhancements included in this release

This section has a table that lists enhancements included in this release when available. We update this article to include features added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Platform | Upcoming Change to Query Timeout Settings | We’re working on optimizing system performance to deliver a smoother, more efficient experience. By updating the default timeout settings, **interactive workloads** that previously had a 30-minute timeout will now reduce to **5 minutes**, and other workloads except OData & Batch will reduce to 10 minutes. This update will help reduce resource usage, minimize blocking, and prevent batch throttling, ensuring your operations remain responsive and reliable. Phased production rollout is planned to start by 01/20/2026.| On by default |
| System administration | Dynamics 365 ERP Model Context Protocol server | In this release the capabilities of the Dynamics 365 ERP MCP server are enhanced by increasing the number of functions the server can perform, and enabling the server to work with extensions and personalization in the environment. For more information, see [Use Model Context Protocol for finance and operations apps](../../dev-itpro/copilot/copilot-mcp.md) | System administrator |
| System Administration | DMF Telemetry integrates with Application Insights| We’re enhancing the Monitoring and Telemetry feature by introducing **DMF telemetry integration** with Application Insights. This capability is currently behind feature flights. While you may notice additional events in the UI, the underlying telemetry is **planned for preview in January 2026**. Additional details will be shared as soon as the feature becomes available. | Feature Management |


### Bug fixes

To see bug fixes in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1070810).

### Dynamics 365: 2025 release wave 2 plan

Want to know about upcoming and recently released capabilities in our business apps or platform?

See the [Dynamics 365: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). This document has all the details you need for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article describes features that are removed or planned for removal in platform updates for finance and operations apps.

- A *removed* feature isn't available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices appear in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before any feature is removed.

For breaking changes that affect only compilation time, but are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. These changes are functional updates that must be made to the compiler.
