---
title: Brokered authentication and Conditional Access for the Warehouse Management mobile app
description: Learn how to set up brokered authentication for the Warehouse Management mobile app, and how to use it with Microsoft Entra Conditional Access on Windows, Android, and iOS.
author: pefreita
ms.author: pefreita
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 09/07/2026
ms.custom:
  - bap-template
---

# Brokered authentication and Conditional Access for the Warehouse Management mobile app

[!INCLUDE [banner](../includes/banner.md)]

The Warehouse Management mobile app supports *brokered authentication*, a sign-in method where an OS-level identity broker, such as Microsoft Authenticator or Intune Company Portal, handles authentication and token management on behalf of the app. When you use brokered authentication, the broker provides Microsoft Entra ID with device identity, compliance status, and security signals during every authentication request.

> [!IMPORTANT]
> Brokered authentication is an advanced capability. It isn't required, and most deployments don't need it. The app signs workers in through the system browser or a native web view, without Microsoft Authenticator, Intune Company Portal, or any other companion app. Read this article only if you want single sign-on (SSO) or Conditional Access policies that depend on device signals. Otherwise, see [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md).
>
> If you already use brokered authentication, keep it. Nothing about it is deprecated, and no change is required.

Brokered authentication isn't a separate authentication method. It's an option of [username/password authentication](warehouse-app-authenticate-user-based.md#usernamePasswordFlow) that does two things: it enables [single sign-on](warehouse-app-authenticate-user-based.md#sso) (SSO), and it makes the app compatible with Microsoft Entra Conditional Access policies that depend on device signals. This article covers both. Use it as the single reference for brokered authentication, whether or not you use Conditional Access.

[Microsoft Entra Conditional Access](/entra/identity/conditional-access/overview) is an optional policy engine that controls access based on conditions such as user identity, device compliance, location, and risk level. It isn't required to run the Warehouse Management mobile app.

> [!IMPORTANT]
> The Warehouse Management mobile app supports *connecting* through brokered authentication. It doesn't define, configure, or enforce Conditional Access policies, and it doesn't change how your policies are evaluated. Responsibilities are divided as follows:
>
> - **The Warehouse Management mobile app (Microsoft)** – Supports brokered authentication so that the broker can pass device identity, compliance status, and security signals to Microsoft Entra ID during sign-in.
> - **Your IT department** – Decides whether to use Conditional Access, and designs, configures, tests, and maintains the policies, device registration, compliance rules, and broker deployment in [Microsoft Entra ID](/entra/identity/conditional-access/overview) and your device management solution.
>
> Because policy design depends on your organization's security requirements, the guidance in this article covers only the app-side setup. For policy decisions and troubleshooting of the policies themselves, work with your Microsoft Entra ID and device management administrators.

> [!NOTE]
> The `"UseBroker"` connection setting defaults to `true`. Therefore, if you don't set it, the app tries to use a broker. This default doesn't create a requirement—when no broker is available on the device, the app signs workers in through the system browser or a native web view instead. Deploying a broker is a security design decision that your organization owns.

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
- The device must be registered with Microsoft Entra ID. The broker can perform this registration (Workplace Join) as part of the first sign-in, so it isn't necessarily something that you set up in advance. The app itself doesn't require any particular registration state. Learn more in [Device registration requirements](warehouse-app-authenticate-user-based.md#device-registration).
- A broker app must be installed on the device (see the following table). If no broker is installed, the app falls back to browser-based sign-in, and device signals aren't available to Conditional Access.

| **Platform** | **Broker app required** |
|---|---|
| **Windows** | No separate app is required. The user must have a work account configured on the device, and the built-in Windows Web Account Manager (WAM) acts as the broker. |
| **Android** | [Microsoft Authenticator](/entra/identity/authentication/concept-authentication-authenticator-app) or [Intune Company Portal](/intune/user-help/company-portal) must be installed. |
| **iOS** | [Microsoft Authenticator](/entra/identity/authentication/concept-authentication-authenticator-app) must be installed. |

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

The global application is provided as a Microsoft first-party application (FPA) and is available on the Azure commercial cloud. If your environment is deployed on a US government cloud—such as US Government Community Cloud (GCC) or GCC High—the global application isn't available, and you must use a manual app registration instead.

If you already use a manual app registration for other reasons (such as on-premises environment requirements or a government cloud deployment), it also works with brokered authentication. Learn more in [Create a custom application registration](warehouse-app-custom-app-registration.md).

<a name="config-devices"></a>

## Configure devices to use brokered authentication

When you use the global application, the `"UseBroker"` setting defaults to `true` on all platforms, so the app tries to use a broker without extra configuration. A broker still has to be present on the device for brokered authentication to take effect. You can configure devices manually through the app UI or automatically by distributing a JSON file via QR code or MDM.

If you don't want to use brokered authentication, set the **Brokered authentication** option to *No* on the **Edit connection** page (or set `"UseBroker": false` in the JSON configuration). If the device doesn't have Microsoft Authenticator installed, the app falls back to a standard username and password connection.

### Configure the connection manually

To manually set up a connection, follow these steps on each device:

1. Open the Warehouse Management mobile app and open the **Edit connection** page by doing one of the following steps:

    - If your device doesn't yet have any defined connections, select **Connect** to create a new one.
    - To edit an existing connection, select **Tap to change**, choose the target connection, and then select **Edit connection settings**.
    - To add a new connection, select **Set up connection** and then select **Input manually**.

1. Make the following settings on the **Edit connection** page:

    - **Authentication method** – Set to *Username and Password*.
    - **Cloud** – Set to *Azure Global* (recommended). If you use a custom app registration, set this field to *Manual* and provide the **Microsoft Entra ID client ID** value.

    Configure all the other settings as described in [Manually configure the application](install-configure-warehouse-management-app.md#config-manually).

1. Select **Save**.
1. Sign in with the worker's Microsoft Entra credentials.

### Configure the connection by using a QR code or MDM system

To prepare for automatic connection configurations distributed by using a QR code or MDM system, create a JSON file that contains the connection details. Learn more in [Connection settings reference](warehouse-app-connection-settings.md#connection-file-qr).

For all platforms, the connection must use username/password authentication, which you specify as follows in the JSON file:

- `"ConnectionType": "UsernamePassword"`

When you use the global application (`"AuthCloud": "AzureGlobal"`), brokered authentication is enabled by default, so you don't have to set `"UseBroker"` explicitly.

The following example shows a JSON configuration that uses the global application with brokered authentication enabled:

```json
{
    "ConnectionList": [
        {
            "ConnectionName": "Connection1",
            "ActiveDirectoryResource": "https://yourenvironment.cloudax.dynamics.com",
            "Company": "USMF",
            "ConnectionType": "UsernamePassword",
            "AuthCloud": "AzureGlobal"
        }
    ]
}
```

> [!NOTE]
> If you use a custom app registration instead of the global application, set `"AuthCloud": "Manual"` and include a value for `"ActiveDirectoryClientAppId"`.

Learn more about distributing the JSON file to your devices in [Read connection settings from a QR code](warehouse-app-qr-code.md) and [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md).

## Conditional Access policy configuration

After you enable brokered authentication on your devices, your organization's IT administrators decide which Conditional Access policies to apply and configure them in the [Microsoft Entra admin center](/entra/identity/conditional-access/overview). The following examples show the kinds of policies that organizations commonly apply. They're examples only, not recommendations, and the choice depends on your organization's security requirements:

- **Require MFA** – Require multifactor authentication for all users or specific groups.
- **Require compliant device** – Block access from devices that don't meet your organization's compliance requirements.
- **Location-based access** – Restrict access to specific network locations or IP ranges.
- **Risk-based access** – Block or challenge sign-ins that Microsoft Entra ID detects as risky.

The Warehouse Management mobile app doesn't need any extra configuration to work with these policies, and it has no settings that override them. When you use brokered authentication, the broker passes the required device and user signals to Microsoft Entra ID, which evaluates the policies and grants or denies access accordingly. If a sign-in is blocked, the policy evaluation occurred in Microsoft Entra ID, so your IT administrators must review the policy and the sign-in logs there.

For more information, see the [Microsoft Entra Conditional Access documentation](/entra/identity/conditional-access/).

## Related information

- [Microsoft Entra Conditional Access overview](/entra/identity/conditional-access/overview)
- [Install and configure the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [User-based authentication for the Warehouse app](warehouse-app-authenticate-user-based.md)
- [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md)
- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
