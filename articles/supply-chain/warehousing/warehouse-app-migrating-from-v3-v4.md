---
title: Migrate the Warehouse Management mobile app from V3 to V4
description: Learn how to migrate from Warehouse Management mobile application from version 3 (V3) to version 4 (V4). The article includes information about compatibility, requirements, and the timeline.
author: pefreita
ms.author: pefreita
ms.topic: how-to
ms.date: 09/02/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Migrate the Warehouse Management mobile app from V3 to V4

[!INCLUDE [banner](../includes/banner.md)]

Version 4 (V4) of the Warehouse Management mobile app brings significant improvements and new features that enhance the user experience and the app's performance.

For V4, Microsoft rewrote the code for the Warehouse Management mobile app to take advantage of the newest software technology. V4 offers the following benefits:

- **Enhanced performance** – Improved application responsiveness and stability.
- **Better customer support capabilities** – Faster issue resolution and customer assistance.
- **Future-ready architecture** – Streamlined development of new features and integrations.

> [!TIP]
>
> - The [Migration information](#migration-information) section provides important advice that can help you avoid unexpected disruptions during the migration process.
> - The [V3 support timeline](#timeline) provides the rollout schedule and download details.
> - If you're migrating iOS devices, read the [Migrating from V3 to V4 for iOS](#migration-information-ios) section before you begin. Connection settings aren't preserved on iOS and Device Code authentication isn't supported.

## <a name="rollout"></a>Rollout

Microsoft has been rolling out V4 globally for several months by progressively increasing coverage of countries and regions. Each expansion wave was carefully tested to ensure stability and readiness. The rollout phase is now nearing completion.

### V4 general availability schedule and sources

The general availability release of V4 is available for the following platforms on the following schedule:

- **Google Android** – Available globally starting at the end of January 2026 from [Google Play](https://play.google.com/store/apps/details?id=com.Microsoft.WarehouseManagement) and [Microsoft App Center](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-android/distribution_groups/official%20release).
- **Microsoft Windows** – Available globally starting in February 2026 from [Microsoft App Center](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-windows/distribution_groups/official%20release).
- **Apple iOS** – The official release of WMA iOS v4 began on 23 February 2026. As of January 2026, it's available through [Apple Test Flight](https://testflight.apple.com/).

## <a name="migration-information"></a>Migration information

### System requirements

The system requirements for V4 are the same as the [system requirements for V3](install-configure-warehouse-management-app.md), except for Android devices. V3 supports Android 5 and later, but **V4 requires Android 7 or later**. Devices that run older Android versions can continue to use V3 until the May 2026 end-of-support date. However, no new releases or feature updates are available for V3, and all newly reported issues are resolved only in V4.

If you're running a newer version of Android, use V4 because it provides better compatibility than V3 on newer systems.

### Compatibility between V3 and V4

V4 supports a smooth transition from V3. The following considerations summarize what stays compatible during the migration and what you should plan for when upgrading.

- **Customizations are preserved** – All customizations and configurations from V3 are fully compatible with V4 and remain functional.
- **On Android and Windows devices, connection settings can be preserved on upgrade** – When you upgrade the Warehouse Management mobile app from version 3.0.8 or higher to V4 on Android or Windows, your existing connection settings are automatically migrated. Connection settings are only preserved during an upgrade, not during a fresh installation. To preserve settings:
    - Don't uninstall V3. Instead, download the V4 installer and select the **Upgrade** option.
    - If you're running V3.0.7 or older, first upgrade to V3.0.8 or V3.0.9, then upgrade to V4.

- **On iOS devices, connection settings aren't preserved on upgrade** – You must reconfigure connections manually after installing V4. To simplify this process, prepare QR codes in advance. Learn more in [Read connection settings from a QR code](warehouse-app-qr-code.md).
- **MDM Deployment** – If you use a mobile device management (MDM) solution to distribute the app, the connection settings are preserved when you migrate from V3.0.9 to V4, or from V4 to any later version of V4.
- **Concurrent operation** – V3 and V4 can operate simultaneously in the same warehouse environment without conflicts provided they're installed on separate devices. You can use different authentication methods for each version without conflict. This capability allows for a phased rollout of V4 without disrupting ongoing operations. However, you can't run V3 and V4 on the same device at the same time.
- **V3 requests remain active** – Microsoft doesn't block requests coming from V3. You can continue using V3 until you're ready to migrate.

> [!IMPORTANT]
> Microsoft doesn't force-update any device. When a new version of the Warehouse Management mobile app is released, Microsoft publishes it to the app stores (Microsoft Store, Google Play, and Apple App Store). The update is only downloaded to a device if auto-update is enabled in the device's store settings. If auto-update is disabled, the device continues to run its current version until an administrator or user manually triggers the update.
>
> To ensure a consistent and predictable migration across your device fleet, use a Mobile Device Management (MDM) solution, such as Microsoft Intune. Unlike app stores, an MDM provides a dedicated management channel that gives administrators full control over when and how updates are applied to each device.

### <a name="migration-information-ios"></a> Migrating from V3 to V4 for iOS

Microsoft started the official release of WMA iOS V4 on February 23, 2026. The rollout is phased, starting with a limited percentage of users and gradually increasing over time.

> [!IMPORTANT]
> iOS migration has two key differences from Android and Windows:
>
> - **Connection settings aren't preserved** – When upgrading from V3 to V4 on iOS, you lose existing connection settings. You must manually reconfigure connections after the upgrade. To simplify this process, generate QR codes in advance. Learn more in [Read connection settings from a QR code](warehouse-app-qr-code.md).
> - **Device Code authentication isn't supported on iOS V4** – Before upgrading, ensure your environment is configured for username/password authentication.

#### Before you upgrade iOS devices

1. Verify that username/password authentication is properly configured in your environment.
1. Prepare QR codes or JSON configuration files for all connections that you need to reconfigure.
1. If you want to validate V4 behavior before the full rollout, join [Apple TestFlight](https://testflight.apple.com/) to test the V4 version.
1. If you want to prevent automatic updates, disable auto-update in your App Store or MDM configurations.

### If you need to return to V3

If critical problems arise while you're testing V4, you can return to V3.0.9. The following conditions apply:

- **Regional rollback** – You can't downgrade a region after migrating it.
- **App downgrade** – You can downgrade individual devices from V4 to V3.0.9 without problem to ensure operational continuity.
- **Download links** – Use the following links to download V3.0.9 installers for Android and Windows devices:
    - [Downgrade to V3 for Android](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-android/distribution_groups/official%20release)
    - [Downgrade to V3 for Windows](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-windows/distribution_groups/official%20release)

- **To install the Microsoft Certificate from an MSIX bundle file** – Follow these steps:
    1. Go to the folder that contains the MSIX bundle folder.
    1. Right-click the MSIX and select **Properties**.
    1. In the **Properties** window, open the **Digital Signatures** tab.
    1. From the list of signatures, select the Microsoft signature.
    1. Select **Details**, and then select **View Certificate**.
    1. Select **Install Certificate**.
    1. Choose the certificate store location.
    1. Select **Local Machine** and select **Next**.
    1. Select **Trusted Root Certification Authorities**.
    1. Select **Next**, and then **Finish** to complete the certificate installation.
  
## <a name="authentication"></a>Authentication

### Authentication in cloud environments

App users must complete a single authentication process the first time they use the app on each device that is migrated to V4. After a device is successfully migrated, it stays authenticated. You don't need to reauthenticate the device when updating to future versions of V4.

### Authentication in on-premises environments

If you use an on-premises environment of Supply Chain Management, you don't need a new Entra ID account or infrastructure configuration to support V4. Continue to use your existing configuration as established for V3. However, to support Windows and Android devices, you must add a new redirect URI to your application registration for the Supply Chain Management tenant in AD FS. For V4 of the Warehouse Management mobile app, the redirect URIs are as follows:

- **Windows** – `ms-appx-web://microsoft.aad.brokerplugin/{clientId}` (where *{clientId}* is your Microsoft Entra client ID).
- **Android** – `msauth://com.Microsoft.WarehouseManagement/hpavxC1xAIAr5u39m1waWrUbsO8=`

For more information and detailed setup instructions, go to [User-based authentication for the Warehouse Management mobile app in on-premises deployments](../../fin-ops-core/dev-itpro/deployment/warehousing-onprem-userauth.md).

### Supported authentication methods

The following table summarizes the supported authentication methods for each platform and type of deployment environment (cloud or on-premises).

| Platform | Cloud environment | On-premises environment |
| --- | --- | --- |
| **Windows** | Username/password, Device code<sup>1</sup> | Username/password, Device code<sup>1</sup> |
| **Android** | Username/password, Device code<sup>1</sup> | Username/password only |
| **iOS** | Username/password only | Username/password only |

Brokered authentication isn't a separate authentication method. It's an option of username/password authentication that enables single sign-on (SSO). Learn more in [Single sign-on](warehouse-app-authenticate-user-based.md#sso).

<sup>1</sup> For backward compatibility, these platforms still support device code flow, but Microsoft no longer recommends it because it's a frequent target of phishing attacks. It's blocked by default in *new* Microsoft Entra ID tenants and doesn't support single sign-on (SSO) or brokered authentication. Use the migration to V4 as an opportunity to move these devices to username/password authentication. Learn more in [Device code flow authentication](warehouse-app-authenticate-user-based.md#deviceCodeFlow).

## <a name="timeline"></a>V3 support timeline

Use the following timeline to plan your transition from V3 and ensure devices are migrated to V4 before support ends.

- **End of support** – May 2026 (estimated).
- **Final version** – Version 3.0.9 is the final V3 release. The development team will address any reported issues in V4.
- **Feature development** – The development team won't develop new features for V3.
