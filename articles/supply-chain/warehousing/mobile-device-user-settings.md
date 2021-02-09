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

This feature introduces the ability to manage mobile device user settings, it can be used to define global user settings to be used on all devices using the Warehouse Management mobile app, or to define more granular user settings based on device model or user.

> [!IMPORTANT]
> This feature applies only to the new Warehouse Management mobile app. It does not work with the legacy warehouse app. 

## Turn on the User settings, icons, and step titles for the new warehouse app feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *User settings, icons, and step titles for the new warehouse app*

## Create and manage user settings

The Warehouse Management mobile app has a set of app specific settings, that can help tailor the user experience. As the app can be used in devices of different screen sizes and configurations (tablet, phone, or armheld), it can be useful to be able to manage these settings centrally from Supply Chain Management. With this feature it makes it possible to define settings profile that would apply to "All" devices and users, and then further set the granularity to apply more specific settings for specific device brands, device models or down to the specific user. When you use the mobile app and log in with a user, the app will fetch the most specific setting that is configured in Supply Chain Management, and apply it dynamically in the mobile app. 

To create and manage user settings for your mobile devices:
<!-- I like numbered procedures. They don't always fit, but often fit more often than you might think. Talk directly to the reader (second person) or name the role (such as "worker") for tasks likely done by somebody not the reader, or "the system" if something will happen automatically (avoid passive voice). -->

1. Go to **Warehouse management \> Mobile device \> Mobile device user settings**.
1. Select a user setting from the list pane or select **New** from the Action Pane to create a new one. <!-- Maybe note briefly how the records in the list pane are labelled and what that says about their specificity (though we may have covered enough of this in the intro). -->
1. Make the following settings in the header section of the new or selected record:
    - **Device brand name** - You can set the brand name if you want the configured setting to apply to only that brand of devices.<!-- Describe how to use this. Mention where these values come from (see also next section). Mention why the user might leave this blank. Same goes for the other settings here. -->
    - **Device model ID** - If you want the configured settings to only apply to a specific device model you can set it here.
    - **User ID** - Select a specific warehouse worker for whom the setting applies.
1. Make the following settings on the **General** FastTab:
    - **Button position** - Select how buttons should be positioned on the device. This will move elements in the app to better fit the preference of the worker. The options are: Bottom right (default), Bottom left, Top rigth, Top left
    - **Display orientation** - Select the display orientation that should be applied by default on the app.
    - **Scan with camera** - When this option is selected, a camera can be used for scanning in the warehouse app on every input field that has the preferred input mode set to "Scanning". If your device has a built-in scanner this option should be set to "No".
    - **Show product photo** - Choose whether or not to show product photos when available for the released product. <!-- Maybe add link to docs for adding image? https://docs.microsoft.com/en-us/dynamics365/supply-chain/pim/tasks/add-image-product --> 
    - **Display color theme** - Select the color theme for the device. 
    - **Sound level** - Select the sound level for the device. Select a value between 0 and 10, where 0 equals no sound, and 10 equals maximum sound. Default is 4.
    - **Vibration level** - Select the vibration level for the device. Select a value between 0 and 5, where 0 equals no vibration, and 5 equals maximum vibration. Default is 1.
    - **Text scale percentage** - Select the text scale percentage for the device. Select a value between 70 and 400, where 70 equals smallest text scale, and 400 equals largest text scale. Default is 100. <!-- Mention the range of valid values. Percentage of what? -->
    - **Button scale percentage** - 

## Create and manage mobile device brands

<!-- Add a full intro to this section. Same basic strategy as the previous. Mention why the user would want to set these up. Mention that these might typically be generated automatically. -->

To create and manage your mobile device brands:

1. Go to **Warehouse management \> Mobile device \> Mobile device brands**.
1. Select a mobile device brand from the list pane or select **New** from the Action Pane to create a new one.
1. Make the following settings in the header section of the new or selected device:
    - **Device brand name** - 
    - **Description** - 
1. Use the **Mobile device models** FastTab to <!-- Explain the general purpose of the items here. -->. Use the toolbar on this FastTab to add or remove rows in the grid. Make the following settings for each row:
    - **Device model ID** - 
    - **Description** - 
