---
# required metadata

title: Mass deployment of new, sealed Commerce self-service components
description: This topic explains how you can use the new framework of self-service component installers to perform silent installation and servicing deployments. It also explains aspects of special deployments.
author: jashanno
manager: AnnBe
ms.date: 04/20/2021
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
| -Config | The configuration file to be used during installation.  A file name example would be **Contoso.CommerceScaleUnit.xml**. |
| -CposAadClientId | AAD client id to be used by Cloud POS while activating a device. Not required for LBD deployments. |
| -Device | The device ID, seen in the **Devices** page in Headquarters. |
| -EnvironmentId | The environment ID. |
| -HardwareStationAppInsightsInstrumentationKey | Hardware Station AppInsights instrumentation key. |
| -Install | Install the component this installer provides.  This field is not required. |
| -InstallOffline | For Modern POS this parameter specifies to additionally install and configure the offline database. Use the parameter **-SQLServerName** as well or the installer will attempt to find a default instance that meets prerequisites. |
| -Port | The port to be associated and used by the Retail Server virtual directory. If no port is set, the default port of 443 will be used. |
| -Register | The register ID, seen in the **Registers** page in Headquarters. |
| -RetailServerAadClientId | AAD client id to be used by Retail Server while communicating with HQ. |
| -RetailServerAadResourceId | Retail Server's AAD App Resource ID to be used while activating a device. Not required for LBD deployments. |
| -RetailServerCertFullPath | The fully formatted URN path with the thumbprint as the search metric of the Retail Server Identity certificate to be used to authenticate with AAD for communications with Headquarters. For example: **store://My/LocalMachine?FindByThumbprint=<MyThumbprint>** is a properly formatted URN where the value **< MyThumbprint >** would be replaced with the certificate thumbprint to be used. Do not use this parameter along with the **-RetailServerCertThumbprint** parameter. |
| -RetailServerCertThumbprint | The thumbprint of the Retail Server Identity certificate to be used to authenticate with AAD for communications with Headquarters. This thumbprint will be used to search the **LocalMachine/My** store location and name to find the correct certificate to use. Do not use this parameter along with the **-RetailServerCertFullPath** parameter. |
| -RetailServerURL | The Retail Server URL (Also called the CSU, or Commerce Scale Unit, URL) to be used by the installer (For Modern POS, this value will be used during device activation). |
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
| -Verbosity | The level of logging requested during installation.  This value typically should not be used. |
| -WindowsPhoneAppInsightsInstrumentationKey | Hardware Station AppInsights instrumentation key. |

## General overview

The new framework for Self-service installers have a variety of features and improvements. The new framework currently only generates installers for Modern POS, hardware station, and Commerce Scale Unit (CSU, Self-hosted).
<ul>
  <li> **Sealed** - The new installer framework completely separates Microsoft distributed base component installers from the extensibility-based customizations. The customizations shall be installed afterwards, but will be then untethered in regards to updating (Allowing updating only the Microsoft base component or only the customizations or both.</li>
  <li> **GUI-less** - There is no longer a user interface, meaning it is completely a command-line driven executable for each component installer. This is one of several key changes or features used to focus the new installer framework for use with mass deployment.</li>
  <li> **Deeper logging** - Enhanced installer logs allow for better validation of installation completion or failure, the steps performed, and any warnings or errors that were generated.</li>
  <li> **Clean-up** - The component installers, under the new framework, work harder to maintain installation directory cleanliness by clearing the full contents of the component folder before installing the newer components. This makes certain there are no leftover files that could cause issues with installation completing successfully.</li>
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

## Modern POS

### Before you begin

It is critical to remove the legacy Self-service Modern POS component. See the migration steps above for additional information.

### Examples of silent deployment

This section shows examples of commands that are used for installation of Modern POS.

#### Silently install Modern POS

The following command silently installs (or updates) Modern POS. It has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe**.

This basic command runs the executable file installer.

```Console
ModernPOS.exe
```

> [!NOTE]
> A configuration file isn't required for Modern POS. The installer now has parameters (Shown above) for the various values used in device activation.

This command specifies all parameters to be used during device activation once the Modern POS application is installed. In the below example, we use the **Houston-3** register which is a commonly used value in Dynamics 365 Commerce demo data.

```Console
ModernPOS.exe -Register "Houston-3" -Device "Houston-3" -RetailServerURL "https://MyDynamics365CommerceURL.dynamics.com/Commerce"
```

This command specifies specifies the parameters to install and configure the offline database.  The SQL server is additionally specified along with a configuration file to use.

```Console
ModernPOS.exe -InstallOffline -SQLServerName "SQLExpress" -Config "ModernPOS.Houston-3.xml"
```

Mix and match these concepts to achieve the installation results desired.

## Hardware station

### Before you begin

It is critical to remove the legacy Self-service hardware station component. See the migration steps above for additional information.  There is no longer a Merchant Account Information Tool, instead the merchant account information is installed when a POS terminal pairs with the hardware station.

### Examples of silent deployment

This section shows examples of commands that are used for installation of hardware station.

#### Silently install hardware station

The following command silently installs (or updates) hardware station. It has the standard command structure that is used for servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe**.

This basic command runs the executable file installer.

```Console
HardwareStation.exe -Port 443 -StoreSystemAOSURL "https://MyDynamics365CommerceURL.dynamics.com/" -StoreSystemChannelDatabaseID "Houston" -SSLCertThumbprint "mysslcertificatethumbprintoftenhasnumberstoo"
```

> [!NOTE]
> A configuration file isn't required for hardware station. The installer now has parameters (Shown above) for the various values necessary.

This command specifies all parameters necessary to skip the prerequisite checks during a standard installation.

```Console
HardwareStation.exe -Config "HardwareStation.Houston.xml"
```

Mix and match these concepts to achieve the installation results desired.

## Commerce Scale Unit (Self-hosted)

### Before you begin

It is critical to remove the legacy Self-service Commerce Scale Unit (CSU, Self-hosted) component. See the migration steps above for additional information.

### Examples of silent deployment

This section shows examples of commands that are used for installation of CSU (Self-hosted).

#### Silently install CSU (Self-hosted)

The following command silently installs (or updates) CSU (Self-hosted). It has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe**.

This is a basic command that to run the executable file installer.

```Console
CommerceScaleUnit.exe -port 446 -SSLCertThumbprint "mysslcertificatethumbprintoftenhasnumberstoo" -retailservercertfullpath "store:///My/LocalMachine?FindByThumbprint=B48FCB4C8A6D6D54CF02D62D9EBFDF9A5929A469" -AsyncClientAadClientId "d3150d79-1d84-4f22-a9c3-5a6a3a41b1de" -RetailServerAadClientId "d3150d79-1d84-4f22-a9c3-5a6a3a41b1de" -CposAadClientId "bb8751eb-70c2-4410-a462-6dadb5b50e57" -RetailServerAadResourceId "https://retailstorescaleunit.retailserver.com" -TrustSqlServerCertificate -config "Contoso.StoreSystemSetup.xml"
```

> [!NOTE]
> A configuration file is still required for CSU (Self-hosted).

This is a thorough command to run the executable file installer.

```Console
CommerceScaleUnit.exe -port 446 -sslcertfullpath \"store:///My/LocalMachine?FindByThumbprint=7F506987C32A752E20E297C6E6E20943744439B3\" -asyncclientcertfullpath \"store:///My/LocalMachine?FindByThumbprint=B48FCB4C8A6D6D54CF02D62D9EBFDF9A5929A469\" -retailservercertfullpath \"store:///My/LocalMachine?FindByThumbprint=B48FCB4C8A6D6D54CF02D62D9EBFDF9A5929A469\" -AsyncClientAadClientId \"d3150d79-1d84-4f22-a9c3-5a6a3a41b1de\" -RetailServerAadClientId \"d3150d79-1d84-4f22-a9c3-5a6a3a41b1de\" -CposAadClientId \"bb8751eb-70c2-4410-a462-6dadb5b50e57\" -RetailServerAadResourceId \"https://retailstorescaleunit.retailserver.com\" -TrustSqlServerCertificate -Verbosity Trace -config \"Contoso.StoreSystemSetup.xml\"
```

This command specifies specifies the parameters to install and configure the offline database.  The SQL server is additionally specified along with a configuration file to use.

```Console
ModernPOS.exe -InstallOffline -SQLServerName "SQLExpress" -Config "ModernPOS.Houston-3.xml"
```

Mix and match these concepts to achieve the installation results desired.

## Mass deployment examples using InTune
This section shall be added in a future update.

## Mass deployment examples using SCCM (System Center Configuration Manager)
This section shall be added in a future update.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
