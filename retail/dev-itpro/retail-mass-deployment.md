---
# required metadata

title: Mass deployment of Retail self-service components
description: This topic explains how you can use self-service silently to perform servicing updates, initial deployments, and some concepts of special deployment.  This topic will be updated repeatedly as the feature is developed further and more functionality is available.  At this time, only the ability to silenty update is available for use.
author: jashanno
manager: AnnBe
ms.date: 08/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
# ms.reviewer: sericks
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jashanno
ms.search.validFrom: 2017-09-31]
ms.dyn365.ops.version: Application update 3
---

# Mass deployment of Retail self-service components

[!include[banner](../includes/banner.md)]

This topic explains how you can use self-service silently to perform servicing updates, initial deployments, and some concepts of special deployment.  This topic will be updated repeatedly as the feature is developed further and more functionality is available.  At this time, only the ability to silenty update is available for use.

## Silent Servicing
### Before you begin
> [!IMPORTANT]
> This functionality only works in Microsoft Dynamics 365 for Retail, version 7.2, App Update 3 and beyond.  Note that silent servicing maintains all currently installed 

### Delimiters for Mass Deployment
This is the list of delimiters that can currently be used in Mass Deployment execution commands.

#### App Update 3 and beyond
- /S or /Silent - Silently run the installer (No graphical user interface).
- /C or /Config - Specify the location and filename of the configuration file to use as part of this installation.
- /FilePath - Specify a custom installation location (Not recommended for standard installation).
- /LogFile - Specify a custom logfile location for installation logs (Not recommended for standard installation).
- /SkipPrerequisiteCheck - Skips the check for prerequisites and prerequisite installation.  Should only be used for development and testing (Not recommended for standard installation).
- /SkipSystemInfoCollection - Skips the System Information collection process at the beginning of the installation.  Should only be used for development and testing (Not recommended for standard installation).
- /SkipMerchantInfo - Skips the Merchant Account Information installation at the end of the hardware station Self-service installer.  Should only be used for development and testing (Not recommended for standard installation).

### Example commands for silent servicing
This sub-section will showcase examples of Self-service Mass Deployment commands.  The commands listed function for all the standard Self-service installers, which include Modern POS (With and without offline), hardware station, and Retail Store Scale Unit.

```
ModernPOSSetup_V72.exe /S
```
This command will silently update the current installation of Retail Modern POS.  This is the standard command structure used for silent servicing of currently installed components.  The structure will follow the basic values of "InstallerName.exe" and the command for silent installation "/S".  This command will utilize the configuration file that is located in the same file location as the installer, if it exists.
> [!NOTE]
> A configuration file is still required for Retail Store Scale Unit.  However, the installer will still keep all possible currently installed values.

```
StoreSystemSetup_V72.exe /S /C "C:\Temp\StoreSystemSetup_V72_Houston.xml" /SkipPrerequisiteCheck
```
This command will silently update the current installation of Retail Store Scale Unit using a specific configuration file (Which may or may not be in the same location as the installer executable file) and will skip the prerequisite check and installation steps (Only recommended for testing and development purposes).
