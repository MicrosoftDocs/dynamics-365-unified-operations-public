---
# required metadata

title: Store Commerce app for mobile platforms
description: This article describes how to get started using the Microsoft Dynamics 365 Commerce Store Commerce app for Android and iOS.
author: stuharg 
ms.date: 04/28/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: global
ms.author: stuharg
ms.search.validFrom: 2018-10-29

---

# Store Commerce app for mobile platforms

[!include [banner](../includes/banner.md)]

This article describes how to get started using the Microsoft Dynamics 365 Commerce Store Commerce apps for Android and iOS.

The Dynamics 365 Commerce mobile apps for Android and iOS make the process of deploying full-featured mobile point of sale (POS) devices for your retail environment straightforward and simple. The Store Commerce mobile apps deliver nearly all the capabilities and advantages of the [Store Commerce app for Windows](store-commerce.md), and perform well on a wide range of iOS and Android phones and tablets. The Store Commerce mobile apps can be installed directly from the Apple and Google Play app stores, and don't require a developer to create a new application package to deploy or update them. 

The Store Commerce mobile apps retain full functional parity with current Retail hybrid apps. In addition, Store Commerce for iOS includes support for a dedicated hardware station, so that iOS devices can communicate with networked payment terminals, receipt printers, and cash drawers without requiring the deployment of a shared hardware station. 

> [!IMPORTANT]
> The Store Commerce apps for Windows, Android, and iOS are the next generation POS applications for Dynamics 365 Commerce. The Store Commerce apps offer numerous improvements over their predecessors while retaining full functional and feature parity. Microsoft will deprecate MPOS and the Retail Hybrid apps for Android and iOS in late 2023, and recommends that you use the Store Commerce apps for Windows, Android, and iOS and Store Commerce for web for all new POS deployments. Existing customers should plan to migrate from MPOS and the Retail hybrid apps to Store Commerce. For more information, see [Migrate Modern POS to Store Commerce](pos-extension/migrate-mpos-store-commerce.md). 

## App architecture

The Store Commerce mobile apps use the same topology as the Store Commerce app for Windows when it's deployed in hybrid mode. The Store Commerce mobile apps are shell applications that render Store Commerce for web directly from the Commerce Scale Unit (CSU), and connect to Headless Commerce and Commerce headquarters via the CSU. The shell application model enables Store Commerce apps to support a dedicated hardware station for direct integration with a payment terminal, printer, cash drawer, and other peripherals. You don't have to set up a shared hardware station to use hardware devices. 

To update a Store Commerce mobile app, just update the CSU. All new POS functionality and features will automatically be picked up by the app. For more information about how to update the CSU, see [Apply updates and extensions to Commerce Scale Unit (cloud)](../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md).

The shell apps are serviced through app store updates. When a minor version reaches general availability (GA), Microsoft will publish it to the app stores. Microsoft might also publish patches between minor version updates to release high-priority bug fixes.

## Prerequisites

The Store Commerce mobile apps require Dynamics 365 Commerce, specifically the Commerce headquarters and CSU components. The following table lists the minimum operating system (OS) and CSU versions that are required by the Android and iOS mobile apps. 

| Prerequisite | Android      | iOS  |
| ------------ | ------------ | ---- |
| OS version   | 7.0          | 15.0 |
| CSU version  | 9.38.22266.8 | TBD  |

## Install the app

You can install Store Commerce mobile apps directly from the Google Play store or Apple App Store. 

- [Store Commerce app for Android](https://aka.ms/storecommerceandroid)
- [Store Commerce app for iOS](https://aka.ms/storecommerceios)

The Android app (.apk) and Apple app (.ipa) packages can also be downloaded from the Shared asset library in Microsoft Dynamics Lifecycle Services (LCS). 

## Device and register setup

Before a register can be activated on the Store Commerce mobile apps, you must set up a device and a register in Commerce headquarters. For more information, see [Devices and registers](../implementation-considerations-devices.md). 

### Device setup

To create and set up a new device, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> Devices**. 
1. Create a new device, and select either **Modern POS - Android** or **Modern POS - iOS** as the application type, depending on the mobile app that you're deploying. 

    > [!NOTE] 
    > The **Modern POS - Android** and **Modern POS - iOS** application types are also used to deploy the current hybrid apps for Android and iOS. After the deprecation of MPOS, the labels for these application types will be updated to **Store Commerce - Android** and **Modern POS - iOS**. 

### Register setup

You can create a new register and associate it with the device that you created, or you can associate an existing register with your new device. For more information about registers, see [Create and associate registers](../tasks/create-associate-registers.md).

### Screen layout setup

If you're repurposing a screen layout that is included in the demo data that is provided with your Dynamics 365 Commerce license, the Store Commerce app will automatically select the included compact layout if the screen resolution of your device is less than 480 &times; 853 pixels in the portrait orientation. However, if you're creating a screen layout from scratch, or if your mobile device uses a larger resolution than the compact layout supports, ensure that you create a resolution and associated button grids that are appropriate for the phone or tablet that you plan to deploy to. For more information about screen layout configurations, see [POS user interface visual configurations](../pos-screen-layouts.md). 

After devices and registers have been configured, in Commerce headquarters, go to **Retail and Commerce \> Retail and Commerce ID \> Distribution Schedules**, and run the registers job.

## Activate a device

To activate a device on a Store Commerce mobile app, follow these steps.

1. Open the app on the mobile device.
1. Enter the CPOS URL, which you can find on the environment details page in LCS, or on the **Channel profiles** page in Commerce headquarters (**Retail and Commerce \> Channel setup \> Channel profiles**).
1. Sign in by using the credentials of a worker who has permission to manage devices.
1. Select the store that is associated with the register that you created or reused in Commerce headquarters.
1. Select the register that you associated with the device that you created in Commerce headquarters.
1. Your device should now be activated. You can sign in to the register by using the operator ID and password for of worker who is associated with the store that you selected. 

For more information about device activation, see [Activate Store Commerce using guided activation](retail-device-activation.md#activate-store-commerce-using-guided-activation).

## Feature parity with Store Commerce for Windows

The following table compares the capabilities of the Store Commerce app across Windows, Android, and iOS platforms.

| Feature                                                                               | Windows | Android | iOS |
| ------------------------------------------------------------------------------------- | ------- | ------- | --- |
| Dedicated hardware station                                                            | Yes     | Yes     | Yes |
| Shared hardware station                                                               | Yes     | Yes     | Yes |
| Communication with networked peripherals (payment terminal, printer, and cash drawer) | Yes     | Yes     | Yes |
| OLE for Point of Sale (OPOS) peripherals through a local hardware station             | Yes     | No      | No  |
| Offline mode                                                                          | Yes     | No      | No  |

## Additional resources

[Store Commerce app](store-commerce.md)

[Choose between Store Commerce app and Store Commerce for web](../mpos-or-cpos.md)

[Troubleshoot Store Commerce setup and installation issues](../troubleshoot/store-commerce-setup-installation.md)
