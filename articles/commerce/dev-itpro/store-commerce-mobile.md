---
# required metadata

title: Store Commerce app for mobile platforms
description: This topic provides all the information you need to get started with the Store Commerce app for Android and iOS.
author: stuharg 
ms.date: 10/6/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: stuharg
ms.search.validFrom: 2018-10-29
ms.dyn365.ops.version: AX 8.0, AX 8.1

---

# Store Commerce app for mobile platforms

[!include [banner](../includes/banner.md)]

Deploying full-featured mobile point of sale devices for your retail environment is straight forward and simple with the Dynamics 365 Commerce mobile apps for Android and iOS. The Store Commerce mobile apps deliver the same capabilities and advantages of the [Store Commerce app for Windows](store-commerce.md) on phone and tablet form factors. The mobile apps can be installed directly from the Apple and Google Play app stores and no longer require a developer to create a new application package to deploy or update the apps. 

The Store Commerce mobile apps retain full functional parity with current Retail hybrid apps. In addition, Store Commerce for iOS includes support for dedicated hardware station. Now iOS devices can communicate with networked payment terminals, receipt printers and cash drawers without requiring a shared hardware station to be deployed. 

The Store Commerce apps for Windows, Android and iOS are the next generation of point of sale applications for Dynamics 365 Commerce. The current Modern point of sale (MPOS) application and the [Retail hybrid apps](hybridapp.md) for mobile will be deprecated in October of 2023. We recommend you use Store Commerce or CPOS for all new POS deployments. Existing customers should plan to migrate from the Retail hybrid app to Store Commerce. For more information about the deprecation schedule for MPOS and the Retail hybrid apps, see the [Modernizing the Dynamics 365 Commerce in-store technology stack](https://www.microsoft.com/en-au/download/details.aspx?id=103896) white paper. 

## App architecture

The Store Commerce mobile apps use the same topology as the Store Commerce app for Windows when it is deployed in hybrid mode. The Store Commerce mobile apps are shell applications that render Cloud Point of Sale (CPOS) directly from the CSU, as well as connecting to Headless Commerce and Commerce Headquarters through the CSU. The shell application model allows Store Commerce to support a dedicated hardware station for direct integration with a payment terminal, printer, cash drawer, and other peripherals. You don't have to set up a shared hardware station to use hardware devices. 

To update the Store Commerce mobile apps, simply update the CSU - all new POS functionality and features will automatically be picked up by the apps. For more information about how to update the CSU, see [Apply updates and extensions to Commerce Scale Unit (cloud)](../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md).

The shell apps are serviced through app store updates. When minor versions reach general availability (GA), Microsoft will publish that version to the app stores. We may also publish patches between minor version updates to release high priority bug fixes.

## Prerequisites

The Store Commerce mobile apps require Dynamics 365 Commerce, and specifically the Commerce headquarters and Cloud Scale Unit components. Below are the minimum OS and CSU versions required by the Android and iOS mobile apps. 

| Prerequisite                       | Android      | iOS  |
| ---------------------------------- | ------------ | ---- |
| OS version                         | 7.0          | 15.0 |
| Commerce Scale Unit (CSU) version | 9.38.22266.8 | TBD  |

## Installation

The Store Commerce mobile apps can be installed directly from the Google Play store or Apple App store. 

- [Store Commerce app for Android](https://aka.ms/storecommerceandroid)
- Store Commerce app for iOS (available soon)

The Android app .apk and Apple .ipa packages can also be downloaded from the Lifecycle Services Portal (LCS) Shared asset library. 

## Device and register setup

Before a register can be activated on the Store Commerce mobile apps, set up a device and a register in Commerce Headquarters. Read more about [devices and registers](../implementation-considerations-devices.md). 

### **Device setup**

In Commerce Headquarters, go to Retail and Commerce > Channel setup > POS setup > Devices and create a new device. Select the Modern POS - Android or Modern POS - iOS application type as appropriate for the mobile app you are deploying. NOTE: These application types are also used to deploy the current Hybrid apps for Android and iOS. following the deprecation of MPOS, these labels will be updated to Store Commerce - Android and Modern POS - iOS. 

### **Register setup**

You can create a new register and associate it with the device you created in the previous step, or you can associate an existing register to your new device. For more information about registers, see the [Create and associate registers](../tasks/create-associate-registers.md) help topic.

### **Screen layout setup**

If you are repurposing a screen layout that is included in the demo data provided with Dynamics 365 Commerce license, the Store Commerce app will automatically select the included Compact layout, as long as the screen resolution of your device is smaller than 480px x 853px in portrait orientation. However, if you are creating a screen layout from scratch, or your mobile device uses a larger resolution than the compact layout supports, be sure to create a resolution and associated button grids appropriate to the phone or tablet you plan to deploy to. For more information about screen layout configuration, see the [POS user interface visual configurations](../pos-screen-layouts.md) help topic. 

After devices and registers have been configured, go to Retail and Commerce > Retail and Commerce ID > Distribution Schedules and run the registers job.

## Activation

To activate a device on the Store Commerce mobile apps:

1. Launch the app on the mobile device
2. Enter the CPOS URL. You can find the CPOS URL on the environment details page in LCS or on the Channel profiles page in Commerce (Dynamics 365 Commerce > Channel setup > Channel profiles).
3. Sign in with credentials that are associated with a worker who has permission to manage devices.
4. Select the store associated with the register you created or reused in Headquarters.
5. Select the register you associated with the device you created in Headquarters.

Your device is now activated. You can sign into the register with the Operator ID and password for a worker associated with the store you selected. 

For more information about device activation, see [Point of sale (POS) device activation](retail-device-activation.md#activate-a-modern-pos-or-cloud-pos-device-by-using-guided-activation)

## Feature parity with Store Commerce for Windows

 The table below compares the capabilities of the Store Commerce app across Windows, Android and iOS platforms.

| Feature                                                      | Windows | Android | iOS  |
| ------------------------------------------------------------ | ------- | ------- | ---- |
| Dedicated hardware station                                   | Y       | Y       | Y    |
| Shared hardware station                                      | Y       | Y       | Y    |
| Communication with networked peripherals (payment terminal, printer, cash drawer) | Y       | Y       | Y    |
| OPOS peripherals through Local HWS                           | y       |         |      |
| Offline mode                                                 | y       |         |      |



## More information

- [Store Commerce app](store-commerce.md)
- [Choose between Store Commerce and Cloud POS](../mpos-or-cpos.md)
- [Troubleshoot Store Commerce setup and installation issues](../troubleshoot/store-commerce-setup-installation.md)
