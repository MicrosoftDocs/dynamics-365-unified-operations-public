---
title: Warehouse Management Application V3 to V4 Migration Guide
description: Learn how to migrate from Warehouse Mobile Application V3 to V4, including compatibility, requirements, and timeline.
author: pefreita
ms.author: pefreita
ms.topic: migration-to
ms.date: 05/30/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:  MigrateWMA, WMAV4, NewWMA, UpdateWMA
---
# Warehouse Management Application V3 to V4 Migration Guide

## Overview

The Warehouse Management Application has been completely rewritten with a modern and more powerful technology stack, enabling better customer support, faster problem resolution, and enhanced development capabilities for new features and integrations.

## What's New in V4

### Complete Application Rewrite
The entire application has been rebuilt from the ground up using modern technologies, providing:
- **Enhanced Performance**: Improved application responsiveness and stability
- **Better Support Capabilities**: Faster issue resolution and customer assistance
- **Future-Ready Architecture**: Streamlined development of new features and integrations

---

## New Features

### Camera Improvements

Camera scanning capabilities have been significantly enhanced, delivering next-level barcode scanning performance.

**Supported Barcode Formats:**
The application now supports a comprehensive range of barcode formats including aztec, codabar, code39, code93, code128, code39mod43, datamatrix, ean13, ean8, interleaved2of5, itf14, maxicode, pdf417, rss14, rssexpanded, upc_a, upc_e, upc_ean, and qr codes. For Windows deployments, all barcode formats are fully supported.

**Key Improvements:**
- **Faster Scanning**: Dramatically improved scan speed and accuracy
- **Multiple Barcode Support**: Simultaneous scanning of multiple barcodes in a single operation
- **Hardware Independence**: Reduces dependency on physical barcode scanners in environments where camera scanning is viable

### Customizable Themes

Enhanced user experience through comprehensive theming options:
- **11 Unique Themes**: Complete set of professionally designed themes
- **Dual Mode Support**: Each theme available in both dark and light modes
- **Unified Settings**: Theme and audio preferences managed through a single settings interface

### Enhanced Audio Experience

Expanded audio customization for improved user interaction:
- **15+ Sound Combinations**: Extensive library of notification and interaction sounds
- **Personalization**: Users can customize their device audio experience
- **Centralized Configuration**: Sound settings integrated with theme preferences

### Advanced Diagnostics

Comprehensive diagnostic capabilities for improved troubleshooting and maintenance.

#### WiFi Diagnostics
- **Self-Diagnostic Capabilities**: Each device can independently assess its network connectivity
- **Service Ping Tests**: Automated connectivity verification to critical services
- **Proactive Monitoring**: Early detection of network-related issues

#### Local Logging System
- **Human-Readable Logs**: Improved log format for easier troubleshooting
- **Filtering Capabilities**: Advanced log filtering for targeted analysis
- **Export Functionality**: Easy log export for support and analysis purposes

#### Accessible Scan Testing
- **Simplified Access**: Scan test functionality available without developer menu navigation
- **User-Friendly Interface**: Streamlined testing process for end users

---

## Migration Information

### Compatibility

**Customization Preservation**: All customizations and configurations from V3 will be fully compatible and functional in V4.

**Connection Migration**: In most cases, existing connections will be automatically migrated. If manual reconfiguration is required, QR code generation and scanning capabilities (camera or beam scanner) are available for easy setup.

### Authentication Requirements

**One-Time Re-authentication**: Users will need to perform a single authentication process for each device during the migration period. Once migrated to V4, the device will not need to re-authenticate again.

### System Requirements

**Android Version Requirements**: V4 requires Android 7 or higher, compared to V3 which supported Android 5 and above. Devices running older Android versions can continue using V3 until the May 2026 end-of-support date.

### Platform-Specific Considerations

**iOS Limitation**: Device code authentication will not be available on iOS platforms. Username and password authentication will be the only supported method for iOS devices.

### Will V4 support certificate authentication?

No, certificate authentication is not supported in V4, consistent with V3 where this feature was also discontinued.

### Transition Period Support

**Concurrent Operation**: V3 and V4 can operate simultaneously in the same warehouse environment during the transition period without conflicts.

**V4 Release Timeline**:
- **Public Preview**: Beginning of January 2026
- **General Availability**: Planned for August 2026 (subject to public preview results)
- **Distribution Channels**: 
  - Windows: App Center
  - Android: App Center and Open Test Programs

**V3 Support Timeline**: 
- **End of Support**: May 2026
- **Feature Development**: No new features will be developed for V3
- **Maintenance**: Critical bug fixes and security updates will continue until end of support