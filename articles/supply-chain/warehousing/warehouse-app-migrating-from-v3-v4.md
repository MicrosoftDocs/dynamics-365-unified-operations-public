---
title: Migrate the Warehouse Management mobile app from V3 to V4 (preview)
description: Learn how to migrate from Warehouse Management mobile application from version 3 (V3) to version 4 (V4). The article includes information about compatibility, requirements, and the timeline.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 06/12/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Migrate the Warehouse Management mobile app from V3 to V4 (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

In June 2025, Microsoft will begin to [roll out](#rollout) version 4 (V4) of the Warehouse Management mobile app. This version introduces significant improvements and new features to enhance the user experience and the app's performance.

For V4, we rewrote the code of the Warehouse Management mobile app by using more modern technology that adds the following benefits:

- **Enhanced performance** – Improved application responsiveness and stability.
- **Better customer support capabilities** – Faster issue resolution and customer assistance.
- **Future-ready architecture** – Streamlined development of new features and integrations.

If you have any feedback about the preview version of this app, please send us email at [D365WMA-feedback@microsoft.com](mailto:D365WMA-feedback@microsoft.com).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## New features in V4

The following subsections summarize the key new features and improvements that are introduced in V4 of the Warehouse Management mobile app.

### Camera improvements

V4 provides improved camera scanning capabilities. Here are some examples:

- **Faster scanning** – Scan speed and accuracy are dramatically improved.
- **Expanded bar code support** – The app now supports a wider range of bar code formats. Learn more in [Scan bar codes using a camera in the Warehouse Management mobile app](scan-bar-codes-using-a-camera.md).
- **Multiple bar code support** – Scan multiple bar codes in a single operation.
- **Hardware independence** – There's less dependency on physical bar code scanners in environments where camera scanning is viable.

### Customizable themes

V4 provides an enhanced user experience through comprehensive theming options. Here are some examples:

- **Eleven unique themes** – A complete set of professionally designed themes is available.
- **Dual-mode support** – Each theme is available in both dark mode and light mode.
- **Unified settings** – Theme preferences are managed through the **Settings** interface.

### Enhanced audio experience

V4 offers expanded audio customization for improved user interaction.

- **Over 15 sound combinations** – An extensive library of notification and interaction sounds is available.
- **Personalization** – Workers can customize their device audio experience.
- **Centralized configuration** – Sound settings are integrated with theme preferences.

### Advanced diagnostics

V4 supports comprehensive diagnostic capabilities for improved troubleshooting and maintenance. Here are some examples:

- **Wi-Fi diagnostics**

    - **Self-diagnostic capabilities** – Each device can independently assess its network connectivity.
    - **Service ping tests** – Verification of connectivity to critical services is automated.
    - **Proactive monitoring** – Detect network-related issues early.

- **Local logging system**

    - **Human-readable logs** – The log format is improved for easier troubleshooting.
    - **Filtering capabilities** – Advanced log filtering allows for targeted analysis.
    - **Export functionality** – Easily export the log for support and analysis purposes.

- **Accessible scan testing**

    - **Simplified access** – Scan test functionality doesn't require developer menu navigation.
    - **User-friendly interface** – The testing process is streamlined for users.

## Migration information

### System requirements

The system requirements for V4 are the same as the [system requirements for V3](install-configure-warehouse-management-app.md), except on Android devices. V4 requires Android 7 or later, whereas V3 supports Android 5 and later. Devices that run older Android versions can continue to use V3 until the May 2026 end-of-support date.

If you're running a newer version of Android, then we recommend using V4 because it provides better compatibility than V3 on newer systems.

### Compatibility between V3 and V4

When you migrate from V3 to V4, the following compatibility features are available:

- **Customizations are preserved** – All customizations and configurations from V3 are fully compatible with V4 and remain functional. 
- **Connection settings can be preserved** – Your existing connection settings from V3 are automatically migrated when you upgrade to V4. This only works if you are upgrading from v3.0.8 or higher to v4. We strongly recommend updating to V3.0.8 or later before upgrading to V4. To preserve your connection settings, don't uninstall V3, download the V4 installer to your device, and be sure to select the **Upgrade** option when you run it. If you uninstall V3 and then install V4, your connection settings will be lost. Connection settings are only preserved during an upgrade, not during a fresh installation. If manual reconfiguration is required, QR code generation and scanning capabilities (camera or beam scanner) are available for easy setup. Learn more in [Use a QR code to connect the mobile app to Supply Chain Management](warehouse-app-qr-code.md).

### Authentication

- **One-time reauthentication** – Admins must complete a single authentication process for each device that they migrate to V4. After a device is successfully migrated, it remains authenticated. No further reauthentication is required.
- **Windows platform configuration** – For Windows applications, you must follow these steps to add a new redirect URI to your Azure application registration.

    1. Open the [Azure portal](https://portal.azure.com).
    1. Go to **App Registrations**.
    1. Select your Microsoft Entra ID registration.
    1. Go to **Manage** \> **Authentication**.
    1. Select **Add a platform**, and then select **Mobile and desktop applications**.
    1. In the **Custom redirect URIs** field, enter `ms-appx-web://microsoft.aad.brokerplugin/{clientId}` (where *{clientId}* is your Microsoft Entra client ID).

### iOS limitations

Device code authentication isn't available on iOS platforms. Username/password authentication is the only supported method for iOS devices.

### On-premises limitations

For on-premises installations of Supply Chain Management, device code authentication isn't supported for iOS or Android devices; only username/password authentication is available for these platforms.

## <a name="rollout"></a>Rollout schedule and transition period support

### V4 public preview

- **Date of availability** – End of June 2025
- **Distribution channels**
    – **Windows** – [App Center](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-windows/distribution_groups/official%20release)
    - **Android** – Google Beta Testers and [App Center](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-android/distribution_groups/official%20release)

- **Concurrent operation** – During the transition period, V3 and V4 can operate simultaneously in the same warehouse environment without conflicts, as long as they are installed on separate devices. This allows for a phased rollout of V4 without disrupting ongoing operations. Please note that V3 and V4 cannot be installed on the same device at the same time. We recommend that you roll out the new version gradually rather than installing it on all devices at once.

- **Authentication benefits for early adopters** – Each device that you update from V3 to V4 must be reauthenticated after the initial update. However, you won't need to reauthenticate the device again when updating to future versions of V4.

### V4 general availability for Android and Windows

- **Date of availability** – End of August 2025 (estimated)

- **Distribution channels**
    - **Windows** – Microsoft Store and [App Center](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-windows/distribution_groups/official%20release)
    - **Android** – Google Play and [App Center](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-android/distribution_groups/official%20release)

- **Concurrent operation** – V3 and V4 can operate simultaneously in the same warehouse environment without conflicts, but we recommend moving to V4 when it becomes generally available.

### V4 general availability for iOS

- **Date of availability**: End of November 2025 (estimated)
 **Distribution channel** – Apple App Store

### V3 support timeline

- **End of support** – May 2026 (estimated).
- **Feature development** – No new features will be developed for V3.
- **Maintenance** – Critical bug fixes and security updates continue until the end of support.

### Install Warehouse Management mobile app V4 on Windows

Before you can install the app on Windows, you must install the certificate that is used to sign the app. For instructions, go to [Install Warehouse Management mobile app V4 on Windows (preview)](warehouse-app-install-certificate.md).
