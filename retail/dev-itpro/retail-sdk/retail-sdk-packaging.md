---
# required metadata

title: Retail SDK packaging
description: This topic explains how to create a Retail deployable package for Microsoft Dynamics 365 for Operations.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 0fa3c8e7-49e4-417d-afe9-fa2055f6546f
ms.search.region: Global
# ms.search.industry: 
ms.author: sijoshi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Retail SDK packaging

This topic explains how to create a retail deployable package for Microsoft Dynamics 365 for Operations manually.

# Prerequisites

For detailed information on Retail SDK, see [Retail SDK overview](retail-sdk-overview.md). The Retail deployable package is a bundle package which includes all the below retail componetst:

-   Commerce runtime (CRT)
-   Retail Server
-   Modern POS
-   Cloud POS
-   Hardware station
-   Channel database scripts

## Retail Deployable Package
Retail deployable package is an asset that can be consumed by the LCS deployment service or it can be deployed manually to service or install a customization. The Retail SDK generates the same package that is developed for Microsoft hotfixes or updates, so that there is one way to install or deploy updates and customizations to the existing solution.

### Steps to create a Retail deployable package

There are two ways to generate the Retail deployable package. One is using the Retail build automation or manually using the build tools in Retail SDK. In this topic we will focus on the manual way.
1. Customize or add functionality to the Retail stack.
2. Use the build tools to give an identity to the customized installation package, code-sign it, and specify the customized CRT, Retail Server, customized Hardware station assemblies, and customized database scripts.
3. After all the settings have been specified on Customization.settings file under Retail SDK\BuildTools folder, run **msbuild /t:rebuild** on the root of the Retail SDK folde using the VS dev command prompt tool to generate the retail deployable packages. Before building the package place all the customized assemblies to Retail SDK\Refernces folder and also place the modified config files like commerceruntime.config, CommerceRuntime.MPOSOffline.config, dllhost.exe.config to the Retail SDk\Assets folder.

## Retail SDK build tools – Customization settings
BuildTools\Customization.setting files is where most of the configuration values for the Retail SDK are set for build and packaging. These values control how binaries, components, and packages are named, versioned, and code-signed. After you define this metadata, The Retail SDK build system uses it to give an identity to the assets, and to package the customization assets for all the Retail components.

Below are the list fo configurations available in Customization.Settings file:
-   **AssemblyNamePrefix** – Specify the prefix name for the assembly. When you build the Retail SDK, all the assemblies are prefixed with this name.
-   **CustomAssemblyVersion** – Specify the custom assembly version for all assemblies that are built by using the Retail SDK.
-   **CustomVersion** – Specify the custom file version for all assemblies that are built by using the Retail SDK.
-   **CustomName** – Specify the custom name for the assembly.
-   **CustomDescription** – Specify the description for the assembly.
-   **CustomDescription** – Specify the publisher for the assembly.
-   **CustomDescription** – Specify the copyright for the assembly.
-   **SignAssembly** – Specify **True** if you want to sign the assembly during the build.
-   **DelaySign** – Specify **True** if you want to delay signing of the assets during the build.
-   **AssemblyOriginatorKeyFile** – Specify the strong name key to use to sign the assembly.
-   **ModernPOSPackageCertificateKeyFile** – Specify the PFX file to use to sign Modern POS and Hardware station.
-   **RetailServerLibraryPathForProxyGeneration** – Specify the customized Retail Server assembly to use for proxy generation (both TypeScript and C\# proxy).
-   In the **ItemGroup** section:
    -   **ISV\_CommerceRuntime\_CustomizableFile** – Specify all the customized CRT assembly. You can have multiple entries, one for each customized CRT assembly.
    -   **ISV\_RetailServer\_CustomizableFile** – Specify all the customized Retail Server assembly. You can have multiple entries, one for each customized Retail Server assembly.
    -   **ISV\_HardwareStation\_CustomizableFile** – Specify all the customized Hardware station assembly. You can have multiple entries, one for each customized Hardware station assembly.
    -   **ISV\_CustomDatabaseFile\_Upgrade\_Custom** – Specify all the customized database scripts.


#### Retail Deployable package

### CRT extension assemblies
By default, there is no separate package for invidual retail componetst, because CRT isn't deployed individually, instead, CRT assets are packaged together with other application components, such as Modern POS, Retail Server, and Microsoft Dynamics 365 for Operations HQ. In order for the Retail SDK build tools to package CRT in all the components where it's used, you must make the following configuration entries:

1.  **CRT extension assemblies** – These will be the new assemblies where you've written CRT extensions. Specify an entry for CRT extension assemblies in Retail SDK\\BuildTools\\Customization.settings. 

    [![crt-customization settings](./media/crt-customization-settings.png)](./media/crt-customization-settings.png)
    
2.  **CRT commerceruntime.config file** – If you have a new CRT assembly, you must add it to the CRT configuration file so that the runtime can load it. Specify an entry for CRT extension assemblies in Retail SDK\\References\\commerceruntime.config. 

    [![crt-config](./media/crt-config.png)](./media/crt-config.png)

#### Retail Server extension assemblies
1.  **Retail Server extension assemblies **– These will be the new assemblies where you've written Retail Server customizations. Specify an entry for CRT extension assemblies in Retail SDK\\BuildTools\\Customization.settings. 

    [![retail server customization setting](./media/retail-server-customization-setting.png)](./media/retail-server-customization-setting.png)
    
2.  **Retail Server web.config file** – You must add an entry for Retail Server extension assemblies to the Retail Server web.config file, so that they are loaded and used. Specify an entry for Retail Server Extension assemblies in Retail SDK\\Packages\\RetailServer\\Code\\web.config. 

    [![retail server web config](./media/retail-server-web-config.png)](./media/retail-server-web-config.png)

##### Database scripts
As a part of a customization, you might have to upgrade a channel database in addition to a Modern POS offline database. Currently, you use upgrade SQL scripts to upgrade the channel and Modern POS offline databases. You can write an upgrade SQL script and put it at Retail SDK\Database\Upgrade\Custom, so that packaging tools can pick it up and include it in the deployable package for the correct components (Retail Server and Modern POS Offline). 

[![custom db script](./media/custom-db-script.png)](./media/custom-db-script.png) 

You must also update Retail SDK\\BuildTools\\Customization.settings to instruct the build tools which files to package for the database. 

[![database upgrade customization setting](./media/database-upgrade-customization-setting-1024x311.png)](./media/database-upgrade-customization-setting.png)
Database scripts are packaged together with the Retail Server and Modern POS Offline packages, and are run when Retail Server and Modern POS are installed. If there are multiple custom database scripts, they are run in alphabetical order. Therefore, if you want to run the scripts in a specific order, you must name them accordingly. The CRT.RETAILUPGRADEHISTORY table keeps track of which scripts are already applied to the database. Therefore, the next database upgrade will run only those upgrade scripts that don't have an entry in the CRT.RETAILUPGRADEHISTORY table.

## Generate a retail deployable package

The Retail SDK fully supports msbuild. To build the Retail SDK and , open a **Visual studio 2015 developer Command Prompt tool** window as an administrator, and run **msbuild** (or, for a non-debug version, run **msbuild /p:Configuration=Release**). 

### Packages

After the build is completed, retail deployable packages(RetailDeployablePackage.zip) is generated in the Retail SDK\Packages\RetailDeployablePackage folder. Note: There will not be any seperate packages for retail, all will be combined and created as one bundle package called RetailDeployablePackage
      
 ## Deploy the Retail Deployable packages:
 
To deploy the packages either manually or using the LCS automated flow, please follow the below link:
[Apply a deployable package](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/deployment/apply-deployable-package-system)

[Install a deployable package](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/deployment/install-deployable-package)
