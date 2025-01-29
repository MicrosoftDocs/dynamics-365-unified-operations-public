---
title: Install the Warehouse Management mobile app
description: Learn how to install the Warehouse Management mobile app on each of your mobile devices and configure it to connect to your environment.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 05/27/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: SysAADClientTable, WHSMobileAppField, WHSMobileAppFieldPriority, WHSRFMenu, WHSRFMenuItem, WHSWorker
---

# Install the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

This article explains how to download and install the Warehouse Management mobile app on each of your mobile devices, and how to configure the app to connect to your Microsoft Dynamics 365 Supply Chain Management environment. You can configure each device manually, or you can import connection settings through a file or by scanning a QR code.

The Warehouse Management mobile app is only for your internal business use. You may not republish or distribute the Warehouse Management mobile app externally in any app store or similar distribution service.

## Prerequisites

### Operating system requirements

The Warehouse Management mobile app is available for Microsoft Windows, Google Android, and Apple iOS operating systems. To use the app, one of the following operating systems must be installed on your mobile devices:

- Windows 10 (Universal Windows Platform \[UWP\]) October 2018 update 1809 (build 10.0.17763) or later
- Android:
    - Warehouse Management mobile app version 3.x requires Android 5.0 or later
    - Warehouse Management mobile app version 4.x requires Android 7.0 or later
- iOS 13.0 or later

### External URLs required by the app

For the Warehouse Management mobile app to function correctly, your internal network must allow it to access the following external URLs:

- \*.microsoft.com
- \*.microsoftonline.com
- login.windows.net
- \*.appcenter.ms
- \*.ces.microsoftcloud.com
- \*.onyx.azure.net
- play.google.com
- itunes.apple.com
- \*.cdn-apple.com
- \*.networking.apple
- login.microsoftonline.com
- login.microsoft.com
- sts.windows.net
- login.partner.microsoftonline.cn
- login.chinacloudapi.cn
- login.microsoftonline.us
- login-us.microsoftonline.com
- \*.applicationinsights.azure.com
- \*.applicationinsights.azure.us
- \*.applicationinsights.azure.cn

### Turn Warehouse Management mobile app features on or off in Supply Chain Management

To use the Warehouse Management mobile app, the *User settings, icons, and step titles for the new warehouse app* feature must be turned on for your system. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. 

## Get the Warehouse Management mobile app

For smaller deployments, you might typically install the app on each device from the relevant store and then manually configure the connection to the environments that you're using.

For larger deployments, you can automate app deployment and/or configuration, which can be more convenient if you manage many devices. For example, you might use a mobile device management and mobile application management solution such as [Microsoft Intune](/mem/intune/fundamentals/what-is-intune). For information about how to mass deploy installations and updates for the Warehouse Management mobile app, see [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md) or [Mass deploy the mobile app with service-based authentication](warehouse-app-intune.md) (depending on which type of authentication method you're using).

### Install the app from an app store

The easiest way to install the app on a single device is to install it from an app store, which always provides the latest generally available version. Microsoft Intune can also fetch apps from the app stores. Use one of the following links to install the app from an app store:

- **Windows (UWP):** [Warehouse Management on Microsoft Store](https://www.microsoft.com/store/apps/9pd35cdqcmg3)
- **Android:** [Warehouse Management on Google Play Store](https://play.google.com/store/apps/details?id=com.Microsoft.WarehouseManagement)
- **iOS:** [Warehouse Management on Apple App Store](https://apps.apple.com/app/microsoft-warehouse-management/id6444014310)

### Download the app from Microsoft App Center

As an alternative to installing from an app store, you can instead download the app from the Microsoft App Center. The App Center provides installable packages that you can sideload. In addition to the current version, the App Center also lets you download previous versions and might provide preview versions with upcoming features that you can try out. To download current, previous, or preview versions of the Warehouse Management mobile app from Microsoft App Center, use one of the following links:

- **Windows (UWP):** [Warehouse Management (Windows)](https://aka.ms/wma-windows-official-release)

    For instructions about how to install a downloaded package on a Windows device and then set up the required certificates, see [Install a Build from App Center](/appcenter/distribution/installation).

- **Android:** [Warehouse Management (Android)](https://aka.ms/wma-android-official-release)

    A few extra steps might be required to install it. For details, see [Testing Android Apps](/appcenter/distribution/testers/testing-android).

- **iOS:** The iOS version of the app is only available through App Store.

For information about how to install a build downloaded from the App Center, see [Install a build](/appcenter/distribution/installation).

The Warehouse Management mobile app isn't available in app stores in China. However, downloading it from Microsoft App Center and using it along with Dynamics 365 Supply Chain Management operated by 21Vianet in China is officially supported.

## <a name="authenticate"></a>Decide which authentication methods you'll use

Because the Warehouse Management mobile app has read/write access to some of your Supply Chain Management data, each device must be authenticated with Supply Chain Management. The app supports several authentication methods. Before you start to deploy the app, take the time to learn about the authentication methods that are available, and decide which one you want to use.

After a device is authenticated with Supply Chain Management, each worker who uses that device signs in by using their Supply Chain Management worker account. That worker's personal preferences (such as their default warehouse and app preferences) are then loaded. Therefore, different workers can sign in and out for each shift, while the device itself remains authenticated with Supply Chain Management.

For details about each authentication method and how to set it up, see the following articles:

- User-based authentication: [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- Service-based authentication (deprecated): [Service-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-service-based.md)

> [!IMPORTANT]
> Service-based authentication methods (including certificates and shared secret) are now deprecated. We strongly recommend that you set up your mobile devices to use user-based authentication (device code flow) instead. For more information about this deprecation, including the deprecation schedule, see [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md).

If a device is lost or compromised, you can revoke its authentication by following the steps in one of the following articles, depending on which authentication method you're using:

- User-based authentication: [Remove access for a device that uses user-based authentication](warehouse-app-authenticate-user-based.md#revoke)
- Service-based authentication (deprecated): [Remove access for a device that authenticates by using a certificate or client secret](warehouse-app-authenticate-service-based.md#revoke)

## Configure the application by importing connection settings

To make it easier to maintain and deploy the application on many mobile devices, you can import the connection settings instead of manually entering them on each device. This section explains how to create and import the settings.

### <a name="connection-file-qr"></a>Create a connection settings file or QR code

You can import connection settings from either a file or a QR code. For both approaches, you must first create a settings file that uses JavaScript Object Notation (JSON) format and syntax. The file must include a connection list that contains the individual connections that have to be added. The following table summarizes the parameters that you must specify in the connection settings file.

| Parameter | Description |
|---|---|
| `"ConnectionName"` | Specify the name of the connection setting. The maximum length is 20 characters. Because this value is the unique identifier for a connection setting, make sure that it's unique in the list. If a connection that has the same name already exists on the device, it will be overridden by the settings from the imported file. |
| `"ActiveDirectoryClientAppId"` | <p>Don't include this parameter if you're using `"AuthCloud": "AzureGlobal"` (recommended).</p><p>Specify the client ID that you made a note of while you were setting up Microsoft Entra ID. (For more information, see one of the following articles, depending on the authentication method that you're using: [User-based authentication](warehouse-app-authenticate-user-based.md) or [Service-based authentication](warehouse-app-authenticate-service-based.md).)</p> |
| `"ActiveDirectoryResource"` | Specify the root URL of Supply Chain Management. |
| `"ActiveDirectoryTenant"` | <p>Don't include this parameter if you're using `"AuthCloud": "AzureGlobal"` (recommended).</p><p>Specify the Microsoft Entra ID domain name that you're using with the Supply Chain Management server. This value has the form `https://login.windows.net/<your-Microsoft-Entra-ID-domain-name>`. Here's an example: `https://login.windows.net/contosooperations.onmicrosoft.com`. For more information about how to find your Microsoft Entra ID domain name, see [Locate important IDs for a user](/partner-center/find-ids-and-domain-names).</p> |
| `"Company"` | Specify the legal entity in Supply Chain Management that you want the application to connect to. |
| `"ConnectionType"` | <p>(Optional) Specify whether the connection setting should use a certificate, a client secret, or a device code to connect to an environment. Valid values are [`"Certificate"`](warehouse-app-authenticate-service-based.md), [`"ClientSecret"`](warehouse-app-authenticate-service-based.md), [`"DeviceCode"`](warehouse-app-authenticate-user-based.md), and [`"UsernamePassword"`](warehouse-app-authenticate-user-based.md). The default value is `"DeviceCode"`.</p><p>**Note:** Client secrets can't be imported.</p> |
| `"IsEditable"` | (Optional) Specify whether the app user should be able to edit the connection setting. Valid values are `"true"` and `"false"`. The default value is `"true"`. |
| `"IsDefaultConnection"` | (Optional) Specify whether the connection is the default connection. A connection that's set as the default connection is automatically preselected when the app is opened. Only one connection can be set as the default connection. Valid values are `"true"` and `"false"`. The default value is `"false"`. |
| `"CertificateThumbprint"` | (Optional) For Windows devices, you can specify the certificate thumbprint for the connection. For Android devices, the app user must select the certificate the first time that a connection is used. |
| `"UseBroker"` | <p>(Optional) This parameter applies only to the `"UsernamePassword"` connection type. It determines whether a broker is used for [single sign-on (SSO)](warehouse-app-authenticate-user-based.md#sso) authentication. Set it to `"true"` for broker-based authentication. Set it to `"false"` to require manual input of a user name and password. It works with the following authentication systems:</p><ul><li>Intune Company Portal ([Android](/mem/intune/user-help/sign-in-to-the-company-portal) only)</li><li>Microsoft Authenticator ([Android](/mem/intune/user-help/sign-in-to-the-company-portal) and [iOS](/mem/intune/user-help/sign-in-to-the-company-portal))</li><li>[Integrated Windows authentication (IWA)](/entra/identity-platform/msal-authentication-flows#integrated-windows-authentication-iwa)</li></ul> |
| `"DomainName"` | (Optional) This parameter applies only to the `"UsernamePassword"` connection type. It allows you to implement a simplified sign-in process. If you don't set this field, workers must always enter their full Microsoft Entra ID user principal name (UPN) to sign in. A UPN has the form \<*user name*\>@\<*domain name*\>. If you specify the \<*domain name*\> part here, workers can sign in by entering only the \<*user name*\> part. (Even if you set the domain name here, workers can still sign in using their full UPN.) |
| `"AuthCloud"` | <p>Specify the type of Microsoft Entra ID app registration to authenticate with:</p><ul><li>`"AzureGlobal"` – Authenticate by using a global Microsoft Entra ID application that's registered and maintained by Microsoft (recommended). If you choose this option, you don't have to register or maintain your own Microsoft Entra ID app, and you shouldn't specify `"ActiveDirectoryTenant"` or `"ActiveDirectoryClientAppId"` values for this connection.</li><li>`"Manual"` – Authenticate through your own custom Microsoft Entra ID app registration. If you choose this option, you must [register and maintain a custom app in Microsoft Entra ID](warehouse-app-authenticate-user-based.md#create-service) and also specify `"ActiveDirectoryTenant"` and `"ActiveDirectoryClientAppId"` values for this connection.</li></ul> |

The following example shows a valid connection settings file that contains two connections. As you can see, the connection list (named `"ConnectionList"` in the file) is an object that has an array that stores each connection as an object. Each object must be enclosed in braces (\{\}) and separated by commas, and the array must be enclosed in brackets (\[\]).

```json
{
    "ConnectionList": [
        {
            "ConnectionName": "Connection1",
            "ActiveDirectoryResource": "https://yourenvironment1.cloudax.dynamics.com",
            "Company": "USMF",
            "IsEditable": true,
            "IsDefaultConnection": false,
            "ConnectionType": "DeviceCode",
            "AuthCloud": "AzureGlobal"
        },
        {
            "ActiveDirectoryClientAppId":"aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
            "ConnectionName": "Connection2",
            "ActiveDirectoryResource": "https://yourenvironment2.cloudax.dynamics.com",
            "ActiveDirectoryTenant": "https://login.windows.net/contosooperations.onmicrosoft.com",
            "Company": "USMF",
            "IsEditable": false,
            "IsDefaultConnection": true,
            "CertificateThumbprint": "aaaabbbbcccccdddddeeeeefffffggggghhhhiiiii",
            "ConnectionType": "Certificate",
            "AuthCloud": "Manual"
        },
        {
            "ActiveDirectoryClientAppId":"aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
            "ConnectionName": "Connection3",
            "ActiveDirectoryResource": "https://yourenvironment3.cloudax.dynamics.com",
            "ActiveDirectoryTenant": "https://login.windows.net/contosooperations.onmicrosoft.com",
            "Company": "USMF",
            "IsEditable": true,
            "IsDefaultConnection": false,
            "ConnectionType": "ClientSecret",
            "AuthCloud": "Manual"
        },
        {
            "ActiveDirectoryClientAppId":"aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
            "ConnectionName": "Connection4",
            "ActiveDirectoryResource": "https://yourenvironment4.cloudax.dynamics.com",
            "ActiveDirectoryTenant": "https://login.windows.net/contosooperations.onmicrosoft.com",
            "Company": "USMF",
            "IsEditable": true,
            "IsDefaultConnection": false,
            "ConnectionType": "DeviceCode",
            "AuthCloud": "Manual"
        },
        {
            "ActiveDirectoryClientAppId":"aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
            "ConnectionName": "Connection5",
            "ActiveDirectoryResource": "https://yourenvironment5.cloudax.dynamics.com",
            "ActiveDirectoryTenant": "https://login.windows.net/contosooperations.onmicrosoft.com",
            "Company": "USMF",
            "IsEditable": true,
            "IsDefaultConnection": false,
            "UseBroker": true,
            "ConnectionType": "UsernamePassword",
            "AuthCloud": "Manual"
        }
    ]
}
```

You can either save the information as a JSON file or generate a QR code that has the same content. If you save the information as a file, we recommend that you save it by using the default name, *connections.json*, especially if you'll store it in the default location on each mobile device.

### Save the connection settings file on each device

Typically, you'll use a device management tool or script to distribute the connection settings files to each device that you're managing. If you use the default name and location when you save the connection settings file on each device, the Warehouse Management mobile app will automatically import it, even during the first run after the app is installed. If you use a custom name or location for the file, the app user must specify the values during the first run. However, the app will continue to use the specified name and location afterward.

Every time that the app is started, it reimports the connection settings from their previous location to determine whether there have been any changes. The app will update only connections that have the same names as the connections in the connection settings file. User-created connections that use other names won't be updated.

You can't remove a connection by using the connection settings file.

As has been mentioned, the default file name is *connections.json*. The default file location depends on which type of device you're using:

- **Windows:** `C:\Users\<User>\AppData\Local\Packages\Microsoft.WarehouseManagement_8wekyb3d8bbwe\LocalState`
- **Android:** `Android\data\com.Microsoft.WarehouseManagement\files`
- **iOS:** File sharing isn't yet supported.

Usually, the paths are automatically created after the first run of the app. However, you can manually create them if you must transfer the connection settings file to the device before installation.

> [!NOTE]
> If the app is uninstalled, the default path and its contents are removed.

### <a name="config"></a>Import the connection settings

Follow these steps to import connection settings from a file or a QR code.

1. Start the Warehouse Management mobile app on your mobile device. The first time that you start the app, a welcome message is shown. Select **Select a connection**.
1. If you're importing the connection settings from a file, and the default name and location were used when the file was saved, the app might already have found the file. In this case, skip ahead to step 4. Otherwise, select **Set up connection**, and then continue to step 3.
1. In the **Connection setup** dialog box, select **Add from file** or **Add from QR code**, depending on how you want to import the settings:

    - If you're importing the connection settings from a file, select **Add from file**, browse to the file on your local device, and select it. If you select a custom location, the app will store it and automatically use it the next time.
    - If you're importing the connection settings by scanning a QR code, select **Add from QR code**. The app prompts you for permission to use the device's camera. After you give permission, the camera is started, so that you can use it for scanning. Depending on the quality of the device's camera and the complexity of the QR code, you might find it difficult to get a correct scan. In that case, try to reduce the complexity of the QR code by generating only one connection per QR code. (Currently, you can use only the device's camera to scan the QR code.)

1. When the connection settings are successfully loaded, the selected connection is shown.
1. Complete one of the following steps to select the authentication certificate, depending on which type of device that you're using.

    - If you're using an Android device and are using a certificate for authentication, the device prompts you to select the certificate.
    - If you're using an iOS device and are using a certificate for authentication, select **Edit connection settings** and then select **Select certificate**. On the page that opens, select **Select certificate** to open a file browser and select your certificate file. The app then shows a **Certificate is selected** confirmation. Enter the certificate password and select **Import certificate**. Finally, save the connection settings.

1. The app connects to your Supply Chain Management server and shows the sign-in page.

## <a name="config-manually"></a>Manually configure the application

If you don't have a file or QR code, you can manually configure the app on the device so that it connects to the Supply Chain Management server through the Microsoft Entra ID application.

1. Start the Warehouse Management mobile app on your mobile device.
1. If the app is started in **Demo mode**, select **Connection settings**. If the **Sign-in** page appears when the app is started, select **Change connection**.
1. Select **Set up connection**.
1. Select **Input manually**. The **New Connection** page appears and shows the settings that are required to manually enter the connection details.
1. Enter the following information:

    - **Connection name** – Enter a name for the new connection. This name will appear in the **Select connection** field the next time that you open the connection settings. The name that you enter must be unique. (In other words, it must differ from all other connection names that are stored on your device, if any other connection names are stored there.)
    - **Environment URL** – Specify the root URL of Supply Chain Management.

        > [!IMPORTANT]
        > - Don't end this value with a slash (/).
        > - Ensure that the HTTPS (SSL) certificate is valid.

    - **Company** – Enter the legal entity (company) in Supply Chain Management that you want the application to connect to.
    - **Authentication method** – Select one of the following values to specify the method that you use to authenticate with Supply Chain Management. The method that you select here must match the setup of the app in Azure.

        - *Device code* – Authenticate by using the device code flow. This method is a [user-based authentication method](warehouse-app-authenticate-user-based.md).
        - *Username and password* – Authenticate by using SSO or by asking the user to enter a user name and password. This method is a [user-based authentication method](warehouse-app-authenticate-user-based.md).
        - *Client secret (Deprecated)* – Authenticate by using a client secret. This method is a [service-based authentication method](warehouse-app-authenticate-service-based.md).
        - *Certificate (Deprecated)* – Authenticate by using a certificate. This method is a [service-based authentication method](warehouse-app-authenticate-service-based.md).

    - **Cloud** – Specify the type of Microsoft Entra ID app registration to authenticate with:

        - *Azure Global* – Authenticate by using the global Microsoft Entra ID application that's registered and maintained by Microsoft (recommended).
        - *Manual* – Authenticate through your own [custom Microsoft Entra ID app registration](warehouse-app-authenticate-user-based.md#create-service).

    - **Microsoft Entra ID client ID** – This field is available only when the **Cloud** field is set to *Manual*. Enter the client ID that you made a note of while you were setting up Microsoft Entra ID. (For more information, see one of the following articles, depending on the authentication method that you're using: [User-based authentication](warehouse-app-authenticate-user-based.md) or [Service-based authentication](warehouse-app-authenticate-service-based.md).)
    - **Microsoft Entra ID tenant** – This field is available only when the **Cloud** field is set to *Manual*. Enter the Microsoft Entra ID domain name that you're using with the Supply Chain Management server. This value has the form `https://login.windows.net/<your-Microsoft-Entra-ID-domain-name>`. Here's an example: `https://login.windows.net/contosooperations.onmicrosoft.com`. For more information about how to find your Microsoft Entra ID domain name, see [Locate important IDs for a user](/partner-center/find-ids-and-domain-names).

        > [!IMPORTANT]
        > Don't end this value with a slash (/).

    - **Microsoft Entra ID client secret** – This field is available only when the **Authentication method** field is set to *Client secret (Deprecated)*. Enter the client secret that you made a note of while you were setting up Microsoft Entra ID. (For more information, see one of the following articles, depending on the authentication method that you're using: [User-based authentication](warehouse-app-authenticate-user-based.md) or [Service-based authentication](warehouse-app-authenticate-service-based.md).)
    - **Certificate thumbprint** – This field is available only for Windows devices, and only when the **Authentication method** field is set to *Certificate (Deprecated)*. Enter the certificate thumbprint that you made a note of while you were setting up Microsoft Entra ID. (For more information, see one of the following articles, depending on the authentication method that you're using: [User-based authentication](warehouse-app-authenticate-user-based.md) or [Service-based authentication](warehouse-app-authenticate-service-based.md).)
    - **Use Broker** – This option applies only when the **Authentication method** field is set to *Username and password*. It determines whether a broker is used for [SSO](warehouse-app-authenticate-user-based.md#sso) authentication with Intune Company Portal ([Android](/mem/intune/user-help/sign-in-to-the-company-portal) only) or Microsoft Authenticator ([Android](/mem/intune/user-help/sign-in-to-the-company-portal) and [iOS](/mem/intune/user-help/sign-in-to-the-company-portal)). Set this option to *Yes* for broker-based authentication and SSO. Set it to *No* to require manual input of a user name and password.
    - **Domain name** – This field applies only when the **Authentication method** field is set to *Username and password*. You can use it to make sign-in easier for workers. If you don't set this field, workers must enter their full Microsoft Entra ID user principal name to sign in. A user principal name has the form \<*user name*\>@\<*domain name*\>. If you specify the \<*domain name*\> part here, workers can sign in by entering only the \<*user name*\> part. (Nevertheless, workers can still enter their full user principal name.)

1. Select the **Save** button in the upper-right corner of the page.
1. If you're using a certificate for authentication, complete one of the following steps:

    - For Android devices, select the certificate when prompted.
    - For iOS devices, follow the instructions given in step 5 in the [Import the connection settings](#config) section.

1. The app connects to your Supply Chain Management server and shows the sign-in page.

## <a name="revoke"></a>Remove access for a lost or compromised device

If a device is lost or compromised, you must remove its ability to access Supply Chain Management. The method that you use to remove access depends on how the device was configured to authenticate with Supply Chain Management. For instructions, see one of the following articles:

- If you use user-based authentication, see [User-based authentication](warehouse-app-authenticate-user-based.md#revoke)
- If you use service-based authentication (deprecated), see [Service-based authentication](warehouse-app-authenticate-service-based.md#revoke)

## Related information

- [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
- [Service-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-service-based.md)
- [Mobile device user settings](mobile-device-user-settings.md)
- [Assign step icons and titles for the Warehouse Management mobile app](step-icons-titles.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
