---
title: Platform updates for version 10.0.29 of finance and operations apps (October 2022)
description: Learn about the features that are included in the platform updates for version 10.0.29 of finance and operations apps released in October 2022.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.date: 04/12/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-07-22
---

# Platform updates for version 10.0.29 of finance and operations apps (October 2022)

[!include [banner](../../../finance/includes/banner.md)]

This article lists the features that are included in the platform updates for version 10.0.29 of finance and operations apps. This version has a build number of 7.0.6545 and is available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** September 2022

## Features included in this release

The following table lists the features that are included in this release.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Data management | <p>**Refresh entity list**</p><p>Refresh entity list has been refactored so that it always run in a batch.</p> | Not applicable | Default |
| Data integration | <p>**User-based service protection API limits**</p><p>User-based service protection API limits help protect system performance and availability from harm by individual users or integrations. The limits are designed to protect the service when client applications make extraordinary demands on server resources through integrations with Open Data Protocol (OData) or custom service APIs.</p><p>In this release, the feature is optional and is disabled by default. In version 10.0.30, the user-based API limits will be enabled by default but can optionally be disabled. The feature is targeted to become mandatory in version 10.0.33.</p> | [Service protection API limits](../../dev-itpro/data-entities/service-protection-api-limits.md) | [Feature management](feature-management/feature-management-overview.md) |
| Web client | <p>**Extended grid aggregation capabilities**</p><p>This feature extends the current "totals" feature in the grid by letting users select one of four aggregation functions for each numeric column. Grid columns can now be configured to show the minimum value, maximum value, or average value in addition to a total. If grouping has been done in the grid, the selected aggregation function for the column will also be shown for each group.</p> | [Grid capabilities](../../dev-itpro/get-started/grid-capabilities.md) | [Feature management](feature-management/feature-management-overview.md) |
| Web client | <p>**Saved views performance enhancement**</p><p>This feature helps improve performance when the default view is loaded at page load, by minimizing the number of times that the query is run. To achieve this result, the feature changes when specific parts of the default view are applied, so that all query-related changes are in place when the form initially runs its query.</p> | [Build forms that fully utilize saved views](../../dev-itpro/user-interface/understanding-saved-views.md) | [Feature management](feature-management/feature-management-overview.md) |
| Web client | <p>**Evaluating math expressions in numeric cells outside the grid**</p><p>To help improve user productivity, numeric cells in the new grid have long enabled users to enter mathematical expressions directly in them. (For example, if a user enters **=15\*4** and then selects **Enter**, the expression is evaluated, and a value of **60** is entered in the cell.) As of this release, this support for mathematical expressions has been extended to numeric controls outside the grid.</p> | [Grid capabilities](../../dev-itpro/get-started/grid-capabilities.md#evaluating-math-expressions) | Default |

> [!Important]
> A new **Allow row version change tracking** metadata property has been added for tables. The default value of this property is set to **No**.  Do not set the value to **Yes**, as this property is reserved for future use.

## Features that are mandatory or turned on by default with this release

The following table lists features that are now mandatory or turned on by default in this release. For more details see [Feature management](feature-management/feature-management-overview.md).

| Module or feature area | Feature name | Feature state |
| --- | --- | --- |
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

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=726559&dbType=3&qc=ec3e3846199f5d3a27a0c4949e3902ffdbc87560f0cf928c4838b3bdd421633c).

### Dynamics 365: 2022 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
