---
# required metadata

title: Platform updates for version 10.0.20 of Finance and Operations apps (August 2021)
description: This topic lists the features that are included in the platform updates for version 10.0.20 of Finance and Operations apps.
author: sericks007
ms.date: 05/27/2021
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
ms.dyn365.ops.version: 10.0.20

---
# Platform updates for version 10.0.20 of Finance and Operations apps (August 2021)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.20 of Finance and Operations apps. This version has a build number of 7.0.XXXX and is available on the following schedule:

- **Preview of release:** May 2021
- **General availability of release (self-update):** July 2021
- **General availability of release (auto-update):** August 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature.

Most of these features must be enabled using [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them. Some of the listed features are still in preview, while others may already be generally available.

| Feature area   | Feature                                                  | More information                                                                    |
|----------------|----------------------------------------------------------|-------------------------------------------------------------------------------------|
| System administration | **Internet Explorer end-of-support notifications**<br><br>Users accessing Finance and Operations apps via Internal Explorer (IE) will start seeing notifications about the end of support for that browser. IE users will first see an informational message that IE support is ending on August 17, 2021 (the publicly announced, end-of-support date for IE), followed by a warning that support has officially ended. Organizations are encouraged to keep these notifications live unless IE is mandated for their users, in which case you can choose to suppress these notifications and rely on internal processes for migrating your user base to Microsoft Edge or another modern browser.<br><br>The current target for blocking IE usage with Finance and Operations app is with the April 2022 release. Starting in January 2022, users will start seeing a non-dismissible error message that indicates that IE support will soon be blocked. This error message is not controlled by this feature, and customers will need to contact Microsoft Support if this message needs to be suppressed for their organization. | <ul><li>[System requirements for cloud deployments](../../fin-ops/get-started/system-requirements.md)</br></li></br><li>[System requirements for on-premises deployments](../../fin-ops/get-started/system-requirements-on-prem.md) |

## New and updated documentation resources
We have recently added or significantly updated the following help topics. They aren't necessarily related to the new features added for this release, as listed in the previous section, but they may help you to get more out of existing features.

| Feature area | New or updated topics |
|--------------|-----------------------|
| Power Platform integration | [Microsoft Power Platform integration with Finance and Operations apps](../power-platform/overview.md)<br>[Virtual entities overview](../power-platform/virtual-entities-overview.md)<br>[Dual-write setup from Lifecycle Services](../data-entities/dual-write/lcs-setup.md)<br>[Add-ins overview](../power-platform/add-ins-overview.md) |
| Office integration | [Customize the Open in Microsoft Office menu](../office-integration/customize-open-office-menu.md) |
| Database| [Point-in-time restore of the production database to a sandbox environment](../database/database-pitr-prod-sandbox.md)<br>[Database point-in-time restore (PITR)](../database/database-point-in-time-restore.md)<br>[Refresh database](../database/database-refresh.md)<br>[Golden configuration promotion](../database/dbmovement-scenario-goldenconfig.md) |
| User productivity| [Create and work with custom fields](../../fin-ops/get-started/user-defined-fields.md)<br>[Saved views](../../fin-ops/get-started/saved-views.md)<br>[Configure document management](../../fin-ops/organization-administration/configure-document-management.md) |
| Self-service deployment   | [Planned maintenance in self-service environments FAQ](../deployment/plannedmaintenance-selfservice.md)  |
| On-premises deployment| [Set up and deploy on-premises environments (Platform update 41 and later](../eployment/setup-deploy-on-premises-pu41.md) |
| LCS | [Asset library in Lifecycle Services (LCS)](lifecycle-services/asset-library.md) |
| Removed or deprecated features | [Removed or deprecated features in previous releases](../migration-upgrade/deprecated-features.md) |


## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://lcs.dynamics.com).

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.
