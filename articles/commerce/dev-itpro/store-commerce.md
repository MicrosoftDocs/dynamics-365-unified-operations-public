---
# required metadata

title: Store commerce
description: This topic explains how to setup and configure Store commerce app.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 04-20-2020
ms.dyn365.ops.version: AX 10.0.19

---

# Store commerce

[!include [banner](../includes/banner.md)]

This topic applies to Dynamics 365 commerce application version 10.0.19 and later.

Store commerce provides rich commerce functionalities for all first-line workers, such as cashiers, sales and inventory associates, stock clerks, and store managers etc. to perform various commerce operations like cash and carry transactions, cash/shift management, customer engagement, assisted selling, clienteling, endless aisle, order processing/fulfillment, inventory management, and reporting.
Store commerce app is Windows Store app that runs in the windows device, the Store commerce app uses the windows chromium engine to render the app which has better rendering performance when compared to the native JavaScript UWP app in windows. The Store commerce app will be available in Windows store for easier discovery, download and deployment, this simplifies the overall ALM of deployment and servicing.

This topic is applicable to app

The Store commerce app is a shell app for Windows which uses the WebView to render the Cloud Point of Sale (CPOS), the CPOS can run only in web browser but the Store commerce can run as native windows app similar to [Modern Point of Sale (MPOS)](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-modern-pos-architecture) and support local hardware station, can be directly integrated to Payment terminal, printer, cash drawer etc. no need to setup shared hardware station to use hardware devices. 
Store commerce uses the windows chromium engine to render the UI instead of the UWP app rendering, the key difference between MPOS and the Store commerce app is the Store commerce app uses the windows chromium engine to render which provides better rendering performance than Windows UWP JavaScript app.

In the future the Store commerce app will replace the Modern Point of Sale (MPOS) when it has full functional parity with MPOS, currently the Store commerce app don’t support in offline mode (when there is no connectivity to Retail Server) but MPOS supports offline. For more details about the different POS app and topology refer this [doc.](https://docs.microsoft.com/en-us/dynamics365/commerce/mpos-or-cpos)

## Setup and Installation:

The Store commerce is available in windows store to download and installation. Open Microsoft Store and search for Microsoft Dynamics 365 Commerce – Store Commerce, after the app discovery click Get to install the app. After installation in the start menu search for Store commerce and open the app.

Once the app is launched follow the below steps for configuration and activating the app:
1.	In the app start page, enter the Cloud POS URL, you can find the Cloud POS URL from LCS environment details page or in Dynamics 365 commerce > Channel Setup > Channel Profiles.
2.	Click Save.
3.	After Saving the URL follow the steps to activate the store commerce app, for detailed steps to activate the app refer [POS activation guide](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-device-activation#activate-a-modern-pos-or-cloud-pos-device-by-using-guided-activation).
4.	Once the app is activated, login with employee account and perform commerce operations.

## Customizing the app:

The Store commerce app can be customized using the POS SDK, the POS SDK supports modifying/creating new POS user experience, out of the box functional enhancements or modifications, validations and adding custom feature/functionalities. 

Extension developed using POS SDK will work for CPOS, MPOS and Store commerce but how its package and deployed between MPOS and CPOS are different.

Since the Store commerce renders the CPOS, so follow the CPOS packaging and deployment options for deploying the store commerce extension.

Refer the POS Independent extension document for how to customize the POS using the POS SDK.

### Hardware station:
The app can also be extended to integrate with hardware devices. Refer the [Integrate the POS with a new hardware device document for more details.](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/hardware-device-extension)
