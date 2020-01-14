---
# required metadata

title: Mass deployment of Retail self-service components
description: This topic explains how you can use self-service to do silent servicing updates and initial deployments. It also explains some aspects of special deployment. 
author: jashanno
manager: AnnBe
ms.date: 01/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jashanno
ms.search.validFrom: 2017-09-31
ms.dyn365.ops.version: Application update 3
---

# Mass deployment of Retail self-service components

[!include [banner](../includes/banner.md)]

This topic explains how you can use self-service to do silent servicing updates and initial deployments. It also explains some aspects of special deployment. This topic will be updated as the feature is developed and more functionality becomes available. Currently, only the capability for silent servicing updates is available.

## Delimiters for mass deployment

The following table shows the delimiters that can currently be used in execution commands for mass deployment. 


| Delimiter                 | Description |
|---------------------------|-------------|
| -S or -Silent             | Silently run the installer. No graphical user interface (GUI) is used. The **-Q** and **-Quiet** delimiters have the same effect and can also be used. |
| -C or -Config             | Specify the location and file name of the configuration file to use as part of this installation. |
| -FilePath                 | Specify a custom installation location.<p>We don't recommend that you use this delimiter for a standard installation.</p> |
| -LogFile                  | Specify a custom file location for the installation logs.<p>We don't recommend that you use this delimiter for a standard installation.</p> |
| -SkipPrerequisiteCheck    | Skip the check for prerequisites and prerequisite installation.<p>You should use this delimiter only for development and testing. We don't recommend that you use it for a standard installation.</p> |
| -SkipSystemInfoCollection | Skip the process of collecting system information at the beginning of the installation.<p>You should use this delimiter only for development and testing. We don't recommend that you use it for a standard installation.</p> |
| -SkipMerchantInfo         | Skip the installation of merchant account information at the end of the self-service installer for Hardware station.<p>You should use this delimiter only for development and testing. We don't recommend that you use it for a standard installation.</p> |
| -SkipAppxInstallation     | Beginning in the October 2018 release of Dynamics 365, this delimiter will skip the installation of the APPX Retail Modern POS application. This delimiter is required to perform the application installation through the SYSTEM account or a service account (Any account that does not have a user profile). |

## Silent servicing

### Before you begin

Note that silent servicing maintains all components that are currently installed. If any configuration is still required, complete it before you begin to follow the instructions in this topic.

### Examples of commands for silent servicing

This section shows examples of commands that are used for self-service mass deployment. These commands work for all the standard self-service installers, such as the installers for Retail Modern POS (both the installer that has offline support and the installer that doesn't have offline support), Hardware station, and Retail Store Scale Unit.

#### Silently update the current installation of Retail Modern POS

The following command silently updates the current installation of Retail Modern POS. This command has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe** and the command for silent installation, **-S**. This command uses the configuration file that is located in the same file location as the installer, if a configuration file exists there.

```
ModernPOSSetup_V72.exe -S
```

> [!NOTE]
> A configuration file is still required for Retail Store Scale Unit. However, the installer keeps all the values that are currently installed, whenever it can.

#### Silently update the current installation of Retail Store Scale Unit

The following command silently updates the current installation of Retail Store Scale Unit by using a specific configuration file. (This configuration file might not be in the same location as the executable file for the installer.) This command skips the prerequisite check and moves on to the installation steps. We recommend that you use this command only for testing and development purposes.

```
StoreSystemSetup_V72.exe -S -C "C:\Temp\StoreSystemSetup_V72_Houston.xml" -SkipPrerequisiteCheck
```

## Mass deployment of Retail Modern POS

### Before you begin

To use this functionality, you must be using version 7.3 or later. It's assumed that the configuration of all stores, registers, and devices, and other configurations in the headquarters have already been completed. If any configuration is still required, complete it before you follow the instructions in this topic.

### Examples of commands for silent mass deployment

This section shows examples of commands that are used for self-service mass deployment of Retail Modern POS, even Retail Modern POS with offline and the installer without offline support. Examples of Windows PowerShell scripts are also included to help users do the installations.

#### Silently install Retail Modern POS

The following command silently installs (or updates) Retail Modern POS. It has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe** and the command for silent installation, **-S**.

This command uses the configuration file that is in the same location as the executable file for the installer, if a configuration file exists there. It should not be used if multiple configuration files are available.

```
ModernPOSSetup_V73.exe -S
```

> [!NOTE]
> A configuration file isn't required for Retail Modern POS. However, the Retail Modern POS application that is installed can't be activated in the appropriate manner unless the associated configuration file can be read from.

#### Silently install Retail Modern POS by using a specific configuration file

The following command silently installs the current installation of Retail Modern POS by using a specific configuration file. This configuration file might not be in the same location as the executable file for the installer, or multiple configuration files might be available.

```
ModernPOSSetup_V72.exe -S -C "C:\Temp\ModernPOSSetup_V73_Houston-3.xml"
```

#### Silently install Retail hardware station

> [!NOTE]
> The **-SkipMerchantInfo** delimiter is required to install Retail hardware station. The Merchant Account Information Utility that is opened at the end of a GUI-based installation of Hardware station no longer has to be used. Because of feature functionality, when Retail Modern POS is paired to Hardware station, it also pushes the latest merchant account information to the component.

The following command silently installs (or updates) Retail hardware station. It has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe** and the command for silent installation, **-S**. It also uses the **-SkipMerchantInfo** delimiter to skip the download of merchant account information through the utility. This command uses the configuration file that is in the same location as the executable file for the installer.

```
HardwareStationSetup_V10.exe -S -SkipMerchantInfo
```

> [!NOTE]
> A configuration file is required to silently deploy Retail hardware station.

#### Silently install Retail hardware station by using a specific configuration file

The following command silently installs the current installation of Retail hardware station by using a specific configuration file. This configuration file might not be in the same location as the executable file for the installer, or multiple configuration files might be available.

```
HardwareStationSetup_V10.exe -S -SkipMerchantInfo -C "C:\Temp\HardwareStationSetup_V10__20-19-35.xml"
```
