---
title: What's new and changed in Platform update 31 for finance and operations apps (January 2020)
description: Learn about features that are in preview in Platform update 31 for finance and operations apps added in the January 2020 update.
author: tonyafehr
ms.author: sericks
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.date: 04/12/2024
ems.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Platform update 31
---
# What's new and changed in Platform update 31 for finance and operations apps (January 2020)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are new or changed for Platform update 31 for finance and operations apps. This version has a build number of 7.0.5457 and is available as follows:

- Preview release is in October 2019.
- General availability (self-update) is in November 2019.
- Auto-update is in January 2020.

For more information about Platform update 31, see [Additional resources](#additional-resources).

## Turn on the new (preview) grid control through Feature management
Previously the new grid control was available by adding "&debug=reactGrid" to the environment URL. Now in Platform update 31, the new grid control can be turned on for qualified environments using the Feature management workspace. Refer to the following instructions about how to enable the flight in non-production environments. Qualified environments include Tier 1 (Dev/Test) and Tier 2 (Sandbox) environments. Note that this feature cannot be turned on in production until version 10.0.9, Platform update 33.

To learn more about the new grid control, see [User productivity - New grid](/dynamics365-release-plan/2019wave2/finance-operations/user-productivity-new-grid).

To enable the new grid while this feature is in preview, follow these steps:

1.   Enable the flight by using the following SQL statement:

      INSERT INTO SYSFLIGHTING (FLIGHTNAME, enabled, FLIGHTSERVICEID, PARTITION) VALUES('CLIReactGridEnableFeature', 1, 0, 5637144576);

2.    Reset IIS to flush the static flighting cache.

3.    Go to the **Feature management** workspace in your finance and operations app. 

4.    Select the **New grid control** feature in the list of features, and then select **Enable now** in the details pane.

      If **New grid control** does not appear in the list of features, select **Check for updates**.

All subsequent user sessions will start with the new grid enabled.


## Updates to saved views
The saved views feature continues to evolve with Platform update 31. Included in this release are an overhaul to the administrator's Personalization page for managing views and personalizations, the ability to bulk import/export views, and the ability to publish views to users in specific legal entities. For more information about Saved views, see [Saved views](../../dev-itpro/get-started/saved-views.md).  

## New controls available for developers
The Website Host control has been added to allow developers to embed third-party apps directly into finance and operations inside iFrames. This is the first step toward allowing users with certain privileges to embed apps via personalization, similar to the existing scenario for embedding PowerApps.

A new star rating control is also available for developers to use. This control shows a rating on a scale of 1 to 5 stars in quarter-star increments.

## Updated icon for finance and operations apps
The new icon for finance and operations apps, which aligns with the latest icon stylings across Dynamics 365, is now visible in the web client.

## Optimization of loading the Data management workspace
Loading of the Data management workspace has been slow under certain conditions. There are new optimizations put in place to reduce the time it takes to load the workspace. This change can be enabled via flight DMFWorkspaceLoadPerformance.

## Inefficient memory usage by Data management export/import jobs
There have been several issues reported where the memory consumed by data management export/import jobs has been high enough to result in performance issues. The SSIS package execution logic has been optimized to address this issue. This change is turned Off by default, as it is guarded by a flight DMFExecuteSSISOutOfProc. This change will be enabled by default in a later Platform update.

## Extensibility enhancements
The following enhanced extensibility capabilities have been added in Platform update 31:

- Adjust method WorkflowDocumentField.substitutePlaceholderAsUser separator from semicolon to bar to eliminate conflicts with exported data (Ref# 299129).
- Refactor method SysWorkflowParticipantProvider.SysWorkflowParticipantProvider to provide access to the list of resolved users (Ref# 310122).
- Allow table display methods added via extension to be cached through cacheCalculateMethod API (Ref# 341431).
- Improve locking approach of SysExtensionAppClassFactory.getClassFromSysExtAttribute to reduce blocking issues (Ref# 338254).
- Enable clearing of Grid.DataGroup property via extension so a group can be added that has a different field group set on it (Ref# 303030).
- Allow extension of DataEntity.PrimaryCompanyContext (Ref# 292575).

## Excel Add-in authentication and authorization enhancements
The Excel Add-in has several authentication and authorization enhancements to improve the handling of certain cases:
- **Authentication token expiration now silent** - The sign-in process validates any existing authentication tokens to determine if the user can continue using an existing authentication context or if they need to sign in again. Previously, if the authentication token had expired, the Excel Add-in would notify the user. Now, the user will simply be presented with the standard sign-in screen and an informational message will report the authentication token expiration for debugging purposes.
- **Authentication timeout** - There were some cases where the authentication process didn't complete in time, so the user was receiving an error message with a **Sign out** button. Ignoring the error and selecting **Sign in** again resulted in a successful authentication, but if users selected **Sign out**, there was a possibility of getting into an endless loop.
- **Support for ADFS sign out improved** - The sign-out mechanism is now inside a dialog box. This improves support for customers that are using Active Directory Federation Services (ADFS), because communication from the Excel Add-in to ADFS servers is only allowed in a separate dialog box.
- **Authorization failure information now provided** - Previously, if the user authenticated successfully but didn't have authorization permissions to communicate with the server, then the Excel Add-in would present a "Load applets" link, because the loading of the applets would fail. This was an implicit authorization permissions failure. Now the authorization permissions failure will be detailed explicitly for the user so they understand what has happened and verify that they are signing in as the correct user to the correct server.

## skipAutoOrderBy API
When using the AX Query object by explicitly specifying not to include an ORDER BY clause, the kernel adds the Primary key to the ORDER BY clause. This API will skip the ORDER BY clause and it will not be added to the query. For more information, see [Q classes](/dotnet/api/dynamics.ax.application).

## Batch framework contention reduction
Performance enhancements have been made to reduce heavy blocking/contention on batch framework tables. This fix is for customer environments that are currently experiencing contention when selecting batch tasks and finishing batch jobs. There are no functional changes associated with this feature. The feature can be enabled under Feature management.

## Additional resources

### Platform update 31 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 31, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=386525&dbType=3&qc=e03ced97fa18dc4439f36de17b00da7257dc15869a72e5b2435fec0acec0c493).

### Dynamics 365: 2019 release wave 2 plan
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) article describes features that have been removed or deprecated.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
