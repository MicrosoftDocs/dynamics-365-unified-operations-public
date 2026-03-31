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

The Warehouse Management mobile app supports two approaches for submitting scanned data:

- **App-controlled (Auto submit = Yes)** — The app decides how to handle scanned data. Behavior varies by device: some devices (such as Zebra) auto-submit, while others (such as Honeywell) require manual confirmation. This option exists for backwards compatibility with versions before 4.0.20.0 and is **not recommended** for new installations.
- **Device-controlled (Auto submit = No)** — The app doesn't auto-submit. Instead, the device controls submission behavior. This is the **recommended setting** because it provides consistent, predictable behavior across all devices.

## Configure auto-submit in the app

1. Sign in to the Warehouse Management mobile app and go to the **Main menu** page.
1. Select the **Settings** button (gear icon in the top-right corner).
1. Set **Auto submit** to *No* (recommended).

## Configure auto-submit on the device

With **Auto submit** set to *No* in the app, you can still achieve auto-submit behavior by configuring your device to simulate an Enter key press after each scan. The exact steps depend on your device model — refer to your device manufacturer's documentation.

> [!TIP]
> For more granular control, you can use *intents* instead of keystroke simulation. Learn more in [Advanced bar code scanner configuration](warehouse-app-adv-scanner-config.md).
