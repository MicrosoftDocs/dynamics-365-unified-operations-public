---
title: Mass deploy the mobile app with user-based authentication
description: Learn how to mass deploy the Warehouse Management app with user-based authentication by using a mobile device management (MDM) solution such as Microsoft Intune.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 02/20/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Mass deploy the mobile app with user-based authentication

[!include [banner](../includes/banner.md)]

Automated deployment and configuration of Warehouse Management can be more efficient than manual deployment when you have many devices to manage. One way to achieve this automation is to use a mobile device management (MDM) solution such as [Microsoft Intune](/mem/intune/fundamentals/what-is-intune). For general information about how to use Intune to add apps, see [Add apps to Microsoft Intune](/mem/intune/apps/apps-add).

This article explains how to mass deploy the Warehouse Management mobile app with user-based authentication by using Microsoft Intune.

> [!IMPORTANT]
> To use mobile mass deployment (MDM), you must configure the Warehouse Management mobile app to use [username/password authentication](warehouse-app-authenticate-user-based.md#usernamePasswordFlow) with [single sign-on](warehouse-app-authenticate-user-based.md#sso). This is because it isn't possible to distribute authentication tokens to mobile devices using MDM.

## Prerequisites

To use an MDM solution to deploy the Warehouse Management mobile app and the related authentication certificates, you must have the following resources available:

- Warehouse Management mobile app version 2.0.41.0 or later (This version number applies to all mobile platforms.)
- A valid store account for each mobile platform that you'll support ([Microsoft account](https://account.microsoft.com/account/), [Google Account](https://www.google.com/account/about/), and/or [Apple ID](https://appleid.apple.com/sign-in))
- [Microsoft Entra ID](https://portal.azure.com/#view/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/~/Overview) (Microsoft Entra ID Premium P2 license)
- [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com/#home) (the Intune website)

## Authenticating with or without single sign-on after mass deployment

You can set up user-based authentication for the Warehouse Management mobile app either with or without single sign-on.

- **Without single sign-on** – If you choose to use device code flow authentication, or username/password authentication without single sign-on, then you (or a worker) must authenticate the Warehouse Management mobile app on each device after deploying with MDM.
- **With single sign-on** – If you use username/password authentication with single sign-on, the Warehouse Management mobile app can authenticate by using an existing authentication token on each device, provided that the Microsoft Entra ID account that is required to authenticate the Warehouse Management mobile app is already signed in for another application on the device (such as Microsoft Teams, Company Portal, or Outlook). In this case, no additional authentication might be needed for the device. However, depending on how you configured your Microsoft Entra ID and work user accounts, workers might still have to sign in by using their warehouse app user account. (Learn more in [Scenarios for managing devices, Microsoft Entra ID users, and mobile device users](warehouse-app-authenticate-user-based.md#scenarios).)

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

The following subsections provide examples that show how to set up Intune to provide managed configuration for each of the supported mobile platforms. Learn more in [App configuration policies for Microsoft Intune](/mem/intune/apps/app-configuration-policies-overview).

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
    - **OMA-URI** – Enter the following value:

        ```txt
        ./User/Vendor/MSFT/EnterpriseModernAppManagement/AppManagement/AppStore/Microsoft.WarehouseManagement_8wekyb3d8bbwe/AppSettingPolicy/ConnectionsJson
        ```

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

## Enroll devices with Intune

Each device that you want to manage by using Intune must be *enrolled* with the system. Enrollment involves registering with Intune and applying organizational policies for security. The Company Portal app is accessible on multiple devices and can be used to enroll devices, depending on the type of device and the platform. The enrollment programs provide access to work or school resources.

### Android and iOS devices

To enroll an Android or iOS device, install the [Intune Company Portal app](/mem/intune/user-help/sign-in-to-the-company-portal) on it. The local user must then sign in to the Company Portal app by using their company account.

### Windows devices

There are several ways to enroll a Windows device. For example, you can install the [Intune Company Portal app](/mem/intune/user-help/sign-in-to-the-company-portal) on it. For information about how to set up the Company Portal app and how to use the other options that are available, see [Enroll Windows 10/11 devices in Intune](/mem/intune/user-help/enroll-windows-10-device).

## Related information

- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
- [Mass deploy the mobile app with service-based authentications](warehouse-app-intune.md)
- [Service-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-service-based.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
