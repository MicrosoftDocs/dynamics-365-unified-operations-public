---
title: Mobile device user settings
description: Learn how to manage mobile device user settings for warehouse workers, including an outline on creating and managing user settings.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 07/08/2025
ms.custom: 
ms.reviewer: kamaybac
ms.search.form: WHSMobileAppDeviceBrand,WHSMobileAppUserDisplaySettings
---

# Mobile device user settings

[!include [banner](../../includes/banner.md)]

The new Warehouse Management mobile app has a set of app-specific settings that help tailor the user experience. Because the app can be used on devices of different screen sizes and configurations (such as tablet, phone, or arm-held), it can be useful to centrally manage these settings from Microsoft Dynamics 365 Supply Chain Management.

The *mobile device user settings* feature lets you define global user settings that will be used on all devices. You can also define more granular user settings for individual device brands, device models, and/or workers. When a worker signs in to the Warehouse Management mobile app, the app fetches and applies the most specific settings profile that is stored in Supply Chain Management for the matching brand, device, and/or user ID.

This feature can help workers get started more quickly whenever they begin to use a new device. Here are some examples:

- Admins can establish a standard set of preferences that work best for devices from a specific manufacturer and/or for specific device models. Therefore, workers can get started with a new device without necessarily having to change the settings.
- If your company has a pool of identical devices that are shared among workers, workers will see their preferred setup every time that they sign in, even if they have never used the specific physical device that they selected on a given day.
- In Supply Chain Management, admins can view and edit all stored settings, even for individual workers. This capability can help them troubleshoot or fine-tune new features.

## Create and manage user settings

Use the **Mobile device user settings** page to create, view, and manage settings profiles at all levels of granularity. The first time that a worker edits their user settings on a new device, a new profile is automatically added on this page, if it doesn't already exist. That profile is then updated every time that the worker makes a change.

You can also define a settings profile that applies to all device brands, device models, and/or workers. You can then increase the granularity by applying more specific settings for individual brands, models, and/or workers.

Follow these steps to create and manage user settings for your mobile devices.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device user settings**.
1. Select an existing user settings profile in the list pane to open its record. Alternatively, select **New** on the Action Pane to create a new profile.

    Each profile in the list pane is labeled to indicate the brand, model, and/or user ID that the profile applies to. More general profiles have a value of *All* for some or all of these characteristics.

1. In the header section of the record for the new or selected settings profile, set the following fields:

    - **Device brand name** – Select the device brand name that the profile should apply to. If the profile should apply to all brands, leave this field blank. The list of values includes all the brands that have been defined in your system. For information about how to define the list of brands, see the next section.
    - **Device model ID** – Select the device model that the profile should apply to. If the profile should apply to all models of the selected brand, leave this field blank. The list of values includes all the models that have been defined for the brand that is selected in the **Device brand name** field. For information about how to define the list of models for each brand, see the next section.
    - **User ID** – Select the user ID of the warehouse worker that the setting profile should apply to. If the profile should apply to all workers, leave this field blank.

1. On the **General** FastTab, set the following fields:

    - **Button position** – Select how buttons should be positioned on the device. Elements in the app will be moved to better fit the preference or handedness of the worker. The available options are *Bottom right (default)*, *Bottom left*, *Top right*, and *Top left*.
    - **Scan with camera** – Set this option to *Yes* to use the device camera to scan input fields where the preferred input mode is set to *Scanning*. If your device has a built-in scanner, set this option to *No* to use the scanner instead.
    - **Product photo placement** – Select how product photos should be shown in the app (learn more about product images in [Add an image to a product](../pim/tasks/add-image-product.md)). Choose one of the following options:
        - *Default (show photo card)* – Display the product image as a large photo card.
        - *Only in step header* – Show the product image within the header section.
        - *Do not show* – Hide the product image in the mobile app.
    - **Display color theme** – Select a color theme for the device.
    - **Sound level** – Select the sound level for the device. Select a value between 0 (zero) and 10. A value of *0* represents no sound, and a value of *10* represents maximum volume. The default value is *4*.
    - **Vibration level** – Select the vibration level for the device. Select a value between 0 (zero) and 5. A value of *0* represents no vibration, and a value of *5* represents maximum vibration. The default value is *1*.
    - **Text scale percentage** – Specify the text size as a percentage of the standard size. Enter a value between 70 and 400. A value of *70* represents the smallest text scale, and a value of *400* represents the largest text scale. The default value is *100*.
    - **Button scale percentage** – Specify the button size as a percentage of the standard size. Enter a value between 50 and 200. A value of *50* represents the smallest button scale, and a value of *200* represents the largest button scale. The default value is *100*.
    - **Field filtering and sorting** – Select which fields are shown on the device and how they're ordered. You can choose to show all fields or just the promoted fields, and you can choose to sort them or not. Learn more in [Configure promoted fields for steps in the Warehouse Management mobile app](warehouse-app-promoted-fields.md).
    - **Button style** – Choose how certain buttons should be displayed in the app. The available options are *Buttons* and *Slider*.
    - **Spinner mode** – *Spinners* provide a way for workers to enter quantity values by spinning through digits using a sliding gesture, similar to using a combination lock. Use this setting to control how spinners are displayed. Choose one of the following values:
        - *Auto* – Allow the system to choose the appearance based on how much room there is on the screen.
        - *Small* – Always show the small spinner, which presents a compact control.
        - *None* – Don't use spinners. Instead, allow workers to enter numerical values using an on-screen keypad.
    - **Play sound when rescan is required** – Choose whether to play a sound when a rescan is required. A rescan might be required, for example, when a scanned value results in an error, such as an invalid item ID.
    - **Show copilot on startup** – Specify whether the Copilot workload page should be shown each time the user signs in to the app. The workload page shows work summaries and AI-generated insights to help warehouse workers better plan their shift. Learn more in [Workload insights with Copilot in the Warehouse Management mobile app](warehouse-management-mobile-app-insights.md).
    - **Show copilot data as** – Specify whether Copilot summaries should be based on work headers or work lines. The choice depends on how workers prefer to think about their daily workload. For example, if all your orders typically contain just a few items, workers might prefer to think about their work in terms of whole orders (*Work headers*). However, if quantities vary greatly from order to order, workers might prefer to think about their work in terms of individual items (*Work lines*).

## Set local user settings in the Warehouse Management mobile app

Workers can set their own local user settings in the Warehouse Management mobile app. These settings override the default settings set by the admin. For example, a worker might prefer to use a different theme, sound level, or text scale. When a worker signs in to the Warehouse Management mobile app, the app fetches and applies the most specific settings profile that is stored in Supply Chain Management for the matching brand, device, and user ID. When a worker changes their local settings, the app updates the settings profile that is stored in Supply Chain Management for the matching brand, device, and user ID. If no matching profile exists, a new one is created.

To set local user settings in the Warehouse Management mobile app, sign in to the app and then select the **Settings** button, which is the gear icon in the top-right corner of the screen. In addition to the settings also managed in Supply Chain Management (described in the previous section), the app provides the following extra options:

- **Server request timeout** – Set how long the app should wait for a response from the server before timing out. You can select a duration from 1 to 30 minutes.
- **Configuration mode** – Enable this option to explore and understand the relationship between UI controls and their underlying XML. This option can be helpful when you're customizing mobile flow behavior. When this is set to *Yes*, you can press and hold on almost any button or label to drill down into the session XML. This feature isn't available for controls that aren't connected to the session XML.

## Create and manage mobile device brands

Use the **Mobile device brands** page to view, create, and manage the device brands and models that can be used with your settings profiles. The mobile app automatically fetches and submits the local brand name and model ID the first time that a worker edits their settings on a given device. Therefore, most of these records will usually be automatically generated. However, you can also manage all the records on this page. For example, you can give more useful descriptions to each brand and model to help distinguish similar or cryptic model IDs.

Follow these steps to create and manage your mobile device brands and models.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device brands**.
1. In the list pane, select a mobile device brand to open its record. Alternatively, select **New** on the Action Pane to create a new brand.
1. In the header section of the record for the new or selected device brand, set the following fields:

    - **Device brand name** – The brand name of the device, such as *Microsoft Corporation*.
    - **Description** – You can enter a description to help distinguish brand names.

1. The **Mobile device models** FastTab shows all the models for the selected device brand. Use the buttons on the toolbar to add rows to the grid or remove rows. For each row, you can set the following fields:

    - **Device model ID** – The device model ID, such as *Surface Book 2*.
    - **Description** – You can enter a description to help distinguish model IDs.

## Related information

- [Install the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Assign step icons and titles for the Warehouse Management mobile app](step-icons-titles.md)