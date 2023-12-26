---
title: Run the point of sale (POS) samples
description: This article explains how to run the POS samples.
author: josaw1
ms.date: 02/01/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-11-27
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update
---

# Run the point of sale (POS) samples

[!include [banner](../../includes/banner.md)]

There are several samples in the Retail SDK that demonstrate extensions. This article explains how to run these samples.

## Run the SampleExtensions in POS
1. Open **ModernPos.Sln** or **CloudPos.sln** from the **Retail SDK\\POS** folder.
2. Select the **POS.Extensions** project in the solution and click **Show All Files**.
3. Right-click the **SampleExtensions** folder and select **Include in Project**.
4. Right-click the **SampleExtensions2** folder and select **Include in Project**.
5. Open the **extensions.json** file and add the extension folder for **SampleExtensions** and **SampleExtensions2**. This means that during runtime POS will include this extension. The **baseUrl** value must exactly match the relative path and extension folder name.

    ```typescript
    {
        "extensionPackages": [
            {
                "baseUrl": "SampleExtensions"
            },
            {
                "baseUrl": "SampleExtensions2"
            }
        ] 
    }
    ```
    > [!Note]  
    > In the extension.json file you must include at least two extension folders. If you add only one extension folder, then POS will not load the extension.
5. Open the **tsconfig.json** file and comment out the extension package folders from the exclude list. POS will use this file to determine whether to compile the extension. By default, the list contains the sample extensions list. If you want to compile any extension to the POS, then you need add the extension folder name and comment out the extension from the extension as shown below. 

    ```typescript
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
            ,"StoreHoursSample"
            ,"SuspendTransactionReceiptSample"
        ],
        "compilerOptions": {
            // There is an unexpected behavior for TypeScript 2.2.2 in map and source roots generated in compiled JS and map files. 
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
    If you want to enable other extensions, comment them out from the exclude list. For example, if you want to include **B2BSample**, the code would be as follows. 
    
    ```typescript
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
        ,"StoreHoursSample"
        ,"SuspendTransactionReceiptSample"
    ],
    ```
    > [!Note] 
    > Other extension package folders, even though not included in the Visual Studio project, should be kept in the exclude list if they are not meant to be included.
6. Set **Solution platform** to **x86** and **Deploy option** to **Local Machine**, or **Simulator** if you are using the Store Commerce app for validation.
7. Select **Save all**, and then select the **F5** key to validate the extensions.

    > [!Note] 
    > For -Store Commerce for web, use a clean solution in Visual Studio, and then rebuild the solution.
8. Go to the product search screen or use the top search bar to search for a product. You should see custom columns in the grid and new app bar buttons.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
