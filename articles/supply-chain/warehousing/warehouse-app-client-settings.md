---
title: Client settings reference for the Warehouse Management mobile app
description: Learn how to provision and lock client settings in the Warehouse Management mobile app by using MDM managed configuration or a connection settings file.
author: pefreita
ms.author: pefreita
ms.topic: reference
ms.date: 10/01/2026
ms.reviewer: kamaybac
ms.search.form:
ms.custom:
  - bap-template
ai-usage: ai-assisted
---

# Client settings reference for the Warehouse Management mobile app

[!INCLUDE [banner](../includes/banner.md)]

*Client settings* control how the Warehouse Management mobile app behaves on a device:

- The Transport Layer Security (TLS) version.
- The browser that shows the sign-in page.
- Whether workers must always enter credentials.
- A device label for telemetry.
- The apps that can exchange data with the app.

Workers see these settings on the **Client settings** page of the app.

You can provision these settings centrally and lock them, so workers can't change them. Add a `ClientSettings` object to the same JSON file that you use for [connection settings](warehouse-app-connection-settings.md). This article helps you decide how to deliver the settings, which ones to set, and whether to lock them. It also describes each setting and how the app applies it.

<a name="two-locks"></a>

## Types of locks

The app has two independent locks that you can set using the `ClientSettings` object in the JSON file. Each lock covers a different part of the configuration, and you set them separately.

- **The client settings lock** (`"LockClientSettings"`) locks the **Client settings** page, which contains the settings listed at the start of this article.
- **The connection settings lock** (`"LockConnectionSettings"`) locks the connections themselves: which Supply Chain Management environment the device connects to, and whether workers can add, import, or edit a connection.

Each lock affects a different page. A device that locks only client settings still lets workers add their own connections. A device that locks only connection settings still lets workers change any client setting that you didn't provision. Setting both locks ensures that workers can only use the app as you configured it.

Neither lock hides information. Workers can still open the pages and read the current values. For exactly what each lock prevents and what it still allows, see [Lock settings](#locks).

<a name="decide"></a>

## Decide how to manage client settings

Make three decisions before you write any JSON:

- **How to deliver the settings** – Determined by your fleet size and mobile device management (MDM) setup.
- **Which settings to provision** – Determined by your goal. Provision only what you need.
- **Whether to lock** – Lock only when you can undo the lock. Without MDM, undoing a lock means a visit to each device.

The recommendations in this section are examples, not rules. You know your devices, sites, staff, and security policies. You decide what works best for your organization.

### Choose a delivery method by situation

If you manage more than about 50 devices, an MDM provider usually pays off. This number is only a guide. The real question is how often you can afford to touch every device. Without MDM, every change means touching every device again. With MDM, you change one policy, and all devices pick it up.

The app reads the standard managed app configuration of each platform. Any MDM provider that supports managed app configuration can deliver the `ConnectionsJson` key. Choose the provider that fits your organization. [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) is one option.

The following table shows example recommendations for common situations.

| Your situation | Example method | Lock? | Why |
|---|---|---|---|
| More than 50 devices, or devices at several sites | [MDM managed configuration](#use-mdm) | Lock both | Only MDM changes settings and removes locks remotely. At this scale, a device-by-device rollout costs more than an MDM rollout. |
| Devices already enrolled in an MDM provider, any number | [MDM managed configuration](#use-mdm) | Lock both | You already have remote control. Use it. |
| 50 or fewer devices at one site, no MDM | [Connection setup QR code](#use-file-qr) | Lock only if IT staff can reach every device | QR code works on every platform and needs no file access. But every change needs a new scan on every device, and a lock has no remote undo. |
| Windows devices without MDM, managed by a script or a software distribution tool | [`connections.json` in the default location](#use-file-qr) | Lock client settings only | The app picks up file changes automatically. If the file sets `"LockConnectionSettings": true`, the app stops reading the file, so you can't push later changes this way. |
| One device, a pilot, or a test | Use **Add from file** or a QR code | No | You test the payload. You can fix mistakes quickly. |

> [!TIP]
> If you expect your fleet to grow, consider starting with MDM now. Moving from file or QR code locks to MDM later means visiting each locked device anyway.

### Choose settings by goal

Start from your goal. Set only the keys in the row. Leave everything else to workers.

| Goal | Keys to set | Notes |
|---|---|---|
| Shared devices. Every worker signs in with their own credentials. | `"PromptType": "login"`, both locks | Add the `"DomainName"` connection parameter, so workers type only their user name. Learn more in [Choose a prompt type](#prompt-type). |
| One worker owns each device, and you use single sign-on | Nothing, or `"PromptType": "None"` | The default reuses the signed-in account. |
| Sign-in fails inside the app, for example with some multifactor authentication methods | `"BrowserOption": "BROWSER"` | Android only. |
| Security policy requires a minimum TLS version | `"TLSConfiguration": "TLS12"` or `"TLSConfiguration": TLS13"` | Test first. If the server or a proxy doesn't support the version, the app can't connect. Learn more in the [TLS note](#tls). |
| Find a misbehaving device in telemetry | `"DeviceName"` | Every device that receives the same payload gets the same name. Learn more in [Device name and telemetry](#device-name). |
| Let a trusted app, such as a wearable scanner app, exchange form data | `"AllowedApps"` | Android only. An allowed app can act as the worker. |
| Workers must not change anything | `"LockClientSettings": true`, `"LockConnectionSettings": true` | Read [Check before you lock](#check) and [Lock settings](#locks) first. |

<a name="check"></a>

### Check before you lock

Answer yes to each of the following questions before you lock your devices:

- Did you test the exact payload on one device of each platform and model?
- Did the device connect and sign in after the payload was applied?
- If you use [Application Insights](application-insights-warehousing.md), did you check that no [`ClientSettingsValidation` event](#validation) reports invalid values? If you don't use Application Insights, open the **Client settings** page, and confirm that each value matches the payload.
- Can you undo the lock? With MDM, you can remove the lock through the MDM provider. With a file or a QR code, you can only unlock by visiting the device. Learn more in the [warning about file and QR code locks](#use-file-qr).

If any answer is no, deploy without locks first. Add locks after the settings work.

## Where to put client settings

Add `ClientSettings` as a sibling of `ConnectionList` at the root of the JSON document.

```json
{
    "ConnectionList": [
        {
            "ConnectionName": "Contoso-Prod",
            "ActiveDirectoryResource": "https://contoso.operations.dynamics.com",
            "Company": "USMF",
            "ConnectionType": "UsernamePassword",
            "AuthCloud": "AzureGlobal"
        }
    ],
    "ClientSettings": {
        "PromptType": "login",
        "DeviceName": "Dock 12 handheld",
        "LockClientSettings": true,
        "LockConnectionSettings": true
    }
}
```

Follow these rules when you write the `ClientSettings` object:

- Spell the `ClientSettings` key exactly as shown, including capitalization. The MDM delivery path doesn't recognize other casing.
- Keys inside `ClientSettings` and their enumeration values are case-insensitive. For example, `"promptType": "LOGIN"` is also accepted.
- Include only the keys you want to control. The app applies only the keys that are present. Every key that you omit stays under the worker's control and keeps its current value.
- An invalid value doesn't cause an error. The app ignores it, uses the default value for that setting instead, and reports it. Learn more in [Find invalid values](#validation). Test every payload on a device before you deploy it widely.
- Omitting the `ClientSettings` object entirely doesn't reset any setting. To return a setting to its default value, provision the default value explicitly, for example `"PromptType": "None"`.

## Settings

The following table describes the client settings that you can provision.

| Key | Values | Default | Platforms | Description |
|---|---|---|---|---|
| `"TLSConfiguration"` | `"None"`, `"TLS12"`, `"TLS13"` | `"None"` | Windows, Android (see the note that follows the table) | Sets the TLS version that the app uses to reach the server. `"None"` leaves the choice to the operating system. Choose a version that your Supply Chain Management environment and any network proxies support. If they don't support it, the app can't connect at all. |
| `"BrowserOption"` | `"None"`, `"NATIVE"`, `"BROWSER"` | `"None"` | Android | Selects the browser that shows the sign-in page. `"NATIVE"` shows sign-in inside the app. `"BROWSER"` hands off to the device's default browser. `"None"` lets the authentication library decide. Use `"BROWSER"` when a sign-in method, such as certain multifactor authentication methods, doesn't finish inside the app. When a broker, such as Microsoft Authenticator, handles sign-in, the broker might control the browser instead. |
| `"PromptType"` | `"login"`, `"None"` | `"None"` | Android, iOS, Windows | Controls whether the sign-in page always asks for credentials. Learn more in [Choose a prompt type](#prompt-type). |
| `"DeviceName"` | Any text, up to 50 characters | Empty | Android, iOS, Windows | Labels the device so you can identify it in telemetry without its serial number. Longer values are truncated to 50 characters. Learn more in [Device name and telemetry](#device-name). |
| `"AllowedApps"` | An array of Android package names, for example `["com.contoso.wearable"]`, or one string with names separated by `;` or `,` | Empty | Android | Sets the other apps on the device that can exchange form data with the Warehouse Management mobile app. Workers see this list as **Allowed apps** on the **Client settings** page. An empty list turns data exchange off in both directions. The app drops entries that aren't valid package names and removes duplicates. An allowed app can read everything the app shows and can act as the worker, so allow only apps that you trust. |
| `"LockClientSettings"` | `true` or `false` | `false` | Android, iOS, Windows | Makes the **Client settings** page read-only. Learn more in [Lock settings](#locks). |
| `"LockConnectionSettings"` | `true` or `false` | `false` | Android, iOS, Windows | Prevents workers from adding or changing connections. Learn more in [Lock settings](#locks). |

For Boolean values (such as the locks), the app reads `true`, `1`, `"true"`, `"1"`, and `"yes"` as `true`, and `false`, `0`, `"false"`, `"0"`, and `"no"` as `false`. It treats any other value, including a typo, as `false` and [reports it](#validation). A malformed lock never locks a device by accident.

<a name="tls"></a>

> [!IMPORTANT]
> TLS behavior differs by platform.
>
> - **Windows** – The app applies the value the next time it starts. `"TLS12"` and `"TLS13"` pin the connection to exactly that version. For example, `"TLS12"` also disables TLS 1.3.
> - **Android** – The app applies the value at startup and immediately whenever it changes, regardless of whether the change comes from MDM, a file, a QR code, or the worker.
> - **iOS** – The setting isn't available. The operating system manages TLS.

<a name="prompt-type"></a>

## Choose a prompt type

By default (`"PromptType": "None"`), the app reuses an account that's already signed in on the device when it can. Keep the default when one worker owns one device, or when you use [single sign-on](warehouse-app-authenticate-user-based.md#sso).

Set `"PromptType": "login"` when every sign-in must show the credentials page, even if an account is already signed in. Typical situations:

- **Shared devices** – Several workers use the same device across shifts. The prompt stops the next worker from continuing in the previous worker's session.
- **Accountability requirements** – Your security or audit policy requires each worker to enter credentials, so every transaction maps to the person holding the device.
- **Shift changes without a device reset** – Devices move between workers without a wipe, and no broker signs workers out globally.

Before you set `"PromptType": "login"`, consider these points:

- Workers type credentials more often. Combine `"login"` with the `"DomainName"` connection parameter, so workers type only their user name. Learn more in [Connection settings reference](warehouse-app-connection-settings.md#connection-file-qr).
- `"login"` forces the credentials page. It doesn't add a multifactor authentication challenge. Use [Conditional Access](warehouse-app-conditional-access-enable.md) for that purpose.
- Connections that use [QR code and PIN sign-in](warehouse-app-authenticate-qr-code.md) always force the prompt, regardless of this setting.

<a name="device-name"></a>

## Device name and telemetry

The app sends `"DeviceName"` with every event to *your* Application Insights resource, if you [set one up](application-insights-warehousing.md). It doesn't send the device name to Microsoft. Use the device name to filter telemetry by device, for example to investigate a handheld that disconnects often.

Because the device name is free text that might identify a person or a location, follow your organization's data policies when you choose names.

The same `ClientSettings` object applies to every device that receives the payload. To give each device a unique name, choose one of these options:

- Use an MDM provider that supports per-device token substitution in app configuration values.
- Leave the device name out of the payload, and let workers or IT staff set it on each device.

<a name="locks"></a>

## Lock settings

Locks control what workers can change on the device. They don't hide information: workers can still see what's configured.

| Lock | What workers can't do | What workers can still do |
|---|---|---|
| `"LockClientSettings": true` | Change any field on the **Client settings** page, including the **Allowed apps** field on Android. The page shows a message that your organization manages the settings. | Open the **Client settings** page and read the current values. |
| `"LockConnectionSettings": true` | Use **Add from file**, **Add from QR code**, or **Input manually**. Select **Edit connection settings**. Change any field on the connection pages. | Select, switch between, and connect to existing connections. Open **Client settings**, diagnostics, **About**, and demo mode. |

To fully standardize a device, set both locks.

## Choose a delivery method

Every method that delivers connection settings also delivers `ClientSettings`, with the same rules. The methods differ in how much control you keep after delivery. For a recommendation by situation, see [Choose a delivery method by situation](#choose-a-delivery-method-by-situation).

| Capability | MDM managed configuration (`ConnectionsJson` key) | Add from file | Connection setup QR code | `connections.json` in the [default location](warehouse-app-connection-settings.md#file-name-location) |
|---|---|---|---|---|
| Applies settings and locks | Yes | Yes | Yes | Yes |
| Updates when you change the source | Yes, automatically | No. A worker must import the file again. | No. A worker must scan the code again. | Yes, automatically, while connection settings aren't locked |
| Removes a lock | Yes. Set the lock to `false`, or remove the key. | Only by importing another file or QR code. Not possible if `"LockConnectionSettings"` is `true`. | Only by scanning another QR code or importing another file. Not possible if `"LockConnectionSettings"` is `true`. | Only by changing the file. Not possible if `"LockConnectionSettings"` is `true`. |
| Overrides the other methods | Yes. MDM always wins. | No | No | No |

<a name="use-mdm"></a>

### Use MDM managed configuration

Use MDM managed configuration for fleets. It's the only method that changes or removes settings and locks remotely. Add `ClientSettings` to the JSON value of the `ConnectionsJson` configuration key, as described in [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md#manage-connection-configurations).

<a name="use-file-qr"></a>

### Use a connection settings file or QR code

Use a file or a QR code for devices that aren't enrolled in MDM. To import a file, select **Set up connection** > **Add from file**. To scan a code, select **Add from QR code**. The app applies the settings and locks immediately. Learn more in [Import connection settings from a QR code](warehouse-app-qr-code.md).

Each key that you add to `ClientSettings` makes the QR code denser. Include only the keys that you need, and test that your devices can scan the code.

On Windows, you can also place `connections.json` in the [default location](warehouse-app-connection-settings.md#file-name-location). The app checks the file at the same times that it checks MDM. It applies `ClientSettings` only when the object changes. It doesn't read the file while connection settings are locked.

> [!WARNING]
> A lock set by a file or QR code has no remote undo. If a file or QR code sets both `"LockConnectionSettings": true` and `"LockClientSettings": true`, nobody can unlock the device from within the app. To unlock it, use one of these options:
>
> - Enroll the device in MDM, and provision `false` for each lock.
> - Clear the app data, or reinstall the app. This option also removes all connections and signs out the worker.

If MDM already locks client settings on the device, the app ignores the entire `ClientSettings` object in a file or QR code, including its locks. The connections are still imported.

<a name="apply"></a>

## How the app applies client settings

The following rules describe how the app combines MDM, files, QR codes, and worker changes.

- **MDM is the source of truth** – Every time the app reads MDM, it reapplies the locks in the policy. If a previous policy set a lock and the current policy drops that key, the app removes the lock. Locks that MDM never mentioned stay as the last file or QR code set them.
- **MDM settings reapply on change and after each app start** – The app reapplies provisioned settings in three cases: the policy changes, the app reads MDM for the first time after it starts, or a file or QR code applies settings. Between those events, a worker can change an unlocked setting. The change stays until the next reapplication. To keep a setting fixed, also set `"LockClientSettings": true`.
- **Locks survive restarts and offline use** – The app stores locks on the device. A device stays locked if it starts without network access or can't read MDM.
- **A failed MDM read changes nothing** – If the app can't read the managed configuration, it keeps the current settings and locks. A failed read never counts as a removed policy.
- **The app reads MDM and the default file only on specific pages** – The app checks while the start page or the **Select connection** page is open: after 5 seconds, 30 seconds, and 60 seconds (twice each), and then every 5 minutes. It doesn't check while a worker is in a mobile device flow. A policy change reaches a device when a worker returns to one of those pages or restarts the app.
- **MDM wins in the same check** – When both MDM and `connections.json` in the default location change, the app applies the file first and then MDM.
- **Earlier settings migrate once** – If a device has client settings from an earlier app version, the app moves them into the new storage one time. It skips the move if administrator settings are already applied.

<a name="validation"></a>

## Find invalid values

When a payload contains values that the app doesn't recognize, the app applies the default value for each one. It reports all of them together, once per payload. If you [set up Application Insights](application-insights-warehousing.md), the app sends a `ClientSettingsValidation` event to your resource with the following properties:

- `source` – Where the payload came from: `MDM`, `File`, or `QR`.
- `appliedAt` – When the app applied the payload.
- `issueCount` – The number of invalid values.
- `issues` – A list with the key, the value that the app received, and the value that it applied instead.

Examples of invalid values include an unknown `"TLSConfiguration"` value, a `"DeviceName"` longer than 50 characters, a malformed package name in `"AllowedApps"`, and a lock value such as `"enabled"` that isn't a recognized Boolean value. After you deploy a new payload, check for this event to confirm that devices applied what you intended.

## Example: Locked shared-device configuration

The following MDM payload configures shared Android devices. It matches the shared-devices row in [Choose settings by goal](#choose-settings-by-goal). It forces the credentials page at every sign-in, uses the device browser for sign-in, and prevents workers from changing settings or connections.

```json
{
    "ConnectionList": [
        {
            "ConnectionName": "Contoso-Prod",
            "ActiveDirectoryResource": "https://contoso.operations.dynamics.com",
            "Company": "USMF",
            "ConnectionType": "UsernamePassword",
            "UseBroker": false,
            "DomainName": "contoso.com",
            "AuthCloud": "AzureGlobal"
        }
    ],
    "ClientSettings": {
        "BrowserOption": "BROWSER",
        "PromptType": "login",
        "LockClientSettings": true,
        "LockConnectionSettings": true
    }
}
```

To release the locks later, update the policy to set `"LockClientSettings": false` and `"LockConnectionSettings": false`, or remove both keys. Devices unlock the next time they read MDM.

## Related information

- [Connection settings reference for the Warehouse Management mobile app](warehouse-app-connection-settings.md)
- [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md)
- [Choose how to distribute connection settings](install-configure-warehouse-management-app.md#distribute)
- [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- [QR code and PIN sign-in for the Warehouse Management mobile app](warehouse-app-authenticate-qr-code.md)
- [Enable warehousing telemetry with Application Insights](application-insights-warehousing.md)
- [What is Microsoft Intune?](/mem/intune/fundamentals/what-is-intune)
