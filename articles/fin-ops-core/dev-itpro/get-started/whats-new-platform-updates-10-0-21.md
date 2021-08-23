---
# required metadata

title: Platform updates for version 10.0.21 of Finance and Operations apps (October 2021)
description: This topic lists the features that are included in the platform updates for version 10.0.21 of Finance and Operations apps.
author: sericks007
ms.date: 08/09/2021
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
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.21

---
# Platform updates for version 10.0.21 of Finance and Operations apps (October 2021)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.21 of Finance and Operations apps. This version has a build number of 7.0.6129 and is available on the following schedule:

- **Preview of release:** August 2021
- **General availability of release (self-update):** September 2021
- **General availability of release (auto-update):** October 2021

## Known deployment issue
When deploying release 10.0.21 on IaaS, you may receive the following deployment warning:

**Warning code:** 95017

**Warning message:** Script [SetupDiagnostics] failed execution against VM

The deployment will work despite the warning, however, the following known issues may occur in Lifecycle Services (LCS):

-	On the **Environment monitoring** page, the **View detailed version information** link will not appear, so you won’t be able to see the specific versions of the modules installed in your environment. Without this data, subsequent hotfixes might fail because the process that applies hotfixes uses this data to verify that the module version prerequisites are met. Because it’s not possible to use the PEAP/Preview build in production or apply hotfixes, the impact should be minimal.
-	The **Performance Metrics** and **Index Analysis** tabs on the **Environment Monitoring** page under SQL Insights won’t display any data. All other **Environment Monitoring** features will work as intended.
-	The **Full System Diagnostics** page will not be accessible. The associated data about the status of the nightly collector runs and issues detected by its rules also won’t show up.


## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature.

Some features must be enabled using [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them.

| Feature area   | Feature                                                  | More information                                                                    |
|----------------|----------------------------------------------------------|-------------------------------------------------------------------------------------|
| Client features | [Improved legal entity support for saved views](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/improved-legal-entity-support-saved-views)  | [Saved views](../../fin-ops/get-started/saved-views.md) |
| System administration | **Enhanced support for full feature lifecycle in Feature management**<br><br>Microsoft will now be able to update the state of optional features to be **On by default**. Previously, the only option for a feature to progress through its lifecycle after being released was to transition it directly to **Mandatory**, which does not permit the feature to be turned off. The ability to change a feature to be **On by default** has been added to provide an intermediate step between features being released and features becoming mandatory.<br><br>Features in the **On by default** state are automatically turned on, though organizations will be able to disable these features if more time is needed to validate them. The grid in the Feature management workspace has also been modified to clearly denote feature state (**Preview**, **Released**, **On by default**, or **Mandatory**) in the new **Feature state** column.<br><br>To help set expectations for when features are expected to transition between states once released, we have made some changes to the documented feature lifecycle and corresponding timelines for features in Feature management. For details, see [Feature management overview](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview). This topic also contains examples of typical timelines for feature progression from **Released** to **On by default** to **Mandatory**.| [Feature management overview](../../fin-ops/get-started/feature-management/feature-management-overview.md) |
| Developer tools | Visual Studio 2019 is now officially supported. | [Development tools in Visual Studio](../dev-tools/development-tools-overview.md) |

## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=605166).

### Dynamics 365: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
