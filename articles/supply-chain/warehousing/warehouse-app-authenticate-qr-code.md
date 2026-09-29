---
title: QR code and PIN sign-in for the Warehouse Management mobile app
description: Learn how to configure Microsoft Entra ID QR code and PIN sign-in for the Warehouse Management mobile app, manually or through mass deployment.
author: pefreita
ms.author: pefreita
ms.topic: how-to
ms.date: 09/29/2026
ms.reviewer: kamaybac
ms.custom: bap-template
---

# QR code and PIN sign-in for the Warehouse Management mobile app

[!INCLUDE [banner](../includes/banner.md)]

The Warehouse Management mobile app supports Microsoft Entra ID QR code and PIN sign-in only on Android and iOS/iPadOS devices. This sign-in method isn't available on Windows. Instead of entering a user name and password, a worker scans a printed QR code badge and enters a personal identification number (PIN). Sign-in is faster on shared devices, and every worker keeps an individual Microsoft Entra ID identity.

In this article, you learn how to:

- Meet prerequisites for the app, devices, licenses, and worker accounts.
- Enable the QR code authentication method and issue codes and PINs in Microsoft Entra ID.
- Turn on QR code sign-in for a connection locally in the app, or deploy it to many devices through mobile device management (MDM).
- Understand what the app controls, what Microsoft Entra ID controls, and where the method is available.

QR code and PIN sign-in is single-factor authentication. It doesn't satisfy multifactor authentication (MFA) requirements.

## Prerequisites

To use QR code and PIN sign-in, ensure that your system and mobile devices meet the following prerequisites:

- **Warehouse Management mobile app version** – You must be running Warehouse Management mobile app version 4.2.0.0 or later to use the QR connection preference.
- **OS and platform** – You must use an Android or iOS/iPadOS device that meets the [OS requirements](install-configure-warehouse-management-app.md#operating-system-requirements) and the Microsoft Entra ID QR code prerequisites. QR code and PIN sign-in isn't supported on Windows.
- **Microsoft Entra ID environment and licensing** – Your Microsoft Entra ID environment must meet all technical and user licensing requirements listed in [Prerequisites to enable the QR code authentication method](/entra/identity/authentication/how-to-authentication-qr-code#prerequisites-to-enable-the-qr-code-authentication-method).
- **Cloud** – You must be running Supply Chain Management in a cloud that supports QR code and PIN sign-in. Most, but not all, clouds currently support this feature. Learn more in [Cloud availability](#clouds).
- **Camera** – Allow camera access in the sign-in experience. Entra ID doesn't currently support hardware barcode scanners for sign-in QR codes.
- **Worker accounts** – Use individual Microsoft Entra ID accounts and QR codes. Configure the corresponding [user and warehouse worker records](mobile-device-work-users.md) in Supply Chain Management.

> [!NOTE]
> The Warehouse Management mobile app doesn't support Microsoft Entra ID *shared device mode*. Sharing physical devices doesn't enable that feature.

## What is QR code authentication?

*QR code authentication* is a simple authentication method primarily designed for frontline workers. It consists of a unique QR code and a numeric PIN. The QR code serves as an identifier and is unique to the user. You can download and print it by using the Microsoft Entra ID admin center, My Staff, or Microsoft Graph. For convenience, attach the QR code to a badge or any other wearable item.

An authentication administrator provides a temporary PIN to workers, who then change it during sign-in. After that, only the workers know their PIN. The PIN is exclusively bound to the QR code and can't be used with other user identifiers, such as a username or phone number. QR code authentication is a *single-factor method* in which the PIN (something you know) is a credential. Learn more in [QR code authentication in Microsoft Entra ID](/entra/identity/authentication/concept-authentication-qr-code).

Use QR code authentication for shared handhelds, shift changes, and frequent device changes. A printed badge reduces typing while preserving individual Microsoft Entra ID identities.

The app uses two types of QR codes, each of which has a different purpose, as shown in the following table:

| QR code type | Purpose | Where to scan |
| --- | --- | --- |
| [Connection setup QR code](warehouse-app-qr-code.md) | Imports connection settings in JSON format, including details such as the environment URL, company, and authentication preferences. This QR code doesn't sign in a worker. | In the Warehouse Management app, go to **Connection setup** > **Add from QR code** |
| Sign-in QR code | Identifies the worker using their Microsoft Entra ID user account. The worker enters a PIN to authenticate. | Microsoft Entra ID sign-in page |

The codes aren't interchangeable. The Android and iOS/iPadOS restriction applies to *sign-in QR codes*, not *connection setup QR codes*. Importing connection settings from a QR code remains supported on Android, iOS/iPadOS, and Windows.

## Configure Microsoft Entra ID to support QR code authentication

Before you enable QR code sign-in in the Warehouse Management mobile app, configure it in Microsoft Entra ID. In this section, you enable the sign-in method for the appropriate worker group, issue QR codes and temporary PINs to workers, and plan how to manage those credentials and related security policies.

### Enable the method for a worker group

To use QR code authentication, an *authentication policy administrator* must first enable the method for a target worker group and configure the necessary settings. You can do this using the Microsoft Entra ID admin center or Microsoft Graph API. During this process, you configure the PIN length, code lifetime, and target worker group. Don't enable it tenant-wide by default.

For instructions, go to [How to enable the QR code authentication method in Microsoft Entra ID](/entra/identity/authentication/how-to-authentication-qr-code).

### Issue QR codes and prepare workers

An *authentication administrator* adds the sign-in method to each worker, sets activation and expiration dates, downloads the QR code, generates a temporary PIN, and prints the QR code on a card or badge. Deliver the code and temporary PIN securely. Don't print the PIN on the badge.

For instructions, go to [Add QR code authentication method for a user](/entra/identity/authentication/how-to-authentication-qr-code#add-qr-code-authentication-method-for-a-user).

> [!IMPORTANT]
> After you enable the sign-in method for a new worker, that worker must sign in using another sign-in method before signing in with a QR code for the first time. Skipping this step can cause an *Incorrect QR code* error. Learn more in [Known limitation](/entra/identity/authentication/concept-authentication-qr-code#known-limitation).

### Plan credential management and security policies

Learn how to manage lost badges, temporary codes, PIN resets, and credential removal in [Edit the QR code authentication method](/entra/identity/authentication/how-to-authentication-qr-code#edit-the-qr-code-authentication-method-for-a-user) and [Delete the QR code authentication method](/entra/identity/authentication/how-to-authentication-qr-code#delete-the-qr-code-authentication-method-for-a-user).

Conditional Access remains enforced. QR code and PIN alone can't satisfy MFA. Policies requiring device signals unavailable in the non-brokered flow can block access. Review [Entra ID QR code security practices](/entra/identity/authentication/concept-authentication-qr-code#best-security-practices-to-implement-with-qr-code-authentication) with your administrators. Don't disable required protections to make sign-in work.

## Enable QR code sign-in in the Warehouse Management mobile app

After you enable QR code authentication for the worker group and configure the necessary settings, follow these steps on an Android or iOS/iPadOS device to enable QR code sign-in in the Warehouse Management mobile app by using its local settings:

1. On your mobile device, open the Warehouse Management mobile app.
1. Select **Tap to change**, choose the connection, and select **Edit connection settings**.
1. On the **Edit connection** screen, make the following settings:
    - **Authentication method** – Set to *Username and password*. This authentication method supports both traditional username and password sign-in and QR code and PIN sign-in.
    - **QRCode** – Set to *Yes*. With this setting, the app requests QR code sign-in when interactive authentication is needed. It doesn't force reauthentication or override tenant policies.

1. Set the remaining connection fields, such as the environment URL and company, as described in [Manually configure the application](install-configure-warehouse-management-app.md#config-manually).
1. Select **Save**.

QR code authentication is *non-brokered* and browser-based. The app handles broker selection automatically when you enable **QRCode**. The UI doesn't require a separate broker setting.

## Mass deploy the QR code sign-in preference

Instead of manually configuring each connection in the app, you can mass deploy the QR code sign-in preference to Android and iOS/iPadOS devices by creating and distributing a connection configuration JSON file. Don't deploy `"PreferredAuthMethod": "QRCode"` to Windows devices. You can distribute the JSON code using a mobile device management (MDM) solution (such as Intune or SOTI) or by creating a *connection setup QR code* and scanning it in the app.

To create a connection configuration JSON file that specifies the QR code sign-in preference, include the `"PreferredAuthMethod": "QRCode"` setting. This setting ensures that the Warehouse Management mobile app prioritizes QR code authentication for all specified connections. The following JSON example uses `"ConnectionType": "UsernamePassword"` and `"UseBroker": false` for the non-brokered flow. It uses the Microsoft-provided global application. Replace the environment URL and company code with your values.

```json
{
    "ConnectionList": [
        {
            "ConnectionName": "Contoso",
            "Company": "YOUR_COMPANY_CODE",
            "ActiveDirectoryResource": "https://contoso.operations.dynamics.com",
            "AuthCloud": "AzureGlobal",
            "ConnectionType": "UsernamePassword",
            "PreferredAuthMethod": "QRCode",
            "UseBroker": false
        }
    ]
}
```

Learn more about how to create connection configuration JSON files in [Connection settings reference for the Warehouse Management mobile app](warehouse-app-connection-settings.md).

Learn more about how to distribute connection configuration JSON files using a *connection setup QR code* in [Import connection settings from a QR code](warehouse-app-qr-code.md).

Learn more about how to distribute connection configuration JSON files using an MDM solution in [Mass deploy the mobile app with user-based authentication](warehouse-app-intune-user-based.md). Deploy the complete JSON through the **ConnectionsJson** managed configuration key in Intune or another compatible MDM provider, such as SOTI. `PreferredAuthMethod` is a connection property, not a separate MDM key. Teams and Managed Home Screen settings such as `preferred_auth_config` aren't Warehouse Management mobile app configuration keys. Target Android and iOS/iPadOS devices that meet the [prerequisites](#prerequisites). MDM distributes settings, not authentication. It doesn't issue codes, provision PINs, or sign workers in. Don't put credentials or tokens in `ConnectionsJson`.

> [!IMPORTANT]
> Before you mass deploy QR code sign-in, run a pilot project to test on representative devices. Cover onboarding, camera access, PIN changes, worker mapping, sign-out, and lost-badge recovery. Keep existing protections active. Evaluate new Conditional Access policies with [report-only mode](/entra/identity/conditional-access/concept-conditional-access-report-only) where appropriate.

## Sign in to the Warehouse Management mobile app using a QR code

### Sign in as a worker on a mobile device

To sign in as a worker on an Android or iOS/iPadOS device using a *sign-in QR code*, follow these steps:

1. On your mobile device, open the Warehouse Management mobile app.
1. Allow camera access if prompted and scan the *sign-in QR code* issued to you.
1. Enter your PIN. If you're using a temporary PIN, follow the prompts to change it.
1. After Microsoft Entra ID authenticates you, complete the Supply Chain Management worker sign-in if required.

You can remove the need for a separate worker sign-in by assigning a [default mobile device user account](mobile-device-work-users.md#set-wma-users) in Supply Chain Management.

Before handing over a shared device, end your worker session and sign out as required by your organization. Learn more in [Log off and Sign out are different actions](warehouse-app-user-based-auth-faq.md#log-off-sign-out).

## What the Warehouse Management mobile app controls

The Warehouse Management mobile app requests authentication through the Microsoft Authentication Library (MSAL). Microsoft Entra ID handles the sign-in flow.

| Area | Responsibility |
| --- | --- |
| Requesting QR code sign-in | The mobile app provides the **QRCode** connection option and the `PreferredAuthMethod` JSON parameter. |
| Sign-in pages and prompts | Microsoft Entra ID owns the interface and prompt sequence. The mobile app can't customize them or substitute a company-specific authentication flow. |
| QR codes and PINs | Administrators manage credentials in Microsoft Entra ID. The mobile app doesn't issue, reset, or validate them. |
| Access decisions | Microsoft Entra ID evaluates authentication and Conditional Access. Your organization owns policies, licensing, and device management. The mobile app can't bypass these controls. |
| Sessions and tokens | Standard MSAL token handling applies. The mobile app QR preference doesn't control token lifetime or sign-in frequency. |
| Warehouse access | Supply Chain Management roles and worker settings control permissions in the mobile app. |

For branding, use only the options supported by [Microsoft Entra ID company branding](/entra/fundamentals/how-to-customize-branding). The mobile app adds no QR sign-in UI customization.

Clearing the local authentication state can require a new sign-in. QR code authentication doesn't preserve erased tokens. Learn more in [MSAL token caching](/entra/identity-platform/msal-acquire-cache-tokens).

<a name="clouds"></a>

## Cloud availability

The availability of this feature depends on your Microsoft Entra ID tenant's cloud, not the device's physical region. The mobile app setting can't enable an authentication method that isn't available in your cloud.

As of September 14, 2026, Microsoft Graph lists the [QR code/PIN authentication-method API](/graph/api/qrcodepinauthenticationmethod-get?view=graph-rest-1.0&preserve-view=true) and [QR code/PIN policy API](/graph/api/qrcodepinauthenticationmethodconfiguration-get?view=graph-rest-1.0&preserve-view=true) as available in Global, but not in the following clouds:

- US Government L4 (GCC High)
- US Government L5 (DoD)
- China operated by 21Vianet

These are API availability statements, not a Warehouse Management mobile app sign-in support matrix. Microsoft 365 GCC uses [worldwide endpoints](/graph/deployments) and must be evaluated separately from GCC High and DoD.

Cloud availability can change. Check the current Microsoft Entra ID and Microsoft Graph documentation, and confirm Warehouse Management mobile app support for your deployment before enabling QR code sign-in in government or China environments. Support for ordinary Warehouse Management mobile app sign-in doesn't establish QR code sign-in support.

## Related information

- [User-based authentication for the Warehouse Management mobile app](warehouse-app-authenticate-user-based.md)
- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
- [QR code authentication in Microsoft Entra ID](/entra/identity/authentication/concept-authentication-qr-code)
- [How to enable QR code authentication in Microsoft Entra ID](/entra/identity/authentication/how-to-authentication-qr-code)
- [Video overview - QR Code Login for Frontline Workers](https://www.youtube.com/watch?v=q7e_oigPMN4)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
