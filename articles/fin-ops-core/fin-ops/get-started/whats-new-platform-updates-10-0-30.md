---
title: Platform updates for version 10.0.30 of finance and operations apps (November 2022)
description: Learn about the features that are included in the platform updates for version 10.0.30 of finance and operations apps released in November 2022.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.date: 04/12/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-08-19
---

# Platform updates for version 10.0.30 of finance and operations apps (November 2022)

[!include [banner](../../../finance/includes/banner.md)]

This article lists the features that are included in the platform updates for version 10.0.30 of finance and operations apps. This version has a build number of 7.0.6592 and is available on the following schedule:

- **Preview of release:** September 2022
- **General availability of release (self-update):** October 2022
- **General availability of release (auto-update):** November 2022

## Features included in this release

The following table lists the features that are included in this release.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Web client | [Standardize keyboard interaction for combo box and lookup controls](/dynamics365-release-plan/2022wave1/finance-operations/finance-operations-crossapp-capabilities/standardize-keyboard-interaction-combo-box-lookup-controls) transitioning from preview to generally available | [Keyboard shortcuts](shortcut-keys.md) | [Feature management](feature-management/feature-management-overview.md) |
| Web client | <p>New grid control support for grouped card lists and multi-column card lists</p><p>Pages with these types of card lists are no longer automatically reverting to use the legacy grid control. In addition, any usages of the `forceLegacyGrid()` API—because of a grouped or multi-column card list—should be safe to remove.</p> | [Grid capabilities](../../dev-itpro/get-started/grid-capabilities.md) | On by default  |
| Data engine | Statement timeout | SQL queries issued from non-interactive sessions will be assigned a timeout duration. The default value is 3 hours for an indivual query. In scenarios when longer query execution is anticipated, use [queryTimeout API](/dotnet/api/microsoft.dynamics.ax.xpp.common.querytimeout) to override the default value. </p> |   On by default  |

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=745468).

### Dynamics 365: 2022 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
