---
# required metadata

title: Platform updates for version 10.0.28 of finance and operations apps (August 2022)
description: This article lists the features that are included in the platform updates for version 10.0.28 of finance and operations apps.
author: sericks007
ms.date: 07/15/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2022-05-11

---
# Platform updates for version 10.0.28 of finance and operations apps (August 2022)

[!include [banner](../includes/banner.md)]

This article lists the features that are included in the platform updates for version 10.0.28 of finance and operations apps. This version has a build number of 7.0.6441 and is available on the following schedule:

- **Preview of release:** May 2021
- **General availability of release (self-update):** July 2022
- **General availability of release (auto-update):** July 2022

## Features included in this release

The following table lists the features that are included in this release.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
| Web client | <p>**Upgrade Highcharts from version 4 to version 9**</p><p>This feature upgrades the charting JavaScript library to version 9 for finance and operations apps. The new library enables a richer set of visualizations when charts and graphs are built, deployed, and used in an app. Before you enable this feature, you should test any extensible controls or custom JavaScript code that uses Highcharts application programming interfaces (APIs), to ensure that there are no issues with the upgrade. This feature is targeted to be required in the April 2023 release, but it's currently optional to allow time for the migration of affected APIs.</p> | Not applicable | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) |
| Web client  | <p>**Enable system notification management**</p><p>This feature lets system administrators monitor and take action on high-volume notification rules that might be affecting the system. By default, rules that generate more than 100 notifications per hour will be flagged as high-volume, but the administrator can adjust this criterion. The administrator will then have the option to block any high-volume rule from continuing to generate notifications, and also the option to delete existing notifications that are associated with that rule.</p>  | Not applicable | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) |

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=694438).

### Dynamics 365: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) article describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) article 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.

