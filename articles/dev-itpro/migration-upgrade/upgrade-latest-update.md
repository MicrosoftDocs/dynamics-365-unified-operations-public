---
# required metadata

title: Process for moving to the latest update of Finance and Operations
description: This topic explains the process for moving to the latest update of Microsoft Dynamics 365 for Finance and Operations.
author: laneswenka
manager: AnnBe
ms.date: 12/04/2018
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
[!include [banner](../includes/preview-banner.md)]

This topic explains the process of updating or upgrading to the latest release of Microsoft Dynamics 365 for Finance and Operations.  It describes the overall process and supported scenarios, but doesn’t provide detailed instructions for every step of the process.

For information about the contents of each release of Dynamics 365 for Finance and Operations, see [What's new or changed](../../fin-and-ops/get-started/whats-new-changed.md).

## Definitions

- *Public preview* – This is a feature that has been made generally available to all, and the functionality is supported.  There are potentially additional functionality improvements, or Known Issues, that look to be resolved to end the preview phase.
- *Deprecation* – This is a feature or process that will not be supported long term.  The date of when this feature or process ends support should be stated.
- *Upgrade* – This is the process of moving from one official release of Finance and Operations to the next, but prior to version 8.0.  Some examples would be moving from 7.1 to 7.3, or 7.3 to 8.1 and so forth.  This involves standing up a free Sandbox environment, Code Upgrade, and Data Upgrade.
- *Update* – This is the process of applying a binary package to your environment to advance it from one official release of Finance and Operations to the next, starting with version 8.0.  This involves drastically lower downtime requirements, and involves no Data Upgrade.


## Introduction to the scenarios

### Scenario 1: Update to a specific application hotfix [To Be Deprecated]

> [!Important]
> This will be deprecated by April, 2019 when all customers should be on version 8.1 or newer.  Version 8.1 no longer releases or supports individual X++ hotfixes.

Use this scenario when one or more small hotfixes are required in order to address a specific issue, but business factors such as time or cost limitations prohibit a complete application update.

### Scenario 2: Upgrade your custom code

This process is required before you can use scenario 3. A developer must complete this process before other activities can begin.

Dynamics 365 for Finance and Operations version 8.0 and newer, does not allow customization via overlayering of Microsoft models. Before you upgrade, you must have a plan to refactor your customizations into extensions. For more information, see [Extensibility homepage](../extensibility/extensibility-home-page.md) and [Refactor overlayering on 8.0 environments](../extensibility/refactoring-over-layering.md).

### Scenario 3: Upgrade to the latest application release

Use this scenario to advance to the latest release of Finance and Operations.  

Using the defined process below, you will be able to stand up a free Sandbox environment and will be in full control of your downtime window in both your pre-production and Production environments.

### Scenario 4: Upgrade to the latest platform only

Use this scenario to update to the latest release of the platform when no application updates are required. Platform updates are always cumulative. Here are some examples of platform updates:

- Microsoft Dynamics AX with platform update 2 (August 2016)
- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition with platform update 9 (July 2017)
- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition with platform update 11 (October 2017)

> [!IMPORTANT]
> Microsoft Dynamics AX with platform update 1 (May 2016) and Platform update 2 enabled overlayering of platform X++ code. In later platform updates, the platform-level X++ is locked for overlayering. If you're upgrading from Platform update 1 or Platform update 2, your developers must refactor the overlayering as extensions before you can upgrade. If you're upgrading from Microsoft Dynamics 365 for Operations with platform update 3 (November 2016) or later to a later platform update, you don't have to refactor your X++ code.

## Scenario 1: Update to a specific application hotfix [To Be Deprecated]

> [!Important]
> This will be deprecated by April, 2019 when all customers should be on version 8.1 or newer.  Version 8.1 no longer releases or supports individual X++ hotfixes.

Use this scenario when one or more small hotfixes are required in order to address a specific issue, but business factors such as time or cost limitations currently prevent you from doing a complete major application update.

To incorporate new features of the application, you don't have to do a complete upgrade of your application. All features in the current update of the application are available individually on Microsoft Dynamics Lifecycle Services (LCS). For more information about how to download hotfixes from LCS, see [Download hotfixes from Lifecycle Services](download-hotfix-lcs.md).

## Scenario 2: Upgrade your custom code

This scenario describes the process for upgrading code from an earlier release to the current release. This process is required before you can use scenario 3. A developer must complete this process before other activities can begin. A code upgrade is required when you deploy new environments as part of the process of upgrading your application to a new major or cumulative release. A code upgrade isn't required for platform updates.

| Source environment | Expected content of the AX7.version file for the source | Target environment | Is the code upgrade service required? |
|--------------------|---------------------------------------------------------|--------------------|---------------------------------------|
| Application 7.3                               | 7.3.11971.56116 | Application release 8.x | Yes |
| July 2017 release (Application 7.2)                               | 7.2.11792.56024 | Application release 8.x or 7.3 | Yes |
| Release 1611 (Application 7.1)                               | 7.1.1541.3036 | Application release 8.x, 7.3, or July 2017 (7.2) | Yes |
| August 2016 release (Application 7.0.1 with Platform update 2) | 7.0.1265.27075 | Application release 8.x, 7.3, July 2017 (7.2) or 1611 (7.1) | Yes |
| May 2016 release (Application 7.0.1)                           | 7.0.1265.23014 | Application release 8.x, 7.3, July 2017 (7.2) or 1611 (7.1) | Yes |
| February 2016 release (Application 7.0)                      | 7.0.1265.3015 |  Application release 8.x, 7.3, July 2017 (7.2) or 1611 (7.1) | Yes |
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

## Scenario 3: Upgrade to the latest application release [Public Preview]

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
 
### Upgrade your Tier2/Standard Acceptance Test (or higher) sandbox environment [Public Preview]

When you’ve completed the code and have been able to execute a data upgrade in your development environment end-to-end without manipulating data in SQL Server, you may elect to begin the process in Sandbox.

To do so, ensure that your account has the Self-Service Upgrade feature enabled by visiting Lifecycle Services -> Preview feature management.  Locate the option for Upgrade environment self serve and ensure it is set to Enabled.

**Prerequisite** - 
As a precursor to beginning your upgrade, it is highly recommended to ensure your Sandbox environment has the latest Production data.  This will give you a higher degree of confidence that the upgrade will work in Production if the data set is current.  To do this, please use our other self-service action for [Database Refresh](../database/database-refresh.md).

**Begin the Upgrade** - 
On your sandbox environment, visit the Maintain menu and select the Upgrade button.

<br/><img src="media/UpgradeAutomation/01_Select.png" width="700px" /><br/>

A new slider will open for you to select the latest Application and Platform combination.

<br/><img src="media/UpgradeAutomation/02_Prepare.png" width="500px" /><br/>

*Note* – if you receive an error for Preparation Failed, see the Known Issues list below.

**Preparation** - 
The environment details screen will now refresh to show two distinct Sandbox environments in the top right corner.  You can toggle back and forth between to get to your old Sandbox or your new Upgrade-in-progress Sandbox.

<br/><img src="media/UpgradeAutomation/03_Provision.png" width="700px" /><br/>

The preparation phase can take upwards of 8 hours as it is similar to a full environment deployment.  The key difference with your Upgrade-in-progress Sandbox is that it is connected to an empty Azure SQL database, and that it is running on the newer version you have selected to deploy.

During this time, your original Sandbox is left untouched and there is zero downtime impact.  

*Note* - if you receive an error that Staging Deployment has failed, Microsoft Dynamics Service Engineering (DSE) team has been notified and we will proactively resolve the issue for you.  You will receive an email when the Staging Deployment has completed successfully.  This can occur if Microsoft Azure doesn’t have the required resources available in your region, we will work with them to provide more allocation.

**Package Application** - 
Once the Staging Deployment completes, you can revisit the Environment Details page -> Upgrade-in-progress view.  On this view, you will see a new Upgrade sub-menu.  

Under this Upgrade menu, you will have an option for Apply Updates.  This is how you can apply your Software Deployable Packages on the new environment.  This includes any binary package be it from an ISV solution, your own Customization packages, and Platform Binary Update packages. 

<br/><img src="media/UpgradeAutomation/06_ApplyUpdates.png" width="700px" /><br/>

As you apply a new package to the environment, it is the same process as normal environment servicing.  When complete, you will be required to use the Sign Off button on that package before you can move forward or apply another package.

If a package deployment fails, you can use the Rollback button to reverse that package deployment.  Note, this is NOT the Rollback option under the Upgrade sub-menu.  Each package deployment can around one hour to complete.

**Data Upgrade & Environment Swap** - 
Once all packages are applied to your Upgrade-in-progress Sandbox and signed off, you can begin the Data Upgrade.  *Note*, this will begin the downtime for your original Sandbox environment.

Using the Upgrade sub-menu, click the Data Upgrade option.  This will power down your original Sandbox environment, and will swap the database connection so that your new environment is connected to the original database.  This process can take up to one hour.

<br/><img src="media/UpgradeAutomation/08_DataUpgrade.png" width="700px" /><br/>

<br/><img src="media/UpgradeAutomation/09_Swap.png" width="500px" /><br/>

After this, the Data Upgrade package for your target version will be automatically applied for you.  The process of applying the Data Upgrade package can vary depending on the size of your database.

**Commit or Rollback** - 
After the Data Upgrade operation completes, you can review the environment and have your users perform business validation activities.  If this validation is successful, you can mark the entire upgrade as a success by using the Commit action from the Upgrade sub-menu.  You must Commit the upgrade to move on to your Production environment.

<br/><img src="media/UpgradeAutomation/10_CommitRollback.png" width="700px" /><br/>

If the validation fails, you can use the Rollback action from the Upgrade sub-menu.  This will perform a Point-in-time restore of the database, and will swap the database connection back to your original Sandbox and bring it back online.  This will provide the Sandbox back in its previous state. 

**Upgrade Production** - 
By reaching this stage you have finished the upgrade process.  You can now begin the same process on your Production environment and can follow the exact same steps.

Should you run in to an issue that is causing undue downtime on your Production upgrade, please use the [Report production outage](https://docs.microsoft.com/en-us/business-applications-release-notes/April18/dynamics365-finance-operations/report-production-outage) process to alert Microsoft for assistance.

**Upgrade additional environments** - 
You can choose to upgrade additional sandbox environments in this same fashion.  You also can simply Deallocate, and Delete your other sandbox environments and then re-deploy on the newer version.  Using the [Database Refresh](../database/database-refresh.md) self-service action, you can copy in the upgraded database from another Sandbox or Production environment.

**Known Issues**

*Prepare operation could not start.  Microsoft support has been notified.  If the issue persists, please contact support with this ID*
This is a known issue around environment certificates on the LCS backend.  If this impacts you please submit a support ticket with your ActivityID from the error message and we will work to get it resolved.  Going forward we are building a list of impacted environments and will proactively fix this issue.

*I want to cancel the upgrade and try again at a later time*
To cancel you can use the Cancel Upgrade action from the Maintain menu.  The Maintain menu is visible from the old or original Sandbox View, and not from the Upgrade-in-progress view.

*Upgrade failed at step X: DVT script for service model: MRProcessService*
This DVT error is intermittent and is resolved by using the Resume button for your data upgrade package.  Click Resume and the process will pick up at this step and move forward.  Going forward we are trying to reliably reproduce this issue and will produce a fix.

*Application configuration sync failed.  Call to TTSCOMMIT without first calling TTSBEGIN.*
This TTSCOMMIT error is intermittent and is resolved by using the Resume button for your data upgrade package.  Click Resume and the process will pick up at this step and move forward.  Going forward we are trying to reliably reproduce this issue and will produce a fix.


## Scenario 4: Upgrade to the most current platform only

If you're running an environment that doesn't contain any customization of the platform AOT models (Application Platform, Application Foundation, and Directory and Test Essentials), you can do an in-place update of your platform without upgrading to a new environment. For more information about this process, see [Upgrade Finance and Operations to the latest platform update](upgrade-latest-platform-update.md). If you upgrade only your platform, you don't have to do a code upgrade (scenario 2 in this topic) or run data upgrade scripts.
