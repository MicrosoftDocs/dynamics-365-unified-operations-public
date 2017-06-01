---
# required metadata

title: Cloud operations and servicing
description: Dynamics 365 for Operations is Microsoft's Cloud ERP offering as a managed service. This means that Microsoft is responsible for managing and operating the production environments. Microsoft’s Dynamics Service Engineering team is available 24 hours a day, 7 days a week, and 365 days a year to operate and manage our customers' production systems. 
author: kfend
manager: AnnBe
ms.date: 06/01/2017
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---
# Cloud operations and servicing
For customers, partners, and Microsoft to be successful in this endeavor, we must ensure that most of the actions are self-serve with the Microsoft Dynamics Service Engineering (DSE) team managing by exception. To attain this self-serve mode, the Microsoft Product team continues to add more automation around the various features needed to operate an environment.

## Monitor and troubleshoot the health of your environment
In the cloud version of Microsoft Dynamics 365 for Operations, a key tenant for a successful onboarding experience to the cloud service is knowing the health of your environments at all times and being able to troubleshoot health issues when necessary. Lifecycle Services (LCS), which is the admin center for Dynamics 365 for Operations, contains a collection of monitoring and diagnostics tools which can help ensure that you have an accurate view of the environments that you manage. For more information, see [Monitoring and diagnostics](monitoring-diagnostics.md).

## Update your environment
After go-live, the Production environment must be updated at regular intervals. Lifecycle Services (LCS) provides a self-serve experience to continuously update your environments.

### Update types
- **Platform**
  - Platform hotfixes are cumulative binary hotfixes that Microsoft releases to address any issues in the platform.
  - Release of a new platform. When Microsoft releases a new update to the platform, use the information provided in [Upgrade to the latest platform update](/migration-upgrade/upgrade-latest-platform-update.md), to uptake the new release.
- **Application**
  - Application hotfixes are X++ hotfixes that address issues in the application.
  - Application customizations are customizations that partners/ISVs develop on the base product that is shipped by Microsoft.
  - New release of the application. For more information about this kind of update, see [Overview of moving to the latest update of Microsoft Dynamics 365 for Operations](/migration-upgrade/upgrade-latest-update.md).

**Cloud infrastructure**
- Microsoft is responsible for managing the infrastructure for your environments. Because of this, there are certain updates, such as operating system updates, that must be done on a monthly basis in a planned maintenance window. Other kinds of updates could include changes to the infrastructure components. 

### Update policy
Currently, service updates require production tenant downtime. Platform, application, and cloud infrastructure updates are applied in two kinds of maintenance windows.
- **Microsoft planned maintenance window** - Microsoft will provide customers with no less than five business days’ notice regarding upcoming planned maintenance downtime. The default downtime window is defined per region and is scheduled to occur over a weekend to minimize impact to the business. Cloud infrastructure updates can be done in this window. For more information about planned maintenance, see the Planned maintenance window FAQ.
- **Customer initiated maintenance window** - A customer selects the maintenance window through LCS as a part of the package application flow. Platform and application updates are done in this maintenance window.

### Search for and apply an update in Lifecycle Services
Platform and application updates are applied as deployable package on an environment. A deployable package is a format that is used to apply updates to all the environments in a project. When you encounter an issue in the production environment, you can quickly find and apply a hotfix on all of the environments (Dev/Sandbox and Prod).
- **Search for and download an update**
  In LCS, you can search for an update using [Issue search](issue-search-lcs.md) or the [Update portal](/migration-upgrade/download-hofix-lcs.md). Because the steps to prepare an update differ based on the update type, after the update is downloaded, use the following list to determine how to proceed with preparation.
  - Platform update: Platform updates are cumulative and binary. This means that platform updates can be applied directly to an environment. After the platform update is downloaded, it can be automatically applied to an environment by uploading it to the Asset Library.
  - Application hotfixes: Application hotfixes are code changes. After the application hotfix is downloaded, it must be applied on a dev environment to generate a deployable package. For more information, see [Create and apply a deployable package](/deployment/create-apply-deployable-package.md) and [Installing a metadata hotfix](/migration-upgrade/install-metadata-hotfix-package.md).
  - Application customizations: These are customizations that ISV or partners create. These are deployable packages that are uploaded to the Asset Library and can be applied from there.
- **Apply an update**
  Use the information in the topic, [Apply a deployable package on a Microsoft Dynamics 365 for Operations environment](/deployment/apply-deployable-package-system.md), to walk through the steps for applying a deployable package on a Dynamics 365 for Operations system. The update package can be a binary hotfix for Application Object Server (AOS) or a deployable package that was created in your development environment.
- **Validate an update**
  After an update is applied, you should validate the application to:
  - Ensure that the update addressed the issue that it was applied for.
  - Verify that no regressions occurred from applying the update.
  - Verify that the build information was updated to reflect an update to the binaries.
    - For Platform updates, verify that the version of the AOS Service Model under Microsoft is updated.
    - For Application updates, check the version of the model that included the fix. For example, if the fix was in Application suite, then the version of the Application suite is updated.

## Upgrade your environment
For information about how to upgrade your Dynamics 365 for Operation instance to the latest version, see [Overview of moving to the latest update of Dynamics 365 for Operations](/migration-upgrade/upgrade-latest-update.md) and [What's new or changed](/get-started/whats-new-changed.md).

## Environment data management
These are the options for managing databases, including the ability to copy a database from one environment to another or restore a database to a previous state.
- Refresh database: Refresh a sandbox environment with a copy of the Production database (database restore from Prod to Sandbox). You can submit a Refresh database request in LCS to copy a database from one Azure SQL Database based environment to another.
- Point-in-time restore: You can submit a request to have a non-production database restored to a specific point in time that is within 35 days of your request. For more information about a database point-in-time restore, see [Request a point-in-time database restore on a non-production environment](/database/request-point-in-time-restore.md).
- Export a database from Azure SQL Database to SQL Server or vice versa. For more information, see [Copy a Microsoft Dynamics 365 for Operations database from SQL Server to an Azure SQL Database environment](/database/copy-database-from-sql-server-to-azure-sql.md) and [Copy a Microsoft Dynamics 365 for Operations database from Azure SQL Database to a SQL Server environment](/database/copy-database-from-azure-sql-to-sql-server.md).

## Sign up for cloud operations notifications
When the status of the package application is changed, LCS sends a notification to all of the users in a project. Any additional stakeholders who should be notified must be specified in the notification list.
1. To add additional stakeholders, in LCS, in the Environment details view, click Notification list.
2. Add the email address of each user who must be notified, and then click Save.
