---
# required metadata

title: Platform updates for version 10.0.29 of finance and operations apps (October 2022)
description: This topic lists the features that are included in the platform updates for version 10.0.29 of finance and operations apps.
author: sericks007
ms.date: 07/26/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2022-07-22

---
# Platform updates for version 10.0.29 of finance and operations apps (October 2022)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.29 of finance and operations apps. This version has a build number of 7.0.XXXX and is available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** September 2022

## Features included in this release

The following table lists the features that are included in this release.

| Module or feature area    | Feature name | More information | Enabled by |
|-----------------|---------|------------------|---------------------------|
| Data management  | Refresh entity list | Refresh entity list is refactored to always run in batch. | Default |
| Web client  | <p>**Extended grid aggregation capabilities**</p><p>This feature extends the current "totals" feature in the grid by allowing users to choose one of four aggregation functions for each numeric column. Besides showing a total, grid columns can now be configured to show the minimum value, maximum value, or averge value in the column. If grouping has been performed within the grid, the chosen aggregation function for that column will be shown for each group, as well.</p> | [Grid capabilities](../../fin-ops/get-started/grid-capabilities.md)  | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) |
| Web client  | <p>**Saved views performance enhancement**</p><p>This feature improves the performance of loading the default view on page load by minimizing the number of times the query is executed. This is accomplished by modifying when certain parts of the default view are applied so that all query-related changes are in place when the form initially executes its query.</p> | [Build forms that fully utilize saved views](../user-interface/understanding-saved-views.md)  | [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) |
| Web client  | <p>**Evaluating math expressions in numeric cells outside the grid**</p><p>Numeric cells in the new grid have long allowed users to enter mathematical expressions directly in cells (e.g. "=15*4" followed by Enter will evaluate the expression and set a value of 60 in the cell) to boost user productivity. Starting with this release, this mathematical expression support has been extended to numeric controls outside the grid as well.</p> | [Grid capabilities](../../fin-ops/get-started/grid-capabilities.md#evaluating-math-expressions)  | Default |
| Feature area  | [Name of feature](URL to feature description in the Release Plans)  | [Topic name](URL to topic with more information in core documentation)  | How do you turn this feature on? If you turn it on in Feature management, say: [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md)   |

## Features that are mandatory or turned on by default in this release

The following table lists features that are now mandatory or turned on by default with this release. For more details see [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md).

| Module or feature area | Feature name | Feature state |
| :--- |  :--- | :--- |
| Data management | Execution history cleanup | On by default | 
| System administration | Customer and vendor master data sharing | Mandatory |
| System administration | Saved views | Mandatory |
| System administration | Designate fields as required using personalization | Mandatory |
| System administration | Translation support for organization views | Mandatory |
| System administration | Improved legal entity support for saved views | Mandatory |
| System administration | Saved views support for dialogs | On by default |
| System administration | Allow queries to be saved to views on Task Single and Task Double pages | On by default |
| System administration | Full pages apps | Mandatory |
| System administration | Allow users to select and change tile sizes | On by default |
| System administration | New grid control | Mandatory |
| System administration | Grouping in grids | Mandatory |
| System administration | Freezing columns in grids | Mandatory |
| System administration | Align combo box interactions with lookup controls | Mandatory |
| System administration | Allow admins to select default document types | Mandatory |
| System administration | Allow configuration of the publish batch size in the Excel add-in | Mandatory |
| System administration | Visual update for wizards | Mandatory |
| System administration | Upgrade to jQuery UI 1.13.0 | Mandatory |
| System administration | Streamline tabbing behavior in full-page forms | On by default |
| System administration | Optimize loading of Action center notifications | On by default |

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://lcs.dynamics.com/).

### Dynamics 365: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
