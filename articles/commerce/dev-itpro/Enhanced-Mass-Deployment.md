---
# required metadata

title: Mass deployment of new, sealed Commerce self-service components
description: This topic explains how you can use the new framework of self-service component installers to perform silent installation and servicing deployments. It also explains aspects of special deployments.
author: jashanno
manager: AnnBe
ms.date: 06/02/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jashanno
ms.search.validFrom: 2021-02-20
ms.dyn365.ops.version: Application update 3
---

# Mass deployment of new, sealed Commerce self-service components

[!include [banner](../includes/banner.md)]

This topic is for the new, sealed framework component installers released each month, beginning with the 10.0.18 release. This article explains how to use these installers to perform silent installation and servicing updates via command line arguments. Using these arguments, mass deployment could be performed through a variety of possible ways.

## Delimiters for mass deployment

The following table shows the delimiters that can be used in the command line execution.


| Delimiter                 | Description |
|---------------------------|-------------|
| -AadTokenIssuerPrefix | AAD Token Issuer prefix. |
| -AsyncClientAadClientId | AAD client id to be used by Async Client while communicating with HQ. |
| -AsyncClientAppInsightsInstrumentationKey | Async Client AppInsights instrumentation key. |
| -AsyncClientCertFullPath | The fully formatted URN path with the thumbprint as the search metric of the Async Client Identity certificate's location to be used to authenticate with AAD for communications with Headquarters. For example: store://My/LocalMachine?FindByThumbprint=<MyThumbprint> is a properly formatted URN where the value '< MyThumbprint >' would be replaced with the certificate thumbprint to be used. Do not use this parameter along with the AsyncClientCertThumbprint parameter. |
| -AsyncClientCertThumbprint | The thumbprint of the Async Client Identity certificate to be used to authenticate with AAD for communications with Headquarters. This thumbprint will be used to search the LocalMachine/My store location and name to find the correct certificate to use. Do not use this parameter along with the AsyncClientCertFullPath parameter. |
| -ClientAppInsightsInstrumentationKey | Client AppInsights instrumentation key. |
| -CloudPosAppInsightsInstrumentationKey | Cloud POS AppInsights instrumentation key. |
| -CposAadClientId | AAD client id to be used by Cloud POS while activating a device. Not required for LBD deployments. |
| -Device | s |
| -EnvironmentId | Environment ID. |
| -HardwareStationAppInsightsInstrumentationKey | Hardware Station AppInsights instrumentation key. |
| -InstallOffline | s |
| -Port | The port to be associated and used by the Retail Server virtual directory. If no port is set, the default port of 443 will be used. |
| -Register | s |
| -RetailServerAadClientId | AAD client id to be used by Retail Server while communicating with HQ. |
| -RetailServerAadResourceId | Retail Server's AAD App Resource ID to be used while activating a device. Not required for LBD deployments. |
| -RetailServerCertFullPath | The fully formatted URN path with the thumbprint as the search metric of the Retail Server Identity certificate to be used to authenticate with AAD for communications with Headquarters. For example: store://My/LocalMachine?FindByThumbprint=<MyThumbprint> is a properly formatted URN where the value '< MyThumbprint >' would be replaced with the certificate thumbprint to be used. Do not use this parameter along with the RetailServerCertThumbprint parameter. |
| -RetailServerCertThumbprint | The thumbprint of the Retail Server Identity certificate to be used to authenticate with AAD for communications with Headquarters. This thumbprint will be used to search the LocalMachine/My store location and name to find the correct certificate to use. Do not use this parameter along with the RetailServerCertFullPath parameter. |
| -RetailServerURL | s |
| -SkipAadCredentialsCheck| Switch indicating whether to skip AAD credentials prerequisite checks. Default is false. |
| -SkipCertCheck | Switch indicating whether to skip then certificate prerequisite checks. Default is false. |
| -SkipIisCheck | Switch indicating whether to skip IIS prerequisite checks. Default is false. |
| -SkipNetFrameworkCheck | Switch indicating whether to skip .Net framework prerequisite checks. Default is false. |
| -SkipScaleUnitHealthcheck | Switch indicating whether to skip runnig healthcheck on installed components. Default is false. |
| -SkipSChannelCheck | Switch indicating whether to skip the secure channel prerequisite checks. Default is false. |
| -SkipSqlFullTextCheck | Switch indicating whether to skip validating SQL Server prerequisite requiring Full Text Search. Default is false. |
| -SkipSqlServerCheck | Switch indicating whether to skip SQL Server prerequisite checks. Default is false. |
| -SqlServerName | SQL Server Name, if not specified the installer will try to locate default instance. |
| -SslcertFullPath | The fully formatted URN path with the thumbprint as the search metric of certificate's location to be used to encrypt HTTP traffic to the scale unit. For example: **store:\/\/My\/LocalMachine\?FindByThumbprint\=\<MyThumbprint\>** is a properly formatted URN where the value **\< MyThumbprint \>** would be replaced with the certificate thumbprint to be used. Do not use this parameter along with the SslCertThumbprint parameter. |
| -SslCertThumbprint | The thumbprint of the certificate to be used to encrypt HTTP traffic to the scale unit. This thumbprint will be used to search the LocalMachine/My store location and name to find the correct certificate to use. Do not use this parameter along with the SslCertFullPath parameter. |
| -StoreSystemAosUrl | Headquarters (AOS) URL. |
| -StoreSystemChannelDatabaseId | Channel database ID (Name). |
| -TenantId | AAD Tenant ID. |
| -TransactionServiceAzureAuthority | Transaction Service AAD Authority. |
| -TransactionServiceAzureResource | Transaction Service AAD Resource. |
| -TrustSqlServerCertificate | Switch indicating whether to trust Server Certificate while establishing a connection to SQL Server. To avoid security risks production deployments should never supply a value of 'True' here. Default is false. |
| -WindowsPhoneAppInsightsInstrumentationKey | Hardware Station AppInsights instrumentation key. |

## General overview

The new framework for Self-service installers have a variety of features and improvements. The new framework currently only generates installers for Modern POS, hardware station, and Commerce Scale Unit (CSU, Self-hosted).
<ul>
  <li>**Sealed** - The new installer framework completely separates Microsoft distributed base component installers from the extensibility-based customizations. The customizations shall be installed afterwards, but will be then untethered in regards to updating (Allowing updating only the Microsoft base component or only the customizations or both.</li>
  <li>**GUI-less** - There is no longer a user interface, meaning it is completely a command-line driven executable for each component installer. This is one of several key changes or features used to focus the new installer framework for use with mass deployment.</li>
  <li>**Deeper logging** - Enhanced installer logs allow for better validation of installation completion or failure, the steps performed, and any warnings or errors that were generated.</li>
  <li>**Clean-up** - The component installers, under the new framework, work harder to maintain installation directory cleanliness by clearing the full contents of the component folder before installing the newer components. This makes certain there are no leftover files that could cause issues with installation completing successfully.</li>
</ul>

There are three components that have not migrated to the new framework. These excluded components are the Virtual Peripheral Simulator, Async Server Connector Service (Used for Dynamics AX 2012 R3 support), and the Real-time Service Replacement (Used for Dynamics AX 2012 R3 support).

> [!NOTE]
> Installers are stored locally and retained.  It is important, over time, to manage or delete the retained installers to not waste disk space. It is recommended to keep the current installer for the base component(s) and any extension installers for the latest version(s) for purposes of recovery from extreme situations.

## Migration

Migrating from the legacy Self-service framework component installers to the new framework component installers requires uninstallation of the legacy components.
<ul>
  <li>**Modern POS** - The new installer framework caused the application to be given a new application signature ID. This requires a full uninstallation of legacy components prior to installation of the new framework Modern POS. Due to the requirement for full uninstallation, device activation will be required again (Still a one time occurrence going forward, presuming uninstallation does not occur again).</li>
  <li>**Hardware station** - As an IIS website, the new installer framework requires a reworking of how the base folder structure exists.  Due to this, a full uninstallation of legacy components is required prior to installation of the new framework hardware station component.</li>
  <li>**Commerce Scale Unit (CSU, Self-hosted)** - As a series of IIS websites, the new installer framework requires a reworking of how the base folder structure exists.  Due to this, a full uninstallation of legacy components is required prior to installation of the new framework CSU (Self-hosted) component.</li>
</ul>








## Mass deployment of Modern POS

### Before you begin

It is critical to remove the legacy Self-service Modern POS component. See the migration steps above for additional information.

### Examples of silent deployment

This section shows examples of commands that are used for legacy self-service mass deployment of Modern POS, even Modern POS with offline and the installer without offline support. Examples of Windows PowerShell scripts are also included to help users do the installations.

#### Silently install Modern POS

The following command silently installs (or updates) Modern POS. It has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe** and the command for silent installation, **-S**.

This command uses the configuration file that is in the same location as the executable file for the installer, if a configuration file exists there. It should not be used if multiple configuration files are available.

```Console
ModernPOSSetup_V73.exe -S
```

> [!NOTE]
> A configuration file isn't required for Modern POS. However, the Modern POS application that is installed can't be activated in the appropriate manner unless the associated configuration file can be read from.

#### Silently install Modern POS by using a specific configuration file

The following command silently installs the current installation of Modern POS by using a specific configuration file. This configuration file might not be in the same location as the executable file for the installer, or multiple configuration files might be available.

```Console
ModernPOSSetup_V72.exe -S -C "C:\Temp\ModernPOSSetup_V73_Houston-3.xml"
```

#### Silently install Retail hardware station

> [!NOTE]
> The **-SkipMerchantInfo** delimiter is required to install Retail hardware station. The Merchant Account Information Utility that is opened at the end of a GUI-based installation of Hardware station no longer has to be used. Because of feature functionality, when Modern POS is paired to Hardware station, it also pushes the latest merchant account information to the component.

The following command silently installs (or updates) Retail hardware station. It has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe** and the command for silent installation, **-S**. It also uses the **-SkipMerchantInfo** delimiter to skip the download of merchant account information through the utility. This command uses the configuration file that is in the same location as the executable file for the installer.

```Console
HardwareStationSetup_V10.exe -S -SkipMerchantInfo
```

> [!NOTE]
> A configuration file is required to silently deploy Retail hardware station.

#### Silently install Commerce Scale Unit (Self-hosted)


## Silent servicing

### Before you begin

Note that silent servicing maintains all components that are currently installed. If any configuration is still required, complete it before you begin to follow the instructions in this topic.

### Examples of commands for silent servicing

This section shows examples of commands that are used for legacy self-service mass deployment. These commands work for all the standard installers, such as the installers for Modern POS (both the installer that has offline support and the installer that doesn't have offline support), Hardware station, and Commerce Scale Unit (self-hosted).

#### Silently update the current installation of Modern POS

The following command silently updates the current installation of Modern POS. This command has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe** and the command for silent installation, **-S**. This command uses the configuration file that is located in the same file location as the installer, if a configuration file exists there.

```Console
ModernPOSSetup_V72.exe -S
```

> [!NOTE]
> A configuration file is still required for Retail Store Scale Unit. However, the installer keeps all the values that are currently installed, whenever it can.

#### Silently update the current installation of Commerce Scale Unit (self-hosted)

The following command silently updates the current installation of Commerce Scale Unit (self-hosted) by using a specific configuration file. (This configuration file might not be in the same location as the executable file for the installer.) This command skips the prerequisite check and moves on to the installation steps. We recommend that you use this command only for testing and development purposes.

```Console
StoreSystemSetup_V72.exe -S -C "C:\Temp\StoreSystemSetup_V72_Houston.xml" -SkipPrerequisiteCheck
```


#### Mass deployment examples using InTune


#### Mass deployment examples using SCCM (System Center Configuration Manager)




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
