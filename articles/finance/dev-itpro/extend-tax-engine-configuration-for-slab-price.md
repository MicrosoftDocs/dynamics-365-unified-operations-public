---
title: Extend Tax engine configurations for slab price
description: This article explains how to extend Goods and Services Tax (GST) tax configurations to add the slab price function in India.
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

# Extend Tax engine configurations for slab price

[!include [banner](../includes/banner.md)]

This article explains how to extend the Tax engine configuration for slab price. Before you extend the Tax engine (also referred to as GTE), you must complete the [prerequisites](extend-tax-engine-configurations.md#prerequisites).

## Create extension configurations

To create extension configurations, first create a new taxable document that is derived from Taxable Document (India).

1. Go to the **Electronic reporting** workspace, and select **Tax configurations**.
2. Go to the **Taxable Document (India)** configuration, and select **Create configuration**.
3. Select the **Taxable document model derived from Name: Taxable Document (India), Microsoft** option. Then enter a name and description for the derived taxable document.
4. Select **Create configuration** to create a new tax document that is derived from Tax (India GST).
5. Go to the **Tax (India GST)** configuration, and select **Create configuration**.
6. Select the **Tax configuration derived from name: Tax (India GST), Microsoft** option. Then enter a name and description for the derived tax document.
7. Select **Create configuration**.

### Add the net price to Taxable document (India Contoso)

1. Go to the **Taxable document (India Contoso)** configuration, and select **Designer**.
2. Go to **Tax document** \> **Header** \> **Lines**, and select **New** to create a node.
3. Enter a name for the node, and select the item type:

    - **Name:** Net Price
    - **Item type:** Real

4. Open **Map model to datasource** to bind **Net Price** to the data model.
5. Select a document type, such as **Sales order**, and open the designer.
6. Expand **Data model**.

    - Header = 'Sales order'.Header
    - Lines = 'Sales order'.Header.Lines

7. In **Net price**, select **Edit**.
8. Select **Go to @**, find **Net Price**, and add the **Net Price** formula.
9. In the **Configurations** workspace, select **Change status**, and then select **Complete**.
10. Enter a description, such as **Slab price**, and then select **OK**.
11. If there are any errors, open the designer, select **Validate**, and fix the errors.

When the status is **Complete**, the configuration is ready for deployment.

### Change the data model of Tax (India GST Contoso)

1. Go to the **Tax (India GST Contoso)** configuration, and select **Designer**.
2. Select **Tax document**, select **Taxable document (India Contoso)** as the data model, and specify **1** as the data model version.
3. Select **Save** to save the configuration.

### Modify rate/percentage lookups

1. Expand the **CGST** component node.
2. Select the **Rate** measure.
3. Go to **Lookups**, and select **Columns** to add **Net Price** as a condition of the rate table.
4. Select the same attributes that SGST has.

    > [!NOTE]
    > Don't select **Add**. Values that you enter here don't affect the actual rate table. To complete the rate table, go to **Tax** \> **Tax configuration** \> **Tax setup**.

5. Save the tax document.

### Complete the tax document configuration

1. In the **Configurations** workspace, select **Change status**, and then select **Complete**.
2. Enter a description, and then select **OK**.
3. If there are any errors, open the designer, select **Validate**, and fix the errors.

After the status is **Complete**, the configuration is ready for deployment.

### Import the configuration and deploy it to a specific company

1. Go to **Tax** \> **Setup** \> **Tax configuration** \> **Tax setup**.
2. Select the current working tax setup.
3. Select **Configurations**.
4. Select **Tax configuration** \> **Available configurations**, and then select **New** to create a tax configuration.

    > [!NOTE]
    > Any tax configurations that you add are listed in the **Available configurations** grid.

5. Select the required configuration. For example, select version **1** of the **Tax (India GST Contoso)** configuration.
6. Select **Save** and then **Synchronize**.

    > [!NOTE]
    > If you want to copy the tax setup data from the original configuration, select **Copy tax setup data from**, and then select the configuration to copy.

7. Select **Activate**.
8. On the **Tax setup** page, go to **Companies**, and select **New**.
9. In the **Companies** field, select **INMF**. 
10. Select **Save**.
11. To activate the configuration for the company, select **Activate**.
12. To set up data for the new version, select **Setup**.

## Modify the data provider in Microsoft Dynamics 365 Finance

### Implement logic to determine the net price

1. In the Application Object Tree (AOT), open **Classes** \> **TaxEngineModelFields**.
2. Add a new constant variable for the net price.

    ```
    public static const str NetPrice = 'Net Price';
    ```

2. Add a new method for the `TaxModelDocLineBaseImpl_IN` class. In the method, implement the determination logic for the net price.

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

### Pass the net price to GTE

1. Pass the net price to GTE in the `TaxableDocumentRowDataProviderLine_IN_Extension.fillInFields()` method.

    ```
    this.addFieldValue(_lineObj, TaxEngineModelFields::NetPrice, taxModelDocLineBaseImpl.getNetPrice());
    ```

2. Add the net price to the `TaxableDocumentRowDataProviderLine_IN_Extension.initValidFields()` method.

    ```
    validFields.add(TaxEngineModelFields::NetPrice, Types::Real);
    ```

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
