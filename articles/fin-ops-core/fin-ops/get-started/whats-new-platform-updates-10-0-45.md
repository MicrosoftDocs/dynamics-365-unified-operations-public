---
title: Platform updates for version 10.0.45 of finance and operations apps (September 2025)
description: This article lists the features and enhancements that are included in the platform updates for version 10.0.45 of finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.date: 09/09/2025
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
---
# Platform updates for version 10.0.45 of finance and operations apps (September 2025)

[!include [banner](../includes/banner.md)]

This article lists the features in the platform updates for version 10.0.45 of finance and operations apps. This version uses build number 7.0.7690.12 and is available on the following schedule:

- **Preview of release:** July 2025
- **General availability of release (self-update):** September 2025
- **General availability of release (auto-update):** October 2025

## Features included in this release

This section lists the features included in this release when available. We might update this article to add features that are added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| No changes reported at this time |---|---|---|

## Feature enhancements included in this release

This section has a table that lists enhancements included in this release when available. We update this article to include features added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| System Administration | Batch Telemetry integrates with Application Insights | As an enhancement to the existing **Monitoring and Telemetry** feature, the platform is expanding its capabilities to include **Batch telemetry integration with Application Insights**. This update introduces a robust telemetry pipeline that enables visibility into critical batch job behaviors directly within the customer's Azure Application Insights instance. Teams can monitor execution timelines, detect throttling, track task distribution, and capture failure diagnostics to eliminate the need for manual incident reporting. This feature isn't limited to future releases. It will also be **backported to version 10.0.44**, ensuring broader availability and immediate impact for customers seeking improved observability and reduced operational overhead. For details, see [Available telemetry in finance and operations platform](../../dev-itpro/monitoring-telemetry/monitoring-available-telemetry.md) | Feature Management |
| Copilot | File attachments with Copilot for finance and operations apps | This release lets you add file and screenshot attachments to your Copilot chat session. For details, see [Use file attachments in Copilot for finance and operations apps](../../dev-itpro/copilot/copilot-attachments.md). | Feature Management |


### Bug fixes

To see bug fixes in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1043223).

### Dynamics 365: 2025 release wave 2 plan

Want to know about upcoming and recently released capabilities in our business apps or platform?

See the [Dynamics 365: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). This document has all the details you need for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article describes features that are removed or planned for removal in platform updates for finance and operations apps.

- A *removed* feature isn't available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices appear in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before any feature is removed.

For breaking changes that affect only compilation time, but are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. These changes are functional updates that must be made to the compiler.
