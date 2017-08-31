---
# required metadata

title: System administration home page
description: This topic lists resources that are available for system administrators.
author: sericks007
manager: AnnBe
ms.date: 08/31/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 13531
ms.assetid: 2bb96ac4-0cef-4f66-a953-bd82c117247b
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# System administration home page

[!include[banner](../includes/banner.md)]


This topic points to content for system administrators of Dynamics 365 for Finance and Operations, Enterprise edition. This content will you configure the system to work smoothly and effectively for your organization.

Lifecycle Services
------------------
Lifecycle Services (LCS) is a collaboration portal that provides an environment and a set of regularly updated services that can help you manage the application lifecycle of your Finance and Operations implementations.

- [Lifecycle Services for Finance and Operations](../lifecycle-services/lcs.md)
- [Dynamics Lifecycle Services user guide](../lifecycle-services/lcs-user-guide.md)

## Deployment
You can deploy Finance and Operations in the cloud or on-premises. Cloud deployments offer an ERP service that is fully managed by Microsoft, while on-premises deployments are deployed locally within a customer's data center.

-   [Online service and on-premises software lifecycle policy](../migration-upgrade/versions-update-policy.md)
- [Dynamics 365 for Finance and Operations, Enterprise edition cloud deployment overview](../deployment/cloud-deployment-overview.md)
-   [System requirements for cloud deployments](../get-started/system-requirements.md)
- [On-premises deployment landing page](/deployment/on-premises-deployment-landing-page.md)
- [System requirements for on-premises deployments](../get-started/system-requirements-on-prem.md)

## Hotfixes and updates
To install the latest monthly platform update on an existing environment, go to LCS. In the Shared asset library, select the **Software deployable package** tab. You will find the latest platform update package that you can deploy. For more details, see [Upgrade Finance and Operations to the latest platform update](../migration-upgrade/upgrade-latest-platform-update.md).

Application updates (X++ and binary) are available in the update tiles based on those applicable to a specific environment. Application updates can be searched for and applied as needed. All available application updates are applicable to the latest platform update. See the details for the release in the [Online service and on-premises software lifecycle policy](../migration-upgrade/versions-update-policy.md). 

If you are already on platform update 4 or later, applying an application **binary** update will also update your Finance and Operations platform to the latest release. 

![Application and binary update tiles](./media/application-and-binary-update-tiles-146x300.png)

For more information about hotfixes and updates, see:
-   [Download hotfixes from Lifecycle Services](../migration-upgrade/download-hotfix-lcs.md)
-   [Install a metadata hotfix](..\migration-upgrade\install-metadata-hotfix-package.md)
-   [Apply a deployable package](..\deployment\apply-deployable-package-system.md)

## Upgrade

-   [Overview of moving to the latest update of Microsoft Dynamics 365 for Finance and Operations](../migration-upgrade/upgrade-latest-update.md) 
-   [Upgrade Finance and Operations to the latest platform update](../migration-upgrade/upgrade-latest-platform-update.md)
-   [Upgrade the Dynamics 365 for Operations platform to the August 2016 release](../migration-upgrade/update-platform-each-release.md)
-   [Process for upgrading a sandbox environment](../migration-upgrade/upgrade-sandbox-environment.md)
-   [Upgrade data in development, demo, or sandbox environments](../migration-upgrade/upgrade-data-to-latest-update.md)


## Database management
-   [Copy a Microsoft Dynamics 365 for Finance and Operations database from Azure SQL Database to a SQL Server environment](../database/copy-database-from-azure-sql-to-sql-server.md)
-   [Copy a Microsoft Dynamics 365 for Finance and Operations database from SQL Server to an Azure SQL Database environment](../database/copy-database-from-sql-server-to-azure-sql.md)
-   [Restore a database on a non-production environment](../database/request-point-in-time-restore.md)
-   [Create a copy of a Finance and Operations database to restore later](../database/copy-operations-database.md)

## Security
-   [Role-based security](role-based-security.md)
-   [Security architecture](security-architecture.md)
-   [Create new users](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/create-new-users) (Task guide)
-   [Assign users to security roles](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/assign-users-security-roles) (Task guide)
-   [Set up segregation of duties](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/set-up-segregation-duties) (Task guide)
-   [Identify and resolve conflicts in segregation of duties](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/identify-resolve-conflicts-segregation-duties) (Task guide)
- [Out-of-the-box security reports](security-reports.md)

## Batch processing
-   [Batch processing overview](batch-processing-overview.md)
-   [Batch server overview](batch-server-overview.md)
-   [Create a batch job](/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/create-batch-job) (Task guide)

## Office integration
- [Office integration](../office-integration/office-integration.md)
- [Office integration tutorial](../office-integration/office-integration-tutorial.md)
- [Use the Excel add-in](../office-integration/use-excel-add-in.md)
- [Create Open in Excel experiences](../office-integration/office-integration-edit-excel.md)
- [Add templates to the Open lines in Excel menu](../user-interface/add-templates-open-lines-excel-menu.md)
- [Customize the Open in Microsoft Office menu](../office-integration/customize-open-office-menu.md)
- [Configure and send email](/dynamics365/unified-operations/fin-and-ops/organization-administration/configure-email)
- [Troubleshoot the Office integration](../office-integration/office-integration-troubleshooting.md)

## Licensing
-   [ISV licensing](../dev-tools/isv-licensing.md)
- [License codes and configuration keys report](license-codes-configuration-keys-report.md)

## Retail
-   [Microsoft Dynamics 365 for Finance and Operations – Retail for IT Pros and developers](/dynamics365/unified-operations/retail/dev-itpro/dev-retail-home-page)

## Mobile
-   [Mobile platform](../mobile-apps/platform/mobile-platform-home-page.md)
- [Mobile app home page](../mobile-apps/Mobile-app-home-page.md)
- [Mobile workspaces](../mobile-apps/mobile-workspaces-released.md)
- [Publish a mobile workspace](../mobile-apps/publish-mobile-workspace.md)


## General administration
-   [Demo data overview](../get-started/demo-data.md)
-   [Cross-company data sharing](../sysadmin/cross-company-data-sharing.md)
-   [Maintenance mode](maintenance-mode.md)
- [Add links to your organization's legal terms and privacy statement](legal-terms-privacy-statement.md)
- [Set a user's preferred time zone](/dynamics365/unified-operations/fin-and-ops/organization-administration/tasks/set-users-preferred-time-zone) (Task guide)





