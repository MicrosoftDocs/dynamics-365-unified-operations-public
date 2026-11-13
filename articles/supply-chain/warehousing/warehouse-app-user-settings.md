---
title: Warehouse Management mobile app user settings
description: Learn how to use local user settings to personalize the way your Warehouse Management mobile app works, looks, and sounds
author: pefreita
ms.author: pefreita
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 11/12/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Warehouse Management mobile app user settings

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to use local user settings to personalize the way your Warehouse Management mobile app works, looks, and sounds.

Workers can set their own preferences locally while working on a device by following the instructions in this article.

Administrators and managers can also set default settings, device-specific settings, and user-specific settings remotely from the web client, as described in [Mobile Device User Settings](mobile-device-user-settings.md).

## Color and sound themes

Warehouse Management mobile app version 4 introduces new color and sound themes that can help make your daily work more enjoyable and visually distinctive.

### Color themes

Each worker can select their own color theme, both to match their personal preference and to make it easy to see which user is signed in. This feature is useful when several different workers use the same device throughout the day.

You can choose from many color themes, including:

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

To make your workflow more fun, choose a sound theme that plays a sound after you complete a task or scan an item. For example, you might hear a bird chirp or a robot beep. You can choose from more than 20 sound themes, and you can select a different sound for success, rescan, and error events. Learn more in [Sound settings](#sound-settings).

## Set user preferences on a mobile device

To set your user preferences on a mobile device, including the color and sound theme, follow these steps:

1. Sign in to the Warehouse Management mobile app and go to the **Main menu** page.
1. Select the **Settings** button, which is the gear icon in the top-right corner of the screen.
1. The **Settings** page groups the settings into the following categories. Select a category to open it:

    - **General** – Field filtering, server timeout, Copilot, and configuration mode options.
    - **Layout** – Theme, buttons, scaling, and display options.
    - **Sounds** – Sound level, vibration, and sounds for each scan event.
    - **Scanner** – Scan behavior, rescan sound, and arm-held device feedback.
    - **Camera** – Camera scanning, preview mirroring, and scan marker options.

1. Make the settings that you want in each category, as described in the following sections.
1. Select **Back** when you're done.

### General settings

The **General** category contains the following settings:

- **Field filtering and sorting** – Select which fields are shown on the device and how they're ordered. You can choose to show all fields or just the promoted fields, and you can choose to sort them or not. Learn more in [Configure promoted fields for steps in the Warehouse Management mobile app](warehouse-app-promoted-fields.md).
- **Server request timeout (minutes)** – Set how long the app should wait for a response from the server before timing out. You can select a duration from 1 to 30 minutes.
- **Show copilot on startup** – Specify whether the Copilot workload page should be shown each time the user signs in to the app. The workload page shows work summaries and AI-generated insights to help warehouse workers better plan their shift. Learn more in [Workload insights with Copilot in the Warehouse Management mobile app](warehouse-management-mobile-app-insights.md). This setting is shown only when the Copilot feature is available for your system.
- **Show copilot data as** – Specify whether Copilot summaries should be based on work headers or work lines. The choice depends on how workers prefer to think about their daily workload. For example, if all your orders typically contain just a few items, workers might prefer to think about their work in terms of whole orders (*Work headers*). However, if quantities vary greatly from order to order, workers might prefer to think about their work in terms of individual items (*Work lines*). This setting is shown only when the Copilot feature is available for your system.
- **Configuration mode** – Set this option to *Yes* to explore and understand the relationship between UI controls and their underlying XML. This option can be helpful when you're customizing mobile flow behavior. When this is set to *Yes*, you can press and hold on almost any button or label to drill down into the session XML. This feature isn't available for controls that aren't connected to the session XML.

### Layout settings

The **Layout** category contains the following settings:

- **Product photo placement** – Select how product photos should be shown in the app (learn more about product images in [Add an image to a product](../pim/tasks/add-image-product.md)). Choose one of the following options:
    - *Default (show photo card)* – Display the product image as a large photo card.
    - *Only in step header* – Show the product image within the header section.
    - *Do not show* – Hide the product image in the mobile app.

- **Color theme** – Select a color theme for the device. Choose from more than 10 color themes.
- **Color mode** – Select a color mode for the device. The available options are *Light*, *Dark*, and *Auto*. The *Auto* option matches the device's default setting.
- **Best button position** – Select how buttons should be positioned on the device. Elements in the app move to better fit the preference or handedness of the worker. The available options are *Bottom right (default)*, *Bottom left*, *Top right*, and *Top left*.
- **Button style** – Choose how certain buttons should be displayed in the app. The available options are *Buttons* and *Slider*.
- **Quantity spinner mode** – *Spinners* provide a way for workers to enter quantity values by spinning through digits using a sliding gesture, similar to using a combination lock. Use this setting to control how spinners are displayed. Choose one of the following values:
    - *Auto* – Allow the system to choose the appearance based on how much room there is on the screen.
    - *Small* – Always show the small spinner, which presents a compact control.
    - *Don't show* – Don't use spinners. Instead, allow workers to enter numerical values using an on-screen keypad.

- **Text scale** – Specify the text size as a percentage of the standard size. Enter a value between 70 and 400. A value of *70* represents the smallest text scale, and a value of *400* represents the largest text scale. *100* is the standard text size.
- **Button scale** – Specify the button size as a percentage of the standard size. Enter a value between 50 and 200. A value of *50* represents the smallest button scale, and a value of *200* represents the largest button scale. *100* is the standard button size.
- **Scrollable details card** – Set this option to *Yes* to let workers scroll the details card so they can view more information on one screen. The default value is *No*. The scrollable details card is designed for larger screens. On smaller devices, the feature might not work as expected. On smaller screens, switching to landscape mode might reduce the available space, which could affect the scrolling behavior.
- **Animations** – Set this option to *On* to play the animated step icons and error illustrations in the app. Set it to *Off* to show them as static images, which can help workers who are sensitive to motion. The default value is *On*.
- **Layout mode** – Select the screen size that the app uses to arrange its layout. Choose *Automatic* (default) to let the app detect the screen size of the device. Alternatively, choose a fixed size to override the detected size. The available sizes are *Extra small (XS)*, *Small (SM)*, *Small-medium (SMD)*, *Medium (MD)*, *Large (LG)*, and *Extra large (XL)*. Sizes from *Small-medium (SMD)* and up use the tablet layout. Smaller sizes use the phone layout. This setting is stored only on the local device and isn't shared with other devices.

### Sound settings

The **Sounds** category contains the following settings:

- **Sound level** – Select the sound level for the device. Choose a value between 0 and 10. A value of *0* means no sound, and a value of *10* means maximum volume.
- **Vibration level** – Select the vibration level for the device. Choose a value between 0 and 5. A value of *0* means no vibration, and a value of *5* means maximum vibration.
- **Success sound** – Select the sound theme that plays when an action succeeds, such as a successful scan.
- **Double scan sound** – Select the sound theme that plays when a rescan is required. This sound plays only when the **Play sound when rescan is required** setting in the **Scanner** category is set to *Yes*.
- **Error sound** – Select the sound theme that plays when an error occurs.

For each sound setting, you can choose from more than 20 sound themes, or select *None* to mute that event. Select the play button next to a sound setting to preview the selected sound. If you don't select a sound for an event, the app uses the sound theme that was selected in earlier versions of the app.

### Scanner settings

The **Scanner** category contains the following settings:

- **Scanning** group:
    - **Auto submit** – Controls whether the app or the device handles scanned data submission. Set to *No* (recommended) for new installations. Learn more in [Data submission behavior in the Warehouse Management mobile app](warehouse-app-autosubmit-behavior.md).
    - **Play sound when rescan is required** – Choose whether to play a sound when a rescan is required. A rescan might be required, for example, when a scanned value results in an error, such as an invalid item ID.
    - **Disable scanner when the app is busy** – Set this option to *Yes* to suspend the hardware scanner while the app is processing a request, and then resume it when the app is ready. The default value is *No*. When this option is set to *No*, the app still rejects scans while it's busy, but the scanner itself stays active. This setting is available only on Android devices, and only for scanners that support it.

- **Arm-held device feedback** group (available only on Android devices):
    - **Success** – Set this option to *Yes* to send feedback to connected arm-held or wearable scanners (such as ProGlove devices) when an action succeeds. The default value is *Yes*.
    - **Error** – Set this option to *Yes* to send feedback to connected arm-held or wearable scanners when an error occurs. The default value is *Yes*.
    - **Info** – Set this option to *Yes* to send feedback to connected arm-held or wearable scanners when the app shows an informational message. The default value is *Yes*.

### Camera settings

The **Camera** category contains the following settings:

- **Scan with camera** – Set this option to *Yes* to use the device camera to scan input fields where the preferred input mode is set to *Scanning*. If your device has a built-in scanner, set this option to *No* to use the scanner instead.
- **Scanner preview mirroring** – Select whether the camera preview is mirrored while you scan. Choose one of the following values:
    - *Automatic* – Mirror the preview only when the app uses a front-facing camera. This value is the default.
    - *On* – Always mirror the preview.
    - *Off* – Never mirror the preview.

    This setting is stored only on the local device and isn't shared with other devices.

- **Scan marker color** – Select the color of the marker that the app draws around a detected barcode. Choose a color that stands out against your typical scanning background. The available colors are *Peach*, *White*, *Black*, *Red*, *Orange*, *Yellow* (default), *Lime*, *Green*, *Teal*, *Blue*, *Purple*, and *Magenta*. Each option shows a preview of the marker.
- **Scan marker thickness** – Select the line thickness of the barcode scan marker. The available options are *Thin*, *Normal* (default), *Medium*, *Thick*, and *Extra thick*. Each option shows a preview of the marker.
