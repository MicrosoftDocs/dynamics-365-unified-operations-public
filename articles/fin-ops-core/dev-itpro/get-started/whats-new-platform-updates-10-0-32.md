---
# required metadata

title: Platform updates for version 10.0.32 of finance and operations apps (April 2023)
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
# Platform updates for version 10.0.32 of finance and operations apps (April 2023)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are included in the platform updates for version 10.0.32 of finance and operations apps. This version has a build number of 7.0.6801 and is available on the following schedule:

- **Preview of release:** February 2023
- **General availability of release (self-update):** March 2023
- **General availability of release (auto-update):** April 2023

## Features included in this release

The following table lists the features that are included in this release.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Web client | [Updates to client feature states with 10.0.32](/dynamics365-release-plan/2023wave1/finance-operations/finance-operations-crossapp-capabilities/view-updates-client-feature-states-version-10032) |  | Default |
| Web client | <p>**Incremental visual refresh of the F&O apps user experience**</p><p>Design languages, like Microsoft Fluent, naturally evolve over time to not only increase the visual appeal of user experiences, but more importantly to make those experiences more intuitive and to help users be more comfortable and productive. Though the F&O user experience is currently based on an old version of Fluent, we've heard your feedback about that experience and will be addressing this with another visual facelift of the product to better align to both the latest guidance from Fluent, which has already been adopted in other Microsoft apps like Word, PowerPoint, Outlook, Teams, and Azure, and the visuals in other Dynamics 365 apps.</p><p>The largest changes to the user experience are included in version 10.0.32, with smaller enhancements targeted for subsequent releases that will continue to evolve and improve the F&O interface for the benefit of end users.</p> |  | Default |
| Web client | <p>**Improvements to the grid control**</p><p>Grids are a critical component to ERP applications that are used extensively throughout all F&O applications and cater to a variety of user scenarios. In this release wave, a number of improvements have been made to the grid control to help users be more efficient and productive when interacting with the grid including making fast data entry more robust, increasing user efficiency inside the grid from the keyboard, allowing users to select a range of cells in the grid for copy and paste, and enhancing the aggregation feature in the grid to show aggregate values for just the selected rows. </p> | [Grid capabilities](../../fin-ops/get-started/grid-capabilities.md) | Default |
| Web client | <p>**New extension methods to improved the handling of default queries with saved views**</p><p>The Saved views feature can be an extremely useful mechansim for users or organizations to optimize the user experience. Data indicates this feature is primarily used today to save queries on list pages, allowing users to quickly return to specific datasets either on page load (when the view is made the default view) or on demand. However, feedback from the community has indicated that view usage on list pages is impeded in some scenarios due to the default handling of the view query in relation to the form query, typically resulting in the default view query not loading and the user receiving a warning or error message. To address the most commonly reported customer concerns and enable users to use views as they expect in more situations, two new extension mechanisms have been added to give form developers more control over the query executed when a page or view is loaded. </p> | [Build forms that fully utilize saved views](../../dev-itpro/user-interface/understanding-saved-views.md) | Default |

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=758525).

### Dynamics 365: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2023 release wave 1 plan](/dynamics365-release-plan/2023wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
