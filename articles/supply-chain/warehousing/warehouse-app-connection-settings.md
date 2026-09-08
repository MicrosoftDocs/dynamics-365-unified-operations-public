---
title: Connection settings reference for the Warehouse Management mobile app
description: Learn how to build the connection settings JSON that tells the Warehouse Management mobile app which environment, company, and authentication method to use.
author: pefreita
ms.author: pefreita
ms.topic: reference
ms.date: 09/04/2026
ms.reviewer: kamaybac
ms.search.form: SysAADClientTable, WHSMobileAppField, WHSMobileAppFieldPriority, WHSRFMenu, WHSRFMenuItem, WHSWorker
ms.custom:
  - bap-template
  - sfi-ropc-nochange
---

# Connection settings reference for the Warehouse Management mobile app

[!INCLUDE [banner](../includes/banner.md)]

*Connection settings* tell the Warehouse Management mobile app which Microsoft Dynamics 365 Supply Chain Management environment to connect to, which legal entity to use, and how to authenticate. They're expressed in JavaScript Object Notation (JSON) format.

The same JSON is used no matter how you deliver it to your devices. To choose a delivery method, see [Choose how to distribute connection settings](install-configure-warehouse-management-app.md#distribute).

<a name="connection-file-qr"></a>

## Create a connection settings file or QR code

The JSON must include a connection list that contains the individual connections that you need to add. After you create the JSON, you can save it as a file, deliver it through your mobile device management (MDM) provider, or [generate a QR code](warehouse-app-qr-code.md) that has the same content.

The following table summarizes the parameters that you can specify for each connection. Required parameters are listed first, followed by optional parameters.

| Parameter | Description |
|---|---|
| `"ConnectionName"` | Specify the name of the connection setting. The maximum length is 20 characters. Because this value is the unique identifier for a connection setting, ensure that it's unique in the list. If a connection that has the same name already exists on the device, the settings from the imported file override it. |
| `"ActiveDirectoryResource"` | Specify the root URL of Supply Chain Management. |
| `"Company"` | Specify the legal entity in Supply Chain Management that you want the application to connect to. |
| `"AuthCloud"` | <p>Specify the type of Microsoft Entra ID app registration to authenticate with:</p><ul><li>`"AzureGlobal"` (recommended) – Authenticate by using the global Microsoft Entra ID application that Microsoft registers and maintains. This option supports most scenarios, including [Microsoft Entra Conditional Access](warehouse-app-conditional-access-enable.md). You don't have to register or maintain your own Microsoft Entra ID app, and you must not specify an `"ActiveDirectoryClientAppId"` value for the connection.</li><li>`"Manual"` – Authenticate through your own custom Microsoft Entra ID app registration. Use this option only when the global application doesn't apply to your deployment. If you choose this option, you must [register and maintain a custom app in Microsoft Entra ID](warehouse-app-custom-app-registration.md) and specify an `"ActiveDirectoryClientAppId"` value for the connection.</li></ul> |
| `"ActiveDirectoryClientAppId"` | (Optional.) Required only when you set `"AuthCloud": "Manual"`. Specify the client ID of your custom app registration. Learn more in [Create a custom application registration](warehouse-app-custom-app-registration.md). |
| `"ConnectionType"` | <p>(Optional.) Specify how the connection authenticates with the environment. If you don't specify a value, then `"UsernamePassword"` is assumed. Valid values are:</p><ul><li>`"UsernamePassword"` (recommended) – Use [username/password authentication](warehouse-app-authenticate-user-based.md#usernamePasswordFlow).</li><li>`"DeviceCode"` (not recommended) – [Use device code flow](warehouse-app-authenticate-user-based.md#deviceCodeFlow).</li></ul> |
| `"UseBroker"` | <p>(Optional.) This parameter applies only to the `"UsernamePassword"` connection type. It determines whether a broker is used for [single sign-on (SSO)](warehouse-app-authenticate-user-based.md#sso) authentication. The default value is `"true"`. Therefore, if you don't set this parameter, the app tries to use a broker. If no broker is available on the device, the app falls back to sign-in through the system browser or a native web view. Set it to `"false"` to always require manual input of a user name and password. Learn more about the broker that each platform requires in [Device requirements](warehouse-app-conditional-access-enable.md#device-requirements).</p> |
| `"DomainName"` | (Optional.) This parameter applies only to the `"UsernamePassword"` connection type. It allows you to implement a simplified sign-in process. If you don't set this field, workers must always enter their full Microsoft Entra ID user principal name (UPN) to sign in. A UPN has the form \<*user name*\>@\<*domain name*\>. If you specify the \<*domain name*\> part here, workers can sign in by entering only the \<*user name*\> part. (Even if you set the domain name here, workers can still sign in using their full UPN.) |
| `"ActiveDirectoryTenant"` | (Optional) Applies only when you set `"AuthCloud": "Manual"`. Specify the Microsoft Entra ID domain name that you're using with the Supply Chain Management server. This value has the form `https://login.windows.net/<your-Microsoft-Entra-ID-domain-name>`. Here's an example: `https://login.windows.net/contosooperations.onmicrosoft.com`. Learn more about how to find your Microsoft Entra ID domain name in [Locate important IDs for a user](/partner-center/find-ids-and-domain-names). |

## Example connection settings file

The following example shows a valid connection settings file that contains three connections: *Connection1* uses the global application (no client ID is needed), *Connection2* uses a custom app registration with brokered authentication, and *Connection3* uses a custom app registration where workers enter a user name and password manually.

```json
{
    "ConnectionList": [
        {
            "ConnectionName": "Connection1",
            "ActiveDirectoryResource": "https://yourenvironment1.cloudax.dynamics.com",
            "Company": "USMF",
            "ConnectionType": "UsernamePassword",
            "UseBroker": true,
            "AuthCloud": "AzureGlobal"
        },
        {
            "ConnectionName": "Connection2",
            "ActiveDirectoryClientAppId": "aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
            "ActiveDirectoryResource": "https://yourenvironment2.cloudax.dynamics.com",
            "Company": "USMF",
            "ConnectionType": "UsernamePassword",
            "UseBroker": true,
            "AuthCloud": "Manual"
        },
        {
            "ConnectionName": "Connection3",
            "ActiveDirectoryClientAppId": "aaaaaaaa-bbbb-ccccc-dddd-eeeeeeeeeeee",
            "ActiveDirectoryResource": "https://yourenvironment3.cloudax.dynamics.com",
            "ActiveDirectoryTenant": "https://login.windows.net/contosooperations.onmicrosoft.com",
            "Company": "USMF",
            "ConnectionType": "UsernamePassword",
            "UseBroker": false,
            "DomainName": "contosooperations.onmicrosoft.com",
            "AuthCloud": "Manual"
        }
    ]
}
```

<a name="file-name-location"></a>

## File name and location on each device

This section applies when you deliver the settings as a file. If you use MDM managed configuration or a QR code, the app stores the settings itself, and you can skip this section.

If you use the default name and location when you save the connection settings file on each device, the app automatically imports it, even during the first run after the app is installed. If you use a custom name or location for the file, the app user must specify the values during the first run. However, the app continues to use the specified name and location afterward.

The default file name is *connections.json*. The default file location depends on which type of device you're using:

- **Windows:** `C:\Users\<User>\AppData\Local\Packages\Microsoft.WarehouseManagement_8wekyb3d8bbwe\LocalState`
- **Android:** `Android\data\com.Microsoft.WarehouseManagement\files`. Because of [Android scoped storage limitations](install-configure-warehouse-management-app.md#distribute), external tools can't write to this path. Use MDM managed configuration or a QR code instead.
- **iOS:** File sharing isn't supported. Use MDM managed configuration or a QR code instead.

Usually, the paths are automatically created after the first run of the app. However, you can manually create them if you must transfer the connection settings file to the device before installation.

> [!NOTE]
> If you uninstall the app, the default path and its contents are removed.

<a name="updates"></a>

## How the app applies changes

Every time that the app starts, it reimports the connection settings from their previous location to check for changes. The app updates only connections that have the same names as the connections in the connection settings file. User-created connections that use other names aren't updated.

You can't remove a connection by using the connection settings file.

## Related information

- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Choose how to distribute connection settings](install-configure-warehouse-management-app.md#distribute)
- [Read connection settings from a QR code](warehouse-app-qr-code.md)
- [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md)
- [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- [Create a custom application registration](warehouse-app-custom-app-registration.md)
