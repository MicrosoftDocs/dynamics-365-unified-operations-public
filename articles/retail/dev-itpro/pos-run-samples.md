---
# required metadata

title: Run Retail POS samples
description: This topic explains how to run the Retail POS samples.
author: mugunthanm
manager: AnnBe
ms.date: 11/27/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Retail, Retail
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-11-27
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Run Retail POS samples

There are several samples in the Retails SDK that demonstrate retail extensions. This topic explains how to run these samples. 

This topic applies to Dynamics 365 for Finance and Operations, Enterprise edition and Dynamics 365 for Retail with Platform update 8 and Retail Application update 4 hotfix.

## Run the StoreHoursSample sample
1. Open **ModernPos.Sln** from the **Retail SDK\\POS** folder.
2. Select the **POS.Extensions** project in the solution and click **Show All Files**.
3. Right-click the **SampleExtensions** folder and select **Include in Project**.
4. Open the **extensions.json** file and add the extension folder for **StoreHoursSample**, so that POS during runtime will include this extension. The **baseUrl** value must exactly match the relative path and extension folder name.

    ```Typescript
    {
        "extensionPackages": [
            {
                "baseUrl": "StoreHoursSample"
            },
            {
                "baseUrl": " SampleExtensions"
            },
            {
                "baseUrl": " SampleExtensions2"
            }
        ] 
    }
    ```
    **Note:** In the extension.json file you must include at least two extension folders. If you add only one extension folder, then POS will not load the extension.
1. Open the **tsconfig.json** file and comment out the extension package folders from the exclude list. POS will use this file to determine whether to compile the extension. By default, the list contains the sample extensions list. If you want to compile any extension to the POS, then you need add the extension folder name and comment out the extension from the extension as shown. 

    ```Typescript
    {
        "extends": "../tsconfigs/tsmodulesconfig",
        "exclude": [
            "AuditEventExtensionSample"
            , "B2BSample"
            ,"CustomerSearchWithAttributesSample"
            ,"FiscalRegisterSample"
            ,"PaymentSample"
            ,"PromotionsSample"
            ,"SalesTransactionSignatureSample"
            // ,"SampleExtensions"
            // ,"SampleExtensions2"
            //,"StoreHoursSample"
            ,"SuspendTransactionReceiptSample"
        ],
        "compilerOptions": {
            // There is a strange behavior for TypeScript 2.2.2 in map and source roots generated in compiled JS and map files. 
            // The following may change in future TypeScript versions.
            // In case there is only one top level extensions folder with .ts files included, the following two root 
            // directories need to be changed to include the extensions folder.
            // For example, change both roots to "./SampleExtensions" if "SampleExtensions" folder is the only top level 
            // folder that has .ts files included in the project.
            // That is, either "SampleExtensions" folder is the only top level folder, or all other top level folders 
            // have .js files only, no .ts files.
            "mapRoot": "./", /* Cannot be specified in base file. Adds full path to ".map" in the js file to enable debug in VS. */
            "sourceRoot": "./" /* Cannot be specified in base file. Adds full path to ".ts" in the map file to enable debug in VS. */
        }
    }
    ```
    If you want to enable other extensions, comment them out from the exclude list. For example, if you want to include the **B2BSample**, the code would be as follows. 
    
    ```Typescript
    "exclude": [
        "AuditEventExtensionSample"
        // ,"B2BSample"
        ,"CustomerSearchWithAttributesSample"
        ,"FiscalRegisterSample"
        ,"PaymentSample"
        ,"PromotionsSample"
        ,"SalesTransactionSignatureSample"
        // ,"SampleExtensions"
        // ,"SampleExtensions2"
        //,"StoreHoursSample"
        ,"SuspendTransactionReceiptSample"
    ],
    ```
    **Note:** Other extension package folders, even though not included in the Visual Studio project, should be kept in the exclude list if they are not meant to be included.
1. Set **Solution platform** to **x86** and **Deploy option** to **Local Machine** or **Simulator**.
1. Click **Save all** and press **F5** to validate the extensions.
