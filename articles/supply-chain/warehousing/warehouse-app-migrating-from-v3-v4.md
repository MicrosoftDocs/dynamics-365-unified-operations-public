---
title: Migrate the Warehouse Management mobile app from V3 to V4
description: Learn how to migrate from Warehouse Mobile Application V3 to V4, including compatibility, requirements, and timeline.
author: pefreita
ms.author: pefreita
ms.topic: migration-to
ms.date: 05/30/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:  MigrateWMA, WMAV4, NewWMA, UpdateWMA
---

# Migrate the Warehouse Management mobile app from V3 to V4

For V4, we rewrote the Warehouse Management mobile app using more modern technology. The app now provides the following benefits:

- **Enhanced performance** – Improved application responsiveness and stability
- **Better customer support capabilities** – Faster issue resolution and customer assistance
- **Future-ready architecture** – Streamlined development of new features and integrations

## New features added in V4

The following subsections summarize the key new features and improvements introduced in V4 of the Warehouse Management mobile app.

### Camera improvements

V4 provides improved camera scanning capabilities, including:

- **Faster scanning** – Dramatically improved scan speed and accuracy
- **Expanded barcode support** – The app now supports a wider range of barcode formats. Learn more in [Scan bar codes using a camera in the Warehouse Management mobile app](scan-bar-codes-using-a-camera.md)..
- **Multiple barcode support** – Simultaneous scanning of multiple barcodes in a single operation
- **Hardware Independence** – Reduces dependency on physical barcode scanners in environments where camera scanning is viable

### Customizable themes

V4 provides an enhanced user experience through comprehensive theming options, including:

- **11 unique themes** – Complete set of professionally designed themes.
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

### Compatibility between V3 and V4

When you migrate from V3 to V4, the following compatibility features are available:

- **Customization preservation** – All customizations and configurations from V3 are fully compatible and functional in V4.
- **Connection migration** – In most cases, existing connections are automatically migrated. If manual reconfiguration is required, QR code generation and scanning capabilities (camera or beam scanner) are available for easy setup. Learn more in [Use a QR code to connect the mobile app to Supply Chain Management](warehouse-app-qr-code.md).

### Authentication

- **One-time reauthentication** – Admins must complete a single authentication process for each device that they migrate to V4. Once successfully migrated, devices remain authenticated without requiring further reauthentication.
- **Windows platform configuration** – For Windows applications, you must add a new redirect URL to your Azure application registration, as described in the following procedure.

Follow these steps to add the redirect URL for Windows applications:

1. Open the [Azure Portal](https://portal.azure.com).
1. Go to **App Registrations**.
1. Select your Entra Client ID registration.
1. Go to **Manage** \> **Authentication**.
1. Select **Add Platform** \> **Mobile and desktop applications**.
1. Enter `ms-appx-web://microsoft.aad.brokerplugin/{clientId}` (where *{clientId}* is your Entra Client ID).

### System requirements

The system requirements for V4 are the [same as for V3](install-configure-warehouse-management-app.md), except for Android devices. V4 requires Android 7 or higher, while V3 which supports Android 5 and above. Devices running older Android versions can continue using V3 until the May 2026 end-of-support date.

### iOS limitations

Device code authentication is not available on iOS platforms. Username and password authentication is the only supported method for iOS devices.

### Certificate authentication isn't supported in V4

As with V3, certificate authentication is not supported in V4. Users must use device code or username/password authentication methods.

### Transition period support

- **Concurrent Operation** – V3 and V4 can operate simultaneously in the same warehouse environment during the transition period without conflicts.

- **V4 Release Timeline**
    - **Public Preview** – Beginning of June 2025
    - **General Availability** – Planned for August 2025 (subject to public preview results)

- **Distribution Channels**
    - **Windows**: App Center
    - **Android**: App Center and Open Test Programs

- **V3 Support Timeline**
    - **End of Support** – May 2026
    - **Feature Development** – No new features are developed for V3
    - **Maintenance** – Critical bug fixes and security updates continue until end of support
