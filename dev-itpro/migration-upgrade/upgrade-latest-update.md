---
# required metadata

title: Overview of moving to the latest update of Dynamics 365 for Operations
description: This topic describes the process for upgrading to the latest update for Microsoft Dynamics 365 for Operations. This topic is intended to describe the overall process and supported scenarios, not to provide detailed instructions for every step of the process.
author: MargoC
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 11
ms.search.scope: Operations, Platform, AX Platform
# ms.tgt_pltfrm: 
ms.custom: 102343
ms.assetid: e48d7424-371a-49ee-882c-07b7ceb00183
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Overview of moving to the latest update of Dynamics 365 for Operations

This topic describes the process for upgrading to the latest update for Microsoft Dynamics 365 for Operations. This topic is intended to describe the overall process and supported scenarios, not to provide detailed instructions for every step of the process.

Overview
--------

This topic describes the overall process and the supported scenarios that are related to an upgrade from earlier releases to the current update for Dynamics 365 for Operations. It isn't intended to provide detailed instructions for every step of the process. For details of the contents of each available upgrade see [What's new or changed](../get-started/whats-new-changed.md).

## Definitions
Dynamics 365 for Operations platform updates consist mainly of the following components: Application Object Server (AOS), analytics and reporting, Microsoft Office integration, data management, integration services, the web client, and other binaries. It also includes the following Application Object Tree (AOT) models:

-   Application Platform
-   Application Foundation
-   Directory and Test Essentials

All other components are referred to as the Dynamics 365 for Operations application.

## Introduction to scenarios
### Scenario 1: Update to a specific application hotfix

Use this scenario when one (or a small number of) hotfix is required for a specific issue and business factors, such as time or cost prohibit taking an entire major application update at that moment.

### Scenario 2: Upgrade your custom code

This process is required before embarking on scenario 3 and is to be completed by a developer before other activities can begin.

### Scenario 3: Upgrade to the most current platform and application update

Use this scenario when business factors such as time or cost permit taking the complete latest update. Typical examples are:

-   Complete upgrade (application and platform) from February 2016 release to May 2016 release.
-   Complete upgrade (application and platform) from Dynamics 365 for Operations to Dynamics 365 for Operations 1611 release.

Note: August release is a platform only release, applying this update to an environment is scenario 4.

### Scenario 4: Upgrade to the most current platform only

Use this scenario to update to the latest release of the platform and no application updates are required at that time. Note that platform updates are always cumulative. Typical examples are:

-   Update your May 2016 (with platform update 1) environments to platform update 2 (August 2016 release) and you do not have any customizations of the following platform models: Application Platform, Application Foundation, Test essentials and Directory.
-   Update your environments from platform update 2 to platform update 3 and you do not have any customisations of the following platform models: Application Platform, Application Foundation, Test Essentials and Directory.

Note: If you have customised platform models scenario 4 explains how you should proceed.

## Scenario 1: Update to a specific application hotfix
Use this scenario when one (or a small number of) hotfix is required for a specific issue and business factors, such as time or cost prohibit taking an entire major application update at that moment. It is not necessary to perform a complete upgrade of your application to uptake new features of the application. All features in the current update of the  **application** are available individually on Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download hotfixes from LCS, see [Download hotfixes from Lifecycle Services](..\migration-upgrade\download-hotfix-lcs.md).

## Scenario 2: Upgrade your custom code
This scenario describes the process for upgrading code from an earlier release to the current release. This process is required before embarking on scenario 3 and is to be completed by a developer before other activities can begin. Code upgrade is needed when you deploy new environments as part of the process of upgrading your application to a new major or cumulative release.

| Source environment                                   | Target environment                                           | Do I need the code upgrade service? |
|-----------------------------------------------------|--------------------------------------------------------------|-------------------------------------|
| Microsoft Dynamics AX 2012                          | Dynamics 365 for Operations                                  | Yes                                 |
| Feb-16                                              | May 2016 (Platform update 1, Application 7.0.1)              | Yes                                 |
| Feb-16                                              | August 2016 (Platform update 2, Application 7.0.1)           | Yes                                 |
| May 2016 (Platform update 1, Application 7.0.1)     | August 2016 (Platform update 2, Application 7.0.1)           | No                                  |
| Feb-16                                              | Release 1611 (Platform update 3 or newer, Application 7.1.0) | Yes                                 |
| May 2016 (Platform update 1, Application 7.0.1)     | Release 1611 (Platform update 3 or newer, Application 7.1.0) | Yes                                 |
| August 2016 (Platform update 2, Application 7.0.1)  | Release 1611 (Platform update 3 or newer, Application 7.1.0) | Yes                                 |
| Release 1611 (Platform update 3, Application 7.1.0) | Newer version of the platform, like platform update 4        | No                                  |

Regardless of whether you're a live customer or you're still in the implementation phase of your project, follow these steps to upgrade your code to the latest platform and application updates.

1.  Use the LCS code upgrade service to upgrade your code.
    -   This step is not required if you're a customer that is running on standard Dynamics 365 for Operations and have no custom code.

2.  Submit a request for a new Dev/Test environment that is running the latest update.
    -   You might have to delete your existing Dev/Test environment if your subscription doesn't allow for a new one.
    -   Depending on your project type, these are the other options to deploy a developer VM:
        -   **Option 1:** Download a Dev VHD.
        -   **Option 2:** If you're running in your own Microsoft Azure subscription, deploy a new developer topology.

3.  Complete the code migration steps.
    1.  Connect your development virtual machine (VM) to Microsoft Visual Studio Team Services (VSTS), and map your local metadata folder to the VSTS branch that contains your upgraded code\*.
    2.  Synchronize, resolve conflicts (when applicable), build, and test.
    3.  Merge the VSTS branch that contains your upgraded code with your main development branch. For more information, see [Merge folders and files](https://www.visualstudio.com/en-us/docs/tfvc/merge-folders-files).
    4.  Build and test.
    5.  Create deployable packages of your code.

    **\*Note:** If the code upgrade service results don't show any conflicts, or if you have no custom code and you did not run the LCS code upgrade service, map your local metadata folder directly to the main development branch of the VSTS project. However, make sure that you delete all existing Microsoft hotfixes from the main branch. Microsoft hotfixes are XML files that belong to Microsoft Sys layer models, these were checked in as part of the process of installing metadata hotfixes on development environments running a previous release.
4.  Install any hotfixes that apply to the environment.
5.  Upload deployable packages to the LCS Asset library of your project.

For more details on code migration steps, see [Code Migration](..\dev-tools\developer-home-page.md#code-migration). After code migration is complete, continue to scenario 3.

## Scenario 3: Upgrade to the most current platform and application update
These steps apply to customers who are live on an earlier release and want to perform a full upgrade to the most recent platform and application versions. Customers who have already deployed and configured a production environment might also fall into this category, even if they haven't gone live yet. If you are not upgrading your application, but want to upgrade your platform to the latest bits, use scenario 4 below, especially if you have no customizations of the platform models.

### Upgrade your code

First, upgrade your code as described in scenario 2. This is a developer task and will happen on a developer environment.

### Upgrade your data

Execute the data upgrade process on a copy of your target database – if already live in production then this would mean a copy of production, prior to go-live it would be your most current database. This is a validation process performed by a developer to ensure the data upgrade completes successfully with the specific set of customizations within this environment – and will drive success in the sandbox and production environments later. To copy your database back to a developer environment follow the steps in [Copy a Microsoft Dynamics 365 for Operations database from Azure SQL Database to a SQL Server environment](..\database\copy-database-from-azure-sql-to-sql-server.md) To execute the data upgrade process follow the steps in [Process for data upgrade for development or demo environments](upgrade-data-to-latest-update.md).

### Upgrade your sandbox environment

1.  Use LCS to submit a request (using the "Other" request type) to update the sandbox environment from your current release to the most recent update. This request represents acknowledgment that you're ready for downtime (up to 48 hours) in your sandbox environment. This request should be submitted at least 48 hours before the upgrade is due to start to ensure that resources are available to execute the request.
    1.  A Dynamics Service Engineer (DSE) detaches your existing sandbox environment from your LCS project.
    2.  You request, via LCS, a new update deployment that has your upgraded AOT deployable packages.
    3.  You approve the configuration and sign off.
    4.  The DSE deploys the environment.
    5.  The DSE connects the update environment to a copy of your current production database.
    6.  The DSE runs data upgrade scripts.
    7.  The DSE attaches the new environment to your LCS project.
    8.  The DSE notifies you about completion of the update.

2.  Validate. The updated environment will have the same URL as the former environment, however the environment name and machine names will change.
3.  When validation is completed successfully, notify DSE via the LCS ticket and the DSE will retire your old environment.

### Upgrade your production environment

1.  Use LCS to submit a request (using the "Other" request type) to update the production environment from your existing environment to the most recent update. This request represents acknowledgement that you're ready for downtime (up to 48 hours). This request should be submitted at least 48 hours before the upgrade is due to start to ensure that resources are available to execute the request.
2.  Repeat step 1, which includes all eight substeps, in the previous procedure.
3.  Validate.
4.  When validation is completed successfully, notify the DSE via the LCS ticket and the DSE will retire your old environment.

## Scenario 4: Upgrade to the most current platform only
If you're running an environment that doesn't contain any customization of the platform AOT models (Application Platform, Application Foundation, Directory and Test Essentials), you can do an in-place update of your platform, without upgrading to a new environment. For more information about this process, see: [Upgrade Dynamics 365 for Operations to the latest platform update](upgrade-latest-platform-update.md). If you only upgrade your platform, there is no need to do code upgrade (Scenario 2 above) or run data upgrade scripts.

