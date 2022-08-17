---
title: Add custom fields to the point of sale (POS) Totals panel
description: This article explains how to add a new custom field to the Totals panel on the POS transaction screen by using the screen layout designer.
author: josaw1
ms.date: 05/23/2018
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2018-05-31
ms.dyn365.ops.version: 8.0.1
---

# Add custom fields to the point of sale (POS) Totals panel

[!include[banner](../includes/banner.md)]

This article explains how to add a new custom field to the **Totals** panel on the POS transaction screen by using the screen layout designer. This article is applicable to Microsoft Dynamics 365 Finance 7.3 and later, and to Microsoft Dynamics 365 Retail 7.3 and later.

Custom fields that you add for the **Totals** panel on the **Custom fields** page will appear in the designer. You can then select which custom fields should be in the left and right columns. The logic for the custom fields should be coded in the point of sale (POS) extensions.

## Scenario/business problem

<span id="_Toc446093285" class="anchor"></span>You will add a custom field to the **Totals** panel on the POS transaction screen by using the screen layout designer. You will also code the business logic for the custom field in the POS extensions.

## Overview of the required steps

First, you must complete these steps to configure Headquarters.

1. On the **Language text** page, add the language text for the custom field.
2. On the **Custom fields** page, add the new custom field.
3. In the screen layout designer, add the new custom field to the **Totals** panel.
4. Run the **Registers** (**1090**) job.

You must then complete this step in the POS extension project.

- Add the business logic for the custom field.

## Configure Headquarters

1. Sign in to Commerce.
2. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Language text**.
3. On the **POS** tab, select **Add** to add a new POS language text.

    The text that appears in the **Totals** panel can be localized. Therefore, you can create multiple texts in different languages for the same text ID. Here is an example.

    | Language ID | Text ID | Text   |
    |-------------|---------|--------|
    | en-US       | 1       | Sample |
    | en-UK       | 1       | Demo   |

4. On the Action Pane, select **Save** to save your changes.
5. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Custom fields**.
6. On the Action Pane, select **New** to add a new custom field, and specify the following information: 

    1. In the **Name** field, enter the name of the custom field.
    2. In the **Type** field, select **Totals area**.
    3. In the **Caption text ID** field, specify the text ID that you used in step 3.

    Here is an example.

    | Name   | Type        | Caption text ID |
    |--------|-------------|-----------------|
    | Sample | Totals area | 1               |


7. On the Action Pane, select **Save** to save your changes.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Screen layouts**.
9. Select the **F3MGR** screen layout ID, and then, on the Action Pane, select **Designer**.

    > [!NOTE]
    > You can select any existing layout or create a new layout. The **F3MGR** screen layout ID is available only if you're using demo data.

10. Select the **1440x960 – Full** layout size, and then select **Layout designer**.
11. If you're prompted to confirm that you want to open the application, select **Open**, and then follow the installation instructions.
12. After the designer is installed, you're asked for Azure Active Directory (Azure AD) credentials. Enter the information to start the designer.
13. In the designer, drag the **Totals panel** control from the left pane to the screen layout. If the layout already includes a **Totals** panel, the control appears dimmed in the left pane.
14. In the screen layout, right-click the **Totals panel**, and then select **Customize**.
15. In the **Customization - Totals panel** dialog box, the **SAMPLE** custom field should appear in the **Available fields** list. Move it to either the left column or the right column by using the arrow buttons.
16. To move the custom field up or down, use the **Up** and **Down** buttons.
17. Select **OK** to save your changes and close the **Customization - Totals panel** dialog box.
18. Select the **Close** button (**X**) in the upper-right corner to close the designer.
19. When you're prompted to save your changes, select **Yes**. If you select **No**, your changes aren't saved.
20. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
21. Select the **Registers** (**1090**) job, and then select **Run now**.

## Add business logic to the custom field

You can find similar sample code in the Retail software development kit (SDK), at …\\RetailSDK\\POS\\Extensions\\SampleExtensions\\ViewExtensions\\Cart\\TipsCustomField.ts.

1. Start Microsoft Visual Studio 2015 in administrator mode.
2. Open the **ModernPOS** solution from **…\\RetailSDK\\POS**.
3. Under the **POS.Extensions** project, create a folder that is named **CustomFieldExtensions**.
4. Under the **CustomFieldExtensions** folder, create a folder that is named **Cart**.
5. In the **Cart** folder, create a .ts (typescript) file that is named **SampleCustomField.ts**.
6. In the **SampleCustomField.ts** file, add the following **import** statement to import the relevant entities and context.

    ```typescript
    import { CartViewTotalsPanelCustomFieldBase } from "PosApi/Extend/Views/CartView";
    import { ProxyEntities } from "PosApi/Entities";
    ```

7. Create a class that is named **SampleCustomField**, and extend it from the **CartViewTotalsPanelCustomFieldBase** class. In this way, the **computeValue** method from the base class will do any custom logic for the custom field.

    ```typescript
    export default class SampleCustomField extends CartViewTotalsPanelCustomFieldBase {

    }
    ```

8. Inside the **SampleCustomField** class, implement the abstract **computeValue** method to set the logic for the custom field.

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

9. In the **CustomFieldExtensions** folder, create a .json file that is named **manifest.json**.
10. In the **manifest.json** file, paste the below code.

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

    In the manifest, note that the **fieldName** value in the **customFields** section should match the name of the custom field added in the Headquarters, the name you specified for the custom field in step 6 of the "Configure Headquarters" procedure. **modulePath** is the name of the implementation file, the implementation file name is the name of the file that you created in step 5 of "Add business logic to the custom field" procedure.
    
    If you add multiple custom fields, you should add multiple implementation files and update the information under the custonFileds section.

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
    
    In this example, **SampleCustomField1** and **SampleCustomField2** are the names of the typescript files where you will do the business logic.

11. Open the **extensions.json** file under the **POS.Extensions** project, and update it with the **CustomFieldExtensions** samples, so that POS will load this extension at runtime.

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

12. Open the **tsconfig.json** file, and add the extension folder name **CustomFieldExtensions** and comment out the extension folder in the **exclude** list. POS will use this file to include or exclude the extension. By default, the **exclude** list contains all the excluded extensions. To include an extension as part of the POS, you must add the extension folder name and comment out the extension in the **extension** list, as shown here.

    ```typescript
    "exclude": [
        "SampleExtensions",
        //"SampleExtensions2",
        //"CustomFieldExtensions"
    ],
    ```

13. Compile and rebuild the project.
14. Deploy the customized version of Retail Modern POS (MPOS) by selecting the **Local Machine** button. Make sure that the solution platform is x86. Alternatively, you can create a deployable package and install MPOS from it.

    > [!NOTE]
    > Although MPOS is used in this article, you can use either MPOS or Cloud POS.

## Validate the customization

1. Sign in to MPOS by using **000160** as the operator ID and **123** as the password.
2. On the welcome screen, select the **Current transaction** button.
3. Add any item to the transaction.

The custom field should appear in the **Totals** panel.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
