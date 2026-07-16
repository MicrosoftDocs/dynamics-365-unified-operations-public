---
title: Store Commerce Hardware station extensibility for Android, iOS, and macOS devices
description: This article describes how to build Microsoft Dynamics 365 Commerce Store Commerce apps for Android, iOS, and macOS with Hardware station extensibility.
author: anush6121
ms.author: anvenkat
ms.date: 06/07/2026
ms.topic: how-to
ms.reviewer: mirao
ms.search.region: global
ms.search.validFrom: 07/01/2020
ms.custom: 
  - bap-template
---

# Store Commerce Hardware station extensibility for Android, iOS, and macOS devices

[!include [banner](../../includes/banner.md)]

This article describes how to build Microsoft Dynamics 365 Commerce Store Commerce apps for Android, iOS, and macOS with Hardware station extensibility.

- As of the Commerce version 10.0.41 release, the Store Commerce app for Android supports Hardware station extensibility.
- As of the Commerce version 10.0.44 release, the Store Commerce app for iOS supports Hardware station extensibility.
- As of the Commerce version 10.0.49 release, the Store Commerce app for macOS is available through the Store Commerce SDK.

This functionality enables the following capabilities:

- Customers can build extensions to support their various Hardware station requirements.
- Organizations with fiscal integration requirements can use Android mobile devices with fiscal printers.
- Customers can create their own Android Application Package (APK) or iOS App Store Package (IPA) and distribute them through their respective app stores or internal channels.
  
## Prerequisites

To build the Store Commerce app for Android or iOS with hardware station extensibility, first install the .NET Multi-platform App UI workload in Visual Studio 2022.
  
## Build the Store Commerce app for Android or iOS by using the Store Commerce mobile SDK

To build the Store Commerce app for Android or iOS by using the Store Commerce mobile software development kit (SDK), follow these steps:

1. Go to the [Microsoft Lifecycle Services Shared Asset Library](https://lcs.dynamics.com/V2/SharedAssetLibrary).
1. Under **Retail Self-service package**, download the latest Store Commerce for Android package (version 10.0.41 onwards for Android extensibility, version 10.0.44 onwards for iOS extensibility).
    > [!NOTE]
    > The **Store Commerce for Android package** includes both **Android and iOS dependencies**. There's no separate iOS package.
1. Unzip the Store Commerce for Android package, and then copy the `packages` folder to your repository root.
1. Next, modify the `nuget.config` file to include the `packages` folder as a package source. Under the `<packageSources>` node, add `<add key="Dynamics365Commerce-Mobile-Dependencies" value="./packages" />`.
1. Change the app name displayed in the Android launcher or iOS home in the mobile app project by setting the `ApplicationTitle` value.
1. Change the package name in the mobile app project by setting the `ApplicationId` value.
1. Build the mobile samples solution.

> [!TIP]
> For the latest sample project and detailed build and packaging instructions for Android, iOS, and macOS, see [StoreCommerceMobile README](https://github.com/microsoft/Dynamics365Commerce.InStore/blob/release/9.58/src/PackagingSamples/StoreCommerceMobile/README.md) in the Dynamics 365 Commerce InStore repository.

### Platform-specific configurations

#### Android

- If you configure an Android emulator, you can start debugging the app directly from Visual Studio 2022.
- If you don't want to develop an Android app, comment out the `net8.0-android` target framework (`<TargetFramework>net8.0-android</TargetFramework>`) in the mobile app project.

#### iOS

- If you're developing on Windows, you must pair a Mac for iOS development as described in [Pair to Mac for iOS development](/dotnet/maui/ios/pair-to-mac).
- If you don't want to develop an iOS app, comment out the `net8.0-ios` target framework (`<TargetFramework>net8.0-ios</TargetFramework>`) in the mobile app project.

#### macOS

- Building the macOS app requires a Mac that runs macOS 26 or later and has the required Xcode and .NET MAUI components installed. The built app runs on macOS 15 or later.
- To build the macOS app, ensure the `net10.0-maccatalyst` target framework is included in the mobile app project.
- If you don't want to develop a macOS app, comment out the `net10.0-maccatalyst` target framework (`<TargetFramework>net10.0-maccatalyst</TargetFramework>`) in the mobile app project.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
