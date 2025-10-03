---
title: Scan behavior on Warehouse Management App
description: Learn about the scanner input behavior changes introduced in version 4.0.20.0 of the WMA and how to configure your devices accordingly.
author: pefreita
ms.author: pefreita
ms.topic: conceptual
ms.date: 03/10/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Auto submit behavior in the Warehouse Management Application (WMA)

Starting with version **4.0.20.0**, the Warehouse Management Application (WMA) introduces a significant change to how scanner input is handled. This update aims to provide a more consistent and reliable experience across all supported devices.

## What's Changing?

Previously, scanner behavior version 3.x varied by device:

- Some devices (e.g., Zebra) automatically submitted scanned data.
- Others (e.g., Honeywell) required manual confirmation.

This inconsistency made it difficult to support and document scanner behavior across the growing range of devices.

**As for version 4.0.20.0.** The default behavior is to auto submit which is the same as in previous version.

## Why Are We Making This Change?

The goal is to create a **predictable and consistent user experience** across all devices and versions.

### Benefits for selecting not auto submit

- **Consistency**: Uniform behavior across all devices.
- **Simplified support**: Reduces device-specific troubleshooting.

### Why to select auto submit?

The only reason is to keep legacy compatibility and not stop the current workflow. But, for the future, you should switch to not *auto submit*.

## What Can You Do?

If you prefer to retain the auto-submit behavior, you can configure your device to simulate an Enter key press after each scan.

### Changing the settings for auto submit

1. After you login, go to the Settings page
2. Choose one of the current values for Auto Submit. (Yes) means that the auto submit will be controlled by the App. (No) means that there is no auto submit.

> [!TIP]
> You can also use the app’s advanced scanner configuration to handle everything via intents.  
> Learn more: [Advanced scanner configuration](https://learn.microsoft.com/en-us/dynamics365/supply-chain/warehousing/warehouse-app-adv-scanner-config)
