---
title: Advanced bar code scanner configuration
description: Learn how to fix compatibility issues between the Warehouse Management mobile app and your bar code scanner with an outline on setting up your mobile device.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 05/31/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: 
---

# Advanced bar code scanner configuration

[!include [banner](../includes/banner.md)]

On most mobile devices, the Warehouse Management mobile app can capture scanned bar code input directly out of the box. Therefore, you just have to install the app, set up the connection to Microsoft Dynamics 365 Supply Chain Management, and start to scan. However, some devices require advanced configuration before their bar code scanner hardware can interact correctly with the Warehouse Management app.

One common method for integrating scanning hardware with the Warehouse Management app is to configure your mobile device to provide *intent output* for bar code scanning. The bar code scanner can then submit scanned data directly to the Warehouse Management app. It doesn't have to send the data as simulated keystroke input instead. If you experience compatibility issues with your bar code scanner, you might be able to fix them by setting up your device to provide intent output.

This article explains how to set up a mobile device to provide intent output for bar code scanning. If your bar code scanner already works correctly with the Warehouse Management app, you don't have to read this article.

> [!NOTE]
> Intent output often replaces keystroke output. Therefore, you shouldn't configure your device to use both types of output at the same time.

## Prerequisites

To use intent output with the Warehouse Management mobile app, you must be running version 2.3.3.0 or later of the app.

## Set up your mobile device

The Warehouse Management mobile app automatically supports intent output for bar code scanning. You don't have to configure any settings in the mobile app or Supply Chain Management to use intent output. However, you must adjust your mobile device's native settings to configure the device to use intent output. The names and locations of these settings vary, depending on the device that you're using. Therefore, see your device's documentation for specific details.

To configure your mobile device to use this feature, look for the following settings:

- **Intent output** – Enable the functionality on your device.
- **Intent action** – Set the value to *com.microsft.warehousemanagement.BARCODE*.
- **Intent type** – Set the value to *Broadcast intent*.
- **Intent category** – Leave the default value.
- **Extra key** – The Warehouse Management mobile app requires that bar code data arrives as a string value for the `com.symbol.datawedge.data_string` key. For Zebra and ProGlove devices, you don't have to specify this value, because the devices use this key name by default. However, you might have to specify the value for other devices.
