---
title: Extend tax engine configurations for slab price
description: This article describes how to extend GST tax configurations to meet slab price function in India.
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

This article describes how to extend the Tax engine configuration for slab price. Before extending the tax engine, complete the following: [Prerequisites step](extend-tax-engine-configurations.md#prerequisites).

## Activate the tax configuration
### Create extension configurations
1. Create a new taxable document derived from a taxable document (India).
2. Go to the **Electronic reporting** workspace.
3. Click **Tax configurations**.
4. Navigate to the **Taxable Document (India)** configuration, and then click **Create configuration**.

   ![Create taxable document India configuration](../general-ledger/media/TaxableDocumentIndiaCreateConfiguration.png)
   
5. Select **Taxable document model derived from Name: Taxable Document (India), Microsoft** option, and then enter a name (i.e., **Taxable Document (India Contoso)**) and description for the derived taxable document.

   ![Derive configuration from taxable document India](../general-ledger/media/TaxableDocumentIndiaDeriveConfiguration.png)
   
6. Click **Create configuration** and create a new tax document that is derived from Tax (India GST).
7. Go to **Tax (India GST)** configuration, and click **Create configuration**.

   ![Create tax India GST configuration](../general-ledger/media/TaxIndiaGSTCreateConfiguration.png)
   
8. Select **Tax configuration derived from Name: Tax (India GST), Microsoft** option.
9. Enter a name (i.e., **Tax (India GST Contoso)**) and description for the derived tax document.
10. Click **Create configuration**.

    ![Derive configuration from tax India GST](../general-ledger/media/TaxIndiaGSTDeriveConfiguration.png)

### Add the net price to Taxable Document (India Contoso)
1. Go to **Taxable Document (India Contoso)** configuration, and click **Designer**.

   ![Open taxable document designer](../general-ledger/media/TaxableDocumentDesigner.png)
   
2. Navigate to **Tax document > Header > Lines**, and click **New** to create a new node.
3. Enter a name for the node, and select the item type:
   - **Name:** Net Price
   - **Item type:** Real

     ![Create new line field on tax configuration](../general-ledger/media/CreateNewLineFieldOnTaxConfiguration.png)
     
4. Open **Map model to datasource** to bind **Net Price** with data model.

   ![Open map model to data source](../general-ledger/media/OpenMapModelToDataSource.png)
   
5. Here takes sales order as an example, select **Sales order document type** and open **Designer**.

   ![Open sales order model designer](../general-ledger/media/OpenSalesOrderModelDesigner.png)
   
6. Expand the **DATA MODEL > Header = 'Sales order'.Header > Lines = 'Sales order'.Header.Lines**, find the **Net price** and click **Edit**.

   ![Open edit net price formula designer](../general-ledger/media/OpenEditNetPriceFormulaDesigner.png)
   
7. Click **Go to @**, and find the **Net Price**.

   ![Expand data source fields](../general-ledger/media/ExpandDataSourceFields.png)
   
8. Add **Net Price** formula.

   ![Add net price formula](../general-ledger/media/AddNetPriceFormula.png)

9. In the **Configurations** workspace, click **Change status**, and select **Complete**.

    ![Complete taxable document India configuration extension](../general-ledger/media/CompleteTaxableDocumentIndiaConfigurationExtension.png)
   
10. Enter a description such as **Slab price**, and click **OK**.
11. If there are any errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

### Change the data model of Tax (India GST Contoso)
1. Navigate to the **Tax (India GST Contoso)** configuration, and then click **Designer**.

   ![Open tax India GST designer](../general-ledger/media/TaxIndiaGSTDesigner.png)
   
2. Click **Tax document**, and then select **Taxable Document (India Contoso)** as the data model and **1** as the data model version.

   ![Change tax India GST data model](../general-ledger/media/ChangeTaxIndiaGSTDataModel.png)
   
3. Click **Save** to save the configuration.

### Modify rate/percentage lookups
1. Expand the **CGST** tax component node.
2. Select the measure of the **Rate**.
3. Go to **Lookups** tab, click **Columns** to add **Net Price** as condition of rate table.

   ![Add net price to tax setup condition](../general-ledger/media/AddNetPriceToTaxSetupCondition.png)
   
4. Select the same attributes that SGST uses.

> [!NOTE]
> Don't click **Add**. Values that you enter here have no effect on the actual rate table. The table should be completed at **Tax > Tax configuration > Tax setup**.

5. Save the tax document.

### Complete the tax document configuration
1. Save the configuration, and close the designer.
2. In the **Configurations** workspace, click **Change status**, and select **Complete**.

   ![Complete tax India GST configuration extension](../general-ledger/media/CompleteTaxIndiaGSTConfigurationExtension.png)
   
3. Enter a description such as **Slab price**, and click **OK**.
4.  If there are any errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

### Import the configuration and deploy it to a specific company
1. Go to **Tax > Setup > Tax configuration > Tax setup**.
2. Select the current working tax setup.
3. Click **Configurations**.

   ![Open configurations on tax setup](../general-ledger/media/OpenConfigurationsOnTaxSetup.png)
   
4. Click the **Tax configuration** tab > **Available configurations**, click **New** to create a tax configuration.

   ![Create new configuration on tax setup](../general-ledger/media/CreateNewConfigurationOnTaxSetup.png)

> [!NOTE]
> Any tax configurations that you add are listed in the **Available configurations** grid.

 5. Select the required configuration (for example, **Tax (India GST Contoso)** and version (for example, **1**)), and then click **Save** and **Synchronize**.

    ![Sync tax configuration](../general-ledger/media/SyncTaxConfiguration.png)

> [!NOTE]
> If you want to copy the tax setup data from original configuration, you can check the **Copy tax setup data from** button and choose the configuration you want to copy.

6. Click **Activate**.

   ![Activate tax configuration](../general-ledger/media/ActivateTaxConfiguration.png)
   
7. Back to **Tax setup** page and go to the **Companies** FastTab.
8. Click **New** and then select **INMF** in the **Companies** field.
9. Click **Save**.
10. Click **Activate** to activate the configuration for the company.

    ![Activate tax setup](../general-ledger/media/ActivateTaxSetup.png)
    
11. Click **Setup** to set up data for the new version.
12. Setup tax rate as per business requirement as below.

    ![Add net price condition to determine tax rate](../general-ledger/media/TaxRateNetPriceConditionSetup.png)
 
## Modify the data provider in Microsoft Dynamics AX
### Implement logic to determine Net Price
1. In the AOT, open Classes > TaxEngineModelFields. Add a new constant variable for Net Price.
   
   ```
   public static const str NetPrice = 'Net Price';
   ```


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
   
   ![Add net price field to data provider](../general-ledger/media/AddNetPriceFieldToDataProvider.png)

2. Add the Net Price to the method `TaxableDocumentRowDataProviderLine_IN_Extension.initValidFields()`.

   ```
   validFields.add(TaxEngineModelFields::NetPrice, Types::Real);
   ```



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
