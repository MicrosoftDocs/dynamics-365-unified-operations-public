---
# required metadata

title: Platform updates for version 10.0.13 of Finance and Operations apps (October 2020)
description: This topic lists the features are included in the platform updates for version 10.0.13 of Finance and Operations apps.
author: sericks007
ms.date: 10/15/2020
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
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: 10.0.13

---
# Platform updates for version 10.0.13 of Finance and Operations apps (October 2020)

[!include [banner](../includes/banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.13 of Finance and Operations apps. (These updates were formerly referred to as *Platform update 37*.) This version has a build number of 7.0.5746 and is available on the following schedule:

- **Preview release:** July 2020
- **General availability (self-update):** September 2020
- **Auto-update:** October 2020

## Features included in this release

-  Visual Studio tools require Microsoft .NET 4.7.2 runtime<br>- For more information, see 
[Action required for non-Microsoft managed developer VMs](https://community.dynamics.com/365/financeandoperations/b/newdynamicsax/posts/action-required---net-version-and-visual-studio-2017).

-  Priority-based throttling<br>- For more information, see 
[Priority-based throttling](../data-entities/priority-based-throttling.md). 

-  [Saved views - general availability](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/saved-views--general-availability)<br>- For more information, see 
[Saved views](../../fin-ops/get-started/saved-views.md). 

-  [New grid control - general availability](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/new-grid-control--general-availability)<br>- For more information, see 
[Grid capabilities](../../fin-ops/get-started/grid-capabilities.md). 

-  [Upgrade three jQuery components libraries](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/upgrade-three-jquery-components-libraries)

-  [Allow validation of control state in task recordings](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/new-task-recorder-capabilities)<br>- For more information, see the "Validate" section in 
[Task recorder resources](../user-interface/task-recorder.md#validate). To use this feature in combination with the Regression suite automation tool (RSAT), you must update to [RSAT 2.0](https://www.microsoft.com/en-us/download/details.aspx?id=57357).  


## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=476824&dbType=3&qc=18d329e7d9887a622bada690791f5814dbbef22bb6f4eaada3718299f40132fd).

### Dynamics 365: 2020 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2020 release wave 2 plan](/dynamics365-release-plan/2020wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]