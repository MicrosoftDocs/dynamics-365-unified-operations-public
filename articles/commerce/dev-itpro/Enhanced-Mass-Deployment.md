---
# required metadata

title: Mass deployment of sealed Commerce self-service components
description: This article explains how to use the framework for self-service component installers to silently install and service deployments.
author: jashanno
ms.date: 01/30/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global 
ms.author: jashanno
ms.search.validFrom: 2021-04-30

---

# Mass deployment of sealed Commerce self-service components

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

> [!WARNING]
> Once Commerce Scale Unit (CSU) is updated to version 10.0.29 or later, the point of sale (Modern POS or Store Commerce) version must be 10.0.27 or later (seen in point of sale as version 9.27). This is due to the migration to .NET Core.

This article applies to the sealed framework, component installers that are released every month, beginning with the 10.0.18 release, and that are made available in the Shared asset library in Microsoft Dynamics Lifecycle Services. Note that the first several releases of these new installers are designated as **(Preview)**. However, the only purpose of this designation is to differentiate the new installers while Microsoft determines whether there are any additional functional requirements to use them. It doesn't mean that the installers aren't valid for production. Based on the release of these new installers, Microsoft plans to deprecate the old (legacy) installers in or around October 2023. 

This article explains how to use the new installers to perform silent installation and servicing updates via command-line arguments. These arguments let you do mass deployment in several different ways.

> [!NOTE]
> - Self-service, sealed installers won't be made available in Commerce headquarters and are only downloadable through LCS.
> - Starting with the Commerce version 10.0.32 release, .NET 6 is required as a prerequisite for the sealed self-service components.

## Delimiters for mass deployment

The following table shows the delimiters that can be used in the command line execution.


| Delimiter                 | Description |
|---------------------------|-------------|
| -AadTokenIssuerPrefix | The prefix for the Microsoft Azure Active Directory (Azure AD) token issuer. |
| -AsyncClientAadClientId | The Azure AD client ID that Async Client should use during communications with Headquarters. |
| -AsyncClientAppInsightsInstrumentationKey | The Async Client AppInsights instrumentation key. |
| -AsyncClientCertFullPath | The fully formatted URN path that uses the thumbprint as the search metric of the Async Client Identity certificate location that should be used to authenticate with Azure AD for communications with Headquarters. For example, `store://My/LocalMachine?FindByThumbprint=<MyThumbprint>` is a correctly formatted URN. The value **\<MyThumbprint\>** will be replaced with the certificate thumbprint that should be used. Don't use this parameter together with the **-AsyncClientCertThumbprint** parameter. |
| -AsyncClientCertThumbprint | The thumbprint of the Async Client Identity certificate that should be used to authenticate with Azure AD for communications with Headquarters. This thumbprint will be used to search the **LocalMachine/My store** location and name to find the correct certificate to use. Don't use this parameter together with the **-AsyncClientCertFullPath** parameter. |
| -ClientAppInsightsInstrumentationKey | The Client AppInsights instrumentation key. |
| -CloudPosAppInsightsInstrumentationKey | The Cloud POS AppInsights instrumentation key. |
| -Config | The configuration file that should be used during installation. An example of a file name is **Contoso.CommerceScaleUnit.xml**. |
| -CposAadClientId | The Azure AD client ID that Cloud POS should use during device activation. This parameter isn't required for on-premises deployments. |
| -Device | The device ID, as shown on the **Devices** page in Headquarters. |
| -EnvironmentId | The environment ID. |
| -HardwareStationAppInsightsInstrumentationKey | The Hardware Station AppInsights instrumentation key. |
| --InPlaceUpgradeFromModernPOS | Used to upgrade from Modern POS to Store Commerce. Unless other parameters are used, the default assumption is to capture the Modern POS device token and then uninstall Modern POS. |
| Install | A parameter that specifies whether the component that this installer provides should be installed. This parameter is required to perform an installation and does not have a leading dash character. |
| -InstallOffline | For Modern POS, this parameter specifies that the offline database should also be installed and configured. Use the **-SQLServerName** parameter too. Otherwise, the installer will try to find a default instance that meets the prerequisites. When using Azure Active Directory (Azure AD) authentication, POS offline will not function, as online connectivity is always required. |
| -Port | The port that should be associated with and used by the Retail Server virtual directory. If no port is set, the default port, 443, will be used. |
| -Register | The register ID, as shown on the **Registers** page in Headquarters. |
| -RetailServerAadClientId | The Azure AD client ID that Retail Server should use during communications with Headquarters. |
| -RetailServerAadResourceId | The Retail Server Azure AD app resource ID that should be used during device activation. This parameter isn't required for on-premises deployments. |
| -RetailServerCertFullPath | The fully formatted URN path that uses the thumbprint as the search metric of the Retail Server Identity certificate that should be used to authenticate with Azure AD for communications with Headquarters. For example, `store://My/LocalMachine?FindByThumbprint=<MyThumbprint>` is a correctly formatted URN where the value **\<MyThumbprint\>** will be replaced with the certificate thumbprint that should be used. Don't use this parameter together with the **-RetailServerCertThumbprint** parameter. |
| -RetailServerCertThumbprint | The thumbprint of the Retail Server Identity certificate that should be used to authenticate with Azure AD for communications with Headquarters. This thumbprint will be used to search the **LocalMachine/My** store location and name to find the correct certificate to use. Don't use this parameter together with the **-RetailServerCertFullPath** parameter. |
| -RetailServerURL | The Retail Server URL that the installer should use. (This URL is also known as the Commerce Scale Unit \[CSU\] URL.) For Modern POS, this value will be used during device activation. |
| -SkipAadCredentialsCheck| A switch that indicates whether Azure AD credential prerequisite checks should be skipped. The default value is **false**. |
| -SkipCertCheck | A switch that indicates whether certificate prerequisite checks should be skipped. The default value is **false**. |
| --SkipEnhancedModernPOSUpgradeValidation | A switch to skip the standard validations that are run prior to performing the device token capture from Modern POS. This flag should only be used in test environments, and shouldn't be used in production. |
| -SkipIisCheck | A switch that indicates whether Internet Information Services (IIS) prerequisite checks should be skipped. The default value is **false**. |
| -SkipNetFrameworkCheck | A switch that indicates whether .NET Framework prerequisite checks should be skipped. The default value is **false**. |
| -SkipScaleUnitHealthcheck | A switch that indicates whether the health check on installed components should be skipped. The default value is **false**. |
| -SkipSChannelCheck | A switch that indicates whether secure channel prerequisite checks should be skipped. The default value is **false**. |
| -SkipSqlFullTextCheck | A switch that indicates whether validation of the SQL Server prerequisite that requires Full Text Search should be skipped. The default value is **false**. |
| -SkipSqlServerCheck | A switch that indicates whether SQL Server prerequisite checks should be skipped. The default value is **false**. |
| --SkipUninstallModernPOSAfterUpgrade | A switch to skip the uninstallation of Modern POS after performing the upgrade to Store Commerce and the device token capture from Modern POS. |
| -SqlServerName | The SQL Server name. If the name isn't specified, the installer will try to find the default instance. |
| -SslcertFullPath | The fully formatted URN path that uses the thumbprint as the search metric of the certificate location that should be used to encrypt HTTP traffic to the scale unit. For example, `store:\/\/My\/LocalMachine\?FindByThumbprint\=\<MyThumbprint\>` is a correctly formatted URN where the value **\<MyThumbprint\>** will be replaced with the certificate thumbprint that should be used. Don't use this parameter together with the **-SslCertThumbprint** parameter. |
| -SslCertThumbprint | The thumbprint of the certificate that should be used to encrypt HTTP traffic to the scale unit. This thumbprint will be used to search the **LocalMachine/My store** location and name to find the correct certificate to use. Don't use this parameter together with the **-SslCertFullPath** parameter. |
| -StoreSystemAosUrl | The Headquarters (AOS) URL. |
| -StoreSystemChannelDatabaseId | The channel database ID (name). |
| -TenantId | The Azure AD tenant ID. |
| -TransactionServiceAzureAuthority | The Transaction Service Azure AD authority. |
| -TransactionServiceAzureResource | The Transaction Service Azure AD resource. |
| -TrustSqlServerCertificate | A switch that indicates whether the Server certificate should be trusted while a connection to SQL Server is being established. To help avoid security risks, production deployments should never supply a value of **true** here. The default value is **false**. |
| --UseCommonApplicationData | A switch to alter the location of the device token. Instead of being in the user context, the token is stored in a shared location so that all Windows users can access the same token, allowing for the use of Store Commerce regardless of the active user. Users must still be in the **RetailChannelUsers** group. |
| -Verbosity | The level of logging that is requested during installation. Typically, this value should not be used. |
| -WindowsPhoneAppInsightsInstrumentationKey | The Hardware Station AppInsights instrumentation key. |

## General overview

The new framework for self-service installers has various features and improvements. The new framework currently generates installers only for Modern POS, hardware station, and CSU (self-hosted). It is important to understand the basic command line usage of the sealed installers, which should look similar to that used in the following example. 
 
```Console
<Component Installer Name>.exe install --<Parameter Name> "<Parameter Information>"
```

The installer requires the parameter **install** (or **uninstall** to remove the installation) and any parameters specific to that installation. **Parameter Name** should include any parameters that are needed such as register, CSU URL, or certificate information. **Parameter Information** should include any additional information about the parameters.

The sealed framework has been created to allow for the following alterations:
- **Sealed** – The new installer framework completely separates Microsoft-distributed base component installers from the extensibility-based customizations. The customizations will be installed afterward but will then be untethered in regard to updates (so that updates will be allowed only for the Microsoft base component, only for the customizations, or for both).
- **GUI-less** – There is no longer a user interface (UI). Instead, there is an entirely command line–driven executable for each component installer. This change is one of several key changes or features that are used to focus the new installer framework for use with mass deployment.
- **Deeper logging** – Enhanced installer logs allow for better validation of installation completion or failure, the steps that were performed, and any warnings or errors that were generated.
- **Clean-up** – In the new framework, the component installers work harder to maintain the cleanliness of installation directories, by clearing the full contents of the component folder before they install the newer components. This clean-up ensures that there are no leftover files that could cause issues and prevent successful installation.

Three components haven't been migrated to the new framework: the Virtual Peripheral Simulator, Async Server Connector Service (used for Dynamics AX 2012 R3 support), and the Real-time Service Replacement (used for Dynamics AX 2012 R3 support).

> [!NOTE]
> Installers are stored locally and retained.  It is important, over time, to manage or delete the retained installers to not waste disk space. It is recommended to keep the current installer for the base component(s) and any extension installers for the latest version(s) for purposes of recovery from extreme situations.

## Migration

Migration from the old self-service framework component installers to the new framework component installers requires uninstallation of the old components.

- **Modern POS** – The new installer framework caused the application to receive a new application signature ID. Therefore, full uninstallation of old components is required before the new framework Modern POS component is installed. Because of the requirement for full uninstallation, device activation will be required again. (This device reactivation is a one-time requirement, provided that uninstallation doesn't occur again.)
- **Hardware station** – As an IIS website, the new installer framework requires that the base folder structure be reworked. Therefore, full uninstallation of old components is required before the new framework hardware station component is installed.
- **Commerce Scale Unit (CSU, self-hosted)** – As a series of IIS websites, the new installer framework requires that the base folder structure be reworked.  Therefore, full uninstallation of old components is required before the new framework CSU (self-hosted) component is installed.

## Modern POS

### Before you begin

It's critical that you remove the old, self-service Modern POS component. For more information, see the migration steps earlier in this article. As an additional requirement, the SQL instance that's used must have both **Windows authentication** and **SQL Server authentication** modes. You can manage and change this configuration under the **Security** subheading in the **Properties** window in SQL Server Management Studio.

> [!NOTE]
> On a single-computer system such as a developer topology or a demo environment, or when Commerce Scale Unit and Modern POS are installed on the same computer, it is possible for Store Commerce to be unable to complete device activation. This issue occurs because Store Commerce can't make network calls to the same computer (that is, calls to itself). While this should never be a scenario in a production setting, the issue can be mitigated by enabling an AppContainer loopback exception so that communications can occur to the same computer. Various applications are publicly available to help enable this loopback. For more information about loopback, see [How to enable loopback and troubleshoot network isolation](/previous-versions/windows/apps/hh780593(v=win.10)). It is important to understand that a loopback can be a security risk, so it is not recommended that you use a loopback unless absolutely necessary.

### Examples of silent deployment

This section shows examples of commands that are used to install Modern POS.

#### Silently install Modern POS

The following command silently installs (or updates) Modern POS. It has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe**.

The following basic command showcases the available options if an installation is requested. It is highly recommended that this command is used when first testing or using the installer.

```Console
CommerceModernPOS.exe help install
```

> [!NOTE]
> A configuration file isn't required for Modern POS. The installer now has parameters (shown earlier in this article) for the various values that are used during device activation.

The following command specifies all the parameters that should be used during device activation after the Modern POS application is installed. This example uses the **Houston-3** register, which is a commonly used value in Dynamics 365 Commerce demo data.

```Console
CommerceModernPOS.exe install --Register "Houston-3" --Device "Houston-3" --RetailServerURL "https://MyDynamics365CommerceURL.dynamics.com/Commerce"
```

The following command specifies the parameters that should be used to install and configure the offline database. The SQL Server is specified together with the configuration file that should be used. Unless a trusted SQL certificate is used, the `--TrustSqlServerCertificate` parameter is required. We don't recommend that you skip checks when you install in production.

```Console
CommerceModernPOS.exe install -InstallOffline -SQLServerName "SQLExpress" -Config "ModernPOS.Houston-3.xml" 
```

The following command specifies the parameters that should be used to upgrade from Modern POS to Store Commerce (with an offline database in use). These parameters capture the device token used by Modern POS (removing the need for a manual device activation process), and then uninstall Modern POS. The SQL Server is specified together with the configuration file that should be used.

```Console
CommerceModernPOS.exe install -InstallOffline -SQLServerName "SQLExpress" --InPlaceUpgradeFromModernPOS
```

You can mix and match these concepts to achieve the installation results that you want.

## Hardware station

### Before you begin

It's critical that you remove the old self-service hardware station component. For more information, see the migration steps earlier in this article. There is no longer a Merchant Account Information Tool. Instead, the merchant account information is installed when a POS terminal is paired with the hardware station. When testing this installer for the first time, it is highly recommended that you run the following command:

```Console
CommerceHardwareStation.exe help install
```

### Examples of silent deployment

This section shows examples of commands that are used to install hardware station.

#### Silently install hardware station

The following command silently installs (or updates) hardware station. It has the standard command structure that is used to service components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe**.

The following basic command runs the executable file installer.

```Console
HardwareStation.exe install --Port 443 --CSUURL "https://MyDynamics365CommerceURL.dynamics.com/" --StoreSystemChannelDatabaseID "Houston" --CertThumbprint "MySSLCertificateThumbprintOftenHasNumbers"
```

> [!NOTE]
> A configuration file isn't required for hardware station. The installer now has parameters (shown earlier in this article) for the various values that are required.

The following command specifies all the parameters that are required to skip the prerequisite checks during a standard installation. 

> [!NOTE]
> We don't recommend that you skip checks unless you do thorough testing ahead of time, or except in development situations. We don't recommend that you skip checks when you install in production.

```Console
HardwareStation.exe install --SkipFirewallUpdate --SkipOPOSCheck --SkipVersionCheck --SkipURLCheck --Config "HardwareStation.Houston.xml"
```

As is customary, it is common to mix and match these concepts to achieve the installation results that you want.

## Commerce Scale Unit (self-hosted)

When testing this installer for the first time, it is highly recommended to that you run the following command:

```Console
CommerceStoreScaleUnitSetup.exe help install
```

### Before you begin

It's critical that you remove the old self-service CSU (self-hosted) component. For more information, see the migration steps earlier in this article.

### Examples of silent deployment

This section shows examples of commands that are used to install CSU (self-hosted).

#### Silently install CSU (self-hosted)

The following command silently installs (or updates) CSU (self-hosted). It has the standard command structure that is used for silent servicing of components that are currently installed. The structure uses the basic values of **&lt;InstallerName&gt;.exe**.

Compared to the other self-service installers, Commerce Scale Unit (CSU) is more complex and requires a fairly large amount of additional information. The following command is the minimum command (with parameters) needed to run the executable file installer when no configuration file is present. Unless a trusted SQL certificate is used, the `--TrustSqlServerCertificate` parameter is required.

```Console
CommerceScaleUnit.exe install --port 446 --SSLCertThumbprint "MySSLCertificateThumbprintOftenHasNumbers" --RetailServerCertFullPath "store://My/LocalMachine?FindByThumbprint=MyCertificateThumbprintUsedByRetailServer" --AsyncClientAADClientID "MyAAD-Client-IDFor-AsyncClient" --RetailServerAADClientID "MyAAD-Client-IDFor-RetailServer" --CPOSAADClientID "MyAAD-Client-IDFor-CloudPOS" --RetailServerAADResourceID "https://retailstorescaleunit.retailserver.com" --Config "Contoso.StoreSystemSetup.xml"
```

> [!NOTE]
> A configuration file is still required for CSU (self-hosted).

The following command is a more thorough command that runs the executable file installer with some alternative parameters. Unless a trusted SQL certificate is used, the `--TrustSqlServerCertificate` parameter is required.

```Console
CommerceScaleUnit.exe install --Port 446 --SSLCertFullPath "store://My/LocalMachine?FindByThumbprint=MySSLCertificateThumbprintOftenHasNumbers" --AsyncClientCertFullPath "store://My/LocalMachine?FindByThumbprint=MySSLCertificateThumbprintOftenHasNumbers" --RetailServerCertFullPath "store://My/LocalMachine?FindByThumbprint=MyCertificateThumbprintUsedByRetailServer" --AsyncClientAADClientID "MyAAD-Client-IDFor-AsyncClient" --RetailServerAADClientID "MyAAD-Client-IDFor-RetailServer" --CPOSAADClientID "MyAAD-Client-IDFor-CloudPOS" --RetailServerAADResourceID "https://retailstorescaleunit.retailserver.com" --Verbosity 0 --Config "Contoso.StoreSystemSetup.xml"
```

The following command specifies parameters required to skip the prerequisite checks during a standard installation. 

> [!NOTE]
> - We don't recommend that you skip checks unless you do thorough testing ahead of time, or except in development situations. We don't recommend that you skip checks when you install in production.
> - Unless a trusted SQL certificate is used, the `--TrustSqlServerCertificate` parameter is required.

```Console
CommerceScaleUnit.exe install --skipscaleunithealthcheck --skipcertcheck --skipaadcredentialscheck --skipschannelcheck --skipiischeck --skipnetcorebundlecheck --skipsqlservercheck --skipnetframeworkcheck --skipversioncheck --skipurlcheck --Config "Contoso.StoreSystemSetup.xml" --SSLCertFullPath "store://My/LocalMachine?FindByThumbprint=MySSLCertificateThumbprintOftenHasNumbers" --AsyncClientCertFullPath "store://My/LocalMachine?FindByThumbprint=MySSLCertificateThumbprintOftenHasNumbers" --RetailServerCertFullPath "store://My/LocalMachine?FindByThumbprint=MyCertificateThumbprintUsedByRetailServer" --AsyncClientAADClientID "MyAAD-Client-IDFor-AsyncClient" --RetailServerAADClientID "MyAAD-Client-IDFor-RetailServer" --CPOSAADClientID "MyAAD-Client-IDFor-CloudPOS" --RetailServerAADResourceID "https://retailstorescaleunit.retailserver.com"
```

You can mix and match these concepts to achieve the installation results that you want.

<!--## Mass deployment examples using InTune

This section will be added in a future update.

## Mass deployment examples using System Center Configuration Manager (SCCM)

This section will be added in a future update.-->

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
