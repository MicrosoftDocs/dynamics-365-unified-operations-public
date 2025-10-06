---
title: User settings, color themes, and sound themes
description: Learn how to use local user settings to personalize the way your Warehouse Management mobile app works, looks, and sounds
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 09/16/2025
ms.custom:
  - bap-template
---

# User settings, color themes, and sound themes

This article explains how to use local user settings to personalize the way your Warehouse Management mobile app works, looks, and sounds.

Workers can set their own preferences locally while working on a device by following the instructions in this article.

Administrators and managers can also set default settings, device-specific settings, and user-specific settings remotely from the web client, as described in [Mobile Device User Settings](mobile-device-user-settings.md).

## Color and sound themes

Warehouse Management mobile app version 4 introduces new color and sound themes that can help make your daily work more enjoyable and visually distinctive.

### Color themes

Each worker can select their own color theme, both to match their personal preference and to make it easy to see which user is signed in. This feature is useful when several different workers use the same device throughout the day.

Many color themes are available, including:

- Blue
- Bronze
- Cyan
- Golden
- Green
- High Contrast
- Lavender
- Orange
- Pink
- Platinum
- Red

Each theme also supports several color modes, which are:

- Light – Bright background
- Dark – Dark background
- Auto – Matches your device's default setting

### Sound themes

To make your workflow more fun, choose a sound theme that plays a sound after you complete a task or scan an item. For example, you might hear a bird chirp or a robot beep. You can choose from more than 20 sound themes.

## Set user preferences on a mobile device

To set your user preferences on a mobile device, including the color and sound theme, follow these steps:

1. Sign in to the Warehouse Management mobile app and go to the **Main menu** page.
1. Select the **Settings** button, which is the gear icon in the top-right corner of the screen.
1. Make the following settings on the **Settings** page as needed:

    - **Product photo placement** – Select how product photos should be shown in the app (learn more about product images in [Add an image to a product](../pim/tasks/add-image-product.md)). Choose one of the following options:
        - *Default (show photo card)* – Display the product image as a large photo card.
        - *Only in step header* – Show the product image within the header section.
        - *Do not show* – Hide the product image in the mobile app.
    - **Color theme** – Select a color theme for the device. Choose from more than 10 color themes.
    - **Color mode** – Select a color mode for the device. The available options are *Light*, *Dark*, and *Auto*. The *Auto* option matches the device's default setting.
    - **Best button position** – Select how buttons should be positioned on the device. Elements in the app move to better fit the preference or handedness of the worker. The available options are *Bottom right (default)*, *Bottom left*, *Top right*, and *Top left*.
    - **Scan with camera** – Set this option to *Yes* to use the device camera to scan input fields where the preferred input mode is set to *Scanning*. If your device has a built-in scanner, set this option to *No* to use the scanner instead.
    - **Field filtering and sorting** – Select which fields are shown on the device and how they're ordered. You can choose to show all fields or just the promoted fields, and you can choose to sort them or not. Learn more in [Configure promoted fields for steps in the Warehouse Management mobile app](warehouse-app-promoted-fields.md).
    - **Vibration level** – Select the vibration level for the device. Select a value between 0 (zero) and 5. A value of *0* represents no vibration, and a value of *5* represents maximum vibration.
    - **Sound level** – Select the sound level for the device. Select a value between 0 (zero) and 10. A value of *0* represents no sound, and a value of *10* represents maximum volume.
    - **Sound theme** – Select a sound theme for the device. Choose from more than 20 sound themes.
    - **Text scale** – Specify the text size as a percentage of the standard size. Enter a value between 70 and 400. A value of *70* represents the smallest text scale, and a value of *400* represents the largest text scale. *100* is the standard text size.
    - **Button scale** – Specify the button size as a percentage of the standard size. Enter a value between 50 and 200. A value of *50* represents the smallest button scale, and a value of *200* represents the largest button scale. *100* is the standard button size.
    - **Server request timeout (minutes)** – Set how long the app should wait for a response from the server before timing out. You can select a duration from 1 to 30 minutes.
    - **Button style** – Choose how certain buttons should be displayed in the app. The available options are *Buttons* and *Slider*.
    - **Quantity spinner mode** – *Spinners* provide a way for workers to enter quantity values by spinning through digits using a sliding gesture, similar to using a combination lock. Use this setting to control how spinners are displayed. Choose one of the following values:
        - *Auto* – Allow the system to choose the appearance based on how much room there is on the screen.
        - *Small* – Always show the small spinner, which presents a compact control.
        - *Don't show* – Don't use spinners. Instead, allow workers to enter numerical values using an on-screen keypad.
    - **Show copilot on startup** – Specify whether the Copilot workload page should be shown each time the user signs in to the app. The workload page shows work summaries and AI-generated insights to help warehouse workers better plan their shift. Learn more in [Workload insights with Copilot in the Warehouse Management mobile app](warehouse-management-mobile-app-insights.md).
    - **Show copilot data as** – Specify whether Copilot summaries should be based on work headers or work lines. The choice depends on how workers prefer to think about their daily workload. For example, if all your orders typically contain just a few items, workers might prefer to think about their work in terms of whole orders (*Work headers*). However, if quantities vary greatly from order to order, workers might prefer to think about their work in terms of individual items (*Work lines*).
    - **Play sound when rescan is required** – Choose whether to play a sound when a rescan is required. A rescan might be required, for example, when a scanned value results in an error, such as an invalid item ID.
    - **Configuration mode** – Set this option to *Yes* to explore and understand the relationship between UI controls and their underlying XML. This option can be helpful when you're customizing mobile flow behavior. When this is set to *Yes*, you can press and hold on almost any button or label to drill down into the session XML. This feature isn't available for controls that aren't connected to the session XML.
    - **Auto submit** – Choose whether the app should control how it submits scanned data or whether the device should control it (learn more in [Data submission behavior in the Warehouse Management mobile app](warehouse-app-autosubmit-behavior.md)). The available options are:
       - *Yes* – The Warehouse Management mobile app controls how it submits scanned data. For some devices (such as Zebra), the app automatically submits scanned data without requiring manual confirmation. For other devices (such as Honeywell), the app requires workers to confirm the submission (for example, by pressing Enter). This how the app behaved in releases before version 4.0.20.0. This option is primarily provided for backwards compatibility. You shouldn't select this option for new installations.
       - *No* – The app doesn't attempt to auto-submit scanned data. This option allows the device, instead of the app, to control how it submits scanned data. Microsoft recommends this setting for all new installations.

1. Select **Back** when you're done.
