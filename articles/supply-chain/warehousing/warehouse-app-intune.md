---
title: Mass deploy the Warehouse Management mobile app
description: This article explains how to mass deploy the Warehouse Management mobile app by using Microsoft Intune.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 03/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Mass deploy the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

Automated deployment and configuration of Warehouse Management can be more efficient than manual deployment when you have many devices to manage. One way to achieve this automation is to use a mobile device management (MDM) solution such as [Microsoft Intune](/mem/intune/fundamentals/what-is-intune). For general information about how to use Intune to add apps, see [Add apps to Microsoft Intune](/mem/intune/apps/apps-add).

This article explains how to mass deploy the Warehouse Management mobile app by using Intune.

## Prerequisites

To use an MDM solution to deploy the Warehouse Management mobile app and the related authentication certificates, you must have the following resources available:

- Warehouse Management mobile app version 2.0.41.0 or later (This version number applies to all mobile platforms.)
- A valid store account for each mobile platform that you'll support ([Microsoft account](https://account.microsoft.com/account/), [Google Account](https://www.google.com/account/about/), and/or [Apple ID](https://appleid.apple.com/sign-in))
- [Azure Active Directory (Azure AD)](https://portal.azure.com/#view/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/~/Overview) (Azure AD Premium P2 license)
- [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com/#home) (the Intune website)
- [Certificate Connector for Microsoft Intune](/mem/intune/protect/certificate-connector-overview) installed on a dedicated Windows PC
- [PowerShell](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)
- [Visual Studio 2022](https://visualstudio.microsoft.com/vs/)

You must also have the following resources, which you'll set up by following the instructions in this article:

- [PFX certificate](#create-a-self-signed-pfx-certificate) for certificate-based authentication (CBA)
- [Connection settings JavaScript Object Notation (JSON) file](#create-a-connection-json-file) for the Warehouse Management app
- [PFXImport tool](#download-and-build-the-pfximport-project) for the Microsoft Endpoint Manager admin center

## Set up the source files for distribution

Each MDM solution offers several methods for sourcing the apps that they deliver to end devices. For example, a solution might use locally stored binary files or fetch binaries from an app store. The preferred method is to use app stores, because it's simple and offers the most convenient way to receive updates.

The following subsections provide examples that show how to set up Intune to fetch apps from the different app stores.

### Set up Intune to fetch the app from Google Play

Follow these steps to set up Intune to fetch the Warehouse Management mobile app from [Google Play](https://play.google.com/store/apps/details?id=com.Microsoft.WarehouseManagement).

1. Sign in to the Microsoft Endpoint Manager admin center.
1. Go to **Apps \> Android**.
1. On the **Android apps** page, on the toolbar, select **Add**.
1. In the **Select app type** dialog box, in the **App type** field, select *Managed Google Play app*. Then select **Select**.
1. On the **Managed Google Play** page, if you're setting up Google Play for the first time, you're prompted to sign in to Google Play. Sign in by using your Google account.
1. In the **Search** field, enter *Warehouse Management*. Then select **Search**.
1. When you've found the Warehouse Management app, select **Approve**.
1. In the **Approve settings** dialog box, select an option to specify how updates should be handled when a new version of the app requests more permissions than the current version. We recommend that you select the **Keep approved when app requests new permissions** option. When you've finished, select **Done** to continue.
1. Select **Sync**.
1. You're returned to the **Android apps** page. On the toolbar, select **Refresh** to refresh the list of applications. Then, in the list, select *Warehouse Management*.
1. On the **Warehouse Management** page, on the **Properties** tab, select the **Edit** link next to the **Assignments** heading.
1. On the **Edit application** page, on the **Assignments** tab, add the user groups and/or devices that the Warehouse Management app should be available and/or required for. For information about how to use the settings, see [Assign apps to groups with Microsoft Intune](/mem/intune/apps/apps-deploy).
1. When you've finished, select **Review + save**.
1. On the **Review + save** tab, review your settings. If they look correct, select **Save** to save them.

### Set up Intune to fetch the app from Microsoft Store

Follow these steps to set up Intune to fetch the Warehouse Management mobile app from [Microsoft Store](https://apps.microsoft.com/store/detail/warehouse-management/9PD35CDQCMG3).

1. Sign in to the Microsoft Endpoint Manager admin center.
1. Go to **Apps \> Windows**.
1. On the toolbar, select **Add**.
1. In the **Select app type** dialog box, in the **App type** field, select *Microsoft Store app (new)*. Then select **Select**.
1. On the **Add App** page, on the **App information** tab, select the **Search the Microsoft Store app (new)** link.
1. In the **Search the Microsoft Store app (new)** dialog box, in the **Search** field, enter *Warehouse Management*.
1. When you've found the Warehouse Management app, select it, and then select **Select**.
1. The **App information** tab now shows information about the Warehouse Management app. Select **Next** to continue.
1. On the **Assignments** tab, add the user groups and/or devices that the Warehouse Management app should be available and/or required for. For information about how to use the settings, see [Assign apps to groups with Microsoft Intune](/mem/intune/apps/apps-deploy).
1. When you've finished, select **Next** to continue.
1. On the **Review + save** tab, review your settings. If they look correct, select **Create** to save them.

### Set up Intune to fetch the app from the Apple App Store

Follow these steps to set up Intune to fetch the Warehouse Management mobile app from the Apple App Store.

1. Sign in to the Microsoft Endpoint Manager admin center.
1. Go to **Devices \> iOS/iPadOS**.
1. On the **iOS/iPad enrollment** tab, select the **Apple MDM Push certificate** tile.
1. In the **Configure MDM Push Certificate** dialog box, follow the on-screen instructions to create and upload the required Apple MDM push certificate. For more information about this step, see [Get an Apple MDM push certificate](/mem/intune/enrollment/apple-mdm-push-certificate-get).
1. Go to **Apps \> iOS/iPadOS**.
1. On the toolbar, select **Add**.
1. In the **Select app type** dialog box, in the **App type** field, select *iOS store app*. Then select **Select**.
1. On the **Add App** page, on the **App information** tab, select the **Search the App Store** link.
1. In the **Search the App Store** dialog box, in the **Search** field, enter *Warehouse Management*. Then, in the drop-down list next to the **Search** field, select your country or region.
1. When you've found the Warehouse Management app, select it, and then select **Select**.
1. The **App information** tab now shows information about the Warehouse Management app. Select **Next** to continue.
1. On the **Assignments** tab, add the user groups and/or devices that the Warehouse Management app should be available and/or required for. For information about how to use the settings, see [Assign apps to groups with Microsoft Intune](/mem/intune/apps/apps-deploy).
1. When you've finished, select **Next** to continue.
1. On the **Review + save** tab, review your settings. If they look correct, select **Create** to save them.

## Manage connection configurations

The Warehouse Management mobile app (version 2.0.41.0 and later) lets you import connection settings as a managed configuration through an MDM solution. The same **ConnectionsJson** configuration key is shared across all platforms.

The following subsections provide examples that show how to set up Intune to provide managed configuration for each of the supported mobile platforms. For more information, see [App configuration policies for Microsoft Intune](/mem/intune/apps/app-configuration-policies-overview).

### Create a connection JSON file

As a prerequisite for setting up managed configuration of all mobile platforms, you must create a connection JSON file as described in [Create a connection settings file or QR code](/dynamics365/supply-chain/warehousing/install-configure-warehouse-management-app#create-a-connection-settings-file-or-qr-code). This file enables the mobile app to connect to and authenticate with your Dynamics 365 Supply Chain Management environment.

> [!TIP]
> If your JSON file includes more than one connection, one of them should be set as the default connection (by setting the `IsDefaultConnection` parameter to *true* for it). If no default connection is set, the app will prompt the user to manually select an initial connection among the available options.

### Set up Intune to support managed configuration for Android devices

Follow these steps to set up Intune to support managed configuration for Android devices.

1. Sign in to the Microsoft Endpoint Manager admin center.
1. Go to **Apps \> App configuration policies**.
1. On the **App configuration policies** page, on the toolbar, select **Add \> Managed devices**.
1. On the **Create app configuration policy** page, on the **Basics** tab, set the following fields:
    - **Name** – Enter a name for the policy.
    - **Platform** – Select *Android Enterprise*.
    - **Profile type** – Select the device profile types that the app configuration profile applies to.
    - **Targeted app** – Select the **Select app** link. In the **Associated app** dialog box, select the Warehouse Management app in the list, and then select **OK** to apply the setting and close the dialog box.
1. Select **Next** to continue.
1. On the **Settings** tab, in the **Permissions** section, select **Add**.
1. In the **Add permissions** dialog box, select the checkboxes for **Camera**, **External storage (read)**, and **External storage (write)**. Then select **OK** to close the dialog box and add those permissions to the **Settings** tab.
1. In the **Permission state** field for each permission that you just added, select *Auto grant*.
1. In the **Configuration Settings** section, in the **Configuration settings format** field, select *Use configuration designer*.
1. In the **Configuration Settings** section, select **Add**.
1. In the dialog box, select the checkbox for **ConnectionsJson**. Then select **OK** to close the dialog box.
1. A new row is added to the grid in the **Configuration Settings** section of the **Settings** tab. The **Configuration key** field is set to *ConnectionsJason*. In the **Value type** field, select *String*. Then, in the **Configuration value** field, paste the entire contents of the JSON file that you created in the [Create a connection JSON file](#create-a-connection-json-file) section.
1. Select **Next** to continue.
1. On the **Assignments** tab, add the user groups and/or devices that the configuration policy should apply to. For information about how to use the settings, see [Add app configuration policies for managed Android Enterprise devices](/mem/intune/apps/app-configuration-policies-use-android).
1. When you've finished, select **Next** to continue.
1. On the **Review + save** tab, review your settings. If they look correct, select **Create** to save them.

### Set up Intune to support managed configuration for Windows devices

Follow these steps to set up Intune to support managed configuration for Windows devices.

1. Sign in to the Microsoft Endpoint Manager admin center.
1. Go to **Devices \> Windows**.
1. On the **Windows devices** page, on the **Configuration profiles** tab, on the toolbar, select **Create profile**.
1. In the **Create a profile** dialog box, set the following fields:
    - **Platform** – Select *Windows 10 and later*.
    - **Profile type** – Select *Templates*.
    - **Template name** – Select *Custom*.
1. Select **Create** to apply your settings and close the dialog box.
1. On the **Custom** page, on the **Basics** tab, enter a name for the configuration profile, and then select **Next** to continue.
1. On the **Configuration settings** tab, select **Add**.
1. In the **Add Row** dialog box, set the following fields:
    - **Name** – Enter a name for the new row.
    - **Description** – Enter a short description for the new row.
    - **OMA-URI** – Enter the following value:<br/>*./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/Microsoft.WarehouseManagement\_8wekyb3d8bbwe/AppSettingPolicy/ConnectionsJson*
    - **Data type** – Select *String*.
    - **Configuration value** – Paste the entire contents of the JSON file that you created in the [Create a connection JSON file](#create-a-connection-json-file) section.
1. Select **Save** to apply your settings and close the dialog box.
1. Select **Next** to continue.
1. On the **Assignments** tab, add the user groups and/or devices that the configuration profile should apply to.
1. When you've finished, select **Next** to continue.
1. On the **Applicability rules** tab, you can limit the set of devices that the configuration profile applies to. To apply the profile to all qualifying Windows devices, leave the fields blank. For more information about how to use the settings, see [Create a device profile in Microsoft Intune](/mem/intune/configuration/device-profile-create#applicability-rules).
1. When you've finished, select **Next** to continue.
1. On the **Review + save** tab, review your settings. If they look correct, select **Create** to save them.

### Set up Intune to support managed configuration for iOS devices

Follow these steps to set up Intune to support managed configuration for iOS devices.

1. Sign in to the Microsoft Endpoint Manager admin center.
1. Go to **Apps \> App Configuration policies**.
1. On the **App configuration policies** page, on the toolbar, select **Add \> Managed devices**.
1. On the **Create app configuration policy** page, on the **Basics** tab, set the following fields:
    - **Name** – Enter a name for the app configuration profile.
    - **Platform** – Select *iOS/iPadOS*.
    - **Profile type** – Select the device profile types that the profile applies to.
    - **Targeted app** – Select the **Select app** link. In the **Associated app** dialog box, select the Warehouse Management app in the list, and then select **OK** to apply the setting and close the dialog box.
1. Select **Next** to continue.
1. On the **Settings** tab, in the **Configuration settings format** field, select *Use configuration designer*.
1. In the grid at the bottom of the page, set the following fields for the first row:
    - **Configuration key** – Enter *ConnectionsJson*.
    - **Value type** – Select *String*.
    - **Configuration value** – Paste the entire contents of the JSON file that you created in the [Create a connection JSON file](#create-a-connection-json-file) section.
1. Select **Next** to continue.
1. On the **Assignments** tab, add the user groups and/or devices that the configuration policy should apply to. For information about how to use the settings, see [Add app configuration policies for managed iOS/iPadOS devices](/mem/intune/apps/app-configuration-policies-use-ios).
1. When you've finished, select **Next** to continue.
1. On the **Review + save** tab, review your settings. If they look correct, select **Create** to save them.

## Set up certificate-based authentication

CBA is widely used for secure and efficient authentication. In mass deployment scenarios, it's advantageous because of the secure access that it provides and the simplicity of deploying certificates to end devices. Therefore, it helps reduce the risk of security breaches, which can be a significant concern in large-scale deployments.

To use the Warehouse Management mobile app, you must have a certificate stored on each device. If you're using Intune to manage your devices, see [Use certificates for authentication in Microsoft Intune](/mem/intune/protect/certificates-configure) for instructions and more information.

The goal is to transfer, to each of your target devices, a personal information exchange (PFX) certificate that has the thumbprint that's specified in the ConnectionsJson file. To achieve this goal, the solution uses an imported public-key cryptography standards (PKCS) certificate configuration profile, which enables the same certificate to be delivered across devices.

### Create and import a certificate

The following subsections guide you through the process of creating the required certificate, setting up the required tools, and importing the certificate into the Certificate Connector for Microsoft Intune.

#### Create a self-signed PFX certificate

Obtain a self-signed PFX certificate (.pfx file) either through the Windows Server Certificate Authority (see [Install the Certification Authority](/windows-server/networking/core-network-guide/cncg/server-certs/install-the-certification-authority)) or by using PowerShell (see [New-SelfSignedCertificate](/powershell/module/pki/new-selfsignedcertificate)). Regardless of the source, when you export the certificate, be sure to include the private key and protect it through a password.

#### Create an app registration for PFXImport PowerShell in Azure AD

Follow these steps to create an app registration for PFXImport PowerShell in Azure AD.

1. Sign in to Azure.
1. From the **Home** page, go to **Manage Azure Active Directory**.
1. In the navigation pane, select **App registrations**.
1. On the toolbar, select **New registration**.
1. On the **Register an application** page, set the following fields:
    - **Name** – Enter a name.
    - **Supported account types** – Specify who can use the new application.
    - **Redirect URI** – Leave this field blank for now.
1. Select **Register**.
1. The new app registration is opened. On the **Certificates & secrets** tab, on the **Client secrets** tab, select **New client secret**.
1. In the **Add a client secret** dialog box, select an expiration date that meets your needs, and then select **Add**.
1. The **Certificates & secrets** tab now shows details about the new client secret. These details will be shown only once and will be hidden when the is page reloaded. Therefore, you must copy them now. Copy the **Value** value, and paste it into a text file. You'll need this value later, when you [set up your Certificate Connector machine](#set-up-a-dedicated-machine-for-the-certificate-connector).
1. On the **Authentication** tab, select **Add a platform**.
1. In the **Configure platforms** dialog box, select the **Mobile and desktop applications** tile.
1. In the **Configure Desktop + devices** dialog box, select the checkbox for each redirect URL that you want to use. (You can probably select all of them.) Then select **Configure**.
1. On the **Overview** tab, copy the **Application (client) ID** and **Directory (tenant) ID** values, and paste them into the text file where you previously pasted the client secret value. You'll need all three of these values later, when you [set up your Certificate Connector machine](#set-up-a-dedicated-machine-for-the-certificate-connector).

#### Download and build the PFXImport project

The PFXImport project consists of PowerShell cmdlets that will help you import PFX certificates into Intune. You can modify and adapt these cmdlets to fit your workflow. For more information, see [S/MIME overview to sign and encrypt email in Intune](/mem/intune/protect/certificates-s-mime-encryption-sign).

Follow these steps to download and build the PFXImport project.

1. Go to the [PFXImport PowerShell Project on GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell), and download the project.
1. Open Visual Studio 2022, and open the *PFXImportPS.sln* file that you downloaded from GitHub. Switch to *Release* mode, and build (or rebuild) the project. For more information, see [Configure and use imported PKCS certificates with Intune](/mem/intune/protect/certificates-imported-pfx-configure).

    [<img src="media/intune-vs-rebuild.png" alt="Changing to Release mode and building the project in Visual Studio." title="Changing to Release mode and building the project in Visual Studio" width="720" />](media/intune-vs-rebuild.png#lightbox)

#### Set up a dedicated machine for the Certificate Connector

Follow these steps to set up your dedicated Certificate Connector machine.

1. Sign in to the machine that you've designated to run the Certificate Connector for Microsoft Intune.
1. Copy the self-signed PFX certificate that you created in the [Create a self-signed PFX certificate](#create-a-self-signed-pfx-certificate) section to the Certificate Connector machine.
1. Copy the PFXImport project binaries that you built in the [Download and build the PFXImport project](#download-and-build-the-pfximport-project) section to the Certificate Connector machine, and save them in the following folder:

    *~\\Intune-Resource-Access-develop\\src\\PFXImportPowershell\\PFXImportPS\\bin\\Release*

1. In the *Release* folder, open the *IntunePfxImport.psd1* file, and edit the values of the following variables:

    - **ClientId** – Set the value to the client ID from the Azure app registration.
    - **ClientSecret** – Set the value to the client secret from the Azure app registration.
    - **TenantId** – Set the value to the tenant ID from the Azure app registration. This variable is required if you use a client secret.

    [<img src="media/intune-enter-client-secret.png" alt="Entering connection details in the IntunePfxImport.psd1 file." title="Entering connection details in the IntunePfxImport.psd1 file" width="720" />](media/intune-enter-client-secret.png#lightbox)

1. Sign in to the Microsoft Endpoint Manager admin center.
1. Go to **Tenant administration \> Connectors and tokens**.
1. On the **Certificate connectors** tab, on the toolbar, select **Add**.
1. In the **Install the certificate connector** dialog box, select the certificate connector link to download the *IntuneCertificateConnector.exe* file. This file is an installer for the Certificate Connector.
1. Transfer the *IntuneCertificateConnector.exe* file to the designated Certificate Connector machine. Then run the file, and follow the on-screen instructions. During the installation process, be sure to select the **PKCS imported certificates** checkbox.
1. Sign in to your Azure AD account as an admin user. If the Certificate Connector was successfully installed, there will be a green check mark on the **Endpoint Manager** page. For more information, see [Install the Certificate Connector for Microsoft Intune](/mem/intune/protect/certificate-connector-install).

#### Import your PFX certificate into the Certificate Connector

Follow these steps to import your PFX certificate on the Certificate Connector machine, so that the certificates can be distributed to users.

1. Sign in to the machine that you've designated to run the Certificate Connector for Microsoft Intune.
1. Run PowerShell Terminal as an administrator.
1. In the terminal, navigate to the *PFXImportPowershell* release folder, which should be at the following path:

    *~\\Intune-Resource-Access-develop\\src\\PFXImportPowershell\\PFXImportPS\\bin\\Release*

1. Run the following commands, in this order.

    1. `Import-Module .\\IntunePfxImport.psd1`
    1. `Set-IntuneAuthenticationToken -AdminUserName "<AdminUserName>"`
    1. `Add-IntuneKspKey -ProviderName "Microsoft Software Key Storage Provider" -KeyName "PFXEncryptionKey"`
    1. `$SecureFilePassword = ConvertTo-SecureString -String "<PFXCertificatePassword>" -AsPlainText -Force`
    1. `$UserPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<PFXCertificatePathAndFile>" $SecureFilePassword "<EndUserName>" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption"`
    1. `Import-IntuneUserPfxCertificate -CertificateList $UserPFXObject`

    Here is an explanation of the placeholders in the commands:

    - *&lt;AdminUserName&gt;* – The user name of the administrator user (typically, an email address).
    - *&lt;PFXCertificatePassword&gt;* – The password of the PFX file.
    - *&lt;PFXCertificatePathAndFile&gt;* – The full folder path (including the drive letter) and file name of the PFX file.
    - *&lt;EndUserName&gt;* – The user name of the user that the system will deliver the certificate to (typically, an email address).

    To deliver the certificate to more users, repeat the fifth and sixth commands for each additional user, and include the user's sign-in information.

1. Run the following command to validate the result.

    `Get-IntuneUserPfxCertificate -UserList "<EndUserName>"`

For more information, go to the [PFXImport PowerShell Project on GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

To troubleshoot this setup, follow these steps to use the Windows Event Viewer to review the CertificateConnectors logs.

1. Open the Windows **Start** menu, enter *Event Viewer* in the search form, and select the **Event Viewer** app in the result list.
1. Select the following item in the Event Viewer navigation panel: **Applications and Services Logs \> Microsoft \> Intune \> CertificateConnectors \> Operational**.
1. Review the events shown. Select an event to see more information about it.

[<img src="media/intune-event-viewer-log.png" alt="Reviewing the CertificateConnectors log in Event Viewer." title="Reviewing the CertificateConnectors log in Event Viewer" width="720" />](media/intune-event-viewer-log.png#lightbox)

### Create configuration profiles to push certificates to end devices

Configuration profiles enable Microsoft Endpoint Manager to push certificates and other settings to devices in your organization. (For more information, see [Create a device profile in Microsoft Intune](/mem/intune/configuration/device-profile-create).)

> [!IMPORTANT]
> Unfortunately, the Warehouse Management mobile app for iOS can't currently accept certificates that are delivered through Intune. Therefore, you must manually transfer certificates to iOS devices (for example, through [iCloud](https://www.icloud.com/iclouddrive/)) and then [import them by using the Warehouse Management app](/dynamics365/supply-chain/warehousing/install-configure-warehouse-management-app#import-the-connection-settings). If you support only iOS devices, you can skip the following procedure.

Follow these steps to create a configuration profile for each mobile platform that you'll support. (The process is nearly the same across all platforms.)

1. Sign in to the Microsoft Endpoint Manager admin center.
1. In the navigation, select **Devices**, and then select the platform to set up (**Windows**, **iOS/iPadOS**, or **Android**).
1. On the **Configuration profiles** tab, on the toolbar, select **Create profile**.
1. In the **Create a profile** dialog box, the required settings depend on the platform that you selected.
    - **Windows** – Set the **Platform** field to *Windows 10 and later*, set the **Profile type** field to *Templates*, and then select the template that's named *PKCS imported certificate*.
    - **iOS/iPadOS** – Set the **Profile type** field to *Templates*, and then select the template that's named *PKCS imported certificate*.
    - **Android** – Set the **Platform** field to *Android Enterprise*, and set the **Profile type** field to *PKCS imported certificate*.
1. Select **Create** to create the profile and close the dialog box.
1. On the **PKCS import certificate** page, on the **Basics** tab, enter a name and description for the certificate.
1. Select **Next** to continue.
1. On the **Configuration settings** tab, set the following fields:
    - **Intended purpose** – Select *S/MIME Encryption*.
    - **Key storage provider (KSP)** – If you're creating a profile for the Windows platform, select *Enroll to Software KSP*. This setting isn't available for other platforms.
1. Select **Next** to continue.
1. On the **Assignments** tab, select the user groups and/or devices that the current profile should apply to.
1. When you've finished, select **Next** to continue.
1. On the **Review + save** tab, review your settings. If they look correct, select **Create** to create the certificate.

### Verify that certificates have been distributed

After your certificate system is fully configured, and you've created the required configuration profiles, you can review how your profiles are performing and verify that the certificates are being distributed as expected. Follow these steps to monitor the performance of your configuration profiles in the Microsoft Endpoint Manager admin center.

1. Sign in to the Microsoft Endpoint Manager admin center.
1. Go to **Devices \> Configuration profiles**.
1. On the **Configuration profiles** page, select the profile to verify.
1. Details for your selected profile are opened. From here, you can get an overview of how many devices have already received certificates, whether any errors have occurred, and other details.

Another way to verify that your certificates are being correctly distributed is to inspect the end devices. You can check the certificates by following one of these steps, depending on the type of device:

- **For Android devices:** You can install an app such as *My certificates* to view installed certificates. To access certificates that are distributed from Intune, the *My certificates* app itself must also be installed by Intune and must use the same work profile.
- **For Windows devices:** Open the Windows **Start** menu, enter *Manage user certificates* in the search form and select **Manage user certificates** in the result list to open the certificate manager. In the certificate manager, expand **Certificates - Current User \> Personal \> Certificates** in the navigation pane to view your certificates and confirm whether the expected certificate has arrived.

[<img src="media/intune-console-certificates.png" alt="Managing user certificates in Windows." title="Managing user certificates in Windows" width="720" />](media/intune-console-certificates.png#lightbox)

## Enroll devices with Intune

Each device that you want to manage by using Intune must be *enrolled* with the system. Enrollment involves registering with Intune and applying organizational policies for security. The Company Portal app is accessible on multiple devices and can be used to enroll devices, depending on the type of device and the platform. The enrollment programs provide access to work or school resources.

### Android and iOS devices

To enroll an Android or iOS device, install the [Intune Company Portal app](/mem/intune/user-help/sign-in-to-the-company-portal) on it. The local user must then sign in to the Company Portal app by using their company account.

### Windows devices

There are several ways to enroll a Windows device. For example, you can install the [Intune Company Portal app](/mem/intune/user-help/sign-in-to-the-company-portal) on it. For information about how to set up the Company Portal app and how to use the other options that are available, see [Enroll Windows 10/11 devices in Intune](/mem/intune/user-help/enroll-windows-10-device).
