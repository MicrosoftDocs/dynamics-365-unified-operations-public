---
title: Store Commerce app
description: This topic explains how to set up and configure the Store Commerce app.
author: mugunthanm
ms.date: 03/04/2022
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-01-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Store Commerce

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic applies to Microsoft Dynamics 365 Commerce version 10.0.25 and later.

The Store Commerce application is the next generation offering for physical stores that unifies Modern Point of Sale (MPOS) and Cloud Point of Sale (CPOS) into a single application, provides deployment choices to retailers, improves performance, and offers superior application life cycle management while retaining all the functionalities of MPOS and CPOS including extensibility.

The Store Commerce app in Dynamics 365 Commerce provides rich commerce functionality for first-line workers such as cashiers, sales associates, inventory associates, stock clerks, and store managers. It lets these workers perform commerce operations such cash-and-carry transactions, cash/shift management, customer engagement, assisted selling, clienteling, endless aisle, order processing/fulfillment, inventory management, and reporting.

Store Commerce is a [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/?view=netdesktop-6.0&preserve-view=true) shell application for Windows that uses the [Microsoft Edge WebView2](/microsoft-edge/webview2/) control to render the Cloud Point of Sale (CPOS) application. Although CPOS can run only in a web browser, Store Commerce can run as a native Windows application such as [Modern Point of Sale (MPOS)](retail-modern-pos-architecture.md), providing the benefits of both MPOS and CPOS.

Store Commerce supports local hardware station and offline usage, and can be directly integrated with a payment terminal, printer, and cash drawer and doesn't require a shared hardware station to be set up to use hardware devices.

To render the user interface (UI), Store Commerce uses the Chromium engine instead of the Universal Windows Platform (UWP) app rendering framework. The Chromium engine has better rendering performance than the native JavaScript UWP app in Windows. The main difference between MPOS and Store Commerce is that Store Commerce uses the Chromium engine to render the app.

## Benefits of Store Commerce

- Simplified Application lifecycle management (ALM).
- Extension or ISV code developed for MPOS or CPOS with the Commerce software development kit (SDK) that can be reused in Store Commerce with minimal changes.
- Store Commerce provides the benefits of both MPOS and CPOS.
- Better performance.
- Easier POS and extension upgrades.
- Support for dedicated hardware station (HWS).
- Support for offline.

## Application lifecycle management

The Store Commerce application runs on Windows devices and can be downloaded from the [Microsoft Lifecycle Services (LCS) Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). To download the application, on the **Sharasset library page, select the Retail Self-service package asset type and then locate the file ending with **Store Commerce**. Make sure to select there the version for the release you need, for instance 10.0.25, 10.0.26 and so on.

### Store Commerce deployment topology:

Store Commerce supports two types of deployment topology - Online (Connected to Cloud Scale Unit (CSU)) and Offline (Connected to locally deployed Commerce Runtime, no connectivity to Commerce Headquarters).

### Online:

Store Commerce is a shell that renders CPOS and connects to Headless Commerce and Commerce HQ using CSU in online mode and there are two options to render the app in Store Commerce online mode:

+ Store Commerce app content can be rendered from CPOS hosted in CSU, this option is called as Remote app content.
+ Store Commerce app content deployed locally within the Store Commerce app like MPOS, this is the default option and it’s called local deployment.

### Store Commerce app content rendered from CPOS hosted in CSU (Remote app content):

With this option the Store Commerce downloads and renders the app content from the CPOS hosted in CSU. To update the Store Commerce, update the CSU and all the Store Commerce app gets the update, in this case the updates are centrally managed in CSU, no need to manage the update at indivdual registers. For more information about how to update the CSU, see [Apply updates and extensions to Commerce Scale Unit (cloud)](../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md). The Store Commerce app shell still need to be updated separately using the installer.

#### Store Commerce app content rendered from local deployment:

With the local deployment option, the app contents are locally deployed within the Store Commerce app, Store Commerce app renders the app content from its local deployment, and it will **not** connect to the CPOS hosted in CSU to get the app content.

If you want to update the app content, then run the latest version of the Store Commerce installer, updating the CSU will not update the app content. This option allows you to manage the updates at individual register.

During installation of the Store Commerce app, user can pass parameter to choose remote app content or local deployment, by default Store Commerce app uses local deployment.

### Offline:

The Store Commerce app supports offline mode, during installation pass the parameter --installoffline to deploy the offline database. During offline the app will not be able to connect to CSU and Commerce HQ, instead it will use the locally deployed Commerce runtime.

## Store Commerce and MPOS parity

Store Commerce will have full functional parity with MPOS. Currently, Store Commerce doesn't support dual display. For more information about the different POS apps and topology, see [Choose between Modern POS (MPOS) and Cloud POS](../mpos-or-cpos.md)

## Store Commerce and CPOS parity

Store Commerce have full functional parity with CPOS, Store Commerce in addition supports dedicated hardware station and supports offline.

## Store Commerce and MPOS/CPOS

The recommendation is to use Store Commerce or CPOS for all new deployment and existing customer should plan for migrating the MPOS to Store Commerce app. 

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
<td>Store Commerce is self-serviced by using LCS and Commerce headquarters. It's packaged and installed by using the Store Commerce installer, and CPOS is deployed through CSU.</td>
<td>MPOS is self-serviced by using LCS and Commerce headquarters. It's packaged and installed by using the MPOS installer.</td>
</tr>
<tr>
<th scope="row">Extensions</th>
<td>Extensions are deployed to CPOS or installed using extension installer.</td>
<td>Extensions are packaged with MPOS, or an independent extension package is used.</td>
</tr>
<tr>
<th scope="row">Support for offline mode</th>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<th scope="row">Support for local hardware station</th>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr>
<th scope="row">UI rendering engine</th>
<td>The Chromium engine is used to render the UI.</td>
<td>The UWP app rendering framework is used to render the UI.</td>
</tr>
</tbody>
</table>

## Setup and installation

### Prerequisite

+ Windows 10 version 17763.0 or higher or Windows 11 or Windows Server 2019.
+ Microsoft Edge, because the app uses the Microsoft Edge WebView2 control.
+ Dynamics 365 Commerce (Back office and CPOS).

### Device setup in Commerce headquarters

For Store Commerce, a new application type that is named **Store Commerce** has been added on the **Devices** page (**Retail and Commerce \> Channel setup \> POS setup \> Devices**). Select this application type when you create a device for Store Commerce.

If you are not able to see the Store Commerce application type in the drop down menu, try running the **Initialize** from the Retail and Commerce > Headquarters setup > Parameters> Commerce parameters > General > **Initializer** and refresh the page.

You must create a [register](../tasks/create-associate-registers.md) and a [device](../tasks/create-associate-device.md) for Store Commerce. Then, before you activate the app, run the register job from the distribution schedule in Commerce headquarters. During device creation, set the **Application type** field to **Store Commerce**.

### Device installation

Store Commerce app can be download from [LCS Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary). In the Shared asset library page, select the Retail Self-service package asset type and then locate the file ending with **Store Commerce**. After downloading follow these steps to install the app:

1. Navigate to the folder where you downloaded the **Store Commerce** app and open PowerShell in admin mode.
2. In the PowerShell, locate the Store Commerce installer and pass the **install** parameter to install the app. To install offline components, pass **installoffline** parameter. Ex: *Store_Commerce Installer_exe_name install --installoffline*. If you want to enable debugging mode during installation pass the --enablewebviewdevtools parameter to enable debugging. 

### Store Commerce installation parameters:

You can also use help command in power shell to find the information about all the parameters, in PowerShell locate the Store Commerce installer and type *Store_Commerce Installer_exe_name help install*

| Parameters | Description |
| ------ | ------ |
| installoffline | Deploys the offline database |
| sqlservername | The SQL Server instance name used by Store Commerce in offline mode. If not specified, the installer will use a default instance |
| skipsqlfulltextcheck | Skips validating the SQL Full Text Search required for Offline. |
| trustsqlservercertificate | Trusts Server Certificate while establishing a connection to SQL Server. To avoid security risks, production deployments should never use this argument. Default is to not trust. |
| enablewebviewdevtools | Enables developer tools for the Store Commerce. If not specified, developer tools will be enabled only if Windows Developer Mode is enabled. |
| retailserverurl | Retail Server URL to be used for Store Commerce application as a default value. If not specified, the user will be prompted to input the Retail Server URL during device activation. |
| useremoteappcontent | Uses the remote application content, downloads the Store Commerce app content from CPOS hosted in CSU. Default is to use the local app content deployed with Store Commerce |
| skipversioncheck | Skips the validation during downgrade. |
| skipurlcheck | Skips the validation of URLs passed to the installer. |
| logdirectorypath | Path to the log’s directory. |
| config | Path to the configuration file to be used as part of this installation. |
| verbosity | Deploys the offline database |
| help | Displays the parameters information |
| version | Displays the app version information. |

### Store Commerce activation

1. After installation, on the Windows **Start** menu, search for **Store Commerce**, and open the app.
2. On the app's start page if you choose Remote app content as the deployment option enter the CPOS URL and click Save. You can find CPOS URL on the environment details page in LCS or on the **Channel profiles** page in Commerce (**Dynamics 365 Commerce \> Channel setup \> Channel profiles**).
3. Activate Store Commerce be following the steps in [POS activation guide](retail-device-activation.md#activate-a-modern-pos-or-cloud-pos-device-by-using-guided-activation).
4. After activation sign into the app by using an employee account.

### Troubleshooting setup issues

#### Reset the app

If the CPOS URL that you entered isn't valid and you want to change it, or if the app is in an error state during activation, you can restart the process by resetting the app.

1. On the Windows **Start** menu, select and hold (or right-click) the app, and then select **More \> App settings**.
2. Scroll down the app settings page until you find the **Reset** button.
3. Select **Reset**, and then, when you're prompted, confirm that you want to reset the app.

## Customizing the app

Store Commerce can be customized by using the Commerce SDK. You can modify and create the POS user experience, enhance, or modify out-of-box functionality, add validations, and add custom features. For more information, see [Point of Sale (POS) extension overview](pos-extension/pos-extension-overview.md) documentation or refer the samples in [GitHub](https://github.com/microsoft/Dynamics365Commerce.InStore).

### Hardware station extension

Store Commerce can be extended so that it's integrated with hardware devices. You can use the [sample extension code](https://github.com/microsoft/Dynamics365Commerce.InStore) that has been added in GitHub to generate Store Commerce hardware station extension (HWS) packages. For more information, see [Integrate the POS with a new hardware device](hardware-device-extension.md).

## Known issues with the Microsoft Edge WebView2 control

+ During activation, when prompted for entering the AAD password with multiple options, choose password. The other options might not work.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
