---
title: Store Commerce app
description: This article explains how to set up and configure the Microsoft Dynamics 365 Commerce Store Commerce app for Windows.
author: anush6121
ms.author: anvenkat
ms.date: 08/14/2024
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.search.validFrom: 2022-03-01
ms.custom: 
  - bap-template
---

# Store Commerce app

[!include [banner](../includes/banner.md)]

This article explains how to set up and configure the Microsoft Dynamics 365 Commerce Store Commerce app for Windows. It applies to Dynamics 365 Commerce versions 10.0.25 and later.

The Dynamics 365 Commerce Store Commerce app is the next generation offering for physical stores. It unifies Modern point of sale (MPOS) and Cloud point of sale (CPOS) (now known as *Store Commerce for web*) into a single application, providing deployment choices to retailers, helping improve performance, and offering superior application lifecycle management (ALM) while retaining all the functionality of MPOS and Store Commerce for web, including extensibility.

The Store Commerce app provides rich commerce functionality for first-line workers such as cashiers, sales associates, inventory associates, stock clerks, and store managers, and allows these workers to perform Commerce operations such as: 

- Cash-and-carry transactions
- Cash and shift management
- Customer engagement
- Assisted selling
- Clienteling
- Endless aisle
- Order processing and fulfillment
- Inventory management
- Reporting

The Store Commerce app is a [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/?view=netdesktop-6.0&preserve-view=true) shell application for Windows that uses the [Microsoft Edge WebView2](/microsoft-edge/webview2/) control to render Store Commerce for web. Although Store Commerce for web can only run in a web browser, Store Commerce can run as a native Windows application like [MPOS](retail-modern-pos-architecture.md) does, providing the benefits of both the Store Commerce app and Store Commerce for web.

Store Commerce supports local hardware station and offline usage, and can be directly integrated with a payment terminal, printer, and cash drawer. It can use hardware devices without requiring you to set up a shared hardware station.

To render the user interface (UI), Store Commerce uses the Chromium engine instead of the Universal Windows Platform (UWP) app rendering framework. The Chromium engine has better rendering performance than the native JavaScript UWP app in Windows. The main difference between MPOS and Store Commerce is that Store Commerce uses the Chromium engine to render the app.

The Store Commerce app is also available for the Android and iOS platforms. For more information, see [Store Commerce for mobile](store-commerce-mobile.md). 

## Benefits of Store Commerce

- Application lifecycle management is simplified.
- Extension or independent software vendor (ISV) code developed for the Store Commerce app or Store Commerce for web using the Commerce software development kit (SDK) can be reused in Store Commerce with minimal changes.
- The industry-standard developer experience uses Microsoft Visual Studio Code and GitHub.
- Store Commerce provides the benefits of both MPOS and Store Commerce for web.
- Performance is improved.
- POS and extension upgrades are simplified through the Commerce sealed installer framework.
- Dedicated hardware station is supported.
- Offline deployment is supported.

To review the capabilities of the Store Commerce app, see [Store Commerce app capabilities](../store-commerce-capabilities.md).

## Application lifecycle management

The Store Commerce app runs on Windows devices and can be downloaded from the [Shared asset library in Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with "Store Commerce." Be sure to select the version for the Commerce release that you're using (for example, 10.0.25 or 10.0.26).

### Store Commerce deployment options

Store Commerce supports two types of deployment topologies:

- **In-app** – All components are deployed locally. Offline mode and local Hardware Station (HWS) are supported.
- **Hybrid** – Store Commerce renders the Cloud POS that is deployed in Commerce Scale Unit (CSU) and supports local Hardware Station. However, offline isn't supported.

There are no separate installers for the hybrid and in-app topologies. The deployment options are determined by the parameters that are passed during installation.

![Store Commerce deployment options.](../media/SC-Deployment.png)

### In-app deployment

For the in-app deployment option, the application content is locally deployed. Store Commerce then renders the application content from its local deployment. It doesn't retrieve the Cloud POS UI hosted in the Commerce Scale Unit (CSU).

To update the application content, run the latest version of the Store Commerce installer. The application content isn't updated if you update the CSU, so you can manage the updates at individual registers.

In-app deployment supports offline mode. During installation, pass the `--installoffline` parameter to deploy the offline database. In offline mode, the application isn't able to connect to CSU or Commerce headquarters, and uses the locally deployed CRT.

> [!NOTE]
> During the installation of Store Commerce, users can pass parameters to select either the hybrid option or the in-app option. The default option is in-app deployment.

### Hybrid deployment

Store Commerce is a shell that connects to Headless Commerce and Commerce headquarters by using CSU in online mode. In hybrid mode, Store Commerce renders the Cloud POS UI that is hosted in the CSU. When the Store Commerce app is opened, it prompts for the Cloud POS URL.

![Active Store Commerce dialog box prompting for the Cloud POS URL.](../media/SC-Hybrid.png)

To update Store Commerce, update the CSU to update Store Commerce automatically. Because updates are centrally managed in CSU, they don't have to be managed at individual registers. The Store Commerce application shell must still be updated separately by using the installer. For more information about how to update the CSU, see [Apply updates and extensions to Commerce Scale Unit (cloud)](../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md). 

## Store Commerce and MPOS parity

Store Commerce has full functional parity with MPOS. For more information about the different POS applications and topologies, see [Choose between Store Commerce app and Store Commerce for web](../mpos-or-cpos.md).

## Hardware parity between MPOS and Store Commerce

The Store Commerce app doesn't support Universal Windows Platform (UWP) peripherals that are [Point of Service devices](/windows/uwp/devices-sensors/pos-get-started). If you're currently using a Universal Serial Bus (USB) scanner or magnetic stripe reader in plug-and-play mode, you must install OLE for Retail POS (OPOS) drivers and configure these devices in your hardware profile so they work with the Store Commerce app. For more information about Store Commerce peripheral support, see [Commerce peripherals](../retail-peripherals-overview.md).

For guidance on migrating from MPOS to Store Commerce, see [Migrate Modern POS to Store Commerce](pos-extension/migrate-mpos-store-commerce.md).

## Store Commerce and Store Commerce for web parity

Store Commerce has full functional parity with Store Commerce for web. In addition, Store Commerce supports dedicated hardware station and offline deployment.

## MPOS and Hybrid app roadmap

The Store Commerce apps for Windows and mobile platforms are the next generation of POS applications for Dynamics 365 Commerce. Microsoft deprecated MPOS and the [Retail hybrid apps](hybridapp.md) in October 2023, and recommends that you use Store Commerce or Store Commerce for web for all new deployments. Existing customers should plan to migrate MPOS to Store Commerce. 

### Comparison between Store Commerce and MPOS

<table>
<thead>
<tr>
<th></th>
<th>Store Commerce</th>
<th>MPOS</th>
</tr>
</thead>
<tbody>
<tr>
<th scope="row">Operating environment</th>
<td>Windows</td>
<td>Windows</td>
</tr>
<tr>
<th scope="row">ALM</th>
<td>Store Commerce is self-serviced by using Lifecycle Services and Commerce headquarters. It's packaged and installed by using the Store Commerce installer, and Store Commerce for web is deployed through CSU.</td>
<td>The Store Commerce app is self-serviced by using Lifecycle Services and Commerce headquarters. It's packaged and installed by using the Store Commerce app installer.</td>
</tr>
<tr>
<th scope="row">Extensions</th>
<td>Extensions are deployed to the CSU or installed by using the extension installer.</td>
<td>Extensions are packaged with the Store Commerce app, or an independent extension package is used.</td>
</tr>
<tr>
<th scope="row">Support for offline mode</th>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<th scope="row">Support for local hardware station</th>
<td>Yes, but doesn't support UWP peripherals that are Point of Service devices. For more information about Store Commerce peripheral support, see <a href="../retail-peripherals-overview.md">Commerce peripherals</a>.</td>
<td>Yes</td>
</tr>
<tr>
<th scope="row">UI rendering engine</th>
<td>The Chromium engine is used to render the UI.</td>
<td>The UWP app rendering framework is used to render the UI.</td>
</tr>
<tr>
<th scope="row">Deployment modes</th>
<td>In-app, hybrid. For more information, see <a href="#hybrid-deployment">Hybrid deployment</a>.</td>
<td>In-app.</td>
</tr>
<tr>
<th scope="row">Full screen mode</th>
<td>Yes. Select Alt+Enter to enter and exit full screen mode.</td>
<td>Yes. Select F11 to enter and exit full screen mode.</td>
</tr>
</tbody>
</table>


## Setup and installation

### Prerequisites

- Store Commerce is supported on the following operating systems:
  - Windows 11 (Pro, Enterprise, Enterprise LTSC, and IoT Enterprise LTSC.)
  - Windows 10 (Pro, Enterprise, Enterprise LTSC, and IoT Enterprise LTSC) with the latest available updates.
  - Windows Server 2022 (Standard, Essentials.) 
  - Windows Server 2019 (Standard, Essentials) with the latest available updates.
  - Windows 10 version 17763.0 or later (Pro, Enterprise, and Enterprise LTSC), Windows 11 (Pro, Enterprise, LTSC, and IoT Enterprise editions), or Windows Server 2019 (Standard, Essentials)
- [Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2/) (Use the Evergreen Standalone Installer.)
- SQL Server Express, SQL Server Standard, or SQL Server Enterprise (required only for offline mode). For information on which SQL Server edition to use, see [Commerce offline implementation and troubleshooting](implementation-considerations-offline.md).
- Dynamics 365 Commerce (Commerce headquarters and Cloud Scale Unit)
- To support the embedded Hardware Station components, you must install the correct version of .NET Framework. For Commerce versions 10.0.42 and later, install .NET Framework 4.8. For Commerce versions 10.0.41 and earlier, install .NET Framework 4.7.2. For more information, see [Install the .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework).  
- .NET Desktop Runtime 6.0.16 or later, which is used by the Store Commerce app for UI rendering.
- The following Store Commerce folders should be excluded when running any external applications or programs such as antivirus applications to prevent the folders from being deleted:
    - User-scoped application data: `C:\Users\**\Microsoft Dynamics 365\10.0\Data\Store Commerce`.
    - Common application data: `C:\ProgramData\Microsoft Dynamics 365\10.0\Data\Store Commerce`.
- The following Store Commerce registry entries should be excluded when running any external applications or programs such as antivirus applications to prevent the registry entries from being deleted:
    - `HKLM:SOFTWARE\Microsoft\Dynamics\Commerce\10.0\Store Commerce\Configuration\*`.
    - `HKLM:Software\Policies\Microsoft\Edge\WebView2\UserDataFolder\Microsoft.Dynamics.Commerce.StoreCommerce.exe`.

### Device setup in Commerce headquarters

For Store Commerce, an application type named **Store Commerce** was added on the **Devices** page (**Retail and Commerce \> Channel setup \> POS setup \> Devices**). Select this application type when you create a device for Store Commerce.

If the **Store Commerce** application type doesn't appear on the drop-down menu, try to run the **Initialize** function from the **General** tab of the **Commerce parameters** page (**Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**). Then refresh the page.

You must create a [register](../tasks/create-associate-registers.md) and a [device](../tasks/create-associate-device.md) for Store Commerce. Then, before you activate the app, run the register job from the distribution schedule in Commerce headquarters. During device creation, set the **Application type** field to **Store Commerce**.

### Device installation

Store Commerce can be downloaded from the [Lifecycle Services Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). On the **Shared asset library** page, select **Retail Self-service package** as the asset type, and then find the file that ends with **Store Commerce**. After the file is downloaded, follow these steps to install the app.

1. Go to the folder where you downloaded Store Commerce, and open PowerShell in administrator mode.
1. In PowerShell, find the Store Commerce installer, and pass the **install** parameter to install the app. To install offline components, pass the `--installoffline` parameter. (For example, enter `Store_Commerce Installer_exe_name install --installoffline`.) If you want to enable debugging mode during installation, pass the `--enablewebviewdevtools` parameter. 

### Store Commerce installation parameters

You can also use the **help** command in PowerShell to find information about all the parameters. In PowerShell, find the Store Commerce installer, and then enter `Store_Commerce Installer_exe_name help install`.

| Parameter | Description |
|---|---|
| --config \<path to config file\> | Specifies the path of the configuration file used as part of the installation. |
| --device \<device identifier\> | Specifies the device identifier to be used for Store Commerce application as a default value. If this parameter is omitted, the user is prompted to input the device identifier during device activation. |
| --disableaadauthentication | Disables the usage of Microsoft Entra authentication during device activation. This parameter is supported in on-premises Active Directory Federation Services (ADFS) based deployments only. |
| --enablewebviewdevtools | Enables developer tools for Store Commerce. If this parameter is omitted, developer tools are only enabled if Windows Developer Mode is enabled. |
| --help | Shows parameter information. |
| --inplaceupgradefrommodernpos | Executes an in-place upgrade from Modern POS. If this parameter is omitted, users will be required to activate Store Commerce after installation. |
| --installoffline | Deploys the offline database. If you're upgrading from Modern POS, you can update the existing offline database by passing the SQL instance in the `--sqlservername` parameter. |
| --logdirectorypath \<path to log directory\> | Specifies the path of the logs directory. |
| --register \<register number\> | Specifies the register number to be used for Store Commerce application as a default value. If not specified, the user is prompted to input the register number during device activation. |
| --retailserverurl \<Retail Server URL\> | Specifies the Retail Server URL to use for Store Commerce. If you don't specify this parameter, the user is prompted to enter the Retail Server URL during device activation. |
| --skipdotnetversioncheck | Bypasses the check to see if .NET is installed. |
| --skipenhancedmodernposupgradevalidation | Bypass enhanced upgrade validation when migrating from an existing Modern POS device. |
| --skipsqlfulltextcheck | Bypasses validation of the SQL Full-Text Search that is required for offline deployment. |
| --skipschannelcheck | Bypasses the secure channel prerequisite checks. |
| --skiptelemetrycheck | Bypasses validation of telemetry endpoints used by the application being installed. |
| --skipuninstallmodernposafterupgrade | Skips uninstalling Modern POS as the last step of the upgrade. |
| --skipurlcheck | Bypasses the validation of URLs that are passed to the installer. |
| --skipversioncheck | Bypasses version validation during downgrade. |
| --sqlservername \<SQL server name\> | Specifies the name of the SQL Server instance that Store Commerce uses in offline mode. If this parameter is omitted, the installer uses the default instance. |
| --trustsqlservercertificate | Trusts the SQL Server certificate when a connection is established to SQL Server. To help avoid security risks, you should never use this argument for production deployments. By default, the SQL Server certificate isn't trusted. |
| --usecommonapplicationdata | Installs the Store Commerce app for all users on the device by placing a token in a common application data folder. To use the Store Commerce app, users must be added to the RetailChannelUsers group on the device. If this parameter is omitted, the Store Commerce app is only installed for the current user. |
| --useremoteappcontent | Download and display the Store Commerce UI from the Commerce Scale Unit (CSU.) If this parameter is omitted, the local application content that is deployed with Store Commerce is used. For more information, see [Hybrid deployment](#hybrid-deployment). |
| --verbosity | Specifies the verbosity of logs (0 - trace, 1 - debug, 2 - informational, 3 - warning, 4 - error, 5 - critical, 6 - silent). When this parameter is omitted, the default value of 2 is used. |
| --version | Shows information about the app version. |

### Uninstall Store Commerce

To uninstall the Store Commerce application from a device, follow these steps.

1. Open PowerShell in administrator mode and navigate to the folder where you downloaded the Store Commerce installer executable.
1. In PowerShell, find the Store Commerce installer executable and pass the `StoreCommerce.Installer.exe uninstall` parameter to uninstall the app. When executed, this command runs immediately and doesn't provide a confirmation dialog before uninstalling Store Commerce.

### Activate Store Commerce

To activate Store Commerce after installation, follow these steps.

1. On the Windows **Start** menu, search for **Store Commerce**, and then open the application. 
    > [!NOTE]
    > The Store Commerce app shouldn't be run with elevated privileges, and shouldn't be run from an account with elevated privileges.
1. On the application's start page, if you select **Remote app content** as the deployment option, enter the Cloud POS URL, and then select **Save**. You can find the Cloud POS URL on the environment details page in Lifecycle Services, or on the **Channel profiles** page in Commerce (**Dynamics 365 Commerce \> Channel setup \> Channel profiles**).
1. Activate Store Commerce by following the steps in [Activate Store Commerce using guided activation](retail-device-activation.md#activate-store-commerce-using-guided-activation).
1. After activation is completed, sign in to the application by using an employee account.

### Troubleshoot setup issues

For troubleshooting information, see [Troubleshoot Store Commerce setup and installation issues](../troubleshoot/store-commerce-setup-installation.md).

## Customize the app

Store Commerce can be customized by using the Commerce SDK. You can modify and create the POS user experience, enhance or modify out-of-box functionality, add validations, and add custom features. For more information, see [Point of Sale (POS) extension overview](pos-extension/pos-extension-overview.md), or review the samples on [GitHub](https://github.com/microsoft/Dynamics365Commerce.InStore).

### Hardware station extension

You can extend Store Commerce to integrate it with hardware devices. You can use the [sample extension code](https://github.com/microsoft/Dynamics365Commerce.InStore) in GitHub to generate Store Commerce hardware station extension packages. For more information, see [Integrate the POS with a new hardware device](hardware-device-extension.md).

## Microsoft Edge WebView2 control

The Store Commerce app for Windows uses the [Microsoft Edge WebView2 control](/microsoft-edge/webview2/) for rendering. Microsoft preinstalls and automatically updates the WebView2 evergreen runtime on all Windows 11 and eligible Windows 10 devices. The evergreen runtime distribution model has the advantage of not requiring additional effort to manage, but it doesn't allow you to control the version of WebView2 used with a particular release of the Store Commerce app. 

Microsoft recommends that you explicitly manage the WebView2 version that is used by a particular update of the Store Commerce app to mitigate the risk of regressions that are caused by incompatibilities between the Store Commerce app and the latest WebView2 control.  

### Manage WebView2 versions

To manage WebView2 versions, follow these steps.

1. Disable automatic WebView2 updates via Group Policy or registry keys. 
1. Use the standalone installer to install a specific version of the WebView2 control.
    > [!NOTE]
    > A given version of the standalone installer always installs the same version of the WebView2 runtime. 
1. Test each incremental release of the Store Commerce app with the latest version of the WebView2 runtime and update the WebView2 runtime on the registers at the same time you update the Store Commerce app. 
1. Use the standalone evergreen installer to deploy the specific version of the WebView2 runtime used during user acceptance testing (UAT) for the Store Commerce app. 
1. Use the [Install (WebView)](/deployedge/microsoft-edge-update-policies#install-webview) policy to force machine-wide installs for the WebView2 runtime, or to disable installs. This policy ensures that all users on the machine use the same version of the WebView2 runtime. 
1. Use the [Update (WebView)](/deployedge/microsoft-edge-update-policies#update-webview) policy to disable all WebView2 runtime updates by Microsoft Edge update. 
    > [!NOTE]
    >  Disabling all WebView2 runtime updates by Microsoft Edge update shouldn't impact the Edge browser version because Edge has a separate [Update policy](/deployedge/microsoft-edge-update-policies#update).
 
### Known issues with the Microsoft Edge WebView2 control

During activation, when prompted to enter the Microsoft Entra password with multiple options, choose the password option. The other options might not work.

## Additional resources

[Store Commerce app capabilities](../store-commerce-capabilities.md)

[Modernizing the Dynamics 365 Commerce in-store technology stack](https://www.microsoft.com/download/details.aspx?id=103896)

[Commerce SDK Tech Talk Series](https://community.dynamics.com/blogs/post/?postid=a7ae4e0b-3af0-48a0-8943-9ee9d0f941c6)

[Store Commerce Extensions Overview](pos-extension/pos-extension-overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
