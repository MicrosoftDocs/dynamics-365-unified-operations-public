---
# required metadata

title: Add custom columns to POS transaction grid
description: 
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
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-01-27
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Add custom columns to a POS transaction grid

This topic explains how to add a new custom column to a POS transaction page using the screen layout designer. You can add more information to a transaction page by using the custom column feature. A custom column can be added to the transaction page receipt grid by using the screen layout designer. You can adjust width and position of the columns by using the designer. We added 10 custom columns in the layout for extensions scenarios. You can use all 10 in out layout. The custom columns are already added to the designer metadata. After adding the column to the layout, you run the distribution job so that the column shows up on the transaction page.

> [!NOTE]
> This topic applies to Dynamics 365 for Finance and Operations, Enterprise edition, and to Microsoft Dynamics 365 for Retail with platform update 8 and Retail App update 4 hotfix.

## Add a custom column to the page.
1. Login to Dynamics 365 for Retail.
2. Navigate to **Retail > Channel setup > POS setup > POS > Screen layouts**. Or, search for **Screen layout** in the search bar.
3. Select the **F3MGR** screen layout ID and click the **Designer** button in the action bar.
4. Follow the instructions if prompted to install and enter the AAD credentials to launch the designer.
5. Select the **1440x960 – Full layout** from the layout sizes and click the **Layout designer** button.
6. If prompted click **Open** and follow the instruction to install the designer tool.
7. After installing it will ask for AAD credentials. Provide your credentials to launch the designer.
8. In the designer right-click the transaction grid (receipt grid) and select customize.
9. In the **customization – Receipt** window, select the Lines in the pivot panel drop down.
10. In the **Available columns** window select the **CUSTOM COLUMN 1** and click the **> (arrow)** button to move the column to the **Selected** columns.
11. Click OK to save and close the window.
12. Adjust the column width in the transaction grid using the **screen layout** designer to make sure the column is visible.
13. Click the **X** button in the designer to close the designer.
14. When prompted to **Save changes**, click **Yes**. If you click No the changes will not be saved.
15. Navigate to **Retail > Retail IT > Distribution schedule**.
16. Select the **Registers (1090)** job and click **Run now**.

 ## Add business logic to custom column

1. Open Visual Studio 2015 in administrator mode.
2. Open the **ModernPOS** solution from **…\\RetailSDK\\POS**.
3. Under the **POS.Extensions** project create a new folder named **CustomColumnExtensions**.
4. Under **CustomColumnExtensions**, create a new folder named **Cart**.
5. Under **Cart**, create a new folder named **LinesGrid**.
6. In the **LinesGrid** folder, add a new Typescript file and name it **CustomColumn1Configuration.ts**.
7. Add the following **import** statements to import the relevant entities and context.
    ```Typescript
    import {

        ICustomLinesGridColumnContext,
        CustomLinesGridColumnBase

    } from "PosApi/Extend/Views/CartView";

    import { CustomGridColumnAlignment } from "PosApi/Extend/Views/CustomGridColumns";
    import { ProxyEntities } from "PosApi/Entities";
    ```
8. Create a new class named **LinesCustomGridColumn1** and extend it from **CustomLinesGridColumnBase**.
    ```typescript
    export default class LinesCustomGridColumn1 extends CustomLinesGridColumnBase {}
    ```
9. Inside the class declare a private variable to capture the selected tender lines.
    ```typescript
    private _selectedTenderLines: ProxyEntities.TenderLine[ ];
    ```
10. Create a class constructor method to initialize the context.
    ```typescript
    constructor(context: ICustomLinesGridColumnContext) {
        super(context);
    }
    ```
11. Add the following methods for the columns title and alignment
    ```typescript
    public title(): string {
        return "Line number";
    } 

    public alignment(): CustomGridColumnAlignment {
        return CustomGridColumnAlignment.Right;
    }
    ```
12. Add the column compute value method, which returns the line number
    ```typescript
    public computeValue(cartLine: ProxyEntities.CartLine): string {
        return cartLine.LineNumber.toString();
    }
    ```
    The code for the entire class is:
    ```typescript
    import {
        ICustomLinesGridColumnContext,
        CustomLinesGridColumnBase
    } from "PosApi/Extend/Views/CartView";
    import { CustomGridColumnAlignment } from "PosApi/Extend/Views/CustomGridColumns";
    import { ProxyEntities } from "PosApi/Entities";

    export default class LinesCustomGridColumn1 extends CustomLinesGridColumnBase {
        constructor(context: ICustomLinesGridColumnContext) {
            super(context);
        }

        public title(): string {
            return "Line number";
        }

        public computeValue(cartLine: ProxyEntities.CartLine): string {
            return cartLine.LineNumber.toString();
        }

        public alignment(): CustomGridColumnAlignment {
            return CustomGridColumnAlignment.Right;
        }
    }
    ```
13. Create a new json file under the **CustomColumnExtensions** folder and name it **manifest.json**.
14. In the **manifest.json** file, replace the generated code with the following code:
    ```typescript
    {
        "$schema": "../manifestSchema.json",
            "name": "Pos_Extensibility_Samples",
                "publisher": "Microsoft",
                    "version": "7.2.0",
                        "minimumPosVersion": "7.2.0.0",
                            "components": {
            "extend": {
                "views": {
                    "CartView": {
                        "linesGrid": {
                            "customColumn1": { "modulePath": "Cart/LinesGrid/CustomColumn1Configuration" }
                        }
                    }
                }
            }
        }
    }
    ```
15. Open the **extensions.json** file under the **POS.Extensions** project and update it with the **CustomColumnExtensions** sample, so that POS during runtime will include this extension.
    ```typescript
    {
        "extensionPackages": [
            {
                "baseUrl": "SampleExtensions2"
            },
            {
                "baseUrl": "CustomColumnExtensions"
            }
        ]
    }
    ```
16. Open the **tsconfig.json** file and comment out the extension package folders from the exclude list. POS will use this file to include or exclude the extension. By default, the list contains all the excluded extensions list. If you want to include any extension part of the POS then you need add the extension folder name and comment the extension from the extension list as shown.
    ```typescript
    "exclude": [
        "AuditEventExtensionSample",
        "B2BSample",
        "CustomerSearchWithAttributesSample",
        "FiscalRegisterSample",
        "PaymentSample",
        "PromotionsSample",
        "SalesTransactionSignatureSample",
        //"SampleExtensions2",
        "SampleExtensions",
        "StoreHoursSample",
        "SuspendTransactionReceiptSample"
        //"CustomColumnExtensions"
    ],
    ```
17. Compile and rebuild the project.

## Validate the customization

1. Login to MPOS using **000160** as the operator id and **123** as the password.
2. Click the **Current transaction** button on the Welcome screen.
3. Add any item **(0005)** to the transaction.
4. The custom column should display the line number.


