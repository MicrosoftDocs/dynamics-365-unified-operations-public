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

[!include [banner](../includes/banner.md)]

This topic explains how to create a POS extension using the independent POS extension model and sealed SDK. This topic applies to Retail software development kit (SDK) version 10.0.18 and later.

## POS

The Dynamics 365 Commerce – Store Commerce application allows first-line workers, such as cashiers, sales and inventory associates, stock clerks, and store managers to perform various commerce operations. The Dynamics 365 Commerce solution provides different device types to perform these operations across platform and form factors.

## Modern-Point of Sale (MPOS)
MPOS is a Universal Windows Platform (UWP) app that runs on a Windows device. The MPOS client can communicate with peripheral devices, such as cash drawers, credit card readers, and printers, by using Hardware Station. 

## Cloud Point of Sale (CPOS)
CPOS is a hosted version of the POS that runs in the browser. The CPOS app is deployed in the cloud.

## Store Commerce
The Store Commerce app is a Windows app from Microsoft Store that runs on a Windows device. The Store Commerce app uses the Chromium engine to render the app. The rendering using the Chromium engine has better rendering performance than the native JavaScript UWP app in Windows.

Store Commerce app will replace MPOS when Store Commerce  has full functional parity with MPOS, Currently, the Store Commerce doesn't support running offline (when there is no connectivity to Retail Server).

## iOS Hybrid app

The iOS hybrid app is shell app that runs in iOS device, the app is shell which hosts the CPOS.

## Android Hybrid app

The Android hybrid app is shell app that runs in android device, the app is shell which hosts the CPOS.

The code base is same for the different POS application but how its packaged, deployed and renders varies by platform and the application type. Customization developed can work across different application type without duplicating or rewriting the code for different platforms, there may be some extension components which are platform specific but most of the extension code can work across platform.

## POS Independent extension

POS application can be extended independently for extension scenarios by using the POS SDK, the POS SDK supports modifying/creating the POS user experience, OOB functional enhancements or modifications, validations and adding custom feature/functionalities.

### Extend POS UI:

The POS UI can be extended to add custom columns, App bar buttons and Custom controls depending on the view. Cart view and Welcome screen supports configuration using the screen layout designer, other views can be extended by writing custom code.

### Override POS Business logic:

POS business logic can be extended to add custom logic by overriding the POS request handlers.

### Pre and Post triggers:

Custom logic can be added before or after any POS operations.

### Consume APIs:

POS also exposes APIs and UX controls which can be consumed in extension scenarios.

### Custom UX and APIs:

POS can be extended to add custom views and APIs to support new functionalities and features.

### Custom operations:
	
Custom operations can be added in POS to perform any custom functionalities.

 [Getting started with POS extension](pos-getting-started.md)
