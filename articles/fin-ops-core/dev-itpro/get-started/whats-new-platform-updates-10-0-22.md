---
# required metadata

title: Platform updates for version 10.0.22 of Finance and Operations apps (November 2021)
description: This topic lists the features that are included in the platform updates for version 10.0.22 of Finance and Operations apps.
author: sericks007
ms.date: 09/29/2021
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2021-08-31

---
# Platform updates for version 10.0.22 of Finance and Operations apps (November 2021)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.22 of Finance and Operations apps. This version has a build number of 7.0.6164 and is available on the following schedule:

- **Preview of release:** September 2021
- **General availability of release (self-update):** October 2021
- **General availability of release (auto-update):** November 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, whereas others might already be generally available. For the official release date of each feature, see the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/planned-features).

| Feature area    | Feature | More information | Enabled by|
|-----------------|---------|------------------|---------------------------|
| Client features | [Open-source software update – upgrade Moment and remove jQWidgets](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/open-source-software-update-upgrade-moment-remove-jqwidgets)| Not applicable | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) |
| Client features | [New color picker control](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/new-color-picker-control) | Not applicable | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) |
| Client features | <p>**Visual updates to the Hierarchy viewer control**</p><p>Modifications were made to the HierarchyViewer control to improve its accessibility, especially for 400-percent zoom scenarios. These modifications included restyling the control so that it's aligned with the Fluent design language, to help readability of the control at all zoom levels. | [HierarchyViewer control](../user-interface/hierarchy-viewer-control.md) | Default |
| Microsoft Power Platform integration | New scenarios are enabled in Microsoft Power Platform integration. These new scenarios include:<br>- Integration setup<br>- Automated setup for dual-write and virtual entities<br> - Streamlined user setup<br>- Finance and Operations apps business events and data events in Microsoft Dataverse <Br>- Improved development tools <br>- Enhanced add-in experience | [New scenarios enabled with Power Platform convergence](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/new-scenarios-enabled-power-platform-convergence) | Default |

## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=615299).

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
