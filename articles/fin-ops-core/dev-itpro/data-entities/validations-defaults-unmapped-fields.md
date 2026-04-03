---
title: Validations, default values, and unmapped fields
description: Learn how data entity values are validated, how default values can be provided, and how to use fields that are not mapped to data source values.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: twheeloc
audience: Developer
ms.assetid: 7ea995fa-8ea0-403d-8a68-f19993c40a6d
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Validations, default values, and unmapped fields

[!include [banner](../includes/banner.md)]

This article describes how to validate data entity values, provide default values, and use fields that aren't mapped to data source values but instead contain virtual or computed data (unmapped fields).

## Validations

Define validations on the tables that back up entities, at both the field level and the record level. You can also define validations at the data entity level.

### Table (data source) vs. entity validation

Tables back entities, and you define validations for these tables at both the field level (**Table.validateField()**) and the record level (**Table.validateWrite()**). Data entities that use those tables respect these validations. Although these validations are intrinsic to the tables that back a data entity, you can also define validations at the data entity level. Like table-based validations, you can write entity-based validations at the field level (**DataEntity.validateField()**) or the record level (**DataEntity.validateWrite()**).

### Table-based validation behavior

Table validations fire automatically as part of the CUD operations. **Table.ValidateField**, **AllowEdit**, and **AllowEditOnCreate** field-level validations fire automatically when you perform inserts or updates on the data entity. This behavior is true for all paths (X++, OData, and so on). These validations occur during the mapping process, when fields are mapped from an entity to individual data sources.

:::image type="content" source="./media/redo1-1024x582.png" alt-text="Screenshot of redo1.":::

After the field values from the data entity are copied to mapped data source fields, field validations run on the set fields. Validations include table-level **validateField**, which validates **AllowEdit** and **AllowEditOnCreate**. If a validation fails because of an error, validation for the remaining fields continues. Finally, validation checks whether any error occurred during the validation process for any of the data sources. If there was an error, the process errors out at this point, and table-level **validateWrite()** isn't called. To skip **validateField** for a back-end table, a consumer can call **DataEntity.skipDataSourceValidateField(Int \_DataEntityFieldId, Boolean \_skip)**. The field ID for this method is the field ID of the data-entity mapped field, not the back-end table field. By using the following API, you can skip validation for a particular field, regardless of the consumer.

:::image type="content" source="./media/over9.png" alt-text="Screenshot of Over9.":::

**Table.ValidateWrite** Record-level **ValidateWrite** validations that are defined in back-end tables fire automatically when you perform data-entity inserts and updates. This behavior is true for all paths (X++, OData, and so on). These validations occur just before the actual insert or update is applied to the data source. If the validation fails, an error is thrown, and the process stops for other data sources.

:::image type="content" source="./media/redo2-1024x636.png" alt-text="Screenshot of redo2.":::

To skip **validateWrite** for all back-end tables for a data entity, a consumer can call **DataEntity.skipDataSourceValidateWrite(Boolean \_skip)**. This method turns **validateWrite** on or off for all data sources. By using the following API, you can skip validation for a particular data source, regardless of the consumer.

:::image type="content" source="./media/over10.png" alt-text="Screenshot of Over10.":::

**Table.ValidateDelete** Record-level **ValidateDelete** validations that are defined in back-end tables fire automatically when you perform data entity deletes. This behavior is true for all paths (X++, OData, and so on). These validations occur just before the delete is applied to the data source. If the validation fails, an error is thrown, and the process stops for other data sources.

:::image type="content" source="./media/over11.png" alt-text="Screenshot of Over11.":::

To skip **validateDelete** for all back-end tables for a data entity, a consumer can call **DataEntity.skipDataSourceValidateDelete(Boolean \_skip)**. This method turns **validateDelete** on or off for all data sources. By using the following API, you can skip validation for a particular data source, regardless of the consumer.

:::image type="content" source="./media/over12.png" alt-text="Screenshot of Over12.":::

### Entity-based validation behavior

| Validation | Target | Caller |
|---|---|---|
| DataEntity.ValidateField | - Data types<br>- Mandatory relationships (both tables and extended data types [EDTs])<br>- Any custom validation<br>- Doesn't call **validateField** for underlying mapped table fields | - Is called automatically from OData<br>- Is called by the form engine when a field is modified<br>- Isn't called automatically if an insert or update is fired from X++ code |
| DataEntity.ValidateWrite | - Mandatory columns<br>- Relationships (both tables and EDTs)<br>- Any custom validation<br>- Doesn't call table-level **validateWrite** for underlying tables | - Is called automatically from OData<br>- Is called by the form engine when a record is saved.<br>- Isn't called automatically if an insert or update is fired from X++ code |
| DataEntity.ValidateDelete | - DeleteActions<br>- Any custom validation<br>- Doesn't call table-level **validateDelete** for underlying tables | - Is called automatically from OData.<br>- Is called by the form engine when a record is deleted<br>- Isn't called automatically if a delete is fired from X++ code |

## Defaults

You can provide default values for initializations and rows.

### Initializations

**DataEntity.initValue:** Initialize a data entity with default values and by using any custom logic that is present in entity-level **initValue**. This method isn't called automatically when an insert or update is performed on a data entity from X++. You must call it explicitly if it's required. The form engine calls the method automatically when a new record is created. **DataEntity.initValue** doesn't call the **initValue** method for back-end tables that are used in the data entity. **Table.initValue:** Table-level **initValue**, as defined for back-end tables, is fired when you perform a data entity insert. This behavior is true for all paths (X++, OData, and so on). **Table.initValue** runs just before the entity is mapped to data source fields.

:::image type="content" source="./media/over13.png" alt-text="Screenshot of Over13.":::

To skip entity-level **initValue** for all back-end tables for a data entity, a consumer can call **DataEntity.skipDataSourceInitValue(Boolean \_skip)**. This method turns **initValue** on or off for all data sources. By using the following API, you can skip **initValue** for a particular field, regardless of the consumer.

:::image type="content" source="./media/capturea.png" alt-text="Screenshot of Capturea.":::

### DefaultRow

**DataEntity.DefaultRow:** Use **DataEntity.DefaultRow** in conjunction with **defaultField** and **getDefaultingDependencies** to provide defaults. X++ and the form engine don't call it automatically. **Table.DefaultRow:** The form engine calls **Table.DefaultRow** automatically for each data source after mapping is completed, and before the insert and validation on the data source.

:::image type="content" source="./media/captureb.png" alt-text="Screenshot of Captureb.":::

## Unmapped fields

A data entity can have *unmapped* fields in addition to the fields that directly map to fields in the data sources. You can generate values for unmapped fields by using two mechanisms:

- Custom X++ code
- SQL that runs in Microsoft SQL Server

The two types of unmapped fields are *virtual* and *computed*. Unmapped fields always support read actions, but the feature specification might not require any development effort to support write actions.

**Virtual field**

- A non-persisted field.
- Controlled by custom X++ code.
- Reads and writes occur through custom X++ code.
- Typically used for intake values that are calculated by using X++ code and can't be replaced by computed columns.

**Computed field**

- The value is generated by an SQL view computed column.
- During reads, SQL computes the data and fetches it directly from the view.
- For writes, custom X++ code parses the input value and then writes the parsed values to the regular fields of the data entity. The values are stored in the regular fields of the data sources of the entity.
- Used mostly for reads.
- Use computed columns instead of virtual fields whenever you can, because computed columns are computed at the SQL Server level, whereas virtual fields are computed row by row in X++.

### Properties of unmapped fields

| Category | Name | Type | Default value | Behavior |
|---|---|---|---|---|
| Data | IsComputedField | NoYes | Yes | - **Yes:** The field is synchronized as a SQL view computed column. An X++ method is required to compute the SQL definition string for the column. The virtual column definition is static and is used when the entity is synchronized. After that, the X++ method isn't called at run time.<br>- **No:** The field is a true virtual field, where inbound and outbound values are fully controlled through custom code. |
| Data | ComputedFieldMethod | String |  | A static **DataEntity** method in X++ is used to build the SQL expression that generates the field definition. This property is disabled and irrelevant if the **IsComputedField** property is set to **No**. The method is required if the **IsComputedField** property is set to **Yes**. |
| Data | ExtendedDataType | String |  |  |

### Unmapped field comparison

|  | Virtual field | Computed field |
|---|---|---|
| Metadata properties | Is computed = No | - Is Computed = Yes<br>- Computed Field Method = static method |
| Read | - X++ (override **postLoad**)<br>- Row by row | - SQL computed column<br>- Set-based read possible |
| Write | X++ (override **mapEntityToDataSource**) | X++ (override **mapEntityToDataSource**) |
| Advantages | - Unbound to the schema, keeps the public contract the same, but the implementation can change<br>- Call X++ methods | Faster reads, large export can occur directly from the view |

### Examples

The following table provides a computed example if a **UnitOfMeasure** relationship exists, and displays that in an unmapped field.

| Virtual field | Computed field |
|---------------|----------------|
| On postLoad()*//Check to see if record exists in UnitOfMeasureInternalCode.UnitOfMeasure//Set hasFixedInternalCode value based on the field*if(this.UnitOfMeasure)this.HasFixedInternalCodeVirtual = NoYes::Yes; else this.HasFixedInternalCodeVirtual = NoYes::No; | On computedFieldMethod()*//Desired SQL computed column statement(CASE WHEN T2.RECID IS NULL THEN 0 ELSE 1 END) AS INT)* |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
