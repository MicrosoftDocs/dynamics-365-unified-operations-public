---
# required metadata

title: Platform updates for version 10.0.22 of Finance and Operations apps (November 2021)
description: This topic lists the features that are included in the platform updates for version 10.0.22 of Finance and Operations apps.
author: sericks007
ms.date: 12/01/2021
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2021-08-31

---
# Platform updates for version 10.0.22 of Finance and Operations apps (November 2021)

[!include [banner](../includes/banner.md)]

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
| Batch processing | <p>**Batch OData API**</p><p>The batch functionality now exposes an Open Data Protocol (OData) application programming interface (API) that can be used to requeue batch jobs. Customers can use the OData endpoint to requeue batch jobs that are in a terminal state. This feature can be integrated with any automation by using Microsoft Power Automate, custom APIs, and so on. | [Batch OData API](../sysadmin/batch-odata-api.md) | Default |
| Microsoft Power Platform integration | <p>New scenarios are enabled in the Microsoft Power Platform integration. Here are some examples:</p><ul><li>Integration setup</li><li>Automated setup for dual-write and virtual entities</li><li>Streamlined user setup</li><li>Finance and Operations apps business events and data events in Microsoft Dataverse</li><li>Improved development tools</li><li>Enhanced add-in experience</li></ul> | [New scenarios enabled with Power Platform convergence](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/new-scenarios-enabled-power-platform-convergence) | Default |
| Power BI |  The Power BI embedded and Power BI.com integration has been upgraded as part of the 10.0.22 release to be compatible with the latest Power BI Desktop releases. With this change, users are now able to use the latest version of Power BI desktop when editing workspace reports. This is an infrastructure change and will happen automatically when an environment is upgraded to release 10.0.22.    | [Configure PowerBI.com integration](../analytics/configure-power-bi-integration.md)<br><br>[Create analytical reports by using Power BI Desktop](../analytics/author-distribute-power-bi-reports.md) | Default |


## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=615299).

### Dynamics 365: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
