---
# required metadata

title: Store Commerce app for mobile platforms
description: This article describes how to get started using the Microsoft Dynamics 365 Commerce Store Commerce app for Android and iOS.
author: stuharg 
ms.date: 10/07/2022
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

Deploying a full-featured mobile point of sale devices for your retail environment is straightforward and simple with the Dynamics 365 Commerce mobile apps for Android and iOS. The Store Commerce mobile apps deliver the same capabilities and advantages of the [Store Commerce app for Windows](store-commerce.md) on phone and tablet form factors. The Store Commerce mobile apps can be installed directly from the Apple and Google Play app stores and don't require a developer to create a new application package to deploy or update the apps. 

The Store Commerce mobile apps retain full functional parity with current Retail hybrid apps. In addition, Store Commerce for iOS includes support for a dedicated Hardware Station so that iOS devices can communicate with networked payment terminals, receipt printers, and cash drawers without requiring a shared Hardware Station to be deployed. 

> [!IMPORTANT]
> The Store Commerce apps for Windows, Android, and iOS are the next generation of point of sale (POS) applications for Dynamics 365 Commerce. The current Modern point of sale (MPOS) application and the [Retail hybrid apps](hybridapp.md) for mobile will be deprecated in October of 2023. Microsoft recommends that you use Store Commerce or Cloud point of sale (CPOS) for all new POS deployments. Existing customers should plan to migrate from the Retail hybrid app to Store Commerce. For more information about the deprecation schedule for MPOS and the Retail hybrid apps, see [Modernizing the Dynamics 365 Commerce in-store technology stack](https://www.microsoft.com/download/details.aspx?id=103896). 

## App architecture

The Store Commerce mobile apps use the same topology as the Store Commerce app for Windows when it is deployed in hybrid mode. The Store Commerce mobile apps are shell applications that render Cloud Point of Sale (CPOS) directly from the Commerce Scale Unit (CSU), and connect to Headless Commerce and Commerce headquarters via the CSU. The shell application model allows Store Commerce apps to support a dedicated hardware station for direct integration with a payment terminal, printer, cash drawer, and other peripherals. You don't have to set up a shared hardware station to use hardware devices. 

To update a Store Commerce mobile app, simply update the CSU and all new POS functionality and features will automatically be picked up by the app. For more information about how to update the CSU, see [Apply updates and extensions to Commerce Scale Unit (cloud)](../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md).

The shell apps are serviced through app store updates. When minor versions reach general availability (GA), Microsoft will publish that version to the app stores. Microsoft may also publish patches between minor version updates to release high priority bug fixes.

## Prerequisites

Store Commerce mobile apps require Dynamics 365 Commerce, specifically the Commerce headquarters and Cloud Scale Unit components. The following table lists the minimum OS and CSU versions required by the Android and iOS mobile apps. 

| Prerequisite                       | Android      | iOS  |
| ---------------------------------- | ------------ | ---- |
| OS version                         | 7.0          | 15.0 |
| Commerce Scale Unit (CSU) version | 9.38.22266.8 | TBD  |

## Install the app

You can install Store Commerce mobile apps directly from the Google Play store or Apple App Store. 

- [Store Commerce app for Android](https://aka.ms/storecommerceandroid)
- Store Commerce app for iOS (available soon)

The Android app (.apk) and Apple app (.ipa) packages can also be downloaded from the Microsoft Dynamics Lifecycle Services portal (LCS) Shared asset library. 

## Device and register setup

Before a register can be activated on the Store Commerce mobile apps, you must first set up a device and a register in Commerce Headquarters. For more information, see [Devices and registers](../implementation-considerations-devices.md). 

### Device setup

To create and set up a new device, follow these steps.

1. In Commerce Headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> Devices**. 
1. Create a new device and select either the **Modern POS - Android** or **Modern POS - iOS** application types as appropriate for the mobile app you are deploying. 

> [!NOTE] 
> The **Modern POS - Android** and **Modern POS - iOS** application types are also used to deploy the current hybrid apps for Android and iOS. Following the deprecation of MPOS, these labels will be updated to **Store Commerce - Android** and **Modern POS - iOS**. 

### Register setup

You can create a new register and associate it with the device you created, or you can associate an existing register to your new device. For more information about registers, see [Create and associate registers](../tasks/create-associate-registers.md).

### Screen layout setup

If you are repurposing a screen layout that is included in the demo data provided with your Dynamics 365 Commerce license, the Store Commerce app will automatically select the included compact layout if the screen resolution of your device is smaller than 480px x 853px in the portrait orientation. However, if you are creating a screen layout from scratch, or your mobile device uses a larger resolution than the compact layout supports, ensure that you create a resolution and associated button grids appropriate to the phone or tablet you plan to deploy to. For more information about screen layout configurations, see [POS user interface visual configurations](../pos-screen-layouts.md). 

After devices and registers have been configured, in headquarters go to **Retail and Commerce \> Retail and Commerce ID \> Distribution Schedules** and run the registers job.

## Activate a device

To activate a device on a Store Commerce mobile app, follow these steps.

1. Launch the app on the mobile device.
1. Enter the CPOS URL, which you can find on the environment details page in LCS, or on the **Channel profiles** page in Commerce headquarters at **Retail and Commerce \> Channel setup \> Channel profiles**.
1. Sign in with the credentials of a worker who has permission to manage devices.
1. Select the store associated with the register you created or reused in headquarters.
1. Select the register you associated with the device you created in headquarters.
1. Your device should now be activated. You can sign into the register with the operator ID and password for a worker associated with the store you selected. 

For more information about device activation, see [Point of sale (POS) device activation](retail-device-activation.md#activate-a-modern-pos-or-cloud-pos-device-by-using-guided-activation).

## Feature parity with Store Commerce for Windows

 The following table compares the capabilities of the Store Commerce app across Windows, Android, and iOS platforms.

| Feature                                                      | Windows | Android | iOS  |
| ------------------------------------------------------------ | ------- | ------- | ---- |
| Dedicated Hardware Station                                   | Yes       | Yes      | Yes    |
| Shared Hardware Station                                      | Yes       | Yes       | Yes    |
| Communication with networked peripherals (payment terminal, printer, cash drawer) | Yes       | Yes       | Yes    |
| OLE for Point of Sale (OPOS) peripherals through local Hardware Station                           | Yes       |         |      |
| Offline mode                                                 | Yes       |         |      |

## Additional resources

[Store Commerce app](store-commerce.md)

[Choose between Store Commerce and Cloud POS](..mpos-or-cpos.md)

[Troubleshoot Store Commerce setup and installation issues](../troubleshoot/store-commerce-setup-installation.md)
