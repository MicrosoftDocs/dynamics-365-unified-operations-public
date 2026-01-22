---
title: Migrate the Warehouse Management mobile app from V3 to V4
description: Learn how to migrate from Warehouse Management mobile application from version 3 (V3) to version 4 (V4). The article includes information about compatibility, requirements, and the timeline.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 01/21/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Migrate the Warehouse Management mobile app from V3 to V4

[!include [banner](../includes/banner.md)]

Version 4 (V4) of the Warehouse Management mobile app brings significant improvements and new features that enhance the user experience and the app's performance.

For V4, Microsoft rewrote the code for the Warehouse Management mobile app to take advantage of the newest software technology. V4 offers the following benefits:

- **Enhanced performance** – Improved application responsiveness and stability.
- **Better customer support capabilities** – Faster issue resolution and customer assistance.
- **Future-ready architecture** – Streamlined development of new features and integrations.

> [!TIP]
>
> - The [Migration information](#migration-information) section provides important advice that can help you avoid unexpected disruptions during the migration process.
> - The [Rollout and transition period support](#rollout) section provides the rollout schedule and download details.

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

The system requirements for V4 are the same as the [system requirements for V3](install-configure-warehouse-management-app.md), except for Android devices. V3 supports Android 5 and later, but V4 requires Android 7 or later. Devices that run older Android versions can continue to use V3 until the May 2026 end-of-support date. However, no new releases or feature updates are available for V3, and all newly reported issues will be resolved only in V4.

If you're running a newer version of Android, you should use V4 because it provides better compatibility than V3 on newer systems.

### Compatibility between V3 and V4

V4 is designed to support a smooth transition from V3. The following considerations summarize what stays compatible during the migration and what you should plan for when upgrading.

- **Customizations are preserved** – All customizations and configurations from V3 are fully compatible with V4 and remain functional.
- **Connection settings can be preserved** – When you upgrade the Warehouse Management mobile app from version 3.0.8 or higher to V4, your existing connection settings are automatically migrated to V4. The settings aren't migrated from older versions of V3, so if you're running version 3.0.7 or older, upgrade to version 3.0.8 or later before upgrading to V4. To preserve connection settings, don't uninstall V3. Instead, just download the V4 installer to the device and select the **Upgrade** option when running it. If you uninstall V3 and then install V4, your connection settings are lost. Connection settings are only preserved during an upgrade, not during a fresh installation. If manual reconfiguration is required, you can generate and scan QR codes for easy setup. Learn more in [Use a QR code to connect the mobile app to Supply Chain Management](warehouse-app-qr-code.md).
- **Concurrent operation** – V3 and V4 can operate simultaneously in the same warehouse environment without conflicts provided they're installed on separate devices. This allows for a phased rollout of V4 without disrupting ongoing operations. However, you can't run V3 and V4 on the same device at the same time.

### Authentication

When you update to V4, the following authentication changes apply:

- **One-time reauthentication** – App users must complete a single authentication process the first time they use the app on each device that is migrated to V4. After a device is successfully migrated, it remains authenticated. You won't need to reauthenticate the device again when updating to future versions of V4.
- **Windows platform configuration** – For Windows applications, follow these steps to add a new redirect URI to your Azure application registration:
    1. Open the [Azure portal](https://portal.azure.com).
    1. Go to **App Registrations**.
    1. Select your Microsoft Entra ID registration.
    1. Go to **Manage** \> **Authentication**.
    1. Select **Add a platform**, and then select **Mobile and desktop applications**.
    1. In the **Custom redirect URIs** field, enter `ms-appx-web://microsoft.aad.brokerplugin/{clientId}` (where *{clientId}* is your Microsoft Entra client ID).

### iOS limitations

Device code authentication isn't available on iOS platforms. Username/password authentication is the only supported method for iOS devices.

It isn't possible to connect iOS devices to on-premises environments of Supply Chain Management.

### On-premises limitations

For on-premises installations of Supply Chain Management, device code authentication isn't supported for Android devices; only username/password authentication is available for this platform.

## <a name="rollout"></a>Rollout and transition period support

Microsoft has been rolling out V4 globally for several months by progressively increasing coverage of countries and regions. Each expansion wave was carefully tested to ensure stability and readiness. We are now approaching the end of this rollout phase.

### V4 general availability schedule and sources

The general availability release of V4 is available for the following platforms on the following schedule:

- **Google Android** – Available globally now from [Google Play](https://play.google.com/store/apps/details?id=com.Microsoft.WarehouseManagement) and [Microsoft App Center](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-android/distribution_groups/official%20release)
- **Microsoft Windows** – Available globally starting in February 2026 from [Microsoft App Center](https://install.appcenter.ms/orgs/warehousing-dynamics-365/apps/dynanics-365-for-finance-and-operations-warehousing-windows/distribution_groups/official%20release).
- **Apple iOS** – Available globally starting in February 2026 from the Apple App Store. As of January 2026, it's available through [Apple Test Flight](https://testflight.apple.com/).

### V3 support timeline

Use the following timeline to plan your transition off V3 and ensure devices are migrated to V4 before support ends.

- **End of support** – May 2026 (estimated).
- **Final version** – Version 3.0.9 is the final V3 release. Any reported issues will be addressed in V4.
- **Feature development** – No new features will be developed for V3.
