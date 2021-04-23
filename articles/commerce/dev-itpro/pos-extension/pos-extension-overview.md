---
title: POS extension overview
description: This topic explains how to create a POS extension using the new independent POS extension model and sealed SDK.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18
---

# POS extension overview

[!include [banner](../../includes/banner.md)]

A POS application can be extended independently by using the POS SDK. The POS SDK supports modifying and creating the POS user experience, out-of-bx functional enhancements or modifications, validations, and adding custom features. The extensions include:

+ Extend POS UI: The POS UI can be extended to add custom columns, app bar buttons, and custom controls depending on the view. The cart view and the welcome screen support configuration using the screen layout designer. Other views can be extended by writing custom code.
+ Override POS business logic: You can extend POS business logic to add custom logic by overriding the POS request handlers.
+ Pre and post triggers: You can add custom logic before or after any POS operation.
+ Consume APIs: POS exposes APIs and UX controls which can be consumed in extension scenarios.
+ Custom UX and APIs: You can extend POS to add custom views and APIs to support new functionalities and features.
+ Custom operations: You can add custom operations to perform custom functionalities.

These topics explain how to create a POS extension using the independent POS extension model and sealed SDK. This topic applies to Retail software development kit (SDK) version 10.0.18 and later.

+ [Getting started with POS extensions](pos-extension-getting-started.md)
+ [Create a POS extension package project](create-pos-extension-package.md)
+ [Create a Modern POS extension appx file](create-pos-extension-appx.md)
+ [Debug a POS extension](debug-pos-extension.md)

## Supported apps

The code base is same for the different POS applications but how its packaged, deployed, and renders varies by platform and the application type. Customizations that you develop work across different application types without duplicating or rewriting the code for different platforms. There may be some extension components that are platform specific, but most of the extension code can work across platforms.

You can create POS extensions for these apps.

App | Description
---|---
POS | The Dynamics 365 Commerce – Store Commerce application allows first-line workers, such as cashiers, sales and inventory associates, stock clerks, and store managers to perform various commerce operations. The Dynamics 365 Commerce solution provides different device types to perform these operations across platform and form factors.
Modern-Point of Sale (MPOS) | MPOS is a Universal Windows Platform (UWP) app that runs on a Windows device. The MPOS client can communicate with peripheral devices, such as cash drawers, credit card readers, and printers, by using Hardware Station.
Cloud Point of Sale (CPOS) | CPOS is a hosted version of the POS that runs in the browser. The CPOS app is deployed in the cloud.
Store Commerce | The Store Commerce app is a Windows app from Microsoft Store that runs on a Windows device. The Store Commerce app uses the Chromium engine to render the app. The rendering using the Chromium engine has better rendering performance than the native JavaScript UWP app in Windows. Store Commerce app will replace MPOS when Store Commerce  has full functional parity with MPOS, Currently, the Store Commerce doesn't support running offline (when there is no connectivity to Retail Server).
iOS hybrid app | The iOS hybrid app is a shell app that runs on an iOS device. The shell hosts CPOS.
Android hybrid app | The Android hybrid app is a shell app that runs on an Android device. The shell hosts CPOS.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
