---
title: POS extension overview
description: This article provides information about how you can create point of sale (POS) extensions by using the new independent POS extension model and sealed software development kit (SDK).
author: josaw1
ms.date: 04/13/2021
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-04-13
ms.dyn365.ops.version: AX 10.0.18
---

# POS extension overview

[!include [banner](../../../includes/banner.md)]

Point of sale (POS) apps can be extended independently by using the POS extension feature of the Commerce software development kit (SDK). You can modify and create the POS user experience, enhance or modify out-of-box functionality, add validations, and add custom features.

You can use extensions in the following ways:

+ **Extend the POS user interface (UI):** You can add custom columns, app bar buttons, and custom controls, depending on the view. The cart view and the welcome page can be configured by using the screen layout designer. Other views can be extended by writing custom code.
+ **Override POS business logic:** By overriding the POS request handlers, you can extend POS business logic to add custom logic.
+ **Add pre-triggers and post-triggers:** You can add custom logic before or after any POS operation.
+ **Consume APIs:** POS exposes APIs and user experience (UX) controls that can be consumed in extension scenarios.
+ **Add custom UX and APIs:** You can extend POS to add custom views and APIs that support new functionality and features.
+ **Add custom operations:** You can add custom operations to perform custom functionality.

The following articles explain how to create a POS extension by using the independent POS extension model and sealed SDK.

+ [Getting started with POS extensions](pos-extension-getting-started.md)
+ [Create a POS extension package project](create-pos-extension-package.md)
+ [Create an .appx file for a Modern POS extension package](create-pos-extension-appx.md)
+ [Debug POS extensions](debug-pos-extension.md)

This article applies to version 10.0.18 and later of the Commerce SDK.

## Supported apps

The different POS apps have the same code base. However, the extensions are packaged, deployed, and rendered differently, depending on the platform and the app type. Customizations that you develop will work across app types without requiring that the code is duplicated or rewritten for different apps. Although some extension components might be app-specific, most of the extension code can work across apps.

The following table shows that apps that you can create POS extensions for.

| App | Description |
|---|---|
| Point of sale (POS) | POS lets first-line workers, such as cashiers, sales and inventory associates, stock clerks, and store managers, perform various commerce operations. The Microsoft Dynamics 365 Commerce solution provides different device types, so that these operations can be performed across platforms and form factors. |
| Modern point of sale (MPOS) | MPOS is a Universal Windows Platform (UWP) app that runs on a Windows device. The MPOS client can communicate with peripheral devices, such as cash drawers, credit card readers, and printers, by using Hardware Station. |
| Cloud point of sale (CPOS) | CPOS is a hosted version of POS that runs in a browser. The CPOS app is deployed in the cloud. |
| Store Commerce | The Store Commerce app in Dynamics 365 Commerce is a Windows app from Microsoft Store that runs on a Windows device. The Chromium engine is used to render the app. The Chromium engine has better rendering performance than the native JavaScript UWP app in Windows. When Store Commerce has full functional parity with MPOS, it will replace MPOS. Currently, Store Commerce doesn't support running offline (when there is no connectivity to Retail Server). |
| iOS hybrid app | The iOS hybrid app is a shell app (wrapper) that runs on an iOS device. The shell hosts CPOS. |
| Android hybrid app | The Android hybrid app is a shell app that runs on an Android device. The shell hosts CPOS. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
