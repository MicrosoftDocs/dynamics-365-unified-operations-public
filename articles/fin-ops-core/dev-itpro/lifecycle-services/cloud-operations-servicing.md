---
# required metadata

title: Cloud operations and servicing
description: This article describes cloud operations and servicing.
author: laneswenka
ms.date: 04/27/2022
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
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---
# Cloud operations and servicing

[!include [banner](../includes/banner.md)]

For customers, partners, and Microsoft to be successful in this endeavor, we must ensure that most of the actions are self-serve with the Microsoft Dynamics Service Engineering (DSE) team managing by exception. To attain this self-serve mode, the Microsoft Product team continues to add more automation around the various features needed to operate an environment.

The finance and operations apps are managed services. This means that Microsoft is responsible for managing and operating the production environments. Microsoft’s Dynamics Service Engineering team is available 24 hours a day, 7 days a week, and 365 days a year to operate and manage our customers' production systems.

## Monitor and troubleshoot the health of your environment
A key tenant for a successful onboarding experience to the cloud service is knowing the health of your environments at all times and being able to troubleshoot health issues when necessary. Lifecycle Services (LCS), which is the admin center for finance and operations, contains a collection of monitoring and diagnostics tools which can help ensure that you have an accurate view of the environments that you manage. For more information, see [Monitoring and diagnostics tools in Lifecycle Services (LCS)](monitoring-diagnostics.md).

## Update your environment
After go-live, the Production environment must be updated at regular intervals. Lifecycle Services (LCS) provides a self-serve experience to continuously update your environments.

### Update types
For customers who are on **Dynamics 365 for Finance and Operations version 8.0 (April 2018) and earlier**, the following updates are available:

- **Platform updates** – A single cumulative binary update of all the platform fixes.
- **Application hotfixes** – Application hotfixes that are released as granular X++ updates.
- **Application release** – A new major release of the application. This type of update typically requires an upgrade.
- **Application customizations** – Customizations that are built on top of the application. The best practice is to apply a single deployable package that consists of all your independent software vendor (ISV) solutions and customizations.

For customers who are on **Dynamics 365 for Finance and Operations version 8.1 (October 2018) and later**, the following updates are available:

- **Application updates** – A single cumulative binary update of the application and the platform fixes. You can update for yourself by using the regular update flows. Otherwise, you will be automatically updated by Microsoft.
- **Application customizations** – Customizations that are built on top of the application. The best practice is to apply a single deployable package that consists of all your ISV solutions and customizations.

#### Cloud infrastructure
Microsoft is responsible for managing the infrastructure for your environments. Therefore, some updates, such as operating system updates, must be done on a monthly basis in a planned maintenance window. Other kinds of updates might include changes to the infrastructure components. 

### Update policy
Currently, service updates require production tenant downtime and are applied in two kinds of maintenance windows.
- **Microsoft planned maintenance window** - Microsoft will provide customers with no less than five business days’ notice regarding upcoming planned maintenance downtime. The default downtime window is defined per region and is scheduled to occur over a weekend to minimize impact to the business. Cloud infrastructure updates can be done in this window. For more information about planned maintenance, see the Planned maintenance window FAQ.
- **Customer initiated maintenance window** - A customer selects the maintenance window through LCS as a part of the package application flow. Updates are done in this maintenance window.

### Search for and apply an update in Lifecycle Services
Updates are applied as deployable packages on an environment. A deployable package is a format that is used to apply updates to all the environments in a project. When you encounter an issue in the production environment, you can quickly find and apply a hotfix to all of the environments in a project.

- **Search for and download an update**
  In LCS, you can search for an update using [Issue search in Lifecycle Services (LCS)](issue-search-lcs.md) or the [Download updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md). Because the steps to prepare an update differ based on the update type, after the update is downloaded, use the following list to determine how to proceed with preparation.
  - Platform update: Platform updates are cumulative and binary. This means that they can be applied directly to an environment. After the update is downloaded, it can be automatically applied to an environment by uploading it to the Asset Library.
  - Application hotfixes: Application hotfixes are code changes. After the application hotfix is downloaded, it must be applied on a dev environment to generate a deployable package. For more information, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md) and [Apply updates to cloud environments](../deployment/apply-deployable-package-system.md).
  - Application customizations: These are customizations that ISV or partners create. These are deployable packages that are uploaded to the Asset Library and can be applied from there.
- **Apply an update**
  Use the information in the article, [Apply updates to cloud environments](../deployment/apply-deployable-package-system.md), to walk through the steps for applying a deployable package. The update package can be a binary hotfix for Application Object Server (AOS) or a deployable package that was created in your development environment.
- **Validate an update**
  After an update is applied, you should validate the application to:
  - Ensure that the update addressed the issue that it was applied for.
  - Verify that no regressions occurred from applying the update.
  - Verify that the build information was updated to reflect an update to the binaries.
    - For Platform updates, verify that the version of the AOS Service Model under Microsoft is updated.
    - For Application updates, check the version of the model that included the fix. For example, if the fix was in Application suite, then the version of the Application suite is updated.

## Servicing changes
Microsoft has introduced a new post-servicing step that lets you do index creation in online mode to help reduce the overall servicing downtime. While the post-processing step is occurring, the LCS dashboard will show **Post-servicing** after offline servicing is completed. During this time, some index creation and modification will be done in online mode. The environment will be accessible so that users can perform regular activities, but performance on the package changes that are involved might be degraded. During post-servicing, users won't be able cancel or trigger new service requests.

![LCS dashboard showing the the post-processing step is progress.](https://user-images.githubusercontent.com/90061039/164792400-d8ca418c-6a5e-468c-a965-eae597bfb737.png)

If any failure occurs during the post-processing step, the LCS dashboard will display **Post-servicing failed**. The environment will still be accessible so that users can perform regular activities, however performance might be degraded. If you experience that the issue is not resolved in 24 hours, then contact Microsoft Support. 

## Upgrade your environment
For information about how to upgrade to the latest version, see [Process for moving to the latest update of finance and operations](../migration-upgrade/upgrade-latest-update.md) and [What's new or changed in finance and operations home page](../../fin-ops/get-started/whats-new-changed.md).

## Environment data management
These are the options for managing databases, including the ability to copy a database from one environment to another or restore a database to a previous state. For more information, see [Database movement operations home page](../database/dbmovement-operations.md).

## Sign up for cloud operations notifications
When the status of the package application is changed, LCS sends a notification to all of the users in a project. Any additional stakeholders who should be notified must be specified in the notification list.
1. To add additional stakeholders, in LCS, in the Environment details view, click Notification list.
2. Add the email address of each user who must be notified, and then click Save.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

