---
title: Use Microsoft Entra Conditional Access with the Warehouse Management mobile app
description: Learn how to configure the Warehouse Management mobile app and Microsoft Entra ID to use Microsoft Entra Conditional Access on Windows, Android, and iOS.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/08/2026
ms.custom:
  - bap-template
---

# Use Microsoft Entra Conditional Access with the Warehouse Management mobile app

The Warehouse Management mobile app supports *brokered authentication*, a sign-in method where an OS-level identity broker, such as Microsoft Authenticator or Intune Company Portal, handles authentication and token management on behalf of the app. When you use brokered authentication, the broker provides Microsoft Entra ID with device identity, compliance status, and security signals during every authentication request.

Brokered authentication makes the app compatible with [Microsoft Entra Conditional Access](/entra/identity/conditional-access/overview) policies. Conditional Access is a policy engine in Microsoft Entra ID that your organization's IT administrators can configure to control access based on conditions such as user identity, device compliance, location, and risk level. For example, you might use Conditional Access to require multifactor authentication (MFA) or block access from unmanaged devices.

> [!IMPORTANT]
> The Warehouse Management mobile app doesn't configure or enforce Conditional Access policies. It uses brokered authentication as a communication layer that passes the required signals to Microsoft Entra ID. Your organization's IT administrators are responsible for the configuration of Conditional Access policies and their rules in [Microsoft Entra ID](/entra/identity/conditional-access/overview).

This article explains how to enable brokered authentication on the Warehouse Management mobile app so that your organization can enforce Conditional Access policies.

## How brokered authentication works

When you use brokered authentication, the following flow occurs during sign-in:

1. The Warehouse Management mobile app delegates authentication to the broker app (Microsoft Authenticator or Intune Company Portal) installed on the device.
1. The broker validates the app's identity and retrieves the device's [primary refresh token (PRT)](/entra/identity/devices/concept-primary-refresh-token), which is a device-bound token that carries device identity and compliance claims.
1. The broker sends the authentication request to Microsoft Entra ID, including the device signals.
1. Microsoft Entra ID evaluates any Conditional Access policies that apply to the user, device, or app, and either grants or denies access.
1. If access is granted, the broker returns the authentication token to the Warehouse Management mobile app.

This process enables features such as single sign-on (SSO) across apps, MFA enforcement, and device-bound token protection—all without requiring the Warehouse Management mobile app to manage these security concerns directly.

## Device requirements

To use brokered authentication, your device must meet the following requirements:

- You must be running Warehouse Management mobile app version 4.0.28 or later.
- Your device must be running a [supported version](install-configure-warehouse-management-app.md#operating-system-requirements) of Windows, Android, or iOS.
- The device must be registered with Microsoft Entra ID (via Workplace Join or Entra ID registration).
- A broker app must be installed on the device (see the following table).

| **Platform** | **Broker app required** |
|---|---|
| **Windows** | The user must have a work account configured on the device. |
| **Android** | Microsoft Authenticator or Intune Company Portal must be installed. |
| **iOS** | Microsoft Authenticator must be installed. |

### Set up Microsoft Authenticator (Android and iOS)

Follow these steps to set up Microsoft Authenticator. The procedure is the same for both Android and iOS.

1. Install **Microsoft Authenticator** from the device's app store (Google Play for Android, App Store for iOS).
1. Open the app and select the **Menu** button.
1. Select **Settings**.
1. Select **Device registration**.
1. Enter your email or organizational account.
1. Select **Register device**.

## App registration

Brokered authentication works with the global Microsoft Entra ID application—you don't need a manual app registration. We recommend the global application because it's simpler to set up and maintain.

If you already use a manual app registration for other reasons (such as on-premises environment requirements), it also works with brokered authentication. In this case, ensure that your registration includes the Android signature hash: `Xo8WBi6jzSxKDVR4drqm84yr9iU=`. Learn more in [Manually create an application registration in Microsoft Entra ID](warehouse-app-authenticate-user-based.md#create-service).

<a name="config-devices"></a>

## Configure devices to use brokered authentication

When you use the global application, brokered authentication is enabled by default on all platforms. The only additional configuration required is enabling the new redirect URI on **Android devices**. You can configure devices manually through the app UI or automatically by distributing a JSON file via QR code or MDM.

### Configure the connection manually

To manually set up a connection, follow these steps on each device:

1. Open the Warehouse Management mobile app and open the **Edit connection** page by doing one of the following steps:

    - If your device doesn't yet have any defined connections, select **Connect** to create a new one.
    - To edit an existing connection, select **Tap to change**, choose the target connection, and then select **Edit connection settings**.
    - To add a new connection, select **Set up connection** and then select **Input manually**.

1. Make the following settings on the **Edit connection** page:

    - **Authentication method** – Set to *Username and Password*.
    - **Cloud** – Set to *Azure Global* (recommended). If you use a manual app registration, set to *Manual* and also provide the **Microsoft Entra ID client** and **Microsoft Entra ID tenant** values.
    - **AndroidNewRedirectURI** – If you're using an Android device, set this option to *Yes*. This is the only additional setting required for Android to use brokered authentication.

    Configure all the other settings as described in [Manually configure the application](install-configure-warehouse-management-app.md#config-manually).

1. Select **Save**.
1. Sign in with the worker's Microsoft Entra credentials.

### Configure the connection by using a QR code or MDM system

To prepare for automatic connection configurations distributed by using a QR code or MDM system, create a JSON file that contains the connection details. Learn more in [Configure the application by importing connection settings](install-configure-warehouse-management-app.md#configure-the-application-by-importing-connection-settings).

For Android devices, add the following setting to your JSON configuration file:

- `"AndroidNewRedirectURI": true`

For all platforms, the connection must use username/password authentication, which you specify as follows in the JSON file:

- `"ConnectionType": "UsernamePassword"`

When you use the global application (`"AuthCloud": "AzureGlobal"`), brokered authentication is enabled by default, so you don't need to set `"UseBroker"` or `"AuthCloud"` explicitly.

The following example shows a JSON configuration that uses the global application with brokered authentication enabled on Android:

```json
{
    "ConnectionName": "Connection1",
    "ActiveDirectoryResource": "https://yourenvironment.cloudax.dynamics.com",
    "Company": "USMF",
    "IsEditable": true,
    "IsDefaultConnection": true,
    "ConnectionType": "UsernamePassword",
    "AuthCloud": "AzureGlobal",
    "AndroidNewRedirectURI": true
}
```

> [!NOTE]
> If you use a manual app registration instead of the global application, set `"AuthCloud": "Manual"` and also include `"ActiveDirectoryClientAppId"` and `"ActiveDirectoryTenant"` values.

For more information about distributing the JSON file to your devices, see [Use a QR code to connect the mobile app to Supply Chain Management](warehouse-app-qr-code.md) and [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md).

## Conditional Access policy configuration

After you enable brokered authentication on your devices, your organization's IT administrators can configure Conditional Access policies in the [Microsoft Entra admin center](/entra/identity/conditional-access/overview) to control access to the Warehouse Management mobile app. Common policies include:

- **Require MFA** – Require multifactor authentication for all users or specific groups.
- **Require compliant device** – Block access from devices that don't meet your organization's compliance requirements.
- **Location-based access** – Restrict access to specific network locations or IP ranges.
- **Risk-based access** – Block or challenge sign-ins that Microsoft Entra ID detects as risky.

The Warehouse Management mobile app doesn't need any extra configuration to work with these policies. When you use brokered authentication, the broker passes the required device and user signals to Microsoft Entra ID, which evaluates the policies and grants or denies access accordingly.

For more information, see the [Microsoft Entra Conditional Access documentation](/entra/identity/conditional-access/).

## Related information

- [Microsoft Entra Conditional Access overview](/entra/identity/conditional-access/overview)
- [Install and configure the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [User-based authentication for the Warehouse app](warehouse-app-authenticate-user-based.md)
- [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md)
- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
