---
# required metadata

title: Mobile device user settings
description: This topic explains how to manage mobile device user settings for warehouse workers.
author: MarkusFogelberg
manager: tfehr
ms.date: 02/09/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSMobileAppDeviceBrand,WHSMobileAppUserDisplaySettings
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
# ms.search.industry: 
ms.author: mafoge
ms.search.validFrom: 2021-02-09
ms.dyn365.ops.version: 10.0.17

---

# Mobile device user settings

The Warehouse Management mobile app has a set of app-specific settings that help tailor the user experience. Because the app can be used on devices of different screen sizes and configurations (such as tablet, phone, or arm-held), it can be useful to manage these settings centrally from Supply Chain Management.

The *mobile device user settings* feature lets you define global user settings to be used on all devices, or to define more granular user settings based on device model and/or individual workers. When a worker signs in to the Warehouse Management mobile app, the app will fetch and apply the most specific settings profile that is stored in Supply Chain Management for the matching brand, device, and/or user ID.

This feature can help workers get started more quickly each time they start to use a new device. For example:

- Admins can establish a standard set of preferences that work best for devices from a specific manufacturer and/or device model. This can help workers get started with a new device without necessarily needing to change the settings.
- If your company has a pool of identical devices that are shared among workers, then each worker will see their preferred setup each time they sign in, even if they never used the specific physical device they selected that day.
- While working in Supply Chain Management, admins can view and edit all stored settings, even for specific workers, which can help with troubleshooting or to fine tune new features.

> [!IMPORTANT]
> This feature applies only to the new Warehouse Management mobile app. It does not work with the legacy warehouse app.

## Turn on the mobile device user settings feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *User settings, icons, and step titles for the new warehouse app*

## Create and manage user settings

Use the **Mobile device user settings** page to create, view, and manage settings profiles at all levels of granularity. The first time a worker edits their user settings on a new device, a new profile will be added here automatically (if it doesn't already exist) and then updated each time the worker makes a change. You can also define a settings profile that would apply to all brands, models, and/or workers, and then further set the granularity to apply more specific settings for specific brands, models, or individual workers.

To create and manage user settings for your mobile devices:

1. Go to **Warehouse management \> Mobile device \> Mobile device user settings**.
1. Select a user setting from the list pane or select **New** from the Action Pane to create a new one. Each record in the list pane is labelled to indicate the brand, model, and/or user ID for which it applies, with the more general profiles showing a value of *All* for some or all of these.
1. Make the following settings in the header section of the new or selected record:
    - **Device brand name** - Select the device brand name for which this settings profile should apply. Leave this blank to allow the profile to apply to all brands. The drop-down list shows the brands that are already defined on your system. See the next section for more information on how to establish the list of brands available here.
    - **Device model ID** - Select the device model for which this settings profile should apply. Leave this blank to allow the profile to apply to all models of the selected brand. The drop-down list shows the brands that are already defined for the brand selected in the **Device brand name** field. See the next section for more information on how to establish the list of models available for each brand.
    - **User ID** - Select the user ID for the warehouse worker for whom the setting applies. Leave this blank to allow the profile to apply to all workers.
1. Make the following settings on the **General** FastTab:
    - **Button position** - Select how buttons should be positioned on the device. This will move elements in the app to better fit the preference or handedness of the worker. The options are: *Bottom right (default)*, *Bottom left*, *Top right*, and *Top left*.
    - **Display orientation** - Select the display orientation that should be applied by default on the app.
    - **Scan with camera** - Set this to *Yes* to use the device camera to scan input fields that have their preferred input mode set to *Scanning*. If your device has a built-in scanner, set this option to *No* to use the scanner instead.
    - **Show product photo** - Choose whether or not to show product photos when available for the released product. For more information about how to add product images, see [Add an image to a product](../pim/tasks/add-image-product.md).
    - **Display color theme** - Select a color theme for the device.
    - **Sound level** - Select the sound level for the device. Select a value between 0 and 10, where 0 equals no sound, and 10 equals maximum volume. Default is 4.
    - **Vibration level** - Select the vibration level for the device. Select a value between 0 and 5, where 0 equals no vibration, and 5 equals maximum vibration. Default is 1.
    - **Text scale percentage** - Specify the text size as a percentage of the standard size. Enter a value between 70 and 400, where 70 equals smallest text scale, and 400 equals largest text scale. Default is 100.
    - **Button scale percentage** - Specify the button size as a percentage of the standard size. Enter a value between 50 and 200, where 50 equals smallest button scale, and 200 equals largest button scale. Default is 100.

## Create and manage mobile device brands

Use the **Mobile device brands** page to view, create, and manage the device brands and models that are available for use with your settings profiles. The mobile app automatically fetches and submits the local brand name and model ID the first time a worker edits their settings on a given device, so  most of these records will usually be generated automatically for you. However, you can also manage all the entries here and give more useful descriptions to each brand and model, for example to help distinguish similar or cryptic model IDs.

To create and manage your mobile device brands and models:

1. Go to **Warehouse management \> Mobile device \> Mobile device brands**.
1. Select a mobile device brand from the list pane or select **New** from the Action Pane to create a new one.
1. Make the following settings in the header section of the new or selected device:
    - **Device brand name** - This is the brand name of a device, for example "Microsoft Corporation".
    - **Description** - You can optionally provide a description to help distinguish between brand names.
1. Use the **Mobile device models** FastTab to see all the different models for a given device brand. Use the toolbar on this FastTab to add or remove rows in the grid. Make the following settings for each row:
    - **Device model ID** - The device model ID, for example "Surface Book 2".
    - **Description** - You can optionally provide a description to help distinguish between model IDs.
