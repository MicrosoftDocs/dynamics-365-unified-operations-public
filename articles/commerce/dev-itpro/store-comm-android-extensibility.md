---
title: Store Commerce Hardware station extensibility for Android devices
description: This article describes how to build out the Microsoft Dynamics 365 Commerce Store Commerce app for Android with hardware station extensibility.
author: anush6121
ms.author: anvenkat
ms.date: 08/08/2024
ms.topic: how-to
ms.reviewer: v-chrgriffin
ms.search.region: global
ms.search.validFrom: 07/01/2020
ms.custom: 
  - bap-template

---

# Store Commerce Hardware station extensibility for Android devices

[!include [banner](../../includes/banner.md)]

This article describes how to build out the Microsoft Dynamics 365 Commerce Store Commerce app for Android with hardware station extensibility.

As of the Dynamics 365 Commerce version 10.0.41 release, the Store Commerce app for Android supports Hardware station extensibility. This functionality enables the following capabilities:
- Customers can build extensions to support their various Hardware station requirements.
- Organizations with fiscal integration requirements can use Android mobile devices with fiscal printers.
- Customers can create their own Android Application Package (APK) and publish it to the Google Play Store or the Google Play for Business Store.
  
## Prerequisites

To build out the Store Commerce app for Android with hardware station extensibility, you must first install the .NET Multi-platform App UI workload in Visual Studio 2022.
  
## Build out the Store Commerce app for Android using the Store Commerce mobile SDK

To build out the Store Commerce app for Android using the Store Commerce mobile software development kit (SDK), follow these steps.

1. Navigate to the [Microsoft Lifecycle Services Shared Asset Library](https://lcs.dynamics.com/V2/SharedAssetLibrary).
1. Under **Retail Self-service package**, download the latest Store Commerce for Android package (version 10.0.41 or later).
1. Unzip the Store Commerce for Android package, and then copy the `packages` folder to your repository root.
1. Next, you must modify the nuget.config file to include the `packages` folder as a package source. Under the `<packageSources>` node, add `<add key="Dynamics365Commerce-Android-Dependencies" value="./packages" />`.
1. Modify the app name displayed in the Android launcher in the MainActivity.cs file by updating the `Label` property of the `Activity` attribute.
1. Modify the package name in the AndroidManifest.xml file by changing the `package` attribute of the manifest node. You should also modify the `android:label` attribute of the `application` node.
1. Build the mobile samples solution.
1. Assuming that an Android emulator is configured, you can start debugging the app from Visual Studio 2022.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
