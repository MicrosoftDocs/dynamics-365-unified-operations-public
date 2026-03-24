---
title: POS extension overview
description: This article provides an overview of how you can create Microsoft Dynamics 365 Commerce point of sale (POS) extensions by using the independent POS extension model and sealed software development kit (SDK).
author: josaw1
ms.date: 02/25/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-04-13
ms.custom: 
  - bap-template
---

# POS extension overview

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/retail-sdk-deprecation-banner.md)]

This article provides an overview of how you can create Microsoft Dynamics 365 Commerce point of sale (POS) extensions by using the independent POS extension model and sealed software development kit (SDK).

You can independently extend point of sale (POS) apps by using the POS extension feature of the Commerce software development kit (SDK). You can modify and create the POS user experience, enhance or modify out-of-box functionality, add validations, and add custom features.

You can use extensions in the following ways:

- **Extend the POS user interface (UI):** Add custom columns, app bar buttons, and custom controls, depending on the view. Configure the cart view and the welcome page by using the screen layout designer. Extend other views by writing custom code.
- **Override POS business logic:** Extend POS business logic to add custom logic by overriding the POS request handlers.
- **Add pre-triggers and post-triggers:** Add custom logic before or after any POS operation.
- **Consume APIs:** POS exposes APIs and user experience (UX) controls that can be consumed in extension scenarios.
- **Add custom UX and APIs:** Extend POS to add custom views and APIs that support new functionality and features.
- **Add custom operations:** Add custom operations to perform custom functionality.

The following articles explain how to create a POS extension by using the independent POS extension model and sealed SDK.

- [Getting started with POS extensions](pos-extension-getting-started.md)
- [Create a POS extension package project](create-pos-extension-package.md)
- [Create an .appx file for a Modern POS extension package](create-pos-extension-appx.md)
- [Debug POS extensions](debug-pos-extension.md)

This article applies to version 10.0.18 and later of the Commerce SDK.

## Supported apps

The different POS apps use the same code base. However, the platform and app type determine how the extensions are packaged, deployed, and rendered. Customizations that you develop work across app types without requiring code duplication or rewriting for different apps. Although some extension components might be app-specific, most of the extension code works across apps.

The following table shows the apps that you can create POS extensions for.

| App | Description |
|---|---|
| Point of sale (POS) | POS lets frontline workers, such as cashiers, sales and inventory associates, stock clerks, and store managers, perform various commerce operations. The Microsoft Dynamics 365 Commerce solution provides different device types, so that these operations can be performed across platforms and form factors. |
| Modern point of sale (MPOS) | MPOS is a Universal Windows Platform (UWP) app that runs on a Windows device. The MPOS client can communicate with peripheral devices, such as cash drawers, credit card readers, and printers, by using Hardware Station. Modern POS is a legacy app and is replaced by the Store Commerce app. Updates and support for Modern POS end in October 2023. For more information, see [Migrate Modern POS to Store Commerce](migrate-mpos-store-commerce.md). |
| Store Commerce for web | Store Commerce for web is a hosted version of POS that runs in a browser. The Store Commerce for web app is deployed in the cloud. |
| Store Commerce | The Store Commerce app in Dynamics 365 Commerce is a Windows app from Microsoft Store that runs on a Windows device. The Chromium engine renders the app. The Chromium engine has better rendering performance than the native JavaScript UWP app in Windows. Store Commerce has full functional parity with MPOS, and replaces MPOS as the default POS app for Dynamics 365 Commerce. For more information, see [Store Commerce app](../store-commerce.md). |
| Store Commerce for iOS | Store Commerce for iOS is a shell app that runs on an iOS device. The shell hosts Store Commerce for web and supports network connectivity to peripheral devices. |
| Store Commerce for Android | Store Commerce for Android is a shell app that runs on an Android device. The shell hosts Store Commerce for web while supporting network connectivity to peripheral devices. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
