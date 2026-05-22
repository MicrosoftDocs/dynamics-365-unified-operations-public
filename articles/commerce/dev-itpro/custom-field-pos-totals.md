---
title: Add custom fields to the point of sale (POS) Totals panel
description: Learn how to add a new custom field to the Totals panel on the POS transaction screen by using the screen layout designer in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/13/2026
ms.topic: how-to
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2018-05-31
ms.custom: 
  - bap-template
---

# Add custom fields to the point of sale (POS) Totals panel

[!include[banner](../includes/banner.md)]

This article explains how to add a new custom field to the **Totals** panel on the POS transaction screen by using the screen layout designer in Microsoft Dynamics 365 Commerce.

Custom fields that you add for the **Totals** panel on the **Custom fields** page appear in the designer. You can then select which custom fields go in the left and right columns. You should code the logic for the custom fields in the point of sale (POS) extensions.

## Scenario/business problem

You want to add a custom field to the **Totals** panel on the POS transaction screen by using the screen layout designer. You also want to code the business logic for the custom field in the POS extensions.

## Overview of the required steps

First, complete these steps to configure headquarters.

1. On the **Language text** page, add the language text for the custom field.
1. On the **Custom fields** page, add the new custom field.
1. In the screen layout designer, add the new custom field to the **Totals** panel.
1. Run the **Registers** (**1090**) job.

Then, complete this step in the POS extension project.

- Add the business logic for the custom field.

## Configure headquarters

1. Sign in to Commerce.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Language text**.
1. On the **POS** tab, select **Add** to add a new POS language text.

    You can localize the text that appears in the **Totals** panel. Create multiple texts in different languages for the same text ID. Here's an example.

    | Language ID | Text ID | Text   |
    |-------------|---------|--------|
    | en-US       | 1       | Sample |
    | en-UK       | 1       | Demo   |

1. On the Action Pane, select **Save** to save your changes.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Custom fields**.
1. On the Action Pane, select **New** to add a new custom field, and specify the following information: 

    1. In the **Name** field, enter the name of the custom field.
    1. In the **Type** field, select **Totals area**.
    1. In the **Caption text ID** field, specify the text ID that you used in step 3.

    Here's an example.

    | Name   | Type        | Caption text ID |
    |--------|-------------|-----------------|
    | Sample | Totals area | 1               |


1. On the Action Pane, select **Save** to save your changes.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Screen layouts**.
1. Select the **F3MGR** screen layout ID, and then, on the Action Pane, select **Designer**.

    > [!NOTE]
    > You can select any existing layout or create a new layout. The **F3MGR** screen layout ID is available only if you're using demo data.

1. Select the **1440x960 – Full** layout size, and then select **Layout designer**.
1. If you're prompted to confirm that you want to open the application, select **Open**, and then follow the installation instructions.
1. After the designer is installed, you're asked for Microsoft Entra credentials. Enter the information to start the designer.
1. In the designer, drag the **Totals panel** control from the left pane to the screen layout. If the layout already includes a **Totals** panel, the control appears dimmed in the left pane.
1. In the screen layout, right-click the **Totals panel**, and then select **Customize**.
1. In the **Customization - Totals panel** dialog box, the **SAMPLE** custom field should appear in the **Available fields** list. Move it to either the left column or the right column by using the arrow buttons.
1. To move the custom field up or down, use the **Up** and **Down** buttons.
1. Select **OK** to save your changes and close the **Customization - Totals panel** dialog box.
1. Select the **Close** button (**X**) in the upper-right corner to close the designer.
1. When you're prompted to save your changes, select **Yes**. If you select **No**, your changes aren't saved.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Select the **Registers** (**1090**) job, and then select **Run now**.

## Add business logic to the custom field

You can find similar sample code in the Retail software development kit (SDK), at `...\RetailSDK\POS\Extensions\SampleExtensions\ViewExtensions\Cart\TipsCustomField.ts`.

1. Start Microsoft Visual Studio 2015 in administrator mode.
1. Open the **ModernPOS** solution from `...\RetailSDK\POS`.
1. Under the **POS.Extensions** project, create a folder named **CustomFieldExtensions**.
1. Under the **CustomFieldExtensions** folder, create a folder named **Cart**.
1. In the **Cart** folder, create a .ts (TypeScript) file named **SampleCustomField.ts**.
1. In the **SampleCustomField.ts** file, add the following **import** statement to import the relevant entities and context.

    ```typescript
    import { CartViewTotalsPanelCustomFieldBase } from "PosApi/Extend/Views/CartView";
    import { ProxyEntities } from "PosApi/Entities";
    ```

1. Create a class named **SampleCustomField**, and extend it from the **CartViewTotalsPanelCustomFieldBase** class. By using this base class, the **computeValue** method can include any custom logic for the custom field.

    ```typescript
    export default class SampleCustomField extends CartViewTotalsPanelCustomFieldBase {

    }
    ```

1. Inside the **SampleCustomField** class, implement the abstract **computeValue** method to set the logic for the custom field.

    ```typescript
    public computeValue(cart: ProxyEntities.Cart): string {

        // Let's show 10% of total amount in the custom field.

        if (isNaN(cart.TotalAmount) || cart.TotalAmount <= 0) {
            return "$0.00";
        }
        return "$" + (cart.TotalAmount * 0.1).toFixed(2).toString();
    }
    ```

    The overall class should look like this.

    ```typescript
    import { CartViewTotalsPanelCustomFieldBase } from "PosApi/Extend/Views/CartView";
    import { ProxyEntities } from "PosApi/Entities";

    export default class SampleCustomField extends CartViewTotalsPanelCustomFieldBase {
        public computeValue(cart: ProxyEntities.Cart): string {

            // Let's show 10% of total amount in the custom field.
            if (isNaN(cart.TotalAmount) || cart.TotalAmount <= 0) {
                return "$0.00";
            }
            return "$" + (cart.TotalAmount * 0.1).toFixed(2).toString();
        }
    }
    ```

1. In the **CustomFieldExtensions** folder, create a .json file named **manifest.json**.
1. In the **manifest.json** file, paste the following code.

    ```typescript
    {
        "$schema": "../manifestSchema.json",
        "name": "Pos_Extensibility_Samples",
        "publisher": "Contoso",
        "version": "7.3.0",
        "minimumPosVersion": "7.3.0.0",
        "components": {
            "extend": {
                "views": {
                    "CartView": {
                        "totalsPanel": {
                            "customFields": [
                                {
                                    "fieldName": "Sample",
                                    "modulePath": "Cart/SampleCustomField"
                                }
                            ]
                    } }
            }  }
    } }
    ```

    In the manifest, the **fieldName** value in the **customFields** section should match the name of the custom field added in headquarters, the name you specified for the custom field in step 6 of the "Configure headquarters" procedure. The **modulePath** value is the name of the implementation file.
    
    If you add multiple custom fields, add multiple implementation files and update the information under the **customFields** section.

    For example, if you add two custom fields, **Sample1** and **Sample2**, you should have two implementation files that extend from the same base class, **CartViewTotalsPanelCustomFieldBase**.

    In this case, the manifest should look like this.

    ```typescript
    "customFields": [
        {
            "fieldName": "Sample1",
            "modulePath": "Cart/SampleCustomField1"
        },
        {
            "fieldName": "Sample2",
            "modulePath": "Cart/SampleCustomField2"
        }
    ]
    ```
    
    In this example, **SampleCustomField1** and **SampleCustomField2** are the names of the TypeScript files where you implement the business logic.

1. Open the **extensions.json** file under the **POS.Extensions** project, and update it with the **CustomFieldExtensions** samples, so that POS loads this extension at runtime.

    ```typescript
    {
        "extensionPackages": [
            { 
                "baseUrl": "SampleExtensions2" 
            }, 
            {
                "baseUrl": "CustomFieldExtensions"
            }
        ]
    }
    ```

1. Open the **tsconfig.json** file, and add the extension folder name **CustomFieldExtensions** and comment out the extension folder in the **exclude** list. POS uses this file to include or exclude the extension. By default, the **exclude** list contains all the excluded extensions. To include an extension as part of the POS, add the extension folder name and comment out the extension in the **extension** list, as shown here.

    ```typescript
    "exclude": [
        "SampleExtensions",
        //"SampleExtensions2",
        //"CustomFieldExtensions"
    ],
    ```

1. Compile and rebuild the project.
1. Deploy the customized version of Retail Modern POS (MPOS) by selecting the **Local Machine** button. Make sure that the solution platform is x81. Alternatively, you can create a deployable package and install MPOS from it.

    > [!NOTE]
    > Although this article uses MPOS, you can use either MPOS or Cloud POS.

## Validate the customization

1. Sign in to MPOS by using **000160** as the operator ID and **123** as the password.
1. On the welcome screen, select the **Current transaction** button.
1. Add any item to the transaction.

The custom field appears in the **Totals** panel.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
