---
title: Add custom columns to a point of sale (POS) transaction grid
description: Learn how to add a new custom column to a POS transaction page using the screen layout designer in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/18/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: anvenkat
ms.search.validFrom: 2017-01-27
ms.custom: 
  - bap-template
---

# Add custom columns to a point of sale (POS) transaction grid

[!include [banner](../../includes/banner.md)]

This article explains how to add a new custom column to a POS transaction page by using the screen layout designer in Microsoft Dynamics 365 Commerce.

Use the custom column feature to add more information to a transaction page. Add a custom column to the transaction page receipt grid by using the screen layout designer. Adjust the width and position of the columns by using the designer. The layout includes 10 custom columns for extension scenarios, and you can use all 10 in one layout. The designer metadata already includes the custom columns. After you add the column to the layout, run the distribution job so that the column shows up on the transaction page.

> [!NOTE]
> This article applies to Dynamics 365 Finance, and to Microsoft Dynamics 365 Retail with platform update 8 and Retail App update 4 hotfix.

## Add a custom column to the page

To add a custom column to the page, follow these steps:

1. Sign in to Dynamics 365 Commerce.
1. Go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **Screen layouts**. Or, search for **Screen layout** in the search bar.
1. Select the **F3MGR** screen layout ID and select the **Designer** button in the action bar.
1. Follow the instructions if prompted to install and enter the Microsoft Entra (Microsoft Entra ID) credentials to launch the designer.
1. Select **1440x960 – Full layout** from the layout sizes and select the **Layout designer** button.
1. If prompted, select **Open** and follow the instruction to install the designer tool.
1. After installing, enter your Microsoft Entra credentials to launch the designer.
1. In the designer, right-click the transaction grid (receipt grid) and select **Customize**.
1. In the **Customization – Receipt** window, select the **lines** in the pivot panel drop-down menu.

   > [!NOTE]
   > Similarly, you can add a custom column to the **Payment and Delivery** tab.

1. In the **Available columns** window, select **Custom column 1**, and then select the **> (arrow)** button to move the column to the **Selected** columns.
1. Select **OK** to save and close the window.
1. Adjust the column width in the transaction grid using the **Screen layout** designer. Make sure the column is visible.
1. Select the **X** button in the designer to close the designer.
1. When prompted to **Save changes**, select **Yes**. If you select **No** the changes aren't saved.
1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**.
1. Select the **Registers (1090)** job and select **Run now**.

## Add business logic to a custom column

To add business logic to a custom column, follow these steps:

1. Open Visual Studio 2015 in administrator mode.
1. Open the **ModernPOS** solution from **…\\RetailSDK\\POS**.
1. Under the **POS.Extensions** project, create a new folder named **CustomColumnExtensions**.
1. Under **CustomColumnExtensions**, create a new folder named **Cart**.
1. Under **Cart**, create a new folder named **LinesGrid**.
1. In the **LinesGrid** folder, add a new TypeScript file and name it **CustomColumn1Configuration.ts**.
1. Add the following **import** statements to import the relevant entities and context.

    ```typescript
    import {

        ICustomLinesGridColumnContext,
        CustomLinesGridColumnBase

    } from "PosApi/Extend/Views/CartView";

    import { CustomGridColumnAlignment } from "PosApi/Extend/Views/CustomGridColumns";
    import { ProxyEntities } from "PosApi/Entities";
    ```
1. Create a new class named **LinesCustomGridColumn1** and extend it from **CustomLinesGridColumnBase**.

    ```typescript
    export default class LinesCustomGridColumn1 extends CustomLinesGridColumnBase {}
    ```
1. Inside the class, declare a private variable to capture the selected tender lines.

    ```typescript
    private _selectedTenderLines: ProxyEntities.TenderLine[ ];
    ```
1. Create a class constructor method to initialize the context.

    ```typescript
    constructor(context: ICustomLinesGridColumnContext) {
        super(context);
    }
    ```
1. Add the following methods for the column's title and alignment.

    ```typescript
    public title(): string {
        return "Line number";
    } 

    public alignment(): CustomGridColumnAlignment {
        return CustomGridColumnAlignment.Right;
    }
    ```
1. Add the column compute value method, which returns the line number.
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

1. Create a new .json file under the **CustomColumnExtensions** folder and name it **manifest.json**.
1. In the **manifest.json** file, replace the generated code with the following code.

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
    
    > [!NOTE]
    > If you are adding a custom column to payment or delivery grid, you need to update the manifest with the following code.
    "paymentsGrid": {
        "customColumn1": { "modulePath": "Cart/PaymentsGrid/CustomColumn1Configuration" }
     },
     "deliveryGrid": {
         "customColumn1": { "modulePath": "Cart/DeliveryGrid/CustomColumn1Configuration" }
     }
    ```
    
    
1. Open the **extensions.json** file under the **POS.Extensions** project and update it with the **CustomColumnExtensions** sample, so that POS during runtime includes this extension.

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
1. Open the **tsconfig.json** file and comment out the extension package folders from the exclude list. POS uses this file to include or exclude the extension. By default, the list contains all the excluded extensions. If you want to include any extension part of the POS, add the extension folder name and comment the extension from the extension list as shown.

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
1. Compile and rebuild the project.

> [!NOTE]
>  You can find the sample for the custom column in the [Retail software development kit (SDK) architecture](./retail-sdk/retail-sdk-overview.md).

## Validate the customization

To validate the customization, follow these steps:

1. Sign in to the Store Commerce app by using **000160** as the operator ID and **123** as the password.
1. Select the **Current transaction** button on the **Welcome** screen.
1. Add item **(0005)** to the transaction.
1. Check that the custom column displays the line number.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
