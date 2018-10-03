---
# required metadata

title: Process for moving to the latest update of Finance and Operations
description: This topic explains the process for upgrading to the latest update for Microsoft Dynamics 365 for Finance and Operations.
author: robadawy
manager: AnnBe

ms.date: 10/03/2018

ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 102343
ms.assetid: e48d7424-371a-49ee-882c-07b7ceb00183
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Process for moving to the latest update of Finance and Operations

[!include [banner](../includes/banner.md)]

This topic explains the process for upgrading from earlier releases to the latest update for Microsoft Dynamics 365 for Finance and Operations. It describes the overall process and the supported scenarios, but doesn't provide detailed instructions for every step of the process.

For information about the contents of each release of Dynamics 365 for Finance and Operations, see [What's new or changed](../../fin-and-ops/get-started/whats-new-changed.md).

## Definitions

Finance and Operations platform updates consist mainly of the following components:

- Application Object Server (AOS)
- Analytics and reporting
- Microsoft Office integration
- Data management
- Integration services
- The web client
- Other binaries

They also include the following Application Object Tree (AOT) models:

- Application Platform
- Application Foundation
- Directory and Test Essentials

All other components are referred to as the Finance and Operations application.

## Introduction to the scenarios

### Scenario 1: Update to a specific application hotfix

Use this scenario when one or more small hotfixes are required in order to address a specific issue, but business factors such as time or cost limitations prohibit a complete application update.

### Scenario 2: Upgrade your custom code

This process is required before you can use scenario 3. A developer must complete this process before other activities can begin.

Dynamics 365 for Finance and Operations version 8.0 and newer, does not allow customization via overlayering of Microsoft models. Before you upgrade, you must have a plan to refactor your customizations into extensions. For more information, see [Extensibility homepage](../extensibility/extensibility-home-page.md) and [Refactor overlayering on 8.0 environments](../extensibility/refactoring-over-layering.md).

### Scenario 3: Upgrade to the latest application release

Use this scenario when business factors such as time or cost limitations prohibit an update to the complete latest application release. Here are some examples of application updates:

- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) (also known as 7.2)
- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.3
- Microsoft Dynamics 365 for Finance and Operations 8.0

To install a platform-only update, use scenario 4 instead.

### Scenario 4: Upgrade to the latest platform only

Use this scenario to update to the latest release of the platform when no application updates are required. Platform updates are always cumulative. Here are some examples of platform updates:

- Microsoft Dynamics AX with platform update 2 (August 2016)
- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition with platform update 9 (July 2017)
- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition with platform update 11 (October 2017)

> [!IMPORTANT]
> Microsoft Dynamics AX with platform update 1 (May 2016) and Platform update 2 enabled overlayering of platform X++ code. In later platform updates, the platform-level X++ is locked for overlayering. If you're upgrading from Platform update 1 or Platform update 2, your developers must refactor the overlayering as extensions before you can upgrade. If you're upgrading from Microsoft Dynamics 365 for Operations with platform update 3 (November 2016) or later to a later platform update, you don't have to refactor your X++ code.

## Scenario 1: Update to a specific application hotfix

Use this scenario when one or more small hotfixes are required in order to address a specific issue, but business factors such as time or cost limitations currently prevent you from doing a complete major application update.

To incorporate new features of the application, you don't have to do a complete upgrade of your application. All features in the current update of the application are available individually on Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download hotfixes from LCS, see [Download hotfixes from Lifecycle Services](download-hotfix-lcs.md).

## Scenario 2: Upgrade your custom code

This scenario describes the process for upgrading code from an earlier release to the current release. This process is required before you can use scenario 3. A developer must complete this process before other activities can begin. A code upgrade is required when you deploy new environments as part of the process of upgrading your application to a new major or cumulative release. A code upgrade isn't required for platform updates.

| Source environment | Expected content of the AX7.version file for the source | Target environment | Is the code upgrade service required? |
|--------------------|---------------------------------------------------------|--------------------|---------------------------------------|
| Application 7.3                               | 7.3.11971.56116 | Application release 8.0 | Yes |
| July 2017 release (Application 7.2)                               | 7.2.11792.56024 | Application release 8.0 or 7.3 | Yes |
| Release 1611 (Application 7.1)                               | 7.1.1541.3036 | Application release 8.0, 7.3, or July 2017 (7.2) | Yes |
| August 2016 release (Application 7.0.1 with Platform update 2) | 7.0.1265.27075 | Application release 8.0, 7.3, July 2017 (7.2) or 1611 (7.1) | Yes |
| May 2016 release (Application 7.0.1)                           | 7.0.1265.23014 | Application release 8.0, 7.3, July 2017 (7.2) or 1611 (7.1) | Yes |
| February 2016 release (Application 7.0)                      | 7.0.1265.3015 |  Application release 8.0, 7.3, July 2017 (7.2) or 1611 (7.1) | Yes |
| Microsoft Dynamics AX 2012                                     | Not applicable | Application release 7.3 or July 2017 (7.2)  | Yes |
| Application release 7.3         | Not applicable | Newer version of the platform | No |
| July 2017 release (Application 7.2)         | Not applicable | Newer version of the platform | No |
| Release 1611 (application 7.1)            | Not applicable | Newer version of the platform | No |
| May 2016 release (Platform update 1, application 7.0.1)        | Not applicable | August 2016 release (Platform update 2, application 7.0.1) | No |

Regardless of whether you're a live customer or you're still in the implementation phase of your project, follow these steps to upgrade your code to the latest platform and application updates.

1. Use the Code upgrade service on LCS to upgrade your code. For more information, see [Configure the code upgrade service in Lifecycle services](../lifecycle-services/configure-execute-code-upgrade.md).

    > [!NOTE]
    > The Code upgrade service also removes any old Microsoft X++ hotfixes that you've installed. Because the removal of old Microsoft X++ hotfixes is a required step, we recommend that you use the Code upgrade service even if you don't have custom code.

2. Deploy a new development environment that runs the new version that you're upgrading to. You will use this environment to merge code and refactor your custom code. Submit a request for a new development/test environment that runs the latest update.

    - You might have to delete your existing development/test environment if your subscription doesn't allow for a new development/test environment.
    - Depending on your project type, you might have these other options for deploying a developer virtual machine (VM):

        - Download a development virtual hard disk (VHD).
        - If you're running in your own Microsoft Azure subscription, deploy a new developer topology.

    - If you want to keep the development data from your old development environment, create a database backup, and keep the BAK file. Then, when you've completed the code upgrade, you can restore the database backup to your new development environment and do a data upgrade by following the steps in [Upgrade data in development, demo or sandbox environments](upgrade-data-to-latest-update.md).

3. Complete the code migration steps.

    1. Connect your development VM to Microsoft Azure DevOps, and map your local metadata folder to the Azure DevOps branch that contains your upgraded code.
    2. Synchronize, resolve any conflicts, build, and test.
    3. Merge the Azure DevOps branch that contains your upgraded code with your main development branch. For more information, see [Merge folders and files](https://www.visualstudio.com/en-us/docs/tfvc/merge-folders-files).
    4. Build and test.
    5. Create deployable packages of your code.

4. Install any hotfixes that apply to the environment.
5. Upload deployable packages to the LCS Asset library of your project.

For details about the code migration steps, see [Code migration](../dev-tools/developer-home-page.md#code-migration). After you've completed the code migration, continue to scenario 3.

## Scenario 3: Upgrade to the latest application release

> [!Important]
> If you are on application version 8.0 and want to move to the 8.1 release, follow the simplified steps in [Update environments from 8.0 to 8.1](./appupdate-80-81.md).

These steps apply to customers who are live on an earlier release and want to do a full upgrade to the most recent platform and application releases. The steps might also apply to customers who have already deployed and configured a production environment, even if they haven't yet gone live. If you aren't upgrading your application but just want to upgrade your platform, use scenario 4 instead.

### Upgrade your code

First, upgrade your code as described in scenario 2. This step is a developer task. It's done in a developer environment that is running the new release that you're upgrading to.

### Upgrade your data in a development environment

Run the data upgrade process on a copy of your source database. If your environment is already live in production, the source database is a copy of the production database. Otherwise, the source database is your most current database. Run this process in the development environment that is running the release that you're upgrading to. This step is a validation process that is done by a developer. It helps the developer verify that the data upgrade can be completed successfully by using the specific set of customizations in this environment.

To make a copy of your production database, follow the steps in [Copy a Microsoft Dynamics 365 for Finance and Operations database from Azure SQL Database to a SQL Server environment](../database/copy-database-from-azure-sql-to-sql-server.md).

To run the data upgrade process, follow the steps in [Process for data upgrade for development or demo environments](upgrade-data-to-latest-update.md).

> [!IMPORTANT]
> - Data upgrade in a development environment is a required step. It helps reduce the risk of extended downtime and upgrade errors later, when you upgrade sandbox user acceptance testing (UAT) and production environments.
> - Several application hotfixes might be required before you can upgrade data. Before you redeploy your existing development environment, verify whether these hotfixes are required. Install the required hotfixes, and check them in to Azure DevOps. This step can be completed only in the old version of your development environment. For a list of the hotfixes that are required in various situations, see [Upgrade data in develop, demo, or sandbox environments](upgrade-data-to-latest-update.md#before-you-begin).
 
### Upgrade your Tier2/Standard Acceptance Test (or higher) sandbox environment

When the following conditions are met, you must request that the Microsoft Servicing Engineering Team (DSE) run this process for you. You submit the request via LCS.

- You've completed the code upgrade process and have tested the data upgrade in your development environment.
- You're live in production, or you've already deployed your production environment.

DSE will upgrade one Tier 2 (Standard Acceptance Test) or higher sandbox environment. This upgrade process is used as a control and is a required step. The same upgrade process, including the same customization packages, will be used for your production environment upgrade. DSE uses this process as a mock upgrade to ensure a successful upgrade of your production environment.

#### Use LCS to submit an upgrade request to DSE

1. On the **Environment details** page for the environment that you're upgrading, select **Maintain**, and then select **Upgrade**. A dialog box appears, where you can enter the upgrade request.

2. Select the target version that you're upgrading to, and specify the start and end times of your preferred downtime window.
    - A date and time picker will show the available times.
    - To help ensure that the upgrade can be done within your expected timeframe, you must submit your upgrade request a minimum of five working days before you expect to upgrade. The advance notice is required so that a new environment can be prepared before your downtime window.
    
    > [!IMPORTANT] 
    > Requests are subject to availability of the DSE team, therefore, we cannot ensure the availability of a specific upgrade window. It is best to request your upgrade window as soon as you can commit to it.
    
    - You must allow for at least eight hours between the start and end of the downtime. This time is required in order to swap in the new environment and complete the data upgrade process.

3. If you have custom code or X++ hotfixes that must be part of your upgraded environment, you must select application (AOT) deployable packages during your upgrade request. Select the AOT deployable packages that contain your upgraded custom code and the required X++ hotfixes that were created in your development or build environment. Use the **Customize solution assets** tab, as shown in the following illustration.

    ![Customize solution assets tab](./media/selectsolutionassets.PNG)

    > [!IMPORTANT]
    > - If you don't select application deployable packages in your service request, DSE might reject the request.
    > - DSE will upgrade a copy of your production database on the UAT environment, DSE will not upgrade your current UAT database. Upgrading the UAT environment is intended as a pre-production validation of the upgrade process.
    > - If an error causes the upgrade process to stop, DSE will roll the environment back to its original state. You can then resolve the issue that caused the failure and reschedule the upgrade at a new time.
    > - If you're using Retail features, a minimum of 16 hours of downtime is required, because additional upgrade steps are required.

#### Validate your sandbox environment

When the DSE team completes the upgrade process, the service request status will change to **Ready for Validation**. The system is available at this stage. The updated environment will have the same URL, the same environment name, and the same machine names as the old environment. Validate and then change the status of the service request to **Validation Successful** or **Validation Failed**. If you set the service request to **Validation Failed**, a rollback of the upgrade can be requested creating a support request. For more information, see [Manage Finance and Operations support experiences](../lifecycle-services/cloud-powered-support-lcs.md). The typical time for the support team to perform the rollback is 2-4 hours. You have up to five working days to request a rollback.  After that time, Microsoft will retire the old environment.

#### Upgrade additional Tier 2 or higher sandbox environments

You don't have to upgrade any additional Tier 2 or higher sandbox environments. Instead, delete and redeploy them, and then create a database refresh request to copy a database from a Tier 2 or higher environment that has already been upgraded. Alternatively, you can manually upgrade these environments by following the steps in [Process for upgrading a sandbox environment](upgrade-sandbox-environment.md).

#### Upgrade Tier 1 environments

You can deploy Tier 1 environments (also known as dev/test or build boxes) by using the new version and then synchronizing to your upgraded Azure DevOps branch. To get data for the Tier 1 environments, a developer can upgrade the database by following the steps in [Process for data upgrade for development or demo environments](upgrade-data-to-latest-update.md).

### Upgrade your production environment

1. Use LCS to submit an upgrade request to update the production environment, just as you did for the sandbox environment.
2. Complete your validation, testing, and sign-off by setting the service request status to **Validation Successful**. If you discover an issue and want to roll back to the old environment, set the status to **Validation Failed** and then submit a production outage. For more information, see [Report production outage](https://docs.microsoft.com/en-us/business-applications-release-notes/April18/dynamics365-finance-operations/report-production-outage). Typical time for the DSE team to perform the rollback is 2-4 hours. You have up to five working days to request a rollback. After that time, Microsoft will retire the old environment.

## Scenario 4: Upgrade to the most current platform only

If you're running an environment that doesn't contain any customization of the platform AOT models (Application Platform, Application Foundation, and Directory and Test Essentials), you can do an in-place update of your platform without upgrading to a new environment. For more information about this process, see [Upgrade Finance and Operations to the latest platform update](upgrade-latest-platform-update.md). If you upgrade only your platform, you don't have to do a code upgrade (scenario 2 in this topic) or run data upgrade scripts.
