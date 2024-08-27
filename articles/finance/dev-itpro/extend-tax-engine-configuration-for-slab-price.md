---
title: Extend tax engine configurations for slab price
description: Learn about how to extend GST tax configurations to meet slab price function in India.
author: prabhatb
ms.author: yungu
ms.topic: article
ms.date: 08/27/2024
ms.reviewer: twheeloc
audience: IT Pro 
ms.search.region: India
ms.search.validFrom: 2024-8-28
ms.search.form: ERSolutionTable, ERDataModelDesigner, ERModelMappingTable
ms.dyn365.ops.version: 7.3
---

# Extend tax engine configurations for slab price
[!include [banner](../includes/banner.md)]

Follow this guide to set up the Tax engine configuration extension for slab price, with steps tailored for India. Ensure that you've completed the [Prerequisites step](extend-tax-engine-configurations.md#prerequisites) before beginning.

## Activate the tax configuration
### Create extension configurations
1. Create a new taxable document that is derived from Taxable Document (India).
   - Open the **Electronic reporting** workspace.
   - Click **Tax configurations**.
   - Navigate to the **Taxable Document (India)** configuration, and then click **Create configuration**.

     ![TaxableDocumentIndiaCreateConfiguration](https://github.com/user-attachments/assets/fe48b1e4-ab92-4d14-b97a-62e2ea1f29d4)

   - Select the **Taxable document model derived from Name: Taxable Document (India), Microsoft** option, and then enter a name and description for the derived taxable document. Then click **Create configuration**.

      ![TaxableDocumentIndiaDeriveConfiguration](https://github.com/user-attachments/assets/c4502caf-ef7b-4367-966d-aaa551ded440)

2. Create a new tax document that is derived from Tax (India GST).
   - Navigate to the **Tax (India GST)** configuration, and then click **Create configuration**.

     ![TaxIndiaGSTCreateConfiguration](https://github.com/user-attachments/assets/5e8582af-4f50-4ef2-b7cd-14fa468f7d0d)

   - Select the **Tax configuration derived from Name: Tax (India GST), Microsoft** option, and then enter a name and description for the derived tax document. Then click **Create configuration**.

     ![TaxIndiaGSTDeriveConfiguration](https://github.com/user-attachments/assets/e86c1c76-91c6-437b-9a28-49723d514211)


### Add the Net price to Taxable Document India (India Contoso)
1. Navigate to the **Taxable Document (India Contoso)** configuration, and then click **Designer**.

   ![TaxableDocumentDesigner](https://github.com/user-attachments/assets/e48885da-471f-47b6-a4a6-61a887273507)

2. Navigate to **Tax document > Header > Lines**, and then click **New** to create a new node.
3. Enter a name for the node, and select the item type:
   - **Name:** Net Price
   - **Item type:** Real

      ![CreateNewLineFieldOnTaxConfiguration](https://github.com/user-attachments/assets/936738ed-3ab7-408e-9af5-e8d570ef3a72)
   
4. Open **Map model to datasource** to bind **Net Price** with data model.

   ![OpenMapModelToDataSource](https://github.com/user-attachments/assets/1af1b90f-7b1f-41c9-a0df-ec44eae0750f)

5. Here takes sales order as an example, select **Sales order document type** and open **Designer**.

   ![OpenSalesOrderModelDesigner](https://github.com/user-attachments/assets/7fa09507-d30b-4213-8ee2-81896aed3ac1)
  
6. Expand the **DATA MODEL > Header = 'Sales order'.Header > Lines = 'Sales order'.Header.Lines**, find the **Net Price** and click **Edit**.

   ![OpenEditNetPriceFormulaDesigner](https://github.com/user-attachments/assets/1e8b7e63-5097-46d9-96ef-c9dbff574e9f)

7. Click **Go to @**, then find the **Net Price**.

   ![ExpandDataSourceFields](https://github.com/user-attachments/assets/1ae5d730-5469-4fc5-aaef-43a174d54fe9)

8. Add **Net Price** formula.

   ![AddNetPriceFormula](https://github.com/user-attachments/assets/1ed23538-c72e-427a-887e-68063b45cc72)

9. In the **Configurations** workspace, click **Change status**, and then select **Complete**.

   ![CompleteTaxableDocumentIndiaConfigurationExtension](https://github.com/user-attachments/assets/f080fc26-e3ca-41a6-b84c-254f6483f204)

10. Enter a description such as **Slab price**, and then click **OK**.
11. If there are any errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

### Change the data model of Tax (India GST Contoso)
1. Navigate to the **Tax (India GST Contoso)** configuration, and then click **Designer**.

   ![TaxIndiaGSTDesigner](https://github.com/user-attachments/assets/ec034adf-519c-4b74-830c-79734a39cba9)

2. Click **Tax document**, and then select **Taxable Document (India Contoso)** as the data model and **1** as the data 
model version.

   ![ChangeTaxIndiaGSTDataModel](https://github.com/user-attachments/assets/3569209c-51aa-4552-bcaa-8a3683c581e5)

3. Click **Save** to save the configuration.

### Modify rate/percentage lookups
1. Expand the **CGST** tax component node.
2. Select the measure of the **Rate**.
3. Go to **Lookups** tab, click **Columns** to add **Net Price** as condition of rate table.

   ![AddNetPriceToTaxSetupCondition](https://github.com/user-attachments/assets/d7c948c9-c18b-498d-943a-fb80988da5c2)

4. Select the same attributes that SGST uses.

> [!NOTE]
> Don't click **Add**. Values that you enter here have no effect on the actual rate table. That table should be 
completed at **Tax > Tax configuration > Tax setup**.

5. Save the tax document.

### Complete the tax document configuration
1. Save the configuration, and close the designer.
2. In the **Configurations** workspace, click **Change status**, and then select **Complete**.

   ![CompleteTaxIndiaGSTConfigurationExtension](https://github.com/user-attachments/assets/17038a35-a285-40c6-9b9e-9c1969caf83f)

3. Enter a description such as **Slab price**, and then click **OK**.
4.  If there are any errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

## Import the configuration and deploy it to a specific company
1. Go to **Tax > Setup > Tax configuration > Tax setup**.
2. Select the current working tax setup.
3. Click **Configurations**.

   ![OpenConfigurationsOnTaxSetup](https://github.com/user-attachments/assets/dad2c233-809b-4345-b40a-01bee01761da)

4. Click the **Tax configuration** tab, and then, under **Available configurations**, click **New** to create a tax 
configuration.

> [!NOTE]
> Any tax configurations that you add are listed in the **Available configurations** grid.

   ![CreateNewConfigurationOnTaxSetup](https://github.com/user-attachments/assets/91c76aaa-8320-405c-a61e-d79ca59d833b)


5. Select the required configuration (for example, **Tax (India GST Contoso)** and version (for example, **1**)), and then click **Save** and **Synchronize**.

    ![SyncTaxConfiguration](https://github.com/user-attachments/assets/24dbe180-abdd-4a58-8fe8-39cdbf2bbe9b)

> [!NOTE]
> If you want to copy the tax setup data from original configuration, you can check the **Copy tax setup data from** button and choose the configuration you want to copy.

6. Click **Activate**.

   ![ActivateTaxConfiguration](https://github.com/user-attachments/assets/d2b2e930-3ec1-4d6f-959f-be6f7945bb95)

7. Back to **Tax setup** form and go to the **Companies** FastTab.
8. Click **New** and then select **INMF** in the Companies field.
9. Click **Save**.
10. Click **Activate** to activate the configuration for the company.

    ![ActivateTaxSetup](https://github.com/user-attachments/assets/02bbaf05-b845-4acb-a79c-21a8ee4027df)

11. Click **Setup** to set up data for the new version.
12. Setup tax rate as per business requirement as below.

    ![TaxRateNetPriceConditionSetup](https://github.com/user-attachments/assets/9e898523-680f-4c14-8f17-91a8b4dca877)

## Modify the data provider in Microsoft Dynamics AX
### Implement logic to determine Net Price
1. In the AOT, open Classes > TaxEngineModelFields. Add a new const variable for Net Price.
   
   ```
   public static const str NetPrice = 'Net Price';
   ```

   ![AddNetPriceConstVariable](https://github.com/user-attachments/assets/9eb7a4fc-b10a-42ed-bdf8-4ade18f1cb0d)

2. Add a new method for the **TaxModelDocLineBaseImpl_IN** class, and implement the determination logic in the method.
   
   ```
    public Amount getNetPrice()
    {
        if (this.getQuantity())
        {
            return this.getLineAmount() / this.getQuantity();
        }
        else
        {
            return this.getLineAmount();
        }

    }
   ```

### Pass the Net Price to GTE
1. Pass the Net Price to GTE in `TaxableDocumentRowDataProviderLine_IN_Extension.fillInFields()`.
   
   ```
   this.addFieldValue(_lineObj, TaxEngineModelFields::NetPrice, taxModelDocLineBaseImpl.getNetPrice());
   ```

   ![AddNetPriceFieldToDataProvider](https://github.com/user-attachments/assets/c731c2dd-7ebd-49a6-a217-fee5de365dfe)

2. Add the Net Price to the method `TaxableDocumentRowDataProviderLine_IN_Extension.initValidFields()`.

   ```
   validFields.add(TaxEngineModelFields::NetPrice, Types::Real);
   ```

   ![AddValidNetPriceFieldAX](https://github.com/user-attachments/assets/0c3e03b2-ab33-4bf7-9304-64383dc5a4b9)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
