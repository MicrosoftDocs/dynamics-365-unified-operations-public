---
# required metadata

title: Platform updates for version 10.0.32 of finance and operations apps (March 2023)
description: This article lists the features that are included in the platform updates for version 10.0.32 of finance and operations apps.
author: twheeloc
ms.date: 01/27/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2022-10-14

---
# Platform updates for version 10.0.32 of finance and operations apps (March 2023)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are included in the platform updates for version 10.0.32 of finance and operations apps. This version has a build number of 7.0.6801 and is available on the following schedule:

- **Preview of release:** January 2023
- **General availability of release (self-update):** February 2023
- **General availability of release (auto-update):** March 2023

## Features included in this release

The following table lists the features that are included in this release.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Web client | [Updates to client feature states with 10.0.32](/dynamics365/release-plan/2023wave1/finance-operations/finance-operations-crossapp-capabilities/view-updates-client-feature-states-version-10032/) | | Default |
| Web client | <p>**Incremental visual refresh of the finance and operations apps user experience**</p><p>Design languages such as Microsoft Fluent naturally evolve over time, not only to increase the visual appeal of user experiences but also, more importantly, to make those experiences more intuitive, and to help users be more comfortable and productive. The user experience in finance and operations apps is currently based on an old version of Fluent. However, based on your feedback about that experience, we'll give the product another visual facelift, for better alignment with both the latest guidance from Fluent (which has already been adopted in other Microsoft apps, such as Word, PowerPoint, Outlook, Teams, and Azure) and the visuals in other Dynamics 365 apps.</p><p>The largest changes to the user experience are included in version 10.0.32. Smaller enhancements that are targeted for subsequent releases will continue to evolve and improve the interface of finance and operations apps for the benefit of users.</p> | | Default |
| Web client | <p>**Improvements to the grid control**</p><p>Grids are a critical component of enterprise resource planning (ERP) applications. They're used extensively throughout all finance and operations apps, and cater to a range of user scenarios. In this release wave, several improvements have been made to the grid control to help users be more efficient and productive when they interact with a grid. For example, fast data entry is more robust, user efficiency inside the grid from the keyboard has been improved, users can select a range of cells in the grid for copy and paste operations, and the aggregation feature in the grid has been enhanced to show aggregate values for just the selected rows. </p> | [Grid capabilities](../../fin-ops/get-started/grid-capabilities.md) | Default |
| Web client | <p>**New extension methods to improved the handling of default queries with saved views**</p><p>The Saved views feature can be an extremely useful way for users or organizations to optimize the user experience. Data indicates that this feature is currently used primarily to save queries on list pages, so that users can quickly return to specific datasets either on page load (when the view is made the default view) or on demand. Feedback from the community has indicated that the use of views on list pages is impeded in some scenarios because of the default handling of the view's query in relation to the form's query. Typically, as a result of this default handling, the default view's query isn't loaded, and the user receives a warning or error message. To address the most commonly reported customer concerns and enable users to use views as they expect in more situations, two new extension mechanisms have been added to give form developers more control over the query that's run when a page or view is loaded.</p> | [Build forms that fully utilize saved views](../../dev-itpro/user-interface/understanding-saved-views.md) | Default |
| Data management | <p>**The Sql row version change tracking configuration key must be enabled for Row version change tracking (preview)**</p><p>The Row version change tracking feature is required if users want to track Sql row version changes. The configuration key is available on the **License configuration** page. </p> | [Allow Row version change tracking for tables and data entities](../../dev-itpro/data-entities/rowversion-change-track.md) | Config key |

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=787268).

### Dynamics 365: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2023 release wave 1 plan](/dynamics365/release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
