---
title: Store Commerce app for mobile platforms
description: Learn how to get started using the Microsoft Dynamics 365 Commerce Store Commerce app for Android and iOS.
author: anush6121
ms.author: anvenkat
ms.date: 09/23/2025
ms.topic: how-to
ms.reviewer: v-chrgriffin
ms.search.region: global
ms.search.validFrom: 2018-10-29
ms.custom: 
  - bap-template
---

# Store Commerce app for mobile platforms

[!include [banner](../includes/banner.md)]

This article explains how to get started using the Microsoft Dynamics 365 Commerce Store Commerce apps for Android and iOS.

The Dynamics 365 Commerce mobile apps for Android and iOS make the process of deploying full-featured mobile point of sale (POS) devices for your retail environment straightforward and simple. The Store Commerce mobile apps deliver nearly all the capabilities and advantages of the [Store Commerce app for Windows](store-commerce.md), and perform well on a wide range of iOS and Android phones and tablets. You can install the Store Commerce mobile apps directly from the Apple and Google Play app stores, so you don't require a developer to create an application package to deploy or update them. 

The Store Commerce mobile apps retain full functional parity with current Retail hybrid apps. In addition, Store Commerce for iOS includes support for a dedicated hardware station, so that iOS devices can communicate with networked payment terminals, receipt printers, and cash drawers without requiring the deployment of a shared hardware station. 

> [!IMPORTANT]
> The Store Commerce apps for Windows, Android, and iOS are the next generation POS applications for Dynamics 365 Commerce. The Store Commerce apps offer numerous improvements over their predecessors while retaining full functional and feature parity. Microsoft deprecated Modern point of sale (MPOS) and the Retail Hybrid apps for Android and iOS in late 2023, and recommends that you use the Store Commerce apps for Windows, Android, and iOS and Store Commerce for web for all new POS deployments. Existing customers should plan to migrate from MPOS and the Retail hybrid apps to Store Commerce. For more information, see [Migrate Modern POS to Store Commerce](pos-extension/migrate-mpos-store-commerce.md). 

## App architecture

The Store Commerce mobile apps use the same topology as the Store Commerce app for Windows when deployed in hybrid mode. The Store Commerce mobile apps are shell applications that render Store Commerce for web directly from the Commerce Scale Unit (CSU), and connect to Headless Commerce and Commerce headquarters via the CSU. The shell application model enables Store Commerce apps to support a dedicated hardware station for direct integration with a payment terminal, printer, cash drawer, and other peripherals. You don't have to set up a shared hardware station to use hardware devices. 

To update a Store Commerce mobile app, just update the CSU. All new POS functionality and features are automatically picked up by the app. For more information about how to update the CSU, see [Apply updates and extensions to Commerce Scale Unit (cloud)](../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md).

The shell apps are serviced through app store updates. When a minor version reaches general availability (GA), Microsoft publishes it to the app stores. Microsoft might also publish patches between minor version updates to release high-priority bug fixes.

## Feature parity with Store Commerce for Windows

> [!IMPORTANT]
> The Dynamics 365 Payment Connector for Adyen doesn't currently support Store Commerce for iOS with local network architecture configurations.

The following table compares the capabilities of the Store Commerce app across Windows, Android, and iOS platforms.

| Feature                                                      | Windows | Android | iOS  |
| ------------------------------------------------------------ | ------- | ------- | ---- |
| Dedicated hardware station                                   | Yes     | Yes     | Yes  |
| Dedicated hardware station extensibility to support external payment connectors | Yes     | Planned for 2024 Wave 2 | No  |
| Shared hardware station                                      | Yes     | Yes     | Yes  |
| Communication with networked peripherals (payment terminal, printer, and cash drawer) | Yes     | Yes     | Yes  |
| OLE for Point of Sale (OPOS) peripherals through a local hardware station | Yes     | No      | No   |
| Offline mode                                                 | Yes     | Yes      | Yes   |
| [Adyen cloud architecture](https://docs.adyen.com/point-of-sale/design-your-integration/choose-your-architecture/) | Yes     | Yes     | Yes  |
| [Adyen local architecture](https://docs.adyen.com/point-of-sale/design-your-integration/choose-your-architecture/) | Yes     | Yes     | No   |

## Prerequisites

The Store Commerce mobile apps require the CSU and Commerce headquarters components of Dynamics 365 Commerce. The following table lists the minimum operating system (OS) and CSU versions required to run the Android and iOS mobile apps. 

| Prerequisite | Android | iOS  |
| ------------ | ------- | ---- |
| OS version   | 8.1     | 17.4 |

## Install the app

You can install Store Commerce mobile apps directly from the Google Play store or Apple App Store. 

- [Store Commerce app for Android](https://aka.ms/storecommerceandroid)
- [Store Commerce app for iOS](https://aka.ms/storecommerceios)

The Android app (.apk) packages can be downloaded from the Shared asset library in Microsoft Dynamics Lifecycle Services (LCS). 

### Access preview builds

To access Android Store Commerce preview builds for beta testing, go to [Android app testing](https://aka.ms/StoreCommerceForAndroidPreview) at the Google Play Store. To access iOS Store Commerce preview builds for beta testing, go to [Join the Store Commerce beta - TestFlight](https://aka.ms/StoreCommerceForiOSPreview) on your iOS device.

> [!NOTE]
> - When a new release reaches GA, it supersedes the previous version. For hotfixes, Microsoft recommends that you use the latest version. Once a current version reaches GA, there aren't any new releases until the next public preview date.
> - Android and iOS apps are backward and forward compatible. Customers can always update to the latest version regardless of the CSU version.
> - To test new versions of the apps before they're pushed to production, customers should configure policies through Google Play Store and Apple App Store to manage automatic updates.
 
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

If you're repurposing a screen layout included in the demo data that is provided with your Dynamics 365 Commerce license, the Store Commerce app automatically selects the included compact layout if the screen resolution of your device is less than 480 x 853 pixels in the portrait orientation. However, if you're creating a screen layout from scratch, or if your mobile device uses a larger resolution than the compact layout supports, ensure that you create a resolution and associated button grids that are appropriate for the phone or tablet that you plan to deploy to. For more information about screen layout configurations, see [POS user interface visual configurations](../pos-screen-layouts.md). 

After devices and registers are configured, in Commerce headquarters go to **Retail and Commerce \> Retail and Commerce ID \> Distribution Schedules** and run the registers job.

## Activate a device

To activate a device on a Store Commerce mobile app, follow these steps.

1. Open the app on the mobile device.
1. Enter the Store Commerce for web (formerly Cloud POS, or CPOS) URL, which you can find on the environment details page in LCS, or on the **Channel profiles** page in Commerce headquarters (**Retail and Commerce \> Channel setup \> Channel profiles**).
1. Sign in by using the credentials of a worker who has permission to manage devices.
1. Select the store that is associated with the register that you created or reused in Commerce headquarters.
1. Select the register that you associated with the device that you created in Commerce headquarters.
1. Your device should now be activated. You can sign in to the register with the operator ID and password of a worker associated with the store you selected. 

For more information about device activation, see [Activate Store Commerce using guided activation](retail-device-activation.md#activate-store-commerce-using-guided-activation).

## Peripheral setup

The Store Commerce apps for Android and iOS can communicate with most commonly used peripherals that use network protocols for connectivity. Peripherals that require OLE for OPOS drivers or direct USB connection typically require a shared hardware station. For more information about network peripherals, see [Support for network peripherals](network-peripherals.md). 

### Receipt printer

The network protocols for Epson and Star printers enable receipt printing on mobile devices running Store Commerce app. For more information, see [Support for network peripherals](network-peripherals.md#epson-or-star-micronics-receipt-printer-and-a-cash-drawer). 

### Cash drawer

Cash drawers that are connected through an Epson or Star receipt printer's drawer kick (DK) port are supported. The cash drawer configuration in the hardware profile is similar to that of the receipt printer connected to it. Specify "Network" for the **Drawer setting**, specify "Epson" or "Star" for the **Device name**, and then in the **Cash drawer** setting in the register's IP Addresses view, enter the printer's IP address into the **IP address** field. 

### Barcode scanner

The following options for barcode and quick-response (QR) code scanning are available for the Store Commerce app for mobile devices:

**Camera-based barcode scanning - native barcode scanning**: The Store Commerce app for Android and iOS can scan barcodes and QR codes with the rear-facing camera. This out-of-box solution supports all workflows where a barcode scanner can be used to capture product, customer, or receipt data. 

To enable native scanning in the Store Commerce app, in headquarters open the hardware profile for the register used on the mobile device, and then set the **Scanner** setting for the first scanner section to **Device**. When done, run the **Registers (1090)** job to realize the change in POS. To run the register job manually, in headquarters go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedules**, in the left pane select **1090 Registers**, and then on the Action Pane select **Run now**.

To ensure that everything works as expected, confirm that the shell application on the device uses Commerce version 10.0.40 or later (from LCS for Android devices), CSU uses version 9.50 (10.0.40) or later, and Commerce headquarters uses version 10.0.40 or later. 

If the scan icon appears but the camera is blocked, confirm that you have camera permissions turned on for the app on your device.

**Optical scanner**: Handheld devices equipped with an optical barcode scanner usually include a location in settings or a utility that configures the scanner. Enabling barcode scanning for the Store Commerce app with one of these devices usually requires that the optical scanner is configured for keyboard wedge mode only, and that a newline character is appended to the decoded output. 

**Peripheral scanner**: Barcode scanners that attach to mobile devices as a sled and communicate via Bluetooth can be successfully used with the Store Commerce app to scan barcodes and QR codes. 

### Payment terminal

See the [Payment terminals and PIN pads](../retail-peripherals-overview.md#payment-terminals-and-pin-pads) section of the [Retail Peripherals](../retail-peripherals-overview.md) help topic for information about how to connect Store Commerce mobile app to a payment terminal. 

### Offline capabilities in iOS and Android (preview)

[!include [banner](../includes/banner.md)]

Starting with the Commerce version 10.0.45 release, the following offline capabilities for iOS and Android are available.

- **Data synchronization scenarios in SQLite**: Enables efficient data synchronization using SQLite. 
- **Store Commerce SDK**: Provides a comprehensive SDK for developing offline capabilities on iOS.
- **Offline support**: Makes offline mode available on both iOS and Android, enabling uninterrupted
   operations during connectivity disruptions.
- **Offline extensions**: Allows for the extension of offline functionalities both in app and database.
- **Support for offline**: Supports 100+ offline retail operations in SQLite.   
- **Database upgrade support**: Supports database upgrades on both iOS and Android, ensuring
   smoother transitions and improved data integrity. 
- **Enhanced offline register form**: Improves logging for offline switching events to help diagnose and
   support effective offline mode transitions. 
- **Consistent activation experience**: Provides a unified setup flow across platforms, with an in-app option to
    enable support for effective offline mode transitions.

For iOS and Android, data is stored locally in SQLite to enable full offline functionality. Key product, customer, pricing, discount, and configuration data is synchronized locally for offline use. When you launch the Store Commerce mobile app, you must trigger a download session to synchronize the data to the device.

When the Store Commerce mobile app is offline, transactions are stored and queued locally and marked for synchronization. When connectivity is restored, queued transactions are uploaded and synchronized to the CSU. 

This [Github example](https://github.com/microsoft/Dynamics365Commerce.InStore/blob/8cc06eb869a8bcca238fa0e2a92d5f64ecda8e41/src/PackagingSamples/StoreCommerceMobile/StoreCommerce.MobileApp/Contoso.StoreCommerce.MobileApp.csproj#L5C38-L5C48) shows where iOS dependencies are updated. Learn more in the [README file](https://github.com/microsoft/Dynamics365Commerce.InStore/blob/release/9.54/src/PackagingSamples/StoreCommerceMobile/README.md#ios%E2%80%8B).



## Additional resources

[Store Commerce app](store-commerce.md)

[Choose between Store Commerce app and Store Commerce for web](../mpos-or-cpos.md)

[Debug Store Commerce setup and installation issues](/previous-versions/troubleshoot/dynamics-365/commerce/point-of-sale/store-commerce-setup-installation)
