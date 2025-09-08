---
title: Platform updates for version 10.0.45 of finance and operations apps (September 2025)
description: This article lists the features and enhancements that are included in the platform updates for version 10.0.45 of finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.date: 08/19/2025
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

This article lists the features that are included in the platform updates for version 10.0.45 of finance and operations apps. This version has a build number of 7.0.7690.12 and is available on the following schedule:

- **Preview of release:** July 2025
- **General availability of release (self-update):** September 2025
- **General availability of release (auto-update):** October 2025

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| No change reported at this time |---|---|---|

## Feature enhancements included in this release

This section will contain a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| System Administration | Batch Telemetry integrates with Application Insights | As an enhancement to the existing **Monitoring and Telemetry** feature, the platform is expanding its capabilities to include **Batch telemetry integration with Application Insights**. This update introduces a robust telemetry pipeline that enables visibility into critical batch job behaviors directly within the customer's Azure Application Insights instance. Teams can monitor execution timelines, detect throttling, track task distribution, and capture failure diagnostics to eliminate the need for manual incident reporting. This feature isn't limited to future releases. It will also be **backported to version 10.0.44**, ensuring broader availability and immediate impact for customers seeking improved observability and reduced operational overhead. | Feature Management |
| Copilot | File attachments with Copilot for finance and operations apps | With this release you can add file and screenshot attachments to your Copilot chat session. See [Use file attachments in Copilot for finance and operations apps](../../dev-itpro/copilot/copilot-attachments.md) for more information. | Feature Management |


### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1043223).

### Dynamics 365: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). All of the details, end to end, top to bottom, are captured in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article describes removed features or features that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices are added to the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
