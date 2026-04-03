---
title: Customize table and column mappings
description: Learn how to customize table and column mappings, add transforms, enable filtering for your data, and add new table maps.
author: nhelgren
ms.date: 04/03/2026
ms.topic: how-to
ms.custom: 
  - bap-template
audience: Developer
ms.reviewer: twheeloc
ms.author: nhelgren
ms.search.region: Global
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Customize table and column mappings

[!include [banner](../../includes/banner.md)]

The default table maps include predefined table and column mappings that enable the flow of data between two apps. In this way, they serve as blueprints. However, because every business is different, the default table maps might sometimes not be enough. Therefore, dual-write fully supports customization by providing ways to change table maps and column mappings.

> [!NOTE]
> The Worker Personal details entity in Microsoft Dataverse doesn't contain the **Professional Suffix** field. However, you can add this field through extensibility. You can't save new values to the **Professional Suffix** and **Personal Suffix** fields of the Worker entity while you're mapping the Worker Personal details entity from Dataverse to the Worker entity in finance and operations apps. The **DirNameAffixPersonalSuffix** data source contains these fields and doesn't save values to fields that aren't available in finance and operations apps.

## Customize column mappings, add transforms, and enable filtering

1. In your finance and operations app, on the **Dual-write** page, on the **Table mappings** tab, select the table map to customize.

    > [!NOTE]
    > Before you change table mappings, stop them. Otherwise, your changes aren't saved.

1. On the **Table mappings** tab, customize a column by selecting a new or custom column from either the finance and operations app or Dataverse.

    :::image type="content" source="media/customize-a-field.png" alt-text="Screenshot of customizing a column.":::

1. Select the map type to customize the synchronization direction (unidirectional or bidirectional) and add transforms.

    :::image type="content" source="media/customize-sync-direction.png" alt-text="Screenshot of customizing the synchronization direction and adding transforms.":::

    The following table describes the available synchronization directions.

    | Symbol | Description |
    |---|---|
    | :::image type="icon" source="media/equal-symbol.png" border="false"::: | Bidirectional column assignment |
    | :::image type="icon" source="media/greater-less-symbol.png" border="false"::: | Bidirectional column assignment that uses transforms |
    | :::image type="icon" source="media/greater-than-symbol.png" border="false"::: | Unidirectional column assignment (left to right) |
    | :::image type="icon" source="media/less-than-symbol.png" border="false"::: | Unidirectional column assignment (right to left) |
    | :::image type="icon" source="media/right-arrow-symbol.png" border="false"::: | Unidirectional column assignment that uses transforms (left to right) |
    | :::image type="icon" source="media/left-arrow-symbol.png" border="false"::: | Unidirectional column assignment that uses transforms (right to left) |

    The following table describes the available transform types.

    | Transform type | Description |
    |---|---|
    | Default | Default values are values that are applied to destination columns when no source column value is available. Use default values for columns that are required on the destination table when you have no corresponding source column. |
    | Value map | Value maps define how values that are present in one table should be mapped to values in the other table. |

   In addition to adding transformation value mappings by adding or updating the mapping fields, you can modify the generated JSON directly. In the **Transform** section of the slide out pane, select **Show JSON** to open the field with the generated JSON for the value mappings. When you modify and save the JSON, the value mapping fields are updated to reflect the changes made to the JSON.

   Directly modifying the JSON is useful when the fields can't manage the values needed. For example, entering "null" in a value mapping field considers "null" as a string value rather than a `null` value. You can work around this situation by modifying the JSON directly. If you need to map the value "0" in finance and operations apps to a `null` value in Dataverse, enter the following JSON:

   ```json
   [
     {
      "transformType": "ValueMap",
      "valueMap": {
       "0": null
      }
     }
    ]

   ```

1. Add a new column by selecting **Add mapping** and then selecting an existing or custom column in the list.

    The following illustration shows an example where a new **birthdate** column is being added.

    :::image type="content" source="media/add-new-field.png" alt-text="Screenshot of adding a new birthdate column.":::

1. When you finish customizing the column mappings, select **Save**. Then follow the prompts to specify a publisher and a version number.

    :::image type="content" source="media/choose-publisher-version.png" alt-text="Screenshot of specifying a publisher and a version number.":::

### Filter your data

Dual-write lets you filter data by using Open Data Protocol (OData) filter expressions for Dataverse. For the finance and operations app, filtering resembles range expressions that are used in the query range.

1. On the table mapping page, select the filter button (funnel symbol).

    :::image type="content" source="media/select-filter-icon.png" alt-text="Screenshot of the filter button.":::

1. In the **Edit query** dialog box, specify your filters. In this example, the filter that you specify returns only accounts where the account type equals **3**.

    :::image type="content" source="media/specify-filters.png" alt-text="Screenshot of specifying filters.":::

    The following table shows some examples of filter expressions.

    | Filter | Dataverse | Finance and operations apps |
    |---|---|---|
    |Enumeration fields| AccountType eq '3'| (AccountType == AccountType::Customer)|
    |Dates|TransactionDate le '2021-06-23'|(TransactionDate <= 23\06\2021)|
    |Multiple criteria combined| numberofemployees gt 1000 and<br>numberofemployees le 2000 | ((numberofemployees > 1000) &&<br>(numberofemployees <= 2000)) |

    The following table lists the filter query operators that dual-write supports:

    | Type | Operators | More information |
    |------|------|------|
    |**Comparison operators** | Use the `eq`, `ne`, `gt`, `ge`, `lt`, and `le` operators to compare a property and a value. | [Comparison operators](/power-apps/developer/data-platform/webapi/query-data-web-api#comparison-operators.md) |
    |**Logical operators** | Use `and`, `or`, and `not` to create more complex expressions. | [Logical operators](/power-apps/developer/data-platform/webapi/query-data-web-api#logical-operators.md) |
    |**Grouping operators** | Use parentheses: `(` and `)` to specify the precedence to evaluate a complex expression. | [Grouping operators](/power-apps/developer/data-platform/webapi/query-data-web-api#grouping-operators.md) |

    > [!NOTE]
    > Dual-write source filters don't support nested lookups. Only standard filter operators used directly against table columns are supported. For more examples, see [Standard filter operators](/powerapps/developer/common-data-service/webapi/query-data-web-api#standard-filter-operators).
    >
    > Query filters with the `contains` operator aren't supported.

    For more examples that show how to use expressions in query ranges, see [Using Expressions in Query Ranges](/dynamicsax-2012/developer/using-expressions-in-query-ranges).

## Add new table maps

Although Microsoft continues to add new tables, you can also add standard or custom table maps.

The following example shows how to add a new table map named **Address books**.

1. In the finance and operations app, on the **Dual-write** page, select **Add table map**.

    :::image type="content" source="media/add-new-entity-map.png" alt-text="Screenshot of adding a new table map.":::

    > [!NOTE]
    > When you [create a new solution](app-lifecycle-management.md#create-new-solution) that uses these modified table maps, you must specify the same publisher.

1. Confirm the table maps that you modified and added. Be sure to enable and test them to ensure that they work as you expect.

    :::image type="content" source="media/confirm-entity-maps.png" alt-text="Screenshot of confirming the table maps.":::

## Next steps

[Error management and alert notifications](errors-and-alerts.md)

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
