---
title: User-based authentication for the Warehouse Management mobile app
description: Learn how to configure the Warehouse Management app to connect to your Dynamics 365 Supply Chain Management environment using user-based authentication.
author: pefreita
ms.author: pefreita
ms.topic: how-to
ms.date: 09/02/2026
ms.reviewer: kamaybac
ms.search.form: SysAADClientTable, WHSMobileAppField, WHSMobileAppFieldPriority, WHSRFMenu, WHSRFMenuItem, WHSWorker
ms.custom:
  - bap-template
  - sfi-ropc-nochange
---

# User-based authentication for the Warehouse Management mobile app

[!INCLUDE [banner](../includes/banner.md)]

The Warehouse Management mobile app supports two types of user-based authentication:

- **[Username/password authentication](#usernamePasswordFlow)** – The standard method for new and existing deployments. It works without any extra configuration and doesn't require a companion app.
- **[Device code flow authentication](#deviceCodeFlow)** – A legacy method that remains available for deployments that still use it. Plan a move to username/password authentication, because Microsoft Entra ID security defaults block device code flow in new tenants.

To work out which combination of accounts and sign-in methods fits your warehouse, start with [Choose an authentication approach](#scenarios).

> [!NOTE]
> Give each Microsoft Entra ID account that signs in to the app only the permissions that it needs for warehousing tasks. Use accounts that are scoped to warehouse mobile device user activities, and don't sign in to devices with admin accounts.

<a name="scenarios"></a>

## Choose an authentication approach

Two decisions determine how you set up authentication. Answer them in order. The following sections give general guidance about what each combination supports. Your IT department makes the final decision, based on your organization's security policies.

1. **Whose identity does the app sign in with?** Use either a *worker identity*, where every warehouse worker has their own Microsoft Entra ID account, or a *device identity*, where a shared account such as `device1@contoso.com` represents the device itself.
1. **Where is the sign-in completed?** Choose either *locally* (on the warehouse device) or *remotely* (on a separate machine such as an admin's PC). Remote sign-in is typically used when devices are deployed at a site that's far from the people who hold the credentials.

The following table summarizes the four combinations.

| | Local sign-in (on the device) | Remote sign-in (on another machine) |
| --- | --- | --- |
| **Worker identity** | <p>[Recommended for most deployments](#worker-local).</p><p>Use username/password; QR code and PIN; multifactor authentication (MFA); or any other method that your tenant supports.</p> | <p>[Supported](#worker-remote).</p><p>The same methods work. [Device code flow](#deviceCodeFlow) is also possible, but it isn't recommended.</p> |
| **Device identity** | <p>[Supported for shared devices](#device-local).</p><p>Workers identify themselves with a mobile device user account after the app is authenticated. Conditional Access signals are less meaningful, because the account represents a device instead of a person.</p> | <p>[Use with care](#device-remote).</p><p>Prefer username/password with MFA, so that you can revoke the session remotely if the device is lost.</p> |

In every combination, each warehouse worker still has a *warehouse worker* record with one or more *mobile device user accounts* in the Warehouse management module. The Microsoft Entra ID account authenticates the app with Supply Chain Management. The mobile device user account identifies the person who does the work. Learn more in [Mobile device user accounts](mobile-device-work-users.md).

<a name="worker-local"></a>

### Worker identity, local sign-in

*Example:* At the Contoso Seattle distribution center, each of the 40 pickers has a Microsoft Entra ID account, such as `maria@contoso.com`. Handhelds are stored in a charging rack. A worker takes any device from the rack and signs in with their own credentials.

It works like this:

1. The worker signs in on the device with their Microsoft Entra ID credentials. Use whichever method suits your security requirements: username/password, [QR code and PIN](#usernamePasswordFlow), or MFA.
1. If a [default user ID](mobile-device-work-users.md#set-wma-users) is configured for the worker's warehouse worker record, this single sign-in authenticates the app and signs the worker in as a warehouse worker in one step.
1. Optionally, [brokered authentication](#sso) shares the same Microsoft Entra ID session with other apps on the device, such as Microsoft Teams or Outlook. This step is an advanced option, and it isn't required.

This combination gives you the strongest identity controls, because every action traces back to a named person, and Conditional Access policies apply to a real user.

<a name="worker-remote"></a>

### Worker identity, remote sign-in

*Example:* Contoso opens a small satellite warehouse with no on-site IT staff. An administrator at headquarters completes the initial sign-in for each device before shipping the device to the site.

The same methods that are available for local sign-in also work here. You can also use [device code flow](#deviceCodeFlow). However, Microsoft no longer recommends it because it's a common target of phishing attacks. Your IT department can decide whether it's acceptable in your environment.

Because the person who enters the credentials often isn't the person who uses the device, plan for the following points:

- Prefer a method that lets the worker complete their own sign-in on the device, even when the device is configured remotely.
- Ensure that you can [revoke sessions](#revoke) for a single account without affecting other workers.

<a name="device-local"></a>

### Device identity, local sign-in

*Example:* Contoso mounts terminals on forklifts. Each terminal authenticates with a shared Microsoft Entra ID account, such as `device1@contoso.com`. Drivers then enter their own mobile device user account credentials to start work.

It works like this:

1. The admin configures the app with [username/password](#usernamePasswordFlow) authentication by using the device's Microsoft Entra ID account.
1. After the app is authenticated, workers sign in with their mobile device user account credentials (user ID and password).
1. When a worker signs out, the app stays authenticated with Supply Chain Management and shows the worker sign-in page for the next person.

This combination works best when many workers share a device, and when you don't want to create a Microsoft Entra ID account for every worker. Be aware of the following limitations:

- Conditional Access policies are harder to apply in a meaningful way. The signed-in identity is a device, not a person, so policies that evaluate user risk or per-user MFA don't produce useful results.
- Supply Chain Management attributes app authentication to the device account. Worker-level traceability comes from the mobile device user account instead.
- Give the device account only the permissions that warehouse mobile device work requires. Learn more in [Mobile device user accounts](mobile-device-work-users.md).

<a name="device-remote"></a>

### Device identity, remote sign-in

*Example:* Contoso ships preconfigured terminals to a third-party logistics provider. An administrator at headquarters authenticates each device before it leaves.

This combination behaves like [worker identity with remote sign-in](#worker-remote), but the risk is higher because many people use a single shared account and the device is out of your physical control.

Take the following precautions:

- Use username/password authentication, ideally with MFA. [Device code flow](#deviceCodeFlow) isn't recommended for this combination, but whether it's acceptable is a decision for your IT department to make, based on your security policies.
- Use a separate Microsoft Entra ID account for each device, rather than one account for all devices. You can then disable or [revoke sessions](#revoke) for a single lost device without disrupting the rest of the fleet.
- Keep the device account's permissions strictly limited to warehouse mobile device work.

<a name="licensing"></a>

## Licensing considerations

The Warehouse Management mobile app doesn't introduce its own identity licensing requirements. It requires only that your organization has a Microsoft Entra ID identity provider, and standard Microsoft Entra licensing terms apply.

Features that you layer on top of sign-in have their own licensing requirements. Check the requirements for each feature that you plan to use:

- **Conditional Access** – See [Microsoft Entra Conditional Access](/entra/identity/conditional-access/overview).
- **QR code and PIN sign-in** – See [Prerequisites to enable the QR code authentication method](/entra/identity/authentication/how-to-authentication-qr-code#prerequisites-to-enable-the-qr-code-authentication-method).
- **Microsoft Entra plans in general** – See [Microsoft Entra ID licensing](/entra/fundamentals/licensing).

> [!IMPORTANT]
> Using a shared device identity doesn't reduce the number of licenses that you need. A device account such as `device1@contoso.com` authenticates the app, but licensing for Supply Chain Management follows the people who do the work. If you license warehouse workers as frontline workers, you still need a license for each worker who uses the app, even when many workers share one device account.

Confirm your specific entitlements with your licensing contact and the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544). This article doesn't replace either. Learn more in [Microsoft Product Terms](https://go.microsoft.com/fwlink/?linkid=2309718).

<a name="usernamePasswordFlow"></a>

## Username/password authentication

When you use username/password authentication, each human worker must enter the Microsoft Entra ID username and password associated either with the device or with themselves (depending on the [approach](#scenarios) you chose). They might also need to enter a mobile device user account ID and password, depending on their [warehouse worker record setup](mobile-device-work-users.md).

Microsoft recommends username/password authentication for all new and existing deployments. It works without any configuration: the app signs workers in through the system browser or a native web view, and it doesn't need Microsoft Authenticator, Intune Company Portal, or any other companion app. Most frontline deployments need nothing more than this.

If you later want single sign-on or Conditional Access policies that depend on device signals, see [Advanced: brokered authentication and single sign-on](#sso).

Microsoft Entra ID also offers *QR code and PIN sign-in*, which lets workers sign in quickly on shared devices by scanning a QR code and entering a PIN, instead of typing a full username and password every time. This flow works without Microsoft Authenticator or Intune Company Portal. Licensing and tenant prerequisites are listed in [Prerequisites to enable the QR code authentication method](/entra/identity/authentication/how-to-authentication-qr-code#prerequisites-to-enable-the-qr-code-authentication-method).

> [!NOTE]
> QR code and PIN sign-in has the following limitations:
>
> - It's available only on Android and iOS/iPadOS devices. It isn't available on Windows devices.
> - In the current version of the Warehouse Management mobile app, it works only when the app authenticates through the browser (browser-based authentication). It isn't supported when a broker handles the sign-in natively on the device. Therefore, you can't combine it with brokered authentication yet. Broader QR code sign-in support is planned for a future version of the app.
> - A worker must complete their first sign-in by using another method before they can use QR code and PIN sign-in.
>
> This QR code is a Microsoft Entra ID sign-in credential for workers. It's not the same as the QR code that you use to distribute connection settings to devices. Learn more in [Read connection settings from a QR code](warehouse-app-qr-code.md).

<a name="create-service"></a>

## Use a custom application registration

By default, the app uses a global application that's provided and maintained by Microsoft, and no application registration is required.

You need to register your own application in Microsoft Entra ID only if you connect to an on-premises environment, connect to a cloud other than Azure Global, or have specific requirements that the global application doesn't meet. For the procedure, see [Create a custom application registration for the Warehouse Management mobile app](warehouse-app-custom-app-registration.md).

<a name="user-azure-ad"></a>

## Set up employee, user, and warehouse worker records in Supply Chain Management

Before workers can sign in by using the mobile app, each Microsoft Entra ID account that you assign to the enterprise app in Azure must have a corresponding employee record, user record, and warehouse worker record in Supply Chain Management. For information about how to set up these records, see [Mobile device user accounts](mobile-device-work-users.md).

<a name="sso"></a>

## Advanced: brokered authentication and single sign-on

*Brokered authentication* is an advanced capability. You don't have to use it. The app signs workers in through the system browser or a native web view, and it doesn't need Microsoft Authenticator, Intune Company Portal, or any other companion app.

Consider it only if you want one of the following things:

- **Single sign-on (SSO)** – Workers sign in to the app without entering a password, because the app reuses credentials from another app on the device.
- **Conditional Access policies that depend on device signals** – For example, a policy that requires a compliant or managed device. A broker supplies those signals.

If you don't need either, you can ignore brokered authentication entirely.

If you already use brokered authentication, keep it. Nothing about it is deprecated, and no change is required. It's described as advanced because it's optional, not because it's going away.

For the concepts, requirements, and setup steps, see [Brokered authentication and Conditional Access](warehouse-app-conditional-access-enable.md).

> [!NOTE]
> SSO requires [username/password](#usernamePasswordFlow) authentication. It doesn't work with [device code flow](#deviceCodeFlow).
>
> Two other limitations apply when a broker handles sign-in:
>
> - The Warehouse Management mobile app *doesn't* support [shared device mode](/entra/identity-platform/msal-shared-devices). To let multiple workers share a device, use the [device identity](#device-local) approach instead.
> - QR code and PIN sign-in isn't available. It currently requires browser-based authentication, as described in [Username/password authentication](#usernamePasswordFlow).

<a name="device-registration"></a>

## Device registration requirements

The Warehouse Management mobile app works on a device in any Microsoft Entra ID registration state. You can sign in on all of the following types of devices:

- Microsoft Entra joined devices
- Microsoft Entra registered devices
- Devices that aren't joined
- Devices that aren't registered at all, including a device that's new and has never been registered

You don't have to join or register a device before workers can sign in.

Two things can still introduce a registration requirement, and neither comes from the app itself:

- **Your Conditional Access policies.** If a policy requires a specific device state or compliance status, that requirement comes from your policy. Learn more in [Brokered authentication and Conditional Access](warehouse-app-conditional-access-enable.md).
- **Brokered authentication.** A broker passes device signals to Microsoft Entra ID by using a device-bound token, so it works with a registered device. The broker can perform the registration itself during the first sign-in, so this requirement usually isn't something that you set up in advance.

Learn more in [What is device identity in Microsoft Entra ID?](/entra/identity/devices/overview).

<a name="revoke"></a>

## Remove access for a device that uses user-based authentication

If a device is lost or compromised, revoke its access to Supply Chain Management immediately. Disabling the associated Microsoft Entra ID user account revokes access for all devices that use that account. This limitation is why you should use a separate account for each device or each worker, as described in [Choose an authentication approach](#scenarios). It lets you isolate and revoke access for a single device without affecting others.

To revoke access, follow these steps:

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. On the left navigation pane, select **Microsoft Entra ID**, and ensure that you're in the correct directory.
1. In the **Manage** list, select **Users**.
1. To open the user's profile, find the user account that's associated with the device or worker, and select the name.
1. On the toolbar, select **Revoke sessions** to revoke the user account's sessions.

> [!NOTE]
> Depending on how you set up your authentication system, you might also want to change the user account's password or completely disable the user account.

<a name="deviceCodeFlow"></a>

## Device code flow authentication (not recommended)

> [!NOTE]
> This section describes a legacy authentication method. It's documented for deployments that already use it. For new deployments, use [username/password authentication](#usernamePasswordFlow).

Device code flow is a two-step sign-in method that was originally designed for devices that don't provide a web browser. Microsoft doesn't recommend it for the Warehouse Management mobile app for the following reasons:

- **It's a frequent target of phishing attacks** – A threat actor can ask a victim to sign in with a device code that the attacker generated, and then use the resulting token to access the victim's account from the attacker's own device. Microsoft Entra ID has no reliable way to verify that the person who enters the code is signing in from the device that generated it.
- **It's blocked by default in new tenants** – Starting July 1, 2026, Microsoft Entra ID security default settings block device code flow on new tenants. This behavior commonly affects new tenants that are created for testing purposes. If you create a new tenant to test the Warehouse Management mobile app, expect device code flow to be blocked by default. Existing tenants aren't automatically affected unless they already have security defaults enabled.
- **It isn't available everywhere** – Device code flow isn't supported on iOS, and it isn't supported for Android devices that connect to on-premises environments.
- **It doesn't support SSO** – It can't be combined with [brokered authentication](warehouse-app-conditional-access-enable.md).

If your environment still depends on device code flow (for example, because you use test scripts or workflows that aren't updated yet), an admin can unblock it for the tenant by disabling security defaults. Because security defaults protect the whole tenant, treat this change as a temporary step while you update your setup to use username/password authentication. For more information, see [Microsoft Entra security defaults](/entra/fundamentals/security-defaults).

### How device code flow works

When you use device code authentication, the Warehouse Management mobile app generates and shows a unique device code. The admin who sets up the device enters this device code into an online form, along with the credentials (name and password) for a Microsoft Entra ID user account. This account can represent either the device itself or the human worker who signs in, depending on how the admin implements the system. In some cases, depending on how the Microsoft Entra ID user account is configured, the admin might also have to approve the sign-in. In addition to the unique device code, the mobile app shows the URL where the admin must enter the code and the credentials for the Microsoft Entra ID user account.

### Requirements and restrictions

If you must temporarily continue to use device code authentication, be aware of the following extra requirements and restrictions:

- Create a unique Microsoft Entra ID user account for each device or human worker. In addition, *strictly limit these accounts so that they can perform only warehouse mobile device user activities*.
- While a worker is signing in by using the Warehouse Management mobile app, the app shows a generated device code. This code expires after 15 minutes and is then hidden by the app. If the code expires before sign-in is completed, the worker must generate a new code by selecting **Connect** again in the app.
- How long a device stays authenticated is controlled by your Microsoft Entra ID token lifetime and Conditional Access policies, not by the app. When the tokens for a device expire or are revoked, the device must be authenticated again. Learn more in [Refresh tokens in the Microsoft identity platform](/entra/identity-platform/refresh-tokens).
- Single sign-on (SSO) isn't supported when you use device code flow authentication together with a mobile mass deployment (MDM) system (such as Intune) to distribute the Warehouse Management mobile app. You can still use an MDM system to deliver the app to each mobile device and deliver a `connections.json` file that sets up connections using device code. The only difference is that workers must manually sign in when they start to use the app. (This step is required only once.)

### Move from device code flow to username/password authentication

To move an existing deployment away from device code flow, follow these steps:

1. Confirm that the Microsoft Entra ID accounts that the devices use can sign in with a username and password. If you use the global application that Microsoft provides, nothing else is required. If you use [a custom application registration](#create-service), also confirm that it allows public client flows.
1. Optional: If you want SSO, enable [brokered authentication](warehouse-app-conditional-access-enable.md). On Android and iOS, that requires a broker app on the device.
1. Update your connection settings to specify `"ConnectionType": "UsernamePassword"` (and, when you use a broker, `"UseBroker": true`). Then redistribute them through your MDM provider, a `connections.json` file, or a QR code. Learn more in [Connection settings reference](warehouse-app-connection-settings.md#connection-file-qr) and [Choose how to distribute connection settings](install-configure-warehouse-management-app.md#distribute).
1. Sign in one time on each device to complete the authentication with the new method.

## Related information

- [User-based authentication FAQ](warehouse-app-user-based-auth-faq.md)
- [Brokered authentication and Conditional Access](warehouse-app-conditional-access-enable.md)
- [Create a custom application registration](warehouse-app-custom-app-registration.md)
- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
