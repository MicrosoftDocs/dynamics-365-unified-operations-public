---
# required metadata

title: Mass deployment of Retail self-service components
description: This topic explains how you can use self-service to do silent servicing updates, initial deployments, and some concepts of special deployment. This topic will be updated as the feature is developed and more functionality becomes available. Currently, only the capability for silent servicing updates is available.
author: jashanno
manager: AnnBe
ms.date: 10/10/2017
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

This topic explains how you can use self-service to do silent servicing updates, initial deployments, and some aspects of special deployment. This topic will be updated as the feature is developed and more functionality becomes available. Currently, only the capability for silent servicing updates is available.

## Silent servicing
### Before you begin
This functionality works in Microsoft Dynamics 365 for Retail. The July 2017 version with Application update 3 or later is required. Note that silent servicing maintains all components that are currently installed.

### Delimiters for mass deployment
The following table shows the delimiters that can currently be used in execution commands for mass deployment. These delimiters apply to App update 3 and later.

| Delimiter                 | Description |
|---------------------------|-------------|
| -S or -Silent             | Silently run the installer. (No graphical user interface is used.) |
| -C or -Config             | Specify the location and file name of the configuration file to use as part of this installation. |
| -FilePath                 | Specify a custom installation location. (We don't recommend that you use this delimiter for a standard installation.) |
| -LogFile                  | Specify a custom log file location for the installation logs. (We don't recommend that you use this delimiter for a standard installation.) |
| -SkipPrerequisiteCheck    | Skip the check for prerequisites and prerequisite installation.  You should use this delimiter only for development and testing. (We don't recommend that you use this delimiter for a standard installation.) |
| -SkipSystemInfoCollection | Skip the process of collecting system information at the beginning of the installation. You should use this delimiter only for development and testing. (We don't recommend that you use this delimiter for a standard installation.) |
| -SkipMerchantInfo         | Skip the installation of merchant account information at the end of the self-service installer for Hardware station. You should use this delimiter only for development and testing. (We don't recommend that you use this delimiter for a standard installation.) |

### Examples of commands for silent servicing
This section shows examples of commands for self-service mass deployment. The commands that are shown work for all the standard self-service installers. These installers include Retail Modern POS (both the installer with offline support and the installer without offline support), hardware station, and Retail Store Scale Unit.

#### Silently update the current installation of Modern POS
The following command silently updates the current installation of Modern POS. It has the standard command structure that is used for silent servicing of currently installed components. The structure uses the basic values of **InstallerName.exe** and the command for silent installation, **-S**. This command uses the configuration file that is located in the same file location as the installer, if a configuration file exists there.

```
ModernPOSSetup_V72.exe -S
```

> [!NOTE]
> A configuration file is still required for Retail Store Scale Unit. However, the installer still keeps all possible values that are currently installed.

#### Silently update the current installation of Retail Store Scale Unit
The following command silently updates the current installation of Retail Store Scale Unit by using a specific configuration file. (This configuration file might not be in the same location as the executable file for the installer.) This command skips the prerequisite check and installation steps. We recommend that you use this command only for testing and development purposes.

```
StoreSystemSetup_V72.exe -S -C "C:\Temp\StoreSystemSetup_V72_Houston.xml" -SkipPrerequisiteCheck
```
