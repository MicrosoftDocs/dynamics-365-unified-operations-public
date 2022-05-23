---
# required metadata

title: Platform updates for version 10.0.28 of Finance and Operations apps (August 2022)
description: This topic lists the features that are included in the platform updates for version 10.0.28 of Finance and Operations apps.
author: sericks007
ms.date: 05/11/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2022-05-11

---
# Platform updates for version 10.0.28 of Finance and Operations apps (August 2022)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.28 of Finance and Operations apps. This version has a build number of 7.0.XXXX and is available on the following schedule:

- **Preview of release:** May 2021
- **General availability of release (self-update):** July 2022
- **General availability of release (auto-update):** August 2022

## Features included in this release

The following table lists the features that are included in this release.

| Feature area    | Feature | More information | Enabled by |
|-----------------|---------|------------------|---------------------------|
| Web client | <p>**Upgrade Highcharts from version 4 to version 9**</p><p>This feature upgrades the charting JS library to version 9 for Finance and Operations applications. The new library enables a richer set of visualizations when building, deploying, and using charts and graphs in an app. Before enabling this feature, you should test any extensible controls or custom JavaScript code utilizing Highcharts APIs to ensure there are no issues with the upgrade. This feature is targeted to be required with the April 2023 release, but is currently optional to allow time for migration of affected APIs.</p> |  | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) |
| Web client  | <p>**Enable system notification management**</p><p>This feature allows system administrators to monitor and take action on high-volume notification rules that may be impacting the system. By default, rules that generate more than 100 notifications per hour will be flagged as high-volume; however, this criteria can be adjusted by the administrator. For any high-volume rules, the administrator will have the option to block the rule from continuing to generate notifications and to delete existing notifications associated with that rule.</p>  |   | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md)   |
| Feature area  | [Name of feature](URL to feature description in the Release Plans)  | [Topic name](URL to topic with more information in core documentation)  | How do you turn this feature on? If you turn it on in Feature management, say: [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md)   |

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://lcs.dynamics.com/).

### Dynamics 365: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
