---
title: Use Microsoft Entra Conditional Access with the Warehouse Management mobile app
description: Learn how to configure the Warehouse Management mobile app and Microsoft Entra ID to use Microsoft Entra Conditional Access on Windows, Android, and iOS.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/09/2026
ms.custom:
  - bap-template
---

# Use Microsoft Entra Conditional Access with the Warehouse Management mobile app

[Microsoft Entra Conditional Access](/entra/identity/conditional-access/overview) is a dynamic policy engine that controls access to applications and data based on real‑time identity, device, location, and risk signals. It enforces [Zero Trust](/security/zero-trust/deploy/identity) and secures modern workplaces. It's a policy-based security feature in Microsoft Entra ID.

The Warehouse Management mobile app uses *brokered authentication* to satisfy Conditional Access requirements. Brokered authentication is a sign‑in method where an OS-level identity broker (such as Microsoft Authenticator) performs authentication and token management on behalf of an application. This method enables secure single sign-on, multifactor authentication (MFA), and device-bound token protection. By using brokered authentication, you can enforce security policies such as MFA and device compliance.

This article explains how to configure the Warehouse Management mobile app and Microsoft Entra ID to use Conditional Access on all supported platforms.

## Device requirements

To use Conditional Access, your device must meet the following requirements:

- You must be running Warehouse Management mobile app version 4.0.28 or later.
- Your device must be running a [supported version](install-configure-warehouse-management-app.md#operating-system-requirements) of Windows, Android, or iOS.
- Depending on your device platform, you might need to install a broker app.

As mentioned in the introduction, Conditional Access requires that your mobile devices use brokered authentication. The system components required to support brokered authentication vary based on the platform you're running the Warehouse Management mobile app on. The following table summarizes the requirements. In addition, each device must include a connection configuration that's set up as described in [Configure devices to use Conditional Access](#config-devices).

| **Platform** | **Broker requirements**                    |
|--------------|--------------------------------------------|
| **Windows**  | The user must have a work account.         |
| **Android**  | Microsoft Authenticator must be installed. |
| **iOS**      | Microsoft Authenticator must be installed. |

## Configure your Microsoft Entra ID app registration to support Conditional Access

To use Conditional Access, you must manually set up an app registration in Microsoft Entra ID (instead of using the global Microsoft Entra ID application). The application registration enables the mobile app to authenticate and connect to your Supply Chain Management environment. When you're setting up the application registration, you must be sure to include the new signature hash for Android devices (`Xo8WBi6jzSxKDVR4drqm84yr9iU=`). Even if you already use a manual app registration, you might need to update it to include this new signature hash, so you should check. Detailed, updated instructions are provided in [Manually create an application registration in Microsoft Entra ID](warehouse-app-authenticate-user-based.md#create-service).

<a name="config-devices"></a>

## Configure devices to use Conditional Access

The [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md#config-manually) article explains how to install the mobile app and configure the connection for each of your mobile devices. It includes details for how to set up devices to use Conditional Access and describes all of the available configuration options. This article highlights the settings that are specific for Conditional Access.

You can configure each device manually by using the Warehouse Management warehouse UI or automatically by using a JSON file distributed with a QR code or mobile device management (MDM) system. This section describes both methods.

### Configure the connection manually

To manually set up a connection that supports Conditional Access:

1. Open the Warehouse Management mobile app and open the **Edit connection** page by doing one of the following steps:

    - If your device doesn't yet have any defined connections, select **Connect** to create a new one.
    - To edit an existing connection, select **Tap to change**, choose the target connection, and then select **Edit connection settings**.
    - To add a new connection, select **Set up connection** and then select **Input manually**.

1. Make the following settings on the **Edit connection** page:

    - **Authentication method** – Set to *Username and Password*.
    - **Cloud** – Set to *Manual*.
    - **Use broker** – If you're using Windows or Android, set this option to *Yes*. If you're using iOS, the system handles this setting automatically, so the setting isn't shown.
    - **AndroidNewRedirectURI** – If you're using an Android device, set this option to *Yes*.

        Configure all the other settings as described in [Manually configure the application](install-configure-warehouse-management-app.md#config-manually). If you previously had **Cloud** set to *Azure Global*, remember also to set **Microsoft Entra ID client** and **Microsoft Entra ID tenant** as described in that article.

1. Select **Save**.
1. Sign in with the worker's Microsoft Entra credentials.

### Configure the connection by using a QR code or MDM system

To prepare for automatic connection configurations to be distributed by using a QR code or mobile device management (MDM) system, create a JSON file that contains the connection details. Learn more in [Configure the application by importing connection settings](install-configure-warehouse-management-app.md#configure-the-application-by-importing-connection-settings).

To configure devices to support Conditional Access, your JSON configuration file must use the following values in addition to the other standard settings:

- `"ConnectionType": "UsernamePassword"`
- `"AuthCloud": "Manual"`
- `"UseBroker": true`
- `"AndroidNewRedirectURI": true`

Remember that when you use `"AuthCloud": "Manual"`, you must also set `ActiveDirectoryClientAppId` and `ActiveDirectoryTenant`.

The following example shows a complete JSON-based connection configuration that includes all the required settings, including the settings needed to support Conditional Access:

```json
{
    "ActiveDirectoryClientAppId": "aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
    "ConnectionName": "Connection5",
    "ActiveDirectoryResource": "<https://yourenvironment5.cloudax.dynamics.com>",
    "ActiveDirectoryTenant": "<https://login.windows.net/7b363b3e-3803-4632-8e5b-e82f45ddc359>",
    "Company": "USMF",
    "IsEditable": true,
    "IsDefaultConnection": false,
    "UseBroker": true,
    "ConnectionType": "UsernamePassword",
    "AuthCloud": "Manual",
    "AndroidNewRedirectURI": true
}
```

For more information about distributing the JSON file to your devices, see [Use a QR code to connect the mobile app to Supply Chain Management](warehouse-app-qr-code.md) and [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md).

## Related information

- [Microsoft Entra Conditional Access overview](/entra/identity/conditional-access/overview)
- [Install and configure the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [User-based authentication for the Warehouse app](warehouse-app-authenticate-user-based.md)
- [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md)
- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
