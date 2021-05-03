---
title: Store Commerce app in Microsoft Dynamics 365 Commerce
description: This topic explains how to setup and configure the Store Commerce app.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 04-20-2020
ms.dyn365.ops.version: AX 10.0.19
---

# Store Commerce app in Microsoft Dynamics 365 Commerce

[!include [banner](../includes/banner.md)]

This topic applies to Dynamics 365 Commerce version 10.0.19 and later.

The Store Commerce app in Microsoft Dynamics 365 Commerce provides rich commerce functionalities for first-line workers, such as cashiers, sales associates, inventory associates, stock clerks, and store managers, to perform various commerce operations like cash and carry transactions, cash/shift management, customer engagement, assisted selling, clienteling, endless aisle, order processing/fulfillment, inventory management, and reporting.

Store Commerce is a Windows app from the Microsoft Store that runs on a Windows device. The Store Commerce app uses the Chromium engine to render the app. The Chromium engine has better rendering performance than the native JavaScript UWP app in Windows. The app will be available in the Microsoft Store for easier discovery, download and deployment, simplifying the overall lifecycle of deployment and servicing.

Store Commerce is a shell app for Windows that uses Microsoft Edge WebView2 to render the Cloud Point of Sale (CPOS). CPOS can run only in a web browser, but Store commerce can run as a native Windows app like [Modern Point of Sale (MPOS)](retail-modern-pos-architecture.md). Store Commerce supports local hardware station and can be directly integrated to payment terminal, printer, and cash drawer. You don't need to setup shared hardware station to use hardware devices. 

Store commerce uses the Chromium engine to render the UI instead of the Universal Windows Platform (UWP) app rendering framework. The key difference between MPOS and Store Commerce is that Store Commerce uses the Chromium engine to render the app.

Store Commerce will replace MPOS when Store Commerce has full functional parity with MPOS. Currently, Store Commerce doesn't support running offline (when there is no connectivity to Retail Server). For more information about the different POS apps and topology, see [Choose between Modern POS (MPOS) and Cloud POS](../mpos-or-cpos.md)

## Setup and Installation:

Prerequisites: Install the Microsoft Edge browser, the app uses the Microsoft Edge WebView2 control.

The Store commerce is available in Microsoft Store to download and installation. Open Microsoft Store and search for Microsoft Dynamics 365 Commerce – Store Commerce, after the app discovery click Get to install the app. After installation in the start menu search for Store commerce and open the app.

Once the app is launched follow the below steps for configuration and activating the app:
1.	In the app start page, enter the Cloud POS URL, you can find the Cloud POS URL from LCS environment details page or in Dynamics 365 commerce > Channel Setup > Channel Profiles.
2.	Click Save.
3.	After Saving the URL follow the steps to activate the store commerce app, for detailed steps to activate the app refer [POS activation guide](retail-device-activation.md#activate-a-modern-pos-or-cloud-pos-device-by-using-guided-activation).
4.	Once the app is activated, login with employee account and perform commerce operations.

### Troubleshooting setup issues:

#### Reset the app:

Suppose if you entered invalid CPOS URL and want to change it or the app get into some error state during activation , then you can restart the process by resetting the app, follow the below steps to reset the app:
+ Right-click the app in the Start menu and Choose More > App settings.
+ Scroll down the app settings page to the “Reset” button.
+ Click “Reset” and acknowledge the confirmation prompt.

## Customizing the app:

The Store commerce app can be customized using the POS SDK, the POS SDK supports modifying/creating new POS user experience, out of the box functional enhancements or modifications, validations and adding custom feature/functionalities. 

Extension developed using POS SDK will work for CPOS, MPOS and Store commerce but how its package and deployed between MPOS and CPOS are different.

Since the Store commerce renders the CPOS, so follow the CPOS packaging and deployment options for deploying the store commerce extension.

Refer the POS Independent extension document for how to customize the POS using the POS SDK.

### Hardware station:
The app can also be extended to integrate with hardware devices. Refer the [Integrate the POS with a new hardware device document for more details](hardware-device-extension.md).
