---
title: Platform updates for version 10.0.20 of finance and operations apps (August 2021)
description: Learn about the features that are included in the platform updates for version 10.0.20 of finance and operations apps.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.date: 05/22/2024
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.20
---

# Platform updates for version 10.0.20 of finance and operations apps (August 2021)

[!include [banner](../includes/banner.md)]

This article lists the features that are included in the platform updates for version 10.0.20 of finance and operations apps. This version has a build number of 7.0.6060 and is available on the following schedule:

- **Preview of release:** May 2021
- **General availability of release (self-update):** July 2021
- **General availability of release (auto-update):** July 2021


## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature.

Most of these features must be enabled using [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them. 

| Feature area   | Feature                                                  | More information                                                                    |
|----------------|----------------------------------------------------------|-------------------------------------------------------------------------------------|
| System administration | [Internet Explorer end-of-support notifications](/dynamics365-release-plan/2021wave1/finance-operations/finance-operations-crossapp-capabilities/internet-explorer-end-of-support-notifications)| [System requirements for cloud deployments](../../fin-ops/get-started/system-requirements.md)</br></br>[System requirements for on-premises deployments](../../fin-ops/get-started/system-requirements-on-prem.md) |
| Organization administration | [Document attachment history](/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/document-attachment-history) | [Configure document management](../../fin-ops/organization-administration/configure-document-management.md#document-attachment-history) |

## New and updated documentation resources
We have recently added or significantly updated the following help topics. They aren't necessarily related to the new features added for this release, as listed in the previous section, but they may help you to get more out of existing features.

| Feature area | New or updated topics |
|--------------|-----------------------|
| Power Platform integration | [Microsoft Power Platform integration with finance and operations apps](../power-platform/overview.md)<br>[Virtual entities overview](../power-platform/virtual-entities-overview.md)<br>[Add-ins overview](../power-platform/add-ins-overview.md)<br>[What's new or changed in dual-write](../data-entities/dual-write/whats-new-dual-write.md)<br>[Dual-write setup from Lifecycle Services](../data-entities/dual-write/lcs-setup.md)<br>[User-specified team owner](../data-entities/dual-write/user-specified-team-owner.md)<br>[Enable dual-write for existing finance and operations apps](../data-entities/dual-write/enable-dual-write.md)<br>[Use the dual-write wizard to link your environments](../data-entities/dual-write/link-your-environment.md) |
| Office integration | [Customize the Open in Microsoft Office menu](../office-integration/customize-open-office-menu.md) |
| Database| [Point-in-time restore of the production database to a sandbox environment](../database/database-pitr-prod-sandbox.md)<br>[Database point-in-time restore (PITR)](../database/database-point-in-time-restore.md)<br>[Refresh database](../database/database-refresh.md) |
)<br>[Golden configuration promotion](../database/dbmovement-scenario-goldenconfig.md) |
| User productivity| [Create and work with custom fields](../../fin-ops/get-started/user-defined-fields.md)<br>[Saved views](../../fin-ops/get-started/saved-views.md)<br>[Configure document management](../../fin-ops/organization-administration/configure-document-management.md) |
| Self-service deployment   | [Planned maintenance in self-service environments FAQ](../deployment/plannedmaintenance-selfservice.md)  |
| On-premises deployment| [Set up and deploy on-premises environments (Platform update 41 and later)](../deployment/setup-deploy-on-premises-pu41.md) |
| Lifecycle Services (LCS) | [Asset library in Lifecycle Services (LCS)](../lifecycle-services/asset-library.md) |
| Development| [Link X++ modules from ISV packages by using ISV Studio](../dev-tools/isv-studio-solutions.md) |
| Removed or deprecated features | [Removed or deprecated features in previous releases](../migration-upgrade/deprecated-features.md) |


## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=586707&dbType=3&qc=d0dad8eee2af234e8c288e2a7df14c579004518673d014be511f900cfed008f8).

### Dynamics 365: 2021 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 1 plan](/dynamics365-release-plan/2021wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.

