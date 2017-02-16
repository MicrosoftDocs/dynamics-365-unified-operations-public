---
# required metadata

title: Upgrade the Dynamics AX platform to the August 2016 release
description: This topic explains how to upgrade your Microsoft Dynamics AX platform to the August 2016 release of Dynamics AX.
author: MargoC
manager: AnnBe
ms.date: 2016-08-15 18 - 30 - 38
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 11
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 125753
ms.assetid: 86ab9d3f-43a6-4670-a1d9-0e81cd8b5049
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.dyn365.ops.intro: Aug-16
ms.dyn365.ops.version: Platform update 2

---

# Upgrade the Dynamics AX platform to the August 2016 release

This topic explains how to upgrade your Microsoft Dynamics AX platform to the August 2016 release of Dynamics AX.

Overview
--------

**Important:** This topic applies only to Microsoft Dynamics AX releases prior to August 2016. For Microsoft Dynamics 365 for Operations updates, see the topic: [Upgrade Dynamics 365 for Operations to the latest platform update](upgrade-latest-platform-update.md). The Microsoft Dynamics AX platform consists of the following components:

-   Dynamics AX platform binaries such as Application Object Server (AOS), the data management framework, the reporting and business intelligence (BI) framework, development tools, and analytics services
-   The following Application Object Tree (AOT) packages:
    -   Application Platform
    -   Application Foundation
    -   Directory
    -   TestEssentials

**Important:** If you want to update the Dynamics AX platform to a new release, your Dynamics AX implementation should not have any customizations (overlayering) of any of the AOT packages that belong to the platform. If you **do** customize platform packages (that is, if your solution contains models that belong to one or more of the platform packages), complete the workaround that is described at the end of this topic, and the overall process that is illustrated and described for Dynamics AX implementations that have customized platform packages.

## Overall flow
The following illustrations show the different overall process for two scenarios for upgrading the Dynamics AX platform to the latest update.

### Dynamics AX implementations that have no customization of the platform

[![Upgrade process for implementations that have no customization of the platform](./media/flownocustomisations.jpg)](./media/flownocustomisations.jpg)

### Dynamics AX implementations that have customized platform packages

[![Upgrade process for implementations that have customized platform packages](./media/flowwithcustomisations.jpg)](./media/flowwithcustomisations.jpg)

## Import the platform update package
Platform update packages are released by Microsoft and can be imported from the Shared Asset Library in Microsoft Lifecycle Services (LCS). The package is named **Dynamics AX platform August 2016 release (Update 2).** If you haven't done so yet, import the **Dynamics AX platform August 2016 release (Update 2)** package to your project's asset library by following these steps:

1.  Go to your LCS project's asset library.
2.  Select the Software Deployable Package tab.
3.  Click **Import **then select the **Dynamics AX platform August 2016 release (Update 2)** shared package.[![importupgradepackage](./media/importupgradepackage.png)](./media/importupgradepackage.png)

## How to apply the platform upgrade package
From a process perspective, a platform upgrade package is similar to a binary hotfix deployable package.

-   To apply the package to your development or build environment, follow the instructions in the sections below.
-   To apply the package to your demo, sandbox tier-2, or production environments, follow the instructions for a binary hotfix in the topic [Apply a Deployable package](apply-deployable-package-system.md).

## Apply the platform update package on your development environment
### Delete any platform metadata hotfixes from your VSTS project

Before you install the new platform update, you need to clean up your Visual Studio Team Services (VSTS) source control project. Remove any X++ or metadata hotfixes you have installed on your existing platform. If you have any X++ or metadata hotfixes that are checked in your VSTS project for any of the following Microsoft models, delete them from your project using the Visual Studio Source Control Explorer.

-   Application Platform
-   Application Foundation
-   Directory
-   TestEssentials

You can find these hotfixes by browsing the check-in history of these models Microsoft models. For example, use Source Control Explorer to browse the check-in history of the folder *TrunkMainMetadataApplicationFoundationApplicationFoundation* and delete all XML files that have been checked in this Microsoft model. [![CheckInHistory](./media/checkinhistory.png)](./media/checkinhistory.png)

### Install the deployable package

1.  Copy the platform update package (AXPlatformUpdate.zip) to your virtual machine.
2.  Unzip the contents to a local directory.
3.  Depending on the type of environment that you're upgrading, open the PlatformUpdatePackages.Config file under AOSServiceScripts, and change the MetaPackage value:
    -   If you're upgrading a development or demo environment that contains source code, change the **MetaPackage** value to **dynamicsax-meta-platform-development**.
    -   If you're upgrading a runtime environment, such as a Tier-2 sandbox or other environment that doesn't contain source code, the default value, **dynamicsax-meta-platform-runtime**, is correct.

4.  Follow the standard instructions for installing a deployable package. See [Install a deployable package in Microsoft Dynamics AX](install-deployable-package.md).
5.  If you're working in a development environment, rebuild your application’s code.

**Important:** Do not apply this update in a runtime environment unless you have validated it in a development environment first.

#### Example for a one-box (development or demo) environment

    AXUpdateInstaller.exe generate -runbookid="OneBoxDev" -topologyfile="DefaultTopologyData.xml" -servicemodelfile="DefaultServiceModelData.xml" -runbookfile="OneBoxDev-runbook.xml"

    AXUpdateInstaller.exe import -runbookfile=OneBoxDev-runbook.xml

    AXUpdateInstaller.exe execute -runbookid=OneBoxDev

### Install the Visual Studio development tools

Update the Microsoft Visual Studio development tools as described in [Updating the Dynamics AX Visual Studio development tools](update-development-tools.md).

### Regenerate form adaptor models

Form adaptor models are required for test automation. Regenerate the platform form adaptor models, based on the newly updated platform models. Use the xppfagen.exe tool to generate the form adaptor models. This tool is located in the package's bin folder (typically, j:AosServicePackagesLocalDirectorybin). Here is a list of the platform form adaptor models:

-   ApplicationPlatformFormAdaptor
-   ApplicationFoundationFormAdaptor
-   DirectoryFormAdaptor

The following examples show how to generate the form adaptor models.

    xppfagen.exe -metadata=j:AosServicePackagesLocalDirectory -model="ApplicationPlatformFormAdaptor" -xmllog="c:templog1.xml"

    xppfagen.exe -metadata=j:AosServicePackagesLocalDirectory -model="ApplicationFoundationFormAdaptor" -xmllog="c:templog2.xml"

    xppfagen.exe -metadata=j:AosServicePackagesLocalDirectory -model="DirectoryFormAdaptor" -xmllog="c:templog3.xml"

### Install the new Data Management service

After the deployable package is installed, follow these instructions to install the new Data Management service. Open a Command Prompt window as an administrator, and run the following commands from the .DIXFServiceScripts folder.

    msiExec.exe /uninstall {5C74B12A-8583-4B4F-B5F5-8E526507A3E0} /passive /qn /quiet

If you're connected to Microsoft SQL Server Integration Services 2016 (13.0), run the following command.

    msiexec /i "DIXF_Service_x64.msi" ISSQLSERVERVERSION="Bin2012" SERVICEACCOUNT="NT AUTHORITYNetworkService" /qb /lv DIXF_log.txt

If you're connected to an earlier release of Microsoft SQL Server Integration Services, run the following command.

    msiexec /i "DIXF_Service_x64.msi" ISSQLSERVERVERSION="Bin" SERVICEACCOUNT="NT AUTHORITYNetworkService" /qb /lv DIXF_log.txt

## Apply the platform update package on a build environment
Applying the platform upgrade package on a build environment requires the same procedure as applying it on a development environment. However, you need to prepare your build environment first before you upgrade it to the latest platform as described next.

### Prepare your build environment

When the build machine has been used for one or more builds, you should restore the metadata packages folder from the metadata backup folder before upgrading the VM to a newer Dynamics AX platform. You should then delete the metadata backup. This will ensure that the platform update will be applied on a clean environment, and the next build process will detect that no metadata backup exists and automatically create a new one, which will include the updated platform. To find out if a complete metadata backup exists, please look for a BackupComplete.txt file in I:DynamicsBackupPackages" (or C:DynamicsBackupPackages on a downloadable VHD). The presence of this file indicates that a metadata backup exists and the file will contain a timestamp of when it was created. To restore the deployment's metadata packages folder from the metadata backup open an elevated PowerShell command prompt and run the below command. This will exercise the same script as used in the first step of the build process.

    if (Test-Path -Path "I:DynamicsBackupPackagesBackupComplete.txt") { C:DynamicsSDKPrepareForBuild.ps1 }

Note: Execute the above command only if a complete metadata backup exists, as it will create a new backup if it does not. This command will stop the Dynamics AX deployment services and IIS before restoring the files from the metadata backup to the deployment's metadata packages folder. You should see output like this: *6:17:52 PM: Preparing build environment...* *6:17:53 PM: Updating Dynamics SDK registry key with specified values...* *6:17:53 PM: Updating Dynamics SDK registry key with values from AOS web config...* *6:17:53 PM: Stopping Dynamics AX deployment...* *6:18:06 PM: **A backup already exists at: I:DynamicsBackupPackages. No new backup will be created**.* *6:18:06 PM: **Restoring metadata packages from backup...*** *6:22:56 PM: **Metadata packages successfully restored from backup**.* *6:22:57 PM: Preparing build environment complete.* *6:22:57 PM: Script completed with exit code: 0* Once the metadata backup has been restored, **delete (or rename) the metadata backup folder (*DynamicsBackupPackages*)** so it will no longer be found by the build process.

### Apply the platform update package

Once you have prepared your build environment for this update, apply the platform update package the same way you apply it on a development environment as describe [above](#apply-the-platform-update-package-on-your-development-environment).

## Features that aren't supported
**Dynamics AX platform August 2016 release (Update 2)** includes the following features:

-   The new Entity Store feature
-   Microsoft Power BI with DirectQuery
-   Microsoft Cortana Analytics for Retail

However, an instance of Dynamics AX that was originally deployed by using the February 2016 release won't have these features if you update by using the process that is described in this topic. To enable these features, you original deployment must be an Update 1 (May 2016) deployment.

## Optional: If your application overlays platform models
Before you apply the platform update package on your development instance, follow these steps if your solution contains models that belong to one of the following packages:

-   Application Platform
-   Application Foundation
-   Directory
-   TestEssentials

1.  In Visual Studio, check in all pending changes to your Microsoft Visual Studio Team Services (VSTS) version control project.
2.  Exit Visual Studio.
3.  Apply the platform update deployable package as described earlier in this topic.
4.  Start Visual Studio.
5.  Resolve potential conflicts in your models that overlay platform models. **Tip:** You can use the Create project from conflicts add-in to create a project from all conflicts in a model.[![Create project from conflicts ](./media/projectforconflicts.jpg)](./media/projectforconflicts.jpg)
6.  Rebuild and validate your application.
7.  Create a custom deployable package from your customized platform package. This package should be applied to your sandbox/pre-production environment for validation.


See also
--------

[Process for upgrading to the latest Dynamics AX update](upgrade-latest-update.md)

