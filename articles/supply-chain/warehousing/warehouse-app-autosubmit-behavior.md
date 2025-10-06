---
title: Data submission behavior in the Warehouse Management mobile app
description: Learn about the options for how the Warehouse Management mobile app submits scanned data.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 10/06/2025
ms.custom:
  - bap-template
---

# Data submission behavior in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

The Warehouse Management mobile app supports two options for how it submits scanned data: *auto-submit* and *manual submit*. This article explains the differences between these options and how to configure them.

## How the app submits scanned data

In releases before version 4.0.20.0, the Warehouse Management mobile app data-submit behavior varied by device:

- On some devices (such as Zebra) the app automatically submitted data as it was scanned. Workers didn't need to confirm the submission (for example, by pressing Enter).
- On other devices (such as Honeywell) manual confirmation was required after each scan.

This inconsistency made it difficult to support and document scanner behavior across the growing range of devices. To create a predictable and consistent user experience across all devices and versions, the Warehouse Management mobile app can now standardize its behavior by requiring confirmation for all devices. You can then use your device's own configuration options to implement auto-submit behavior if you want it.

## Configure auto-submit behavior for the Warehouse Management mobile app

To set the auto-submit behavior for the Warehouse Management mobile app, follow these steps:

1. Sign in to the Warehouse Management mobile app and go to the **Main menu** page.
1. Select the **Settings** button, which is the gear icon in the top-right corner of the screen.
1. Find and select the **Auto submit** menu item and set it to one of the following values:
    - *Yes* – The Warehouse Management mobile app controls how it submits scanned data. For some devices (such as Zebra), the app automatically submits scanned data without requiring manual confirmation. For other devices (such as Honeywell), the app requires workers to confirm the submission (for example, by pressing Enter). This is how the app behaved in releases before version 4.0.20.0. This option is primarily provided for backwards compatibility. You shouldn't select this option for new installations.
    - *No* – The app doesn't attempt to auto-submit scanned data. This option allows the device, instead of the app, to control how it submits scanned data. Microsoft recommends this setting for all new installations.

## Configure auto-submit behavior for your device

When you configure the Warehouse Management mobile app with **Auto submit** set to *No*, which is the recommended setting, you can still implement auto-submit behavior by configuring your device to simulate an Enter key press after each scan. The exact steps to do this depend on which device you're using, so see your device's documentation for instructions.

> [!TIP]
> You can also use advanced scanner configuration to use *intents* to control how the app submits data. Learn more in [Advanced bar code scanner configuration](warehouse-app-adv-scanner-config.md).
