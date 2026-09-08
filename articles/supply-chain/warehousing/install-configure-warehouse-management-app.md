---
title: Install the Warehouse Management mobile app
description: Learn how to install the Warehouse Management mobile app on each of your mobile devices and configure it to connect to your environment.
author: pefreita
ms.author: pefreita
ms.topic: how-to
ms.date: 09/07/2026
ms.reviewer: kamaybac
ms.search.form: SysAADClientTable, WHSMobileAppField, WHSMobileAppFieldPriority, WHSRFMenu, WHSRFMenuItem, WHSWorker
ms.custom:
  - bap-template
  - sfi-ropc-nochange
---

# Install the Warehouse Management mobile app

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to download and install the Warehouse Management mobile app on each of your mobile devices, and how to configure the app to connect to your Microsoft Dynamics 365 Supply Chain Management environment. You can configure each device manually, or you can distribute connection settings through your mobile device management (MDM) provider, a file, or a QR code. To compare those options, see [Choose how to distribute connection settings](#distribute).

The Warehouse Management mobile app is only for your internal business use. You may not republish or distribute the Warehouse Management mobile app externally in any app store or similar distribution service.

## Operating system requirements

The Warehouse Management mobile app is available for Microsoft Windows, Google Android, and Apple iOS operating systems. To use the app, your mobile devices must have one of the following operating systems installed:

- Windows 10 May 2020 update 1904.1 or later
- Android 7.0 or later
- iOS 13.0 or later

## Get the Warehouse Management mobile app

For smaller deployments, you'll typically install the app on each device from the relevant store. Then, manually configure the connection to the environments that you're using.

For larger deployments, automate app deployment and configuration. This approach is more convenient if you manage many devices. For example, use a mobile device management and mobile application management solution such as [Microsoft Intune](/mem/intune/fundamentals/what-is-intune). For information about how to mass deploy installations and updates for the Warehouse Management mobile app, see [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md).

### Install the app from an app store

The easiest way to install the app on a single device is to install it from an app store. The store always provides the latest generally available version. Microsoft Intune can also fetch apps from the app stores. Use one of the following links to install the app from an app store:

- **Windows:** [Warehouse Management on Microsoft Store](https://www.microsoft.com/store/apps/9pd35cdqcmg3)
- **Android:** [Warehouse Management on Google Play Store](https://play.google.com/store/apps/details?id=com.Microsoft.WarehouseManagement)
- **iOS:** [Warehouse Management on the Apple App Store](https://apps.apple.com/app/microsoft-warehouse-management/id6444014310)

### Download the app from Microsoft App Center

Instead of installing the app from an app store, you can download it from the Microsoft App Center. The App Center provides installable packages that you can sideload. In addition to the current version, the App Center also lets you download previous versions and might provide preview versions with upcoming features that you can try out. To download current, previous, or preview versions of the Warehouse Management mobile app from Microsoft App Center, use one of the following links:

- **Windows:** [Warehouse Management (Windows)](https://aka.ms/wma-windows-official-release)

    For instructions about how to install a downloaded package on a Windows device and then set up the required certificates, see [Install a Build from App Center](/appcenter/distribution/installation).

- **Android:** [Warehouse Management (Android)](https://aka.ms/wma-android-official-release)

    A few extra steps might be required to install it. For details, see [Testing Android Apps](/appcenter/distribution/testers/testing-android).

- **Android (ARMv7 / armeabi-v7a):** [Warehouse Management (Android armeabi-v7a)](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/warehouse-management-android-armeabi-v7a/distribution_groups/preview%20program)

    This release targets older Android devices that use 32-bit ARMv7 processors and require a build compiled for the `armeabi-v7a` ABI. Install this package on devices that can't run the standard 64-bit Android release.

- **iOS:** The iOS version of the app is only available through App Store.

For information about how to install a build downloaded from the App Center, see [Install a build](/appcenter/distribution/installation).

The Warehouse Management mobile app isn't available in app stores in China. However, you can download it from Microsoft App Center and use it along with Dynamics 365 Supply Chain Management operated by 21Vianet in China.

<a name="authenticate"></a>

## Decide which authentication methods you'll use

Because the Warehouse Management mobile app has read and write access to some of your Supply Chain Management data, each device must authenticate with Supply Chain Management. The app supports several authentication methods. Before you start to deploy the app, learn about the available authentication methods and decide which one you want to use.

After a device authenticates with Supply Chain Management, each worker who uses that device signs in by using their Supply Chain Management worker account. The app loads the worker's personal preferences, such as their default warehouse and app preferences. Therefore, different workers can sign in and out for each shift, while the device itself remains authenticated with Supply Chain Management.

For details about each authentication method and how to set it up, see [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md).

> [!IMPORTANT]
> Use [username/password authentication](warehouse-app-authenticate-user-based.md#usernamePasswordFlow) for all new and existing deployments. It works without any configuration, and no companion app is required. [Device code flow](warehouse-app-authenticate-user-based.md#deviceCodeFlow) remains available for existing deployments, but Microsoft no longer recommends it.

If a device is lost or compromised, see [Remove access for a device that uses user-based authentication](warehouse-app-authenticate-user-based.md#revoke).

> [!NOTE]
> [Shared Device Mode](/entra/identity-platform/msal-shared-devices) authentication isn't currently supported for the Warehouse Management mobile app.

<a name="distribute"></a>

## Choose how to distribute connection settings

Every device needs the same connection settings, expressed in JavaScript Object Notation (JSON) format. What differs is how you deliver that JSON to each device. To find your method, ask yourself the following questions:

1. **Do you use a mobile device management (MDM) provider, such as Microsoft Intune?** If you do, use *MDM managed configuration*. It's the only method that requires no setup work on the device itself, and it works on all three platforms.
1. **No MDM provider?** Use a *QR code*. It also works on all three platforms, and it's the practical choice for Android and iOS devices, which restrict file access.
1. **Do you deploy to Windows devices and already push files or run scripts on them?** You can use a *JSON file* instead.
1. **Are you setting up a single device or troubleshooting one?** Enter the settings with *manual input*.

| Method | When to use it | Platform support | Work required on each device |
|---|---|---|---|
| [MDM managed configuration](warehouse-app-intune-user-based.md) (`ConnectionsJson` key) | You manage devices with an MDM provider. The provider pushes connection settings through app configuration policies, without touching the device file system. | Android, iOS, Windows | None |
| [QR code](warehouse-app-qr-code.md) | You don't use an MDM provider, or you set up devices individually. The app scans a QR code that contains the connection JSON. | Android, iOS, Windows | Scan a code |
| [JSON file](warehouse-app-connection-settings.md#file-name-location) (*connections.json*) | You can place files on the device file system. | Windows; Android only through **Add from file** (see the following note) | None, if you use the default file name and location |
| [Manual input](#config-manually) | You're setting up a single device or troubleshooting a connection. | Android, iOS, Windows | Type each setting |

> [!IMPORTANT]
> **Android limitation:** Starting with Android 11, [scoped storage](https://developer.android.com/about/versions/11/privacy/storage) prevents external tools (MDM file push, file managers, and USB transfer) from writing to the app's private folder. Therefore, a *connections.json* file can't be delivered to the [default path](warehouse-app-connection-settings.md#file-name-location) on Android.
>
> On Android, use *MDM managed configuration* or a *QR code* instead. To import a file on a single device, use the app's **Add from file** option, and select a JSON file from an accessible location, such as the downloads folder.

<a name="connection-file-qr"></a>

## Create a connection settings file or QR code

All the methods except manual input use the same JSON. For the parameters that you can specify, an example file, and the file name and location rules, see [Connection settings reference for the Warehouse Management mobile app](warehouse-app-connection-settings.md).

After you create the settings, import them on the device as described in the next section.

<a name="config"></a>

## Import the connection settings on a device

Follow these steps to import connection settings from a file or a QR code.

1. Start the Warehouse Management mobile app on your mobile device. The first time that you start the app, a welcome message appears. Select **Connect**.
1. If you're importing the connection settings from a file and you used the default name and location when you saved the file, the app might find the file automatically. In this case, skip ahead to step 4. Otherwise, select **Set up connection**, and then continue to step 3.
1. In the **Connection setup** dialog, select **Add from file** or **Add from QR code**, depending on how you want to import the settings:

    - If you're importing the connection settings from a file, select **Add from file**, browse to the file on your local device, and select it. If you select a custom location, the app stores it and automatically uses it the next time.
    - If you're importing the connection settings by scanning a QR code, select **Add from QR code**. The app prompts you for permission to use the device's camera. After you give permission, the camera starts, so that you can use it for scanning. Depending on the quality of the device's camera and the complexity of the QR code, you might find it difficult to get a correct scan. In that case, try to reduce the complexity of the QR code by generating only one connection per QR code. (Currently, you can use only the device's camera to scan the QR code.)

1. After the connection settings load successfully, the selected connection appears.
1. The app connects to your Supply Chain Management server and shows the sign-in page.

<a name="config-manually"></a>

## Manually configure the application

If you don't have a file or QR code, you can manually configure the app on the device so that it connects to the Supply Chain Management server through the Microsoft Entra ID application.

1. Start the Warehouse Management mobile app on your mobile device.
1. If the app starts in **Demo mode**, select **Connection settings**. If the **Sign-in** page appears when the app starts, select **Change connection**.
1. Select **Set up connection**.
1. Select **Input manually**. The **New Connection** page appears and shows the settings that you need to enter manually.
1. Enter the following information:

    - **Connection name** – Enter a name for the new connection. This name appears in the **Select connection** field the next time you open the connection settings. The name you enter must be unique. (In other words, it must differ from all other connection names that are stored on your device, if any other connection names are stored there.)
    - **Environment URL** – Specify the root URL of Supply Chain Management.

        > [!IMPORTANT]
        > - Don't end this value with a slash (/).
        > - Ensure that the HTTPS (SSL) certificate is valid.

    - **Company** – Enter the legal entity (company) in Supply Chain Management that you want the application to connect to.
    - **Authentication method** – Select one of the following values to specify the method that you use to authenticate with Supply Chain Management. The method that you select here must match the setup of the app in Azure.

        - *Username and password* (recommended) – Ask the worker to enter a user name and password. This option also supports [brokered authentication](warehouse-app-conditional-access-enable.md) and single sign-on, which are optional.
        - *Device code* (not recommended) – Authenticate by using the [device code flow](warehouse-app-authenticate-user-based.md#deviceCodeFlow). If a device is still configured this way, reconfigure it to use *Username and password*.

    - **Cloud** – Specify the type of Microsoft Entra ID app registration to authenticate with:

        - *Azure Global* (recommended) – Authenticate by using the global Microsoft Entra ID application that's registered and maintained by Microsoft. This option supports most scenarios, including [Microsoft Entra Conditional Access](warehouse-app-conditional-access-enable.md). You don't have to register or maintain your own Microsoft Entra ID app, and you don't have to enter a client ID or tenant.
        - *Manual* – Authenticate through your own [custom Microsoft Entra ID app registration](warehouse-app-custom-app-registration.md). Use this option only when the global application doesn't apply to your deployment because you connect to a Finance + Operations (on-premises) environment, you connect to a cloud other than Azure Global (such as a sovereign cloud), or you have specific requirements that the global application doesn't meet. If you choose this option, you must register and maintain a custom app in Microsoft Entra ID and specify a **Microsoft Entra ID client ID** value for the connection.

    - **Microsoft Entra ID client ID** – This field is available only when the **Cloud** field is set to *Manual*. Enter the client ID of your custom app registration. Learn more in [User-based authentication](warehouse-app-authenticate-user-based.md).
    - **Microsoft Entra ID tenant** – (Optional) This field is available only when the **Cloud** field is set to *Manual*. Enter the Microsoft Entra ID domain name that you're using with the Supply Chain Management server. This value has the form `https://login.windows.net/<your-Microsoft-Entra-ID-domain-name>`. Here's an example: `https://login.windows.net/contosooperations.onmicrosoft.com`. Learn more about how to find your Microsoft Entra ID domain name in [Locate important IDs for a user](/partner-center/find-ids-and-domain-names).

        > [!IMPORTANT]
        > Don't end this value with a slash (/).

    - **Use Broker** – This option applies only when the **Authentication method** field is set to *Username and password*. It determines whether a broker is used for [SSO](warehouse-app-authenticate-user-based.md#sso) authentication. Set this option to *Yes* for broker-based authentication and SSO. Set it to *No* to require manual input of a user name and password. Learn more about the broker that each platform requires in [Device requirements](warehouse-app-conditional-access-enable.md#device-requirements).
    - **Domain name** – This field applies only when the **Authentication method** field is set to *Username and password*. You can use it to make sign-in easier for workers. If you don't set this field, workers must enter their full Microsoft Entra ID user principal name to sign in. A user principal name has the form \<*user name*\>@\<*domain name*\>. If you specify the \<*domain name*\> part here, workers can sign in by entering only the \<*user name*\> part. (Nevertheless, workers can still enter their full user principal name.)

1. Select the **Save** button in the upper-right corner of the page.
1. The app connects to your Supply Chain Management server and shows the sign-in page.

<a name="revoke"></a>

## Remove access for a lost or compromised device

If a device is lost or compromised, remove its access to Supply Chain Management. The method you use to remove access depends on how the device is configured to authenticate with Supply Chain Management. For instructions, see [Remove access for a device that uses user-based authentication](warehouse-app-authenticate-user-based.md#revoke).

## Related information

- [Connection settings reference for the Warehouse Management mobile app](warehouse-app-connection-settings.md)
- [Warehouse Management mobile app release schedule](warehouse-app-control-updates.md)
- [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
- [Mobile device user settings](mobile-device-user-settings.md)
- [Assign step icons and titles for the Warehouse Management mobile app](step-icons-titles.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
