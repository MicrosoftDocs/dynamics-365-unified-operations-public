---
title: Migrate the Warehouse Management mobile app from V3 to V4 (preview)
description: Learn how to migrate from Warehouse Mobile Application V3 to V4, including compatibility, requirements, and timeline.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 06/04/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Migrate the Warehouse Management mobile app from V3 to V4 (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Starting in June 2025, Microsoft will begin [rolling out](#rollout) Warehouse Management mobile app version 4 (V4). This new version introduces significant improvements and new features, enhancing the user experience and performance of the app. For V4, we rewrote the Warehouse Management mobile app using more modern technology, which adds the following benefits:

- **Enhanced performance** – Improved application responsiveness and stability
- **Better customer support capabilities** – Faster issue resolution and customer assistance
- **Future-ready architecture** – Streamlined development of new features and integrations

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## New features added in V4

The following subsections summarize the key new features and improvements introduced in V4 of the Warehouse Management mobile app.

### Camera improvements

V4 provides improved camera scanning capabilities, including:

- **Faster scanning** – Dramatically improved scan speed and accuracy.
- **Expanded barcode support** – The app now supports a wider range of barcode formats. Learn more in [Scan bar codes using a camera in the Warehouse Management mobile app](scan-bar-codes-using-a-camera.md).
- **Multiple barcode support** – Scan multiple barcodes in a single operation.
- **Hardware independence** – Reduces dependency on physical barcode scanners in environments where camera scanning is viable.

### Customizable themes

V4 provides an enhanced user experience through comprehensive theming options, including:

- **11 unique themes** – A complete set of professionally designed themes.
- **Dual-mode support** – Each theme is available in both dark and light modes.
- **Unified settings** – Theme preferences are managed through the **Settings** interface.

### Enhanced audio experience

V4 offers expanded audio customization for improved user interaction:

- **Over 15 sound combinations** – Includes an extensive library of notification and interaction sounds.
- **Personalization** – Workers can customize their device audio experience.
- **Centralized configuration** – Sound settings are integrated with theme preferences.

### Advanced diagnostics

V4 supports comprehensive diagnostic capabilities for improved troubleshooting and maintenance, including:

- **WiFi diagnostics**
    - **Self-diagnostic capabilities** – Each device can independently assess its network connectivity.
    - **Service ping tests** – Automated connectivity verification to critical services.
    - **Proactive monitoring** – Early detection of network-related issues.

- **Local logging system**
    - **Human-readable logs** – Improved log format for easier troubleshooting.
    - **Filtering capabilities** – Advanced log filtering for targeted analysis.
    - **Export functionality** – Easy log export for support and analysis purposes.

- **Accessible scan testing**
    - **Simplified access** – Scan test functionality is available without developer menu navigation.
    - **User-friendly interface** – Streamlined testing process for end users.

## Migration information

### System requirements

The system requirements for V4 are the [same as for V3](install-configure-warehouse-management-app.md), except for Android devices. V4 requires Android 7 or higher, while V3 which supports Android 5 and above. Devices running older Android versions can continue using V3 until the May 2026 end-of-support date.

### Compatibility between V3 and V4

When you migrate from V3 to V4, the following compatibility features are available:

- **Customization preservation** – All customizations and configurations from V3 are fully compatible and functional in V4.
- **Connection migration** – In most cases, existing connections are automatically migrated. If manual reconfiguration is required, QR code generation and scanning capabilities (camera or beam scanner) are available for easy setup. Learn more in [Use a QR code to connect the mobile app to Supply Chain Management](warehouse-app-qr-code.md).

### Authentication

- **One-time reauthentication** – Admins must complete a single authentication process for each device that they migrate to V4. Once successfully migrated, devices remain authenticated without requiring further reauthentication.
- **Windows platform configuration** – For Windows applications, you must add a new redirect URI to your Azure application registration, as described in the following procedure.

Follow these steps to add the redirect URI for Windows applications:

1. Open the [Azure portal](https://portal.azure.com).
1. Go to **App Registrations**.
1. Select your Microsoft Entra ID registration.
1. Go to **Manage** \> **Authentication**.
1. Select **Add a platform** and then select **Mobile and desktop applications**.
1. In the **Custom redirect URIs** field, enter `ms-appx-web://microsoft.aad.brokerplugin/{clientId}` (where *{clientId}* is your Entra Client ID).

### iOS limitations

Device code authentication isn't available on iOS platforms. Username and password authentication is the only supported method for iOS devices.

### Certificate authentication isn't supported in V4

As with V3, certificate authentication isn't supported in V4. Users must use the device code or username/password authentication methods.

### <a name="rollout"></a>Rollout schedule and transition period support

- **Concurrent operation** – V3 and V4 can operate simultaneously in the same warehouse environment during the transition period without conflicts.

- **V4 release timeline**
    - **Public preview** – Beginning of June 2025
    - **General Availability** – Planned for August 2025 (subject to public preview results)

- **Distribution channels**
    - **Windows** – App store
    - **iOS** – App store
    - **Android** – App store and open test programs

- **V3 support timeline**
    - **End of support** – May 2026
    - **Feature development** – No new features are developed for V3
    - **Maintenance** – Critical bug fixes and security updates continue until end of support
