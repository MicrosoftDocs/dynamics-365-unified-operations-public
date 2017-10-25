---
# required metadata

title: Upgrade Finance and Operations to the latest platform update
description: This topic explains how to upgrade your Microsoft Dynamics 365 for Finance and Operations platform version to the latest platform release.
author: tariqbell
manager: AnnBe
ms.date: 05/23/2017
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
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 253274
ms.assetid: a70a4f28-9269-4b35-bc29-1edba0b92d83
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3
---

# Upgrade Finance and Operations to the latest platform update

[!include[banner](../includes/banner.md)]

This topic explains how to upgrade your Microsoft Dynamics 365 for Finance and Operations platform version to the latest platform release.

Overview
--------

The Microsoft Dynamics 365 for Finance and Operations platform consists of the following components:

-   Finance and Operations platform binaries such as Application Object Server (AOS), the data management framework, the reporting and business intelligence (BI) framework, development tools, and analytics services.
-   The following Application Object Tree (AOT) packages:
    -   Application Platform
    -   Application Foundation
    -   Test Essentials

> [!IMPORTANT]
> To move to the latest Finance and Operations platform, your Finance and Operations implementation **cannot** have any customizations (overlayering) of any of the AOT packages that belong to the platform. This restriction was introduced in Platform update 3, so that seamless continuous updates can be made to the platform. If you are running on an platform that is older than Platform update 3, see the section [Upgrading to Platform update 3 from an earlier build](#Upgrading-to-platform-update-3-from-an-earlier-build) section at the end of this topic.

## Overall flow
The following illustration shows the overall process for upgrading the Finance and Operations platform to the latest update.

[![Upgrade process for implementations that have no customization of the platform](./media/flownocustomisations.jpg)](./media/flownocustomisations.jpg)

If you are already running on platform update 4 or later, updating the Finance and Operations platform to the latest release is a simple servicing operation. Once the platform update package is in your LCS asset library, follow the flow to apply an update from the LCS environment page: Select Apply updates under Maintain then select the platform update package.

[![Apply updates](./media/applyupdates.jpg)](./media/applyupdates.jpg)

Learn how to get the latest platform package in the next section.

## How to get the latest platform package
There are 3 ways to get the latest platform update package.
- In Lifecycle Services (LCS), import the platform update package from the Shared Asset Library.
- Search for "platform update" in LCS **Issue Search**.
- Click the **Binary Updates** tile of your environment's page in LCS (As of Platform update 4, binary updates from LCS include an upgrade to the latest platform).

### Import the platform update package
Platform update packages are released by Microsoft and can be imported from the Shared asset library in Microsoft Dynamics Lifecycle Services (LCS). Dynamics 365 packages are currently prefixed with *Finance and Operations Platform Update* (for example, Finance and Operations Platform Update 3)*.* Use these steps to import the platform update package:

1.  Go to your LCS project's Asset library.
2.  On the **Software deployable package** tab, click **Import** to create a reference to the platform update package. [![Import button](./media/importupgradepackage.png)](./media/importupgradepackage.png)
3.  Select the desired platform update package.

## Choose the correct package deployment method
From a process perspective, deploying a platform upgrade package resembles a binary hotfix deployable package.

-   To apply a platform update package to your cloud development, build, demo, tier-2 sandbox, or production environment, update directly from LCS.
[![Apply updates](./media/applyupdates.jpg)](./media/applyupdates.jpg) 
For more details, follow the instructions for applying a binary hotfix in [Apply a deployable package on a Microsoft Dynamics 365 for Finance and Operations system](..\deployment\apply-deployable-package-system.md).

-   To apply a platform update package to your local development environments (environments not connected to LCS servicing), follow the instructions in the next section.

> [!NOTE]
> **Migrate files for Document management**: After upgrading to Platform update 6 or later, an administrator needs to click the **Migrate Files** button on the **Document management parameters** page to finish the upgrade process. This will migrate any attachments stored in the database to blob storage. The migration will run as a batch process and could take a long time, depending on the number and size of the files being moved from the database into Azure blob storage. The attachments will continue to be available to users while the migration process is running, so there should be no noticeable effects from the migration. To check if the batch process is still running, look for the **Migrate files stored in the database to blob storage** process on the **Batch jobs** page.

## Apply the platform update package on your development environment
Follow the instructions in this section if you are upgrading your local development or build environment to the latest platform. 
> [!NOTE]
> This only applies to environments that cannot be updated directly from LCS.

### Install the deployable package

1.  Download the platform update package (AXPlatformUpdate.zip) to your virtual machine (VM).
2.  Unzip the contents to a local directory.
3.  Depending on the type of environment that you're upgrading, open the PlatformUpdatePackages.Config file under \\AOSService\\Scripts, and change the **MetaPackage** value.
    -   If you're upgrading a development or demo environment that contains source code, change the **MetaPackage** value to **dynamicsax-meta-platform-development**.
    -   If you're upgrading a runtime environment, such as a tier-2 sandbox environment or another environment that doesn't contain source code, the default value, **dynamicsax-meta-platform-runtime**, is correct.

> [!NOTE]
> Step 3 is not applicable when upgrading to platform update 4 or newer.

4.  Follow the instructions for installing a deployable package. See [Install a deployable package](../deployment/install-deployable-package.md).
5.  If you're working in a development environment, rebuild your application’s code.


#### Example

    AXUpdateInstaller.exe generate -runbookid="OneBoxDev" -topologyfile="DefaultTopologyData.xml" -servicemodelfile="DefaultServiceModelData.xml" -runbookfile="OneBoxDev-runbook.xml"

    AXUpdateInstaller.exe import -runbookfile=OneBoxDev-runbook.xml

    AXUpdateInstaller.exe execute -runbookid=OneBoxDev

### Install the Visual Studio development tools

> [!NOTE]
> Skip this section if you are updating to platform update 4 or newer, development tools are automatically installed as part of installing the deployable package.

Update the Visual Studio development tools as described in [Updating the Visual Studio development tools](../dev-tools/update-development-tools.md).

### Regenerate form adaptor models

Form adaptor models are required for test automation. Regenerate the platform form adaptor models, based on the newly updated platform models. Use the xppfagen.exe tool to generate the form adaptor models. This tool is located in the package's bin folder (typically, j:\\AosService\\PackagesLocalDirectory\\bin). Here is a list of the platform form adaptor models:

-   ApplicationPlatformFormAdaptor
-   ApplicationFoundationFormAdaptor
-   DirectoryFormAdaptor

The following examples show how to generate the form adaptor models.

    xppfagen.exe -metadata=j:\AosService\PackagesLocalDirectory -model="ApplicationPlatformFormAdaptor" -xmllog="c:\temp\log1.xml"

    xppfagen.exe -metadata=j:\AosService\PackagesLocalDirectory -model="ApplicationFoundationFormAdaptor" -xmllog="c:\temp\log2.xml"

    xppfagen.exe -metadata=j:\AosService\PackagesLocalDirectory -model="DirectoryFormAdaptor" -xmllog="c:\temp\log3.xml"

### Install the new Data Management service

> [!NOTE]
> Skip this section if you are updating to platform update 4 or newer, the data management service is automatically installed as part of installing the deployable package.

After the deployable package is installed, follow these instructions to install the new Data Management service. Open a **Command Prompt** window as an administrator, and run the following commands from the .\\DIXFService\\Scripts folder.

    msiExec.exe /uninstall {5C74B12A-8583-4B4F-B5F5-8E526507A3E0} /passive /qn /quiet

If you're connected to Microsoft SQL Server Integration Services 2016 (13.0), run the following command.

    msiexec /i "DIXF_Service_x64.msi" ISSQLSERVERVERSION="Bin\2012" SERVICEACCOUNT="NT AUTHORITY\NetworkService" /qb /lv DIXF_log.txt

If you're connected to an earlier release of Microsoft SQL Server Integration Services, run the following command.

    msiexec /i "DIXF_Service_x64.msi" ISSQLSERVERVERSION="Bin" SERVICEACCOUNT="NT AUTHORITY\NetworkService" /qb /lv DIXF_log.txt

## Apply the platform update package on a build environment

> [!NOTE]
> Skip this section if you are updating to platform update 7 or newer. This was a pre-requesite step for build environments.

If the build machine has been used for one or more builds, you should restore the metadata packages folder from the metadata backup folder before you upgrade the VM to a newer Dynamics 365 for Finance and Operations platform. You should then delete the metadata backup. These steps help ensure that the platform update will be applied on a clean environment. The next build process will then detect that no metadata backup exists and will automatically create a new one. This new metadata backup will include the updated platform. To determine whether a complete metadata backup exists, look for a BackupComplete.txt file in I:\\DynamicsBackup\\Packages (or C:\\DynamicsBackup\\Packages on a downloadable virtual hard disk \[VHD\]). If this file is present, a metadata backup exists, and the file will contain a timestamp that indicates when it was created. To restore the deployment's metadata packages folder from the metadata backup, open an elevated Windows PowerShell **Command Prompt** window, and run the following command. This command will run the same script that is used in the first step of the build process.

    if (Test-Path -Path "I:\DynamicsBackup\Packages\BackupComplete.txt") { C:\DynamicsSDK\PrepareForBuild.ps1 }

**Note:** Run the preceding command only if a complete metadata backup exists. If a complete metadata backup doesn't exist, the command will create a new backup. This command will stop the Finance and Operations deployment services and Internet Information Services (IIS) before it restores the files from the metadata backup to the deployment's metadata packages folder. You should see output that resembles the following example. <br><br>*6:17:52 PM: Preparing build environment...* *6:17:53 PM: Updating Dynamics SDK registry key with specified values...* *6:17:53 PM: Updating Dynamics SDK registry key with values from AOS web config...* *6:17:53 PM: Stopping Finance and Operations deployment...* *6:18:06 PM: **A backup already exists at: I:\\DynamicsBackup\\Packages. No new backup will be created**.* *6:18:06 PM: **Restoring metadata packages from backup...*** *6:22:56 PM: **Metadata packages successfully restored from backup**.* *6:22:57 PM: Preparing build environment complete.* *6:22:57 PM: Script completed with exit code: 0* <br><br> After the metadata backup has been restored, delete (or rename) the metadata backup folder (DynamicsBackup\\Packages), so that it will no longer be found by the build process.

### Apply the platform update package

After you've prepared your build environment for this update, apply the platform update package by using the same method that you use on other environments.

## Upgrading to platform update 3 from an earlier build
When upgrading to platform update 3 from an earlier build, there are some very important considerations because of two key changes in update 3:

- It is no longer possible to overlayer platform models (Application Platform, Application Foundation, Test Essentials).
- You need to delete all X++ hotfixes to the platform that are in you version control (see the section below)
- The Directory model is no longer in platform, it has moved to the application in Finance and Operations release 1611.

This means two things:

1.  If taking only platform update 3 and not taking the application update (Finance and Operations version 1611), then you cannot have overlayering on any of the following models. All overlayering on these models must be removed before attempting to install update 3:
    -   Application Platform
    -   Application Foundation
    -   Test Essentials
    -   Directory

2.  If you cannot remove over-layering from the Directory model, and you still want to upgrade, you will have to do a complete upgrade of the platform and the application (Finance and Operations version 1611) as described in [Overview of moving to the latest update of Finance and Operations](upgrade-latest-update.md).

### How to Delete platform metadata hotfixes from your VSTS project?

> [!NOTE]
> This section is not relevant if you are already on Platform update 3 and updating to a newer platform.

Before you install the new platform update, you must clean up your Microsoft Visual Studio Team Services (VSTS) source control project.
Remove any X++ or metadata hotfixes that you've installed on your existing platform. If you have any X++ or metadata hotfixes that are checked in to your VSTS project for any of the following Microsoft models, delete them from your project by using the Microsoft Visual Studio Source Control Explorer.

-   Application Platform
-   Application Foundation
-   TestEssentials
-   Directory

You can find these hotfixes by browsing the check-in history of these Microsoft models. For example, use Source Control Explorer to browse the check-in history of the Trunk\\Main\\Metadata\\ApplicationFoundation\\ApplicationFoundation folder, and delete all XML files that have been checked in to it.
![View History](./media/checkinhistory.png)

See also
--------

[Overview of moving to the latest update of Microsoft Dynamics 365 for Finance and Operations](upgrade-latest-update.md)



