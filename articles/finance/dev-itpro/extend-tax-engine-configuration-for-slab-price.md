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

This article describes how to extend the Tax engine configuration for slab price. Before extending the tax engine, complete the [Prerequisites](extend-tax-engine-configurations.md#prerequisites).

## Create extension configurations

To create extension configurations, first create a new taxable document derived from a taxable document (India).
1. Go to the **Electronic reporting** workspace, click **Tax configurations**.
2. Go to **Taxable Document (India)** configuration, and click **Create configuration**.
3. Select **Taxable document model derived from Name: Taxable Document (India), Microsoft** option. Enter a name and description for the derived taxable document.
4. Click **Create configuration** to create a new tax document that is derived from Tax (India GST).
5. Go to **Tax (India GST)** configuration, click **Create configuration**.
6. Select **Tax configuration derived from name: Tax (India GST), Microsoft** option.
7. Enter a name and description for the derived tax document.
8. Click **Create configuration**.


### Add the net price to Taxable Document (India Contoso)
1. Go to **Taxable document (India Contoso)** configuration, click **Designer**.
2. Navigate to **Tax document > Header > Lines**, and click **New** to create a new node.
3. Enter a name for the node, and select the item type:
   - **Name** - Net Price
   - **Item type** - Real
4. Open **Map model to datasource** to bind **Net Price** with the data model.
5. Select a document type. For example, select **Sales order**, open **Designer**.
6. Expand **DATA MODEL**.
 - Header = 'Sales order'.Header
 - Lines = 'Sales order'.Header.Lines
7. In the **Net price**, click **Edit**.
8. Click **Go to @**, find the **Net Price**, add **Net Price** formula.
9. In the **Configurations** workspace, click **Change status**, and select **Complete**.
10. Enter a description such as **Slab price**, and click **OK**.
11. If there are any errors, open the designer, click **Validate**, and fix the errors.

When the status is **Complete**, the configuration is ready for deployment.

### Change the data model of Tax (India GST Contoso)
1. Go to the **Tax (India GST Contoso)** configuration, and click **Designer**.
2. Click **Tax document**, select **Taxable document (India Contoso)** as the data model and **1** as the data model version.
3. Click **Save** to save the configuration.

### Modify rate/percentage lookups
1. Expand the **CGST** component node.
2. Select the measure of the **Rate**.
3. Go to **Lookups**, click **Columns** to add **Net Price** as condition of rate table.
4. Select the same attributes as SGST.

> [!NOTE]
> Don't click **Add**. Values entered here don't affect the actual rate table. To complete the rate table, go to **Tax > Tax configuration > Tax setup**.

5. Save the tax document.

### Complete the tax document configuration
1. In the **Configurations** workspace, click **Change status**, and select **Complete**.
2. Enter a description, click **OK**.
3. If there are errors, open the designer, click **Validate**, and fix the errors.

After the status is updated to **Complete**, the configuration is ready for deployment.

### Import the configuration and deploy it to a specific company
1. Go to **Tax > Setup > Tax configuration > Tax setup**.
2. Select the current working tax setup.
3. Click **Configurations**.
4. Click **Tax configuration** > **Available configurations**, click **New** to create a tax configuration.

> [!NOTE]
> Any tax configurations added are listed in the **Available configurations** grid.

 5. Select the required configuration. For example, Tax (India GST Contoso) and version, 1.
 6. Click **Save** and **Synchronize**.

> [!NOTE]
> If you want to copy the tax setup data from the original configuration, click **Copy tax setup data from** and select the configuration to copy.

7. Click **Activate**.
8. On the **Tax setup** page, go to **Companies**, click **New**.
9. In the **Companies** field, select **INMF**. 
10. Click **Save**.
11. To activate the configuration for the company, click **Activate**. 
12. To set up data for the new version, click **Setup**.

 
## Modify the data provider in Microsoft Dynamics 365 Finance
### Implement logic to determine net price
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


2. Add the Net Price to the method `TaxableDocumentRowDataProviderLine_IN_Extension.initValidFields()`.

   ```
   validFields.add(TaxEngineModelFields::NetPrice, Types::Real);
   ```



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
