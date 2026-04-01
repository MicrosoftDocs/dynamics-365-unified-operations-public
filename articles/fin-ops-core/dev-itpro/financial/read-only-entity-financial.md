---
title: Create read-only entities that expose financial dimensions
description: Learn about how to build an entity for registered transactions, including outlines on creating a basic entity and customizing the basic entity. 
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2026
ms.reviewer: twheeloc
ms.assetid: 119610df-3975-43ce-830b-84fe58266321
ms.search.region: Global
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30
---

# Create read-only entities that expose financial dimensions

[!include [banner](../includes/banner.md)]

In this article, you learn how to build an entity for registered transactions.

> [!NOTE]
> This article comes from Per Baarsoe Jorgensen of the Solutions Architecture team. It describes a real-world scenario that the team encountered while working with customers.

Imagine a scenario where you must expose all vendor invoice line transactions together with the financial dimensions that the distributions apply. Because easy consumption by a third-party tool is essential, create an entity for this scenario. As a result, the entity shouldn't require joining with other related entities but should provide value on its own.

This article walks through the process of creating a sample entity to meet these requirements. (The article leaves out instructions for integrating with Microsoft Azure DevOps, because those steps are already well documented.)

## Create a basic entity

First, create a new element in a project by selecting **New Item**.

:::image type="content" source="./media/fd-basic.png" alt-text="Screenshot of the New item option.":::

In the form that opens, under Data Model, select the **Data Entity** element type.

:::image type="content" source="./media/fd-element.png" alt-text="Screenshot of the Data element type selection.":::

> [!NOTE]
> Be careful when you name the entity, because you can't rename it later.

Next, in the Data Entity wizard, select the primary data source. For this scenario, the data source is VendInvoiceTrans.

:::image type="content" source="./media/fd-wizard.png" alt-text="Screenshot of the Data entity wizard.":::

The wizard doesn't accept tables that don't have a natural key, as is the case with VendInvoiceTrans. Therefore, you see the following error message.

:::image type="content" source="./media/fd-error.png" alt-text="Screenshot of the natural key error message.":::

Select any other primary data source that has a natural key associated, such as VendGroup.

Because you don't need this data source, you also don't need any fields for it. Therefore, clear the **Select all** check box.

:::image type="content" source="./media/fd-wizard2.png" alt-text="Screenshot of the cleared Select all check box in the wizard.":::

Finally, create the template for your entity by selecting **Finish**.

## Customize the basic entity

After you create the entity, staging table, and security assets, you can create your custom entity. In the project, open the **VendorInvoiceTransactionDetailsEntity** entity in the designer.

:::image type="content" source="./media/fd-designer.png" alt-text="Screenshot of VendorInvoiceTransactionDetailsEntity in the designer.":::

In the designer, replace the dummy table (**VendGroup**) that you used in the wizard with the transaction table **VendInvoiceTrans**. Because you didn't choose to add the fields, you don't need to remove fields in the entity.

:::image type="content" source="./media/fd-menu.png" alt-text="Screenshot of the Data Entity Type property.":::

> [!NOTE]
> Because this entity exposes transactional data, mark the entity as read-only. Set the **Is read only** property to **Yes** on the top node. Because accounting distributions are versioned, only the current version should be returned when you query. Therefore, create a view that makes this part easily reusable across multiple entities.

:::image type="content" source="./media/fd-menu2.png" alt-text="Screenshot of replacing the data source with VendInvoiceTrans.":::

In the properties, assign **ReferenceDistribution** a range filter value of **0** and **ReferenceRole** a range filter value of **1**. The join mode property for the **AccountDistributionReverse** data source must be **NoExistsJoin**. After you add the new view, add it to the **VendorInvoiceTransactionDetailsEntity** entity.

:::image type="content" source="./media/fd-menu3.png" alt-text="Screenshot of adding to VendorInvoiceTransactionDetailsEntity.":::

## Expose financial dimensions as fields

The next important step is to expose the financial dimensions as separate fields on the entity. Because your scenario builds on top of a posted transaction, add the fields to the **DimensionCombinationentity** entity. Make the adjustments in a resilient manner by using the extension approach, so that minimal maintenance is required when you upgrade the code base to newer versions in the future.

### Dynamics 365 Finance and Operations, Enterprise edition version 1611

For version 1611 or later, use the wizard that's available in Microsoft Visual Studio (at **Dynamics 365** &gt; **Addins** &gt; **Add financial dimensions for Odata**). For instructions, see [Add dimensions to Excel templates](dimensions-overview.md).

### Earlier versions

If you're working with earlier versions, complete the steps outlined in this section. First, add the entity extension itself. Select **Create extension** on the context menu (shortcut menu). Next, create the code that retrieves the data. Because the entity extension is already in place, you must create a new class. The following example adds code for an arbitrary dimension that is named **ProductLine**.

```xpp
[ExtensionOf(dataentityviewstr(DimensionCombinationentity))]
  public final class DimensionCombinationentity_Extension
  {
    private static server str getEmptyOrDimensionValueSqlString(str _attributeName)
    {
        str sqlStatement;

        DimensionAttribute dimensionAttribute = DimensionAttribute::findByName(_attributeName);

        if (!dimensionAttribute)
        {
            sqlStatement = SysComputedColumn::returnLiteral('');
        }
        else
        {
            sqlStatement = strFmt('SELECT TOP 1 T1.%1 ', dimensionAttribute.DimensionValueColumnName);
        }

        return sqlStatement;
    }

    /// Generates the sql to populate the FOTA view field.
    public static server str ProductLineValue()
    {
        return DimensionCombinationentity::getEmptyOrDimensionValueSqlString('ProductLine');
    }
  }
```

Add fields to the newly created entity extension by using custom fields that reference these methods.

:::image type="content" source="./media/fd-menu4.png" alt-text="Screenshot of adding fields to the entity extension.":::

Next, set the property values to reflect the fact that the field is unmapped and should be retrieved through the code that you made for the extension class. When you create the relation, also set the following values:

- Cardinality: **ZeroMore**
- Related data entity: **DimensionCombinationentity**
- Related data entity cardinality: **ZeroOne**
- Relationship type: **Association**

:::image type="content" source="./media/fd-menu5.png" alt-text="Screenshot of creating a relation with property values.":::

> [!NOTE]
> You must fully qualify the data method with the class name.

You're now ready to add the DimensionCombinationentity entity to your new VendInvoiceTransactionentity entity.

:::image type="content" source="./media/fd-menu6.png" alt-text="Screenshot of adding DimensionCombinationentity to the new entity.":::

Notice that both the AccountingDistributionCurrent and the DimensionCombinationentity entity should be outer-joined.

:::image type="content" source="./media/fd-menu7.png" alt-text="Screenshot of the outer join configuration.":::

Now, drag the required fields from the various data sources to the **Fields** node on the new entity (that is, to the newly created ProductLine).

:::image type="content" source="./media/fd-menu8.png" alt-text="Screenshot of dragging fields to the ProductLine node.":::

Add a key to the entity to enable the incremental update functionality during the export configuration. Therefore, make sure that RecId from the VendInvoiceTrans data source is part of the fields named e.g. VendInvoiceTransRecId. After the field is in the field list, drag it to the **EntityKey** node.

:::image type="content" source="./media/fd-menu9.png" alt-text="Screenshot of dragging a field to the EntityKey node.":::

To make sure that the staging table is associated with the fully configured entity, update it. On the context menu for the entity, select **Update staging table**.

:::image type="content" source="./media/fd-menu10.png" alt-text="Screenshot of the Update staging table option on the context menu.":::

The entity work is now complete, and you can build it.

> [!NOTE]
> In this scenario, a LedgerDimension was associated with the DimensionCombinationentity entity. In scenarios where there's a DefaultDimension, you must associate it with the DimensionSetentity entity. The improvements and extensions that are required are identical to the improvements and extensions that you made to the DimensionCombinationentity entity.

## Additional resources

[Export Dynamics AX 7 Entities to your own Azure SQL Database](/archive/blogs/dynamicsaxbi/export-dynamics-ax7-entities-to-your-own-azure-sql-database)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
