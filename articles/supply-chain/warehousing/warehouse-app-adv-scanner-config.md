---
title: Advanced barcode scanner configuration
description: This article explains how to solve compatibility issues between the Warehouse Management mobile app and your barcode scanner.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 05/31/2024
audience: Application User
ms.custom: 
  - bap-template
---


# Advanced barcode scanner configuration

[!include [banner](../includes/banner.md)]

On most mobile devices, the Warehouse Management mobile app can capture scanned barcode input right out of the box, so all you need to do is install the app, set up the connection to Supply Chain Management, and start scanning. However, some devices might require advanced configuration to make their barcode-scanner hardware interact correctly with the Warehouse Management app.
One common method for integrating scanning hardware with the Warehouse Management app is to configure your mobile device to provide *intent output* for barcode scanning. This technique allows the barcode scanner to submit scanned data directly to the Warehouse Management app rather than send it as simulated keystroke input. If you're experiencing compatibility issues with your barcode scanner, then setting up your device to use intent output might enable you to solve them.

This article explains how to set up a mobile device to provide intent output for barcode scanning. If your barcode scanner is already working fine with the Warehouse Management app, then you don't need to read this article.

> [!NOTE]
> Intent output often replaces keystroke output, so you shouldn't configure your device to use both types of output at the same time.

## Prerequisites

To use intent output with the Warehouse Management app, you must be running Warehouse Management mobile app version 2.3.3.0 or newer.

## Set up your mobile device

The Warehouse Management mobile app automatically supports intent output for barcode scanning. You don't need to make any settings in the mobile app or in Supply Chain Management to use it. However, you do need to adjust your device's native settings to configure the device to use intent output. The names and locations of these settings vary based on which device you're using, so see your device's documentation for specific details. Look for the following settings to configure your device to use this feature:

- **Intent output** – Enable the functionality on your device.
- **Intent action** – Set to *com.microsft.warehousemanagement.BARCODE*.
- **Intent type** – Set to *Broadcast intent*.
- **Intent category** – Leave set to its default setting.
- **Extra key** – The Warehouse Management mobile app requires barcode data to arrive as a string value for the key `com.symbol.datawedge.data_string`. For Zebra and ProGlove devices, you don't need to specify this value because they use this key name by default, but other devices might require you to specify it.
