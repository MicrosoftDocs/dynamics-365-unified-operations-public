---
# required metadata

title: Platform updates for version 10.0.17 of Finance and Operations apps (April 2021)
description: This topic lists the features that are included in the platform updates for version 10.0.17 of Finance and Operations apps.
author: sericks007
ms.date: 03/22/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.17

---
# Platform updates for version 10.0.17 of Finance and Operations apps (April 2021)

[!include [banner](../includes/banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.17 of Finance and Operations apps. This version has a build number of 7.0.5934 and is available on the following schedule:

- **Preview of release:** February 2021
- **General availability of release (self-update):** March 2021
- **General availability of release (auto-update):** April 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature.

-  Visual Studio 2017 is now the primary supported version for X++ tools. Visual Studio 2015 is deprecated.<br>- For more information, see [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md#visual-studio-2015).

-  [(Preview) Translation support for organization views](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/translation-support-organizational-saved-views)<br>- For more information, see [Saved views](../../fin-ops/get-started/saved-views.md).

-  [Upgrade to React 17](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/upgrade-react-17)

-  [Freeze columns in grids](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/freeze-columns-grids)<br>- For more information, see [Grid capabilities](../../fin-ops/get-started/grid-capabilities.md).

-  [Updates to client feature states](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/updates-client-feature-states)<br>- See the release plan for details about the client features that were turned on by default or made mandatory with this release. 

-  View independent software vendor (ISV) license status<br>- It is now possible to view status and expiration dates for an ISV license. For more information, see [View independent software vendor license status](../sysadmin/view-isv-license-status.md).

- [executeQueryWithParameters](../dev-ref/query-with-parameters.md) method<br>- This method runs SQL queries by using statement parameters that can help mitigate SQL injection attacks.

- [Batch notifications](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/batch-notifications)<br>- For more information, see [Batch business events](../business-events/system-business-events.md).

Most of these features must be enabled using [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them.

## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=551039&dbType=3&qc=510c0f86ac24207edecf80d9f313de2065ba105446736042428e3b5489fdf607).

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]