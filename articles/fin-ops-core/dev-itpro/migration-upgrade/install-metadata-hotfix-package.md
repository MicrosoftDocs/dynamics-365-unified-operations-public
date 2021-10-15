---
# required metadata

title: Install metadata hotfixes in development environments
description: This topic will guide you through installing an Application Metadata hotfix on your development environment.
author: RobinARH
ms.date: 09/18/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 79822
ms.assetid: 9b132253-1748-4b71-b128-c4b9d3a311ae
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Install metadata hotfixes in development environments

[!include [banner](../includes/banner.md)]

This topic will guide you through installing an Application Metadata hotfix on your development environment.

A metadata hotfix package contains changes (metadata or X++ source code) to model elements (XML files) in your development environment. A hotfix can also contain new model elements. A metadata hotfix package is in the form of an SCDP file. This article describes the process for installing a metadata hotfix package and explains how to share the package with other developers who are working on the same project.

## Overall flow
The following diagram shows the overall flow. 

[![Process for installing a metadata hotfix package.](./media/configureinstallhotfix-1.png)](./media/configureinstallhotfix-1.png)

## Download the hotfix from LCS
For instructions about how to download a hotfix, see [Download updates from Lifecycle Services (LCS)](download-hotfix-lcs.md). After you download the zip file, extract the SCDP metadata hotfix package from it, and put it in a local folder.

## Install the hotfix
### Before you begin

-   This topic assumes that your packages folder is located at c:\\AOSService\\PackagesLocalDirectory\\Bin. On some virtual machines (VMs), it might be located at c:\\Packages, i:\\AOSService\\PackagesLocalDirectory\\Bin, or k:\\AOSService\\PackagesLocalDirectory\\Bin.
-   If you're not using Microsoft Azure DevOps or another source control system, create a backup of your packages folder (which is also known as the metadata store). We don't recommend that you do development unless you use Azure DevOps.
-   If you have Azure DevOps or Microsoft Team Foundation Server (TFS) version control, make sure that there are no files in the **Pending Changes** list of your current workspace. If you have pending changes, we recommend that you submit them or shelve them before you install the metadata hotfix.

### Install the metadata hotfix package

To invoke the installation of the metadata hotfix, you can call the SCDPBundleInstall.exe utility from a command prompt. SCDPBundleInstall.exe is located in your packages bin folder.

#### Without version control (not recommended)

If you're not using Azure DevOps or TFS for source control, use the following command.

```Console
SCDPBundleInstall.exe -install -packagepath=<scdp file containing the hotfix> -metadatastorepath=<metadata packages root folder>
```

#### With version control (recommended)

If you're using Azure DevOps or TFS for source control, follow the steps below: **Prepare** the installation of the hotfix package using the command below. This step is not available if you are using a platform that is older than Platform update 2 (August 2016))

```Console
SCDPBundleInstall.exe -prepare -packagepath=<scdp file containing the hotfixes> -metadatastorepath=<metadata packages root folder> -tfsworkspacepath=<path of local workspace folder> -tfsprojecturi=<URI of the Azure DevOps or TFS project collection>
```

This will create a changeset of all the existing files on your environment that will be modified by the hotfix package, the prepare command will not install the hotfixes. Here is an example.

```Console
SCDPBundleInstall.exe -prepare -packagepath=c:\temp\hotfixbundle1234.axscdppkg -metadatastorepath= c:\AOSService\PackagesLocalDirectory -tfsworkspacepath= c:\AOSService\PackagesLocalDirectory -tfsprojecturi=https://myaccount.visualstudio.com/defaultcollection
```

**Check-in** your pending changes to create a backup of these files in your version control system. This will enable rolling back the hotfixes if needed. **Install** the hotfix package using the command below.

```Console
SCDPBundleInstall.exe -install -packagepath=<scdp file containing the hotfixes> -metadatastorepath=<metadata packages root folder> -tfsworkspacepath=<path of local workspace folder> -tfsprojecturi=<URI of the Azure DevOps or TFS project collection>
```

If you are using a platform that is older than Platform update 2 (August 2016), you do not need to specify the **-install** option. Here is an example.

```Console
SCDPBundleInstall.exe -install -packagepath=c:\temp\hotfixbundle1234.axscdppkg -metadatastorepath= c:\AOSService\PackagesLocalDirectory -tfsworkspacepath= c:\AOSService\PackagesLocalDirectory -tfsprojecturi=https://myaccount.visualstudio.com/defaultcollection
```

Azure DevOps/TFS parameters let you add the files that are modified by the package to your list of pending changes in Team Explorer.

### Required parameters

```Console
/packagepath=[Path of the local scdp file containing the hotfixes downloaded from Lifecycle Service (LCS)]

/metadatastorepath=[Path of the local metadata store folder, such as c:\AOSService\PackagesLocalDirectory]
```

### TFS parameters

If you're using Azure DevOps or TFS for source control, you should specify the following two parameters.

```Console
/tfsprojecturi=[URI of the TFS Project to connect to]

/tfsworkspacepath=[Path of the local workspace, usually equal to the metadatastorepath]
```

After the install command is invoked, the package installation process begins. As part of the installation process, some XML files in your metadata store folder will be updated to reflect the changes that were made in the fix itself. If you’re using Azure DevOps or TFS, these files will be added to the list of included changes in the **Pending Changes** window in Team Explorer. 

[![List of included changes in the Pending Changes window.](./media/configureinstallhotfix-2.png)](./media/configureinstallhotfix-2.png)

## Resolve conflicts that are generated by the installation of the hotfix
Sometimes, a metadata hotfix package contains changes to objects that have been customized in higher-layer models. In this case, the installation process automatically generates conflicts that must be resolved after the hotfix has been installed. The development tools let you create a project that groups all items that have conflicts. For example, if you have a VAR layer model in the Application Suite package that customizes the VendTable form, and you install a hotfix that modifies the VendTable form in the Sys layer model, conflicts might occur in your VAR layer model.

1.  Click **Dynamics 365** &gt; **Addins** &gt; **Create project from conflicts**.
2.  In the dialog box, select a model to check for conflicts.
3.  Click **Create project**. A project is generated that contains only those elements in the selected model that were found to have conflicts after the hotfix was applied.
4.  Open the designer for the conflicting element to view conflicts, and resolve them by using the tools that are provided.

## Build and test on a local VM
Build all models that are affected by the hotfix, and test your application.

## Check pending changes in to version control
When you're satisfied with all changes that are related to this update, check in your pending changes to Azure DevOps by using Team Explorer in Microsoft Visual Studio. Enter a comment in the **Comment** field, and then click **Check In**. A history of the changes is preserved in your source code repository. 

> [!NOTE]
> If you use a build environment for build and test automation, the build automation process can build metadata hotfix files are in your Azure DevOps project. A hotfix can be built only if the descriptor file of the model that it belongs to is checked in to version control. For example, if the hotfix installation process modified a file that belongs to the Directory model (this file will appear in your list of pending changes), make sure that the descriptor file of the Directory model (c:\\AOSService\\PackagesLocalDirectory\\Directory\\Descriptor\\Directory.xml) is already checked in to your Azure DevOps project. If it isn't checked in, manually add it to your list of pending changes before you check in by using Source Control Explorer. 

[![Manually adding the descriptor file to the list of pending changes.](./media/configureinstallhotfix-8.png)](./media/configureinstallhotfix-8.png)

## Synchronize other development VMs
After a hotfix has been installed on a development VM as described in this article, you don't have to reinstall, resolve conflicts, and validate on other development VMs that are connected to the same Azure DevOps project. Developers and testers who are connected to the same Azure DevOps project can just synchronize the changes into their local VM and then build.

## Deploy
After you’ve applied a metadata hotfix to your development environment, resolved conflicts, and validated your changes, you must create a deployable package and apply your changes to your test or sandbox environment. If you use a build instance for build and test automation, the build process will automatically create the deployable package for you. For more information, see [Create deployable packages of models](../deployment/create-apply-deployable-package.md).



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]