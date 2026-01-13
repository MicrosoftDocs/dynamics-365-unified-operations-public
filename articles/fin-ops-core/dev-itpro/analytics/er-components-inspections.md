---
title: Inspect the configured ER component to prevent runtime issues
description: Learn about how to inspect the configured Electronic reporting (ER) components to prevent runtime issues that might occur.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 01/12/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: ERSolutionTable, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner, EROperationDesigner
ms.dyn365.ops.version: Version 7.0.0
ms.assetid: 
---

# Inspect the configured ER component to prevent runtime issues

[!include[banner](../includes/banner.md)]

You can [validate](er-fillable-excel.md#validate-an-er-format) each configured [Electronic reporting (ER)](general-electronic-reporting.md) [format](er-overview-components.md#format-components-for-outgoing-electronic-documents) and [model mapping](er-overview-components.md#model-mapping-component) at design time. During this validation, a consistency check runs to help prevent runtime problems, such as execution errors and performance degradation. For every problem that the check finds, it provides the path of a problematic element. For some problems, an automatic fix is available.

By default, the validation automatically runs in the following cases for an ER configuration that contains the previously mentioned ER components:

- You [import](general-electronic-reporting.md) a new version of an ER configuration into your instance of Microsoft Dynamics 365 Finance.
- You change the status of the editable ER configuration from **Draft** to **Completed**.
- You [rebase](general-electronic-reporting.md#upgrading-a-format-selecting-a-new-version-of-base-format-rebase) an editable ER configuration by applying a new base version.

You can explicitly run this validation. Select one of the following three options, and follow the steps that are provided:

- Option 1:

    1. Go to **Organization administration \> Electronic reporting \> Configurations**.
    1. In the configurations tree in the left pane, select the desired ER configuration that contains the ER format or ER model mapping component.
    1. On the **Versions** FastTab, select the desired version of the selected ER configuration.
    1. On the Action Pane, select **Validate**.

- Option 2, for an ER format:

    1. Go to **Organization administration \> Electronic reporting \> Configurations**.
    1. In the configurations tree in the left pane, select the desired ER configuration that contains the ER format component.
    1. On the **Versions** FastTab, select the desired version of the selected ER configuration.
    1. On the Action Pane, select **Designer**.
    1. On the **Format designer** page, on the Action Pane, select **Validate**.

- Option 3, for an ER model mapping:

    1. Go to **Organization administration \> Electronic reporting \> Configurations**.
    1. In the configurations tree in the left pane, select the desired ER configuration that contains the ER model mapping component.
    1. On the **Versions** FastTab, select the desired version of the selected ER configuration.
    1. On the Action Pane, select **Designer**.
    1. On the **Model to datasource mapping** page, on the Action Pane, select **Designer**.
    1. On the **Model mapping designer** page, on the Action Pane, select **Validate**.

To skip the validation when importing the configuration, follow these steps:

1. Go to **Organization administration \> Electronic reporting \> Configurations**.
1. On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
1. Set the **Validate the configuration after importing** option to **No**.

To skip the validation when you change or rebase the version's status, follow these steps:

1. Go to **Organization administration \> Electronic reporting \> Configurations**.
1. On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
1. Set the **Skip validation at configuration's status change and rebase** option to **Yes**.

ER uses the following categories to group consistency check inspections:

- **Executability** – Inspections that detect critical issues that might occur at runtime. These issues are mostly at an **Error** level.
- **Performance** – Inspections that detect issues that might cause inefficient execution of configured ER components. These issues are mostly at a **Warning** level.
- **Data integrity** – Inspections that detect issues that might cause data loss or runtime issues. These issues are mostly at a **Warning** level.

## List of inspections

The following table provides an overview of the inspections that ER provides. For more information about these inspections, use the links in the first column to go to the relevant sections of this article. Those sections explain the types of components that ER provides inspections for and how you can reconfigure ER components to help prevent issues.

| Name | Category | Level | Message |
|------|----------|-------|---------|
| [Type conversion](#i1) | Executability | Error | Can't convert expression of type &lt;type&gt; to field of type &lt;type&gt;.<br><br>**Runtime error:** Exception for type |
| [Type compatibility](#i2) | Executability | Error | The configured expression can't be used as the binding of the current format element to a data source as this expression returns value of the data type &lt;type&gt; that is beyond the scope of data types that are supported by the current format element of type &lt;type&gt;.<br><br>**Runtime error:** Exception of type |
| [Missing configuration element](#i3) | Executability | Error | Path not found &lt;path&gt;.<br><br>**Runtime error:** Element of the configuration &lt;path&gt; not found |
| [Executability of an expression with FILTER function](#i4) | Executability | Error | The list expression of FILTER function isn't queryable.<br><br>**Runtime error:** Filtering isn't supported. Validate the configuration to get more details about this. |
| [Executability of a GROUPBY data source](#i5) | Executability | Error | Path &lt;path&gt; doesn't support querying. |
| [Executability of a GROUPBY data source](#i5) | Executability | Error | Group by function can't be executed with query.<br><br>**Runtime error:** Group by function can't be executed with query. |
| [Executability of a JOIN data source](#i6) | Executability | Error | Can't join a list &lt;path&gt; that isn't a filter in query.<br><br>**Runtime error:** Function Joined datasource should be a filter expression calculated field has been incorrectly called. |
| [Preferability of FILTER vs WHERE function](#i7) | Performance | Warning | Using FILTER function for the expression is preferable than WHERE from the performance perspective. Select Fix to replace it automatically. |
| [Preferability of ALLITEMSQUERY vs ALLITEMS function](#i8) | Performance | Warning | Using ALLITEMSQUERY function for the expression is preferable than ALLITEMS from the performance perspective. Select Fix to replace it automatically. |
| [Consideration of empty list cases](#i9) | Executability | Warning | List &lt;path&gt; doesn't have any check for empty list case, it can result an error at run time. Add a check for empty list case.<br><br>**Runtime error:** List is empty at &lt;path&gt;<br><br>**[Potential issue](#i9a):** Line is getting populated once while a data source it's populated from contains multiple records |
| [Executability of an expression with FILTER function (caching)](#i10) | Executability | Error | FILTER function can't be applied to the selected type of data source. A data source of the Table records type is applicable only when it isn't cached and has no manually added nested data sources.<br><br>**Runtime error:** Filtering isn't supported. Validate the configuration to get more details about this. |
| [Missing binding](#i11) | Executability | Warning | Path &lt;path&gt; has no binding to any datasource in using model's mapping.<br><br>**Runtime error:** Path &lt;path&gt; isn't bound |
| [Not linked template](#i12) | Data integrity | Warning | File &lt;name&gt; isn't linked to any file components and will be removed after changing status of configuration version. |
| [Not synced format](#i13) | Data integrity | Warning | Defined name &lt;component name&gt; doesn't exist in Excel sheet &lt;sheet name&gt; |
| [Not synced format](#i14) | Data integrity | Warning | &lt;Tagged Word content control&gt; tag doesn't exist in Word template file<br><br>**Runtime error:** &lt;Tagged Word content control&gt; tag doesn't exist in Word template file. |
| [No default mapping](#i15) | Data integrity | Error | More than one model mapping exists for the &lt;model name (root descriptor)&gt; data model in the configurations &lt;configuration names separated by comma&gt;. Set one of the configurations as default<br><br>**Runtime error:** More than one model mapping exists for the &lt;model name (root descriptor)&gt; data model in the configurations &lt;configuration names separated by comma&gt;. Set one of the configurations as default. |
| [Inconsistent setting of Header or Footer components](#i16) | Data integrity | Error | Headers/footers (&lt;component type: Header or Footer&gt;) are inconsistent<br><br>**Runtime:** The last configured component is used at runtime if the draft version of the configured ER format is executed. |
| [Inconsistent setting of Page component](#i17) | Data integrity | Error | There are more than two range components without replication. Remove unnecessary components. |
| [Executability of an expression with ORDERBY function](#i18) | Executability | Error | The list expression of ORDERBY function isn't queryable.<br><br>**Runtime error:** Sorting isn't supported. Validate the configuration to get more details about this. |
| [Obsolete application artifact](#i19) | Data integrity | Warning | The element &lt;path&gt; is marked as obsolete.<br>or<br>The element &lt;path&gt; is marked as obsolete with message &lt;message text&gt;.<br><br>**Runtime error sample:** Class '&lt;path&gt;' not found. |

## <a id="i1"></a>Type conversion

ER checks whether the data type of a data model field is compatible with the data type of an expression that you configure as the binding for that field. If the data types are incompatible, the ER model mapping designer shows a validation error. The error message states that ER can't convert an expression of type A to a field of type B.

The following steps show how this issue might occur.

1. Start to configure the ER data model and the ER model mapping components simultaneously.
1. In the data model tree, add a field that you name **X**, and select **Integer** as the data type.

    :::image type="content" source="./media/er-components-inspections-01.png" alt-text="Screenshot of X field and Integer data type added to the data mode tree on the Data model page.":::

1. In the model mapping designer, in the **Data sources** pane, add a data source of the **Calculated field** type.
1. Name the new data source **Y**, and configure it so that it contains the expression `INTVALUE(100)`.
1. Bind **X** to **Y**.
1. In the data model designer, change the data type of the **X** field from **Integer** to **Int64**.
1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page.

    :::image type="content" source="./media/er-components-inspections-01.gif" alt-text="Screenshot of validating the editable model mapping component on the Model mapping designer page.":::

1. Select **Validate** to inspect the model mapping component of the selected ER configuration on the **Configurations** page.

    :::image type="content" source="./media/er-components-inspections-01a.png" alt-text="Screenshot of inspecting the model mapping component on the Configurations page.":::

1. Notice that a validation error occurs. The message states that the value of the **Integer** type that the `INTVALUE(100)` expression of the **Y** data source returns can't be stored in the **X** data model field of the **Int64** type.

The following illustration shows the runtime error that occurs if you ignore the warning and select **Run** to run a format that is configured to use the model mapping.

:::image type="content" source="./media/er-components-inspections-01b.png" alt-text="Screenshot of runtime errors on the Format designer page.":::

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Update the data model structure by changing the data type of the data model field so that it matches the data type of the expression that you configure for the binding of that field. For the preceding example, change the data type of the **X** field back to **Integer**.

#### Option 2

Update the model mapping by changing the expression of the data source that you bind to the data model field. For the preceding example, change the expression of the **Y** data source to `INT64VALUE(100)`.

## <a id="i2"></a>Type compatibility

ER checks whether the data type of a format element is compatible with the data type of an expression that you configure as the binding of that format element. If the data types are incompatible, a validation error occurs in the ER Operations designer. The message that you receive states that the configured expression can't be used as the binding of the current format element to a data source, because the expression returns a value of data type A that is beyond the scope of the data types that the current format element of type B supports.

The following steps show how this issue might occur.

1. Start to configure the ER data model and the ER format components simultaneously.
1. In the data model tree, add a field that you name **X**, and select **Integer** as the data type.
1. In the format structure tree, add a format element of the **Numeric** type.
1. Name the new format element **Y**. In the **Numeric type** field, select **Integer** as the data type.
1. Bind **X** to **Y**.
1. In the format structure tree, change the data type of the **Y** format element from **Integer** to **Int64**.
1. Select **Validate** to inspect the editable format component on the **Format designer** page.

    :::image type="content" source="./media/er-components-inspections-02.gif" alt-text="Screenshot of validating type compatibility on the Format designer page.":::

1. Notice that a validation error occurs. The message states that the configured expression can accept only **Int64** values. Therefore, the value of the **X** data model field of the **Integer** type can't be entered in the **Y** format element.

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Update the format structure by changing the data type of the **Numeric** format element so that it matches the data type of the expression that you configured for the binding of that element. In the preceding example, change the **Numeric type** value of the **X** format element back to **Integer**.

#### Option 2

Update the format mapping of the **X** format element by changing the expression from `model.X` to `INT64VALUE(model.X)`.

## <a id="i3"></a>Missing configuration element

ER checks whether the binding expressions contain only data sources that the editable ER component configures. For every binding that contains a data source that the editable ER component is missing, a validation error occurs in the ER Operations designer or the ER model mapping designer.

The following steps show how this issue might occur.

1. Start to configure the ER data model and the ER model mapping components simultaneously.
1. In the data model tree, add a field that you name **X**, and select **Integer** as the data type.

    :::image type="content" source="./media/er-components-inspections-01.png" alt-text="Screenshot of data model tree with X field and Integer data type on the Data model page.":::

1. In the model mapping designer, in the **Data sources** pane, add a data source of the **Calculated field** type.
1. Name the new data source **Y**, and configure it so that it contains the expression `INTVALUE(100)`.
1. Bind **X** to **Y**.
1. In the model mapping designer, in the **Data sources** pane, delete the **Y** data source.
1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page.

    :::image type="content" source="./media/er-components-inspections-03.gif" alt-text="Screenshot of inspecting the editable ER model mapping component on the Model mapping designer page.":::

1. Notice that a validation error occurs. The message states that the binding of the **X** data model field contains the path that refers to the **Y** data source, but this data source isn't found.

### Automatic resolution

Select **Unbind** to automatically fix this issue by removing the missing data source binding.

### Manual resolution

#### Option 1

Unbind the **X** data model field to stop referring to the nonexistent **Y** data source.

#### Option 2

In the model mapping designer, in the **Data sources** pane, add the **Y** data source again.

## <a id="i4"></a>Executability of an expression with FILTER function

Use the built-in [FILTER](er-functions-list-filter.md) ER function to access application tables, views, or data entities. The function places a single SQL call to get the required data as a list of records. Use a data source of the **Record list** type as an argument of this function to specify the application source for the call. ER checks whether a direct SQL query can be established to a data source that you refer to in the `FILTER` function. If a direct query can't be established, the ER model mapping designer shows a validation error. The error message states that the ER expression that includes the `FILTER` function can't be run at runtime.

The following steps show how this issue might occur.

1. Start to configure the ER model mapping component.
1. Add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Vendor**. In the **Table** field, select **VendTable** to specify that this data source requests the VendTable table.
1. Add a data source of the **Calculated field** type.
1. Name the new data source **FilteredVendor**, and configure it so that it contains the expression `FILTER(Vendor, Vendor.AccountNum="US-101")`.
1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page and verify that the `FILTER(Vendor, Vendor.AccountNum="US-101")` expression in the **Vendor** data source can be queried.
1. Modify the **Vendor** data source by adding a nested field of the **Calculated field** type to get the trimmed vendor account number.
1. Name the new nested field **$AccNumber**, and configure it so that it contains the expression `TRIM(Vendor.AccountNum)`.
1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page and verify that the `FILTER(Vendor, Vendor.AccountNum="US-101")` expression in the **Vendor** data source can be queried.

    :::image type="content" source="./media/er-components-inspections-04.gif" alt-text="Screenshot of verifying that the expression that has the FILTER function can be queried on the Model mapping designer page.":::

1. Notice that a validation error occurs, because the **Vendor** data source contains a nested field of the **Calculated field** type that doesn't allow the expression of the **FilteredVendor** data source to be translated to the direct SQL statement.

The following illustration shows the runtime error that occurs if you ignore the warning and select **Run** to run a format that is configured to use the model mapping.

:::image type="content" source="./media/er-components-inspections-04a.png" alt-text="Screenshot of runtime errors that occur when you run the editable format on the Format designer page.":::

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Instead of adding a nested field of the **Calculated field** type to the **Vendor** data source, add the **$AccNumber** nested field to the **FilteredVendor** data source, and configure it so that it contains the expression `TRIM(FilteredVendor.AccountNum)`. By using this approach, you can run the `FILTER(Vendor, Vendor.AccountNum="US-101")` expression at the SQL level and calculate the **$AccNumber** nested field afterward.

#### Option 2

Change the expression of the **FilteredVendor** data source from `FILTER(Vendor, Vendor.AccountNum="US-101")` to `WHERE(Vendor, Vendor.AccountNum="US-101")`. Don't change the expression for a table that has a large volume of data (transactional table), because this change fetches all records and selects the required records in memory. Therefore, this approach can cause poor performance. For more information, see [WHERE ER function](er-functions-list-where.md).

## <a id="i5"></a>Executability of a GROUPBY data source

The **GROUPBY** data source divides the query result into groups of records, usually to perform one or more aggregations on each group. You can configure every **GROUPBY** data source to run either at the database level or in memory. When you configure a **GROUPBY** data source to run at the database level, ER checks whether it can create a direct SQL query to a data source that the **GROUPBY** data source refers to. If ER can't create a direct query, the ER model mapping designer shows a validation error. The error message states that the configured **GROUPBY** data source can't run at runtime.

The following steps show how this issue might occur.

1. Start to configure the ER model mapping component.
1. Add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Trans**. In the **Table** field, select **VendTrans** to specify that this data source requests the VendTrans table.
1. Add a data source of the **Group by** type.
1. Name the new data source **GroupedTrans**, and configure it in the following way:

    - Select the **Trans** data source as the source of records that should be grouped.
    - In the **Execution location** field, select **Query** to specify that you want to run this data source at the database level.

    :::image type="content" source="./media/er-components-inspections-05a.gif" alt-text="Screenshot of configuring the data source on the Edit 'Group By' parameters page.":::

1. Select **Validate** to check the editable model mapping component on the **Model mapping designer** page and verify that the configured **GroupedTrans** data source can be queried.
1. Modify the **Trans** data source by adding a nested field of the **Calculated field** type to get the trimmed vendor account number.
1. Name the new data source **$AccNumber**, and configure it so that it contains the expression `TRIM(Trans.AccountNum)`.

    :::image type="content" source="./media/er-components-inspections-05a.png" alt-text="Screenshot of configuring the data source on the Model mapping designer page.":::

1. Select **Validate** to check the editable model mapping component on the **Model mapping designer** page and verify that the configured **GroupedTrans** data source can be queried.

    :::image type="content" source="./media/er-components-inspections-05b.png" alt-text="Screenshot of validating the ER model mapping component and verifying that the GroupedTrans data source can be queried on the Model mapping designer page.":::

1. Notice that a validation error occurs, because the **Trans** data source contains a nested field of the **Calculated field** type that doesn't allow the call for the **GroupedTrans** data source to be translated to the direct SQL statement.

The following illustration shows the runtime error that occurs if you ignore the warning and select **Run** to run a format that is configured to use the model mapping.

:::image type="content" source="./media/er-components-inspections-05c.png" alt-text="Screenshot of runtime errors that occur when the warning is ignored on the Format designer page.":::

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Instead of adding a nested field of the **Calculated field** type to the **Trans** data source, add the **$AccNumber** nested field for the **GroupedTrans.lines** item of the **GroupedTrans** data source, and configure it so that it contains the expression `TRIM(GroupedTrans.lines.AccountNum)`. In this way, you can run the **GroupedTrans** data source at the SQL level and calculate the **$AccNumber** nested field afterward.

#### Option 2

Change the value of the **Execution location** field for the **GroupedTrans** data source from **Query** to **In memory**. Don't change the value for a table that has a large volume of data (transactional table), because this change fetches all records and does grouping and aggregation in memory. Therefore, this approach can cause poor performance.

## <a id="i6"></a>Executability of a JOIN data source

The [JOIN](er-join-data-sources.md) data source combines records from two or more database tables, based on related fields. You can configure every **JOIN** data source to run either at the database level or in memory. When you configure a **JOIN** data source to run at the database level, ER checks whether it can create a direct SQL query to data sources that the data source refers to. If ER can't create a direct SQL query to at least one referenced data source, the ER model mapping designer shows a validation error. The error message states that the configured **JOIN** data source can't run at runtime.

The following steps show how this issue might occur.

1. Start to configure the ER model mapping component.
1. Add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Vendor**. In the **Table** field, select **VendTable** to specify that this data source requests the VendTable table.
1. Add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Trans**. In the **Table** field, select **VendTrans** to specify that this data source requests the VendTrans table.
1. Add a data source of the **Calculated field** type as the nested field of the **Vendor** data source.
1. Name the new data source **FilteredTrans**, and configure it so that it contains the expression `FILTER(Trans, Trans.AccountNum=Vendor.AccountNum)`.
1. Add a data source of the **Join** type.
1. Name the new data source **JoinedList**, and configure it in the following way:

    1. Add the **Vendor** data source as the first set of records to join.
    1. Add the **Vendor.FilteredTrans** data source as the second set of records to join. Select **INNER** as the type.
    1. In the **Execute** field, select **Query** to specify that you want to run this data source at the database level.

    :::image type="content" source="./media/er-components-inspections-06a.gif" alt-text="Screenshot of configuring the data source on the Join designer page.":::

1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page and verify that the configured **JoinedList** data source can be queried.
1. Change the expression of the **Vendor.FilteredTrans** data source from `FILTER(Trans, Trans.AccountNum=Vendor.AccountNum)` to `WHERE(Trans, Trans.AccountNum=Vendor.AccountNum)`.
1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page and verify that the configured **JoinedList** data source can be queried.

    :::image type="content" source="./media/er-components-inspections-06b.png" alt-text="Screenshot of validating the editable model mapping component and verifying that the JoinedList data source can be queried on the Model mapping designer page.":::

1. Notice that a validation error occurs, because the expression of the **Vendor.FilteredTrans** data source can't be translated to the direct SQL call. Additionally, the direct SQL call doesn't allow the call for the **JoinedList** data source to be translated to the direct SQL statement.

    :::image type="content" source="./media/er-components-inspections-06c.png" alt-text="Screenshot of runtime errors from the failed validation of the JoinedList data source on the Model mapping designer page.":::

The following illustration shows the runtime error that occurs if you ignore the warning and select **Run** to run a format that is configured to use the model mapping.

:::image type="content" source="./media/er-components-inspections-06e.png" alt-text="Screenshot of run the editable format on the Format designer page.":::

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Change the expression of the **Vendor.FilteredTrans** data source from `WHERE(Trans, Trans.AccountNum=Vendor.AccountNum)` back to `FILTER(Trans, Trans.AccountNum=Vendor.AccountNum)`, as the warning advises.

:::image type="content" source="./media/er-components-inspections-06d.png" alt-text="Screenshot of updated expression of data source on the Model mapping designer page.":::

#### Option 2

Change the value of the **Execute** field for the **JoinedList** data source from **Query** to **In memory**. Don't change the value for a table that has a large volume of data (transactional table), because this change fetches all records, and the join happens in memory. Therefore, this approach can cause poor performance. A validation warning informs you about this risk.

## <a id="i7"></a>Preferability of FILTER vs WHERE function

Use the built-in [FILTER](er-functions-list-filter.md) ER function to access application tables, views, or data entities. It places a single SQL call to get the required data as a list of records. The [WHERE](er-functions-list-where.md) function fetches all records from the given source and does record selection in memory. Both functions use a data source of the **Record list** type as an argument and specify a source for getting records. ER checks whether a direct SQL call can be established to a data source that you refer to in the **WHERE** function. If a direct call can be established, a validation warning occurs in the ER model mapping designer. The message that you receive recommends that you use the **FILTER** function instead of the **WHERE** function to help improve efficiency.

The following steps show how this issue might occur.

1. Start to configure the ER model mapping component.
1. Add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Trans**. In the **Table** field, select **VendTrans** to specify that this data source requests the VendTrans table.
1. Add a data source of the **Calculated field** type as the nested field of the **Vendor** data source.
1. Name the new data source **FilteredTrans**, and configure it so that it contains the expression `WHERE(Trans, Trans.AccountNum="US-101")`.
1. Add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Vendor**. In the **Table** field, select **VendTable** to specify that this data source requests the VendTable table.
1. Add a data source of the **Calculated field** type.
1. Name the new data source **FilteredVendor**, and configure it so that it contains the expression `WHERE(Vendor, Vendor.AccountNum="US-101")`.
1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page.

    :::image type="content" source="./media/er-components-inspections-07a.png" alt-text="Screenshot of inspect the editable model mapping component on the Model mapping designer page.":::

1. Notice that validation warnings recommend that you use the **FILTER** function instead of the **WHERE** function for the **FilteredVendor** and **FilteredTrans** data sources.

    :::image type="content" source="./media/er-components-inspections-07b.png" alt-text="Screenshot of recommendation to use the FILTER function instead of the WHERE function on the Model mapping designer page.":::

### Automatic resolution

Select **Fix** to automatically replace the **WHERE** function with the **FILTER** function in the expression of all data sources that appear in the grid on the **Warnings** tab for this type of inspection.

Alternatively, select the row for a single warning in the grid and then select **Fix selected**. In this case, the expression is automatically changed only in the data source that the selected warning mentions.

:::image type="content" source="./media/er-components-inspections-07c.png" alt-text="Screenshot of selecting Fix to automatically replace the WHERE function with the FILTER function on the Model mapping designer page.":::

### Manual resolution

Manually adjust the expressions of all the data sources in the validation grid by replacing the **WHERE** function with the **FILTER** function.

## <a id="i8"></a>Preferability of ALLITEMSQUERY vs ALLITEMS function

The built-in [ALLITEMS](er-functions-list-allitems.md) and [ALLITEMSQUERY](er-functions-list-allitemsquery.md) ER functions return a flattened **Record list** value that consists of a list of records that represent all items that match the specified path. ER checks whether it can establish a direct SQL call to a data source that the **ALLITEMS** function refers to. If ER can establish a direct call, a validation warning occurs in the ER model mapping designer. The message that you receive recommends that you use the **ALLITEMSQUERY** function instead of the **ALLITEMS** function to help improve efficiency.

The following steps show how this issue might occur.

1. Start to configure the ER model mapping component.
1. Add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Vendor**. In the **Table** field, select **VendTable** to specify that this data source requests the VendTable table.
1. Add a data source of the **Calculated field** type to get records for several vendors.
1. Name the new data source **FilteredVendor**, and configure it so that it contains the expression `FILTER(Vendor, OR(Vendor.AccountNum="US-101",Vendor.AccountNum="US-102"))`.
1. Add a data source of the **Calculated field** type to get the transactions of all filtered vendors.
1. Name the new data source **FilteredVendorTrans**, and configure it so that it contains the expression `ALLITEMS(FilteredVendor.'<Relations'.'VendTrans.VendTable_AccountNum')`.
1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page.

    :::image type="content" source="./media/er-components-inspections-08a.png" alt-text="Screenshot of inspecting the editable model mapping component on the Model mapping designer page.":::

1. Notice that a validation warning occurs. The message recommends that you use the **ALLITEMSQUERY** function instead of the **ALLITEMS** function for the **FilteredVendorTrans** data source.

    :::image type="content" source="./media/er-components-inspections-08b.png" alt-text="Screenshot of recommendation to use the ALLITEMSQUERY function instead of the ALLITEMS function on the Model mapping designer page.":::

### Automatic resolution

Select **Fix** to automatically replace the **ALLITEMS** function with the **ALLITEMSQUERY** function in the expression of all data sources that appear in the grid on the **Warnings** tab for this type of inspection.

Alternatively, select the row for a single warning in the grid and then select **Fix selected**. In this case, the expression is automatically changed only in the data source that the selected warning mentions.

:::image type="content" source="./media/er-components-inspections-08c.png" alt-text="Screenshot of selecting Fix selected on the Model mapping designer page.":::

### Manual resolution

To resolve the issue, manually adjust the expressions for all data sources mentioned in the validation grid. Replace the **ALLITEMS** function with the **ALLITEMSQUERY** function.

## <a id="i9"></a>Consider empty list cases

You can configure your ER format or model mapping component to get the field value of a data source of the **Record list** type. ER checks whether your design considers the case where a data source that you call contains no records (that is, it's empty). This check prevents runtime errors when a value is fetched from a field of a nonexistent record.

The following steps show how this issue might occur.

1. Start to configure the ER data model, the ER model mapping, and the ER format components simultaneously.
1. In the data model tree, add a root item that you name **Root3**.
1. Modify the **Root3** item by adding a nested item of the **Record list** type.
1. Name the new nested item **Vendor**.
1. Modify the **Vendor** item in the following way:

    - Add a nested field of the **String** type, and name it **Name**.
    - Add a nested field of the **String** type, and name it **AccountNumber**.

    :::image type="content" source="./media/er-components-inspections-09a.png" alt-text="Screenshot of adding nested fields on the Data model page.":::

1. In the model mapping designer, in the **Data sources** pane, add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Vendor**. In the **Table** field, select **VendTable** to specify that this data source requests the VendTable table.
1. Add a data source of the **General \\ User input parameter** type to search for a vendor account in the runtime dialog box.
1. Name the new data source **RequestedAccountNum**. In the **Label** field, enter **Vendor account number**. In the **Operations data type name** field, keep the default value, **Description**.
1. Add a data source of the **Calculated field** type to filter a vendor that the user inquires about.
1. Name the new data source **FilteredVendor**, and configure it so that it contains the expression `FILTER(Vendor, Vendor.AccountNum=RequestedAccountNum)`.
1. Bind the data model items to configured data sources in the following way:

    - Bind **FilteredVendor** to **Vendor**.
    - Bind **FilteredVendor.AccountNum** to **Vendor.AccountNumber**.
    - Bind **FilteredVendor.'name()'** to **Vendor.Name**.

    :::image type="content" source="./media/er-components-inspections-09b.png" alt-text="Screenshot of binding data model items on the Model mapping designer page.":::

1. In the format structure tree, add the following items to generate an outbound document in XML format that contains the vendor details:

    1. Add the **Statement** root XML element.
    1. For the **Statement** XML element, add the nested **Party** XML element.
    1. For the **Party** XML element, add the following nested XML attributes:

        - Name
        - AccountNum

1. Bind format elements to provided data sources in the following way:

    - Bind the **Statement\\Party\\Name** format element to the **model.Vendor.Name** data source field.
    - Bind the **Statement\\Party\\AccountNum** format element to the **model.Vendor.AccountNumber** data source field.

1. Select **Validate** to inspect the editable format component on the **Format designer** page.

    :::image type="content" source="./media/er-components-inspections-09c.png" alt-text="Screenshot of validating the format elements that you bound to data sources on the Format designer page.":::

1. Notice that a validation error occurs. The message states that an error might be thrown for the configured **Statement\\Party\\Name** and **Statement\\Party\\AccountNum** format components at runtime if the `model.Vendor` list is empty.

    :::image type="content" source="./media/er-components-inspections-09d.png" alt-text="Screenshot of validation error about a potential error for the configured format components.":::

The following illustration shows the runtime error that occurs if you ignore the warning, select **Run** to run the format, and select the account number of a nonexistent vendor. Because the requested vendor doesn't exist, the `model.Vendor` list is empty (that is, it contains no records).

:::image type="content" source="./media/er-components-inspections-09e.png" alt-text="Screenshot of runtime errors that occur during the format mapping run.":::

### Automatic resolution

For the selected row in the grid on the **Warnings** tab, select **Unbind**. This action automatically removes the binding from the format elements that the **Path** column points to.

### Manual resolution

#### Option 1

Bind the **Statement\\Party\\Name** format element to the `model.Vendor` data source item. At runtime, this binding calls the `model.Vendor` data source first. When `model.Vendor` returns an empty record list, the nested format elements don't run. Therefore, no validation warnings occur for this format configuration.

:::image type="content" source="./media/er-components-inspections-09e.gif" alt-text="Screenshot of binding the format element to the data source item on the Format designer page.":::

#### Option 2

Change the binding of the **Statement\\Party\\Name** format element from `model.Vendor.Name` to `FIRSTORNULL(model.Vendor).Name`. The updated binding conditionally converts the first record of the `model.Vendor` data source of the **Record list** type to a new data source of the **Record** type. This new data source contains the same set of fields.

- If at least one record is available in the `model.Vendor` data source, the fields of that record are filled with the values of the fields of the first record of the `model.Vendor` data source. In this case, the updated binding returns the vendor name.
- Otherwise, every field of the record that is created is filled with the default value for the data type of that field. In this case, the blank string is returned as the default value of the **String** data type.

Therefore, no validation warnings occur for the **Statement\\Party\\Name** format element when it's bound to the `FIRSTORNULL(model.Vendor).Name` expression.

:::image type="content" source="./media/er-components-inspections-09f.gif" alt-text="Screenshot of changed binding resolves validation warnings on the Format designer page.":::

#### Option 3

If you want to explicitly specify the data that's entered in a generated document when the `model.Vendor` data source of the **Record list** type returns no records (the text **Not available** in this example), change the binding of the **Statement\\Party\\Name** format element from `model.Vendor.Name` to `IF(NOT(ISEMPTY(model.Vendor)), model.Vendor.Name, "Not available")`. You can also use the expression `IF(COUNT(model.Vendor)=0, model.Vendor.Name, "Not available")`.

## <a id="i9a"></a>Additional consideration

The inspection also warns you about another potential problem. By default, when you bind the **Statement\\Party\\Name** and **Statement\\Party\\AccountNum** format elements to the appropriate fields of the `model.Vendor` data source of the **Record list** type, you run those bindings and take the values from the appropriate fields of the first record of the `model.Vendor` data source, if that list isn't empty.

If you don't bind the **Statement\\Party** format element with the `model.Vendor` data source, the **Statement\\Party** element doesn't iterate for every record of the `model.Vendor` data source during format execution. Instead, the generated document fills with information from only the first record of the record list, if that list contains multiple records. To fix this problem, bind the **Statement\\Party** element with the `model.Vendor` data source.

## <a id="i10"></a>Executability of an expression with FILTER function (caching)

To access application tables, views, or data entities, several built-in ER functions, including [FILTER](er-functions-list-filter.md) and [ALLITEMSQUERY](er-functions-list-allitemsquery.md), make a single SQL call to get the required data as a list of records. You use a data source of the **Record list** type as an argument for each of these functions to specify an application source for the call. ER checks whether it can establish a direct SQL call to a data source that you refer to in one of these functions. If ER can't establish a direct call because you marked the data source as [cached](trace-execution-er-troubleshoot-perf.md#improve-the-model-mapping-based-on-information-from-the-execution-trace), the ER model mapping designer shows a validation error. The message states that the ER expression that contains one of these functions can't run at runtime.

The following steps show how this issue might occur.

1. Start to configure the ER model mapping component.
1. Add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Vendor**. In the **Table** field, select **VendTable** to specify that this data source requests the VendTable table.
1. Add a data source of the **General \\ User input parameter** type to search for a vendor account in the runtime dialog box.
1. Name the new data source **RequestedAccountNum**. In the **Label** field, enter **Vendor account number**. In the **Operations data type name** field, keep the default value, **Description**.
1. Add a data source of the **Calculated field** type to filter a vendor that the user inquires about.
1. Name the new data source **FilteredVendor**, and configure it so that it contains the expression `FILTER(Vendor, Vendor.AccountNum=RequestedAccountNum)`.
1. Mark the configured **Vendor** data source as cached.

    :::image type="content" source="./media/er-components-inspections-10a.gif" alt-text="Screenshot of configuring the model mapping component on the Model mapping designer page.":::

1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page.

    :::image type="content" source="./media/er-components-inspections-10a.png" alt-text="Screenshot of validating the FILTER function that is applied to the cached Vendor data source on the Model mapping designer page.":::

1. Notice that a validation error occurs. The message states that the **FILTER** function can't be applied to the cached **Vendor** data source.

The following illustration shows the runtime error that occurs if you ignore the warning and select **Run** to run the format.

:::image type="content" source="./media/er-components-inspections-10b.png" alt-text="Screenshot of runtime error that occurs during the format mapping run on the Format designer page.":::

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Remove the **Cache** flag from the **Vendor** data source. The **FilteredVendor** data source then becomes executable, but the **Vendor** data source that the VendTable table refers to is accessed every time the **FilteredVendor** data source is called.

#### Option 2

Change the expression of the **FilteredVendor** data source from `FILTER(Vendor, Vendor.AccountNum="US-101")` to `WHERE(Vendor, Vendor.AccountNum="US-101")`. In this case, the **Vendor** data source that the VendTable table refers to is accessed only during the first call of the **Vendor** data source. However, the selection of records is done in memory. Therefore, this approach can cause poor performance.

## <a id="i11"></a>Missing binding

When you configure an ER format component, the base ER data model is the default data source for the ER format. When you run the configured ER format, the [default model mapping](er-country-dependent-model-mapping.md) for the base model fills the data model with application data. The ER format designer shows a warning if you bind a format element to a data model item that isn't bound to any data source in the model mapping currently selected as the default model mapping for the editable format. You can't run this type of binding at runtime, because the format that runs can't fill a bound element with application data. Therefore, an error occurs at runtime.

The following steps show how this issue might occur.

1. Start to configure the ER data model, the ER model mapping, and the ER format components simultaneously.
1. In the data model tree, add a root item that you name **Root3**.
1. Modify the **Root3** item by adding a new nested item of the **Record list** type.
1. Name the new nested item **Vendor**.
1. Modify the **Vendor** item in the following way:

    - Add a nested field of the **String** type, and name it **Name**.
    - Add a nested field of the **String** type, and name it **AccountNumber**.

    :::image type="content" source="./media/er-components-inspections-11a.png" alt-text="Screenshot of adding nested fields to the Vendor item on the Data model page.":::

1. In the model mapping designer, in the **Data sources** pane, add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Vendor**. In the **Table** field, select **VendTable** to specify that this data source requests the VendTable table.
1. Add a data source of the **General \\ User input parameter** type to inquire about a vendor account in the runtime dialog box.
1. Name the new data source **RequestedAccountNum**. In the **Label** field, enter **Vendor account number**. In the **Operations data type name** field, keep the default value, **Description**.
1. Add a data source of the **Calculated field** type to filter a vendor that the user inquires about.
1. Name the new data source **FilteredVendor**, and configure it so that it contains the expression `FILTER(Vendor, Vendor.AccountNum=RequestedAccountNum)`.
1. Bind the data model items to configured data sources in the following way:

    - Bind **FilteredVendor** to **Vendor**.
    - Bind **FilteredVendor.AccountNum** to **Vendor.AccountNumber**.

    > [!NOTE]
    > The **Vendor.Name** data model field remains unbound.

    :::image type="content" source="./media/er-components-inspections-11b.png" alt-text="Screenshot of data model items bound to configured data sources and a data mode item that remains unbound on the Model mapping designer page.":::

1. In the format structure tree, add the following items to generate an outbound document in XML format that contains the details of the vendors that the user inquires about:

    1. Add the **Statement** root XML element.
    1. For the **Statement** XML element, add the nested **Party** XML element.
    1. For the **Party** XML element, add the following nested XML attributes:

        - Name
        - AccountNum

1. Bind the format elements to provided data sources in the following way:

    - Bind the **Statement\\Party** format element to the `model.Vendor` data source item.
    - Bind the **Statement\\Party\\Name** format element to the **model.Vendor.Name** data source field.
    - Bind the **Statement\\Party\\AccountNum** format element to the **model.Vendor.AccountNumber** data source field.

1. Select **Validate** to inspect the editable format component on the **Format designer** page.

    :::image type="content" source="./media/er-components-inspections-11c.png" alt-text="Screenshot of validate the ER format component on the Format designer page.":::

1. Notice that a validation warning occurs. The message states that the **model.Vendor.Name** data source field isn't bound to any data source in the model mapping that you configured to be used by the format. Therefore, the **Statement\\Party\\Name** format element might not be filled at runtime, and a runtime exception might occur.

    :::image type="content" source="./media/er-components-inspections-11d.png" alt-text="Screenshot of validating the ER format component on the Format designer page.":::

The following illustration shows the runtime error that occurs if you ignore the warning and select **Run** to run the format.

![Running the editable format on the Format designer page.](./media/er-components-inspections-11e.png)

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Modify the configured model mapping by adding a binding for the **model.Vendor.Name** data source field.

#### Option 2

Modify the configured format by removing the binding for the **Statement\\Party\\Name** format element.

## <a id="i12"></a>Not linked template

When you [manually](er-fillable-excel.md#manual-entry) configure an ER format component to use a template to generate an outbound document, you must manually add the **Excel\\File** element, add the required template as an attachment of the editable component, and select that attachment in the added **Excel\\File** element. By using this process, you indicate that the added element fills the selected template at runtime. When you configure a format component version in **Draft** status, you can add several templates to the editable component and then select each template in the **Excel\\File** element to run the ER format. By using this process, you can see how different templates are filled at runtime. If you have templates that aren't selected in any **Excel\\File** elements, the ER format designer warns you that those templates are deleted from the editable ER format component version when its status changes from **Draft** to **Completed**.

The following steps show how this issue might occur.

1. Start to configure the ER format component.
1. In the format structure tree, add the **Excel\\File** element.
1. For the **Excel\\File** element that you just added, add an Excel workbook file, **A.xlsx**, as an attachment. Use the document type that is configured in the [ER parameters](electronic-reporting-er-configure-parameters.md#parameters-to-manage-documents) to specify the storage of ER format templates.
1. For the **Excel\\File** element, add another Excel workbook file, **B.xlsx**, as an attachment. Use the same document type that you used for workbook file A.
1. In the **Excel\\File** element, select workbook file A.
1. Select **Validate** to inspect the editable format component on the **Format designer** page.

    :::image type="content" source="./media/er-components-inspections-12a.gif" alt-text="Screenshot of validating the editable format component of the workbook file on the Format designer page.":::

1. Notice that a validation warning occurs. The message states that workbook file B.xlsx isn't linked to any components, and that it's removed after the status of the configuration version changes.

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

Modify the configured format by removing all templates that aren't linked to any **Excel\\File** element.

## <a id="i13"></a>Not synced format

When you [configure](er-fillable-excel.md) an ER format component to use an Excel template to generate an outbound document, you can manually add the **Excel\\File** element, add the required template as an attachment of the editable component, and select that attachment in the added **Excel\\File** element. In this way, you indicate that the added element fills the selected template at runtime. Because you designed the added Excel template externally, the editable ER format might contain Excel names that are missing from the added template. The ER format designer warns you about any inconsistencies between the properties of the ER format elements and the names that aren't included in the added Excel template.

The following steps show how this issue might occur.

1. Start to configure the ER format component.
1. In the format structure tree, add the **Excel\\File** element **Report**.
1. For the **Excel\\File** element that you just added, add an Excel workbook file, **A.xlsx**, as an attachment. Use the document type that is configured in the [ER parameters](electronic-reporting-er-configure-parameters.md#parameters-to-manage-documents) to specify the storage of ER format templates.

    > [!IMPORTANT]
    > Make sure that the added Excel workbook doesn't contain the name **ReportTitle**.

1. Add the **Excel\\Cell** element **Title** as a nested element of the **Report** element. In the **Excel range** field, enter **ReportTitle**.
1. Select **Validate** to inspect the editable format component on the **Format designer** page.

    :::image type="content" source="./media/er-components-inspections-13a.png" alt-text="Screenshot of validating the nested elements and fields on the Format designer page.":::

1. Notice that a validation warning occurs. The message states that the name **ReportTitle** doesn't exist on sheet **Sheet1** of the Excel template that you're using.

    :::image type="content" source="./media/er-components-inspections-13b.png" alt-text="Screenshot of validation warning that the name ReportTitle doesn't exist on Sheet1 of the Excel template.":::

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Modify the configured format by removing all elements that refer to Excel names that are missing from the template.

#### Option 2

[Update](er-fillable-excel.md#template-import) the editable ER format by importing an Excel template. The structure of the editable ER format is [synced](modify-electronic-reporting-format-reapply-excel-template.md) with the structure of the imported Excel template.

### Additional consideration

To learn how the format structure can be synced with an ER template in the template editor of [Business document management](er-business-document-management.md), see [Update the structure of a business document template](er-bdm-update-structure.md).

## <a id="i14"></a>Not synced with a Word template format

When you [configure](er-fillable-excel.md) an ER format component to use a Word template to generate an outbound document, you can manually add the **Excel\\File** element, add the required Word template as an attachment of the editable component, and select that attachment in the added **Excel\\File** element.

> [!NOTE]
> When the Word document is attached, the ER format designer presents the editable element as **Word\\File**.

In this way, you indicate that the added element fills the selected template at runtime. Because you externally design the added Word template, the editable ER format might contain references to Word content controls that are missing from the added template. The ER format designer warns you about any inconsistencies between the properties of the ER format elements and the content controls that aren't included in the added Word template.

For an example that shows how this issue might occur, see [Configure the editable format to suppress the summary section](er-design-configuration-word-suppress-controls.md#configure-to-suppress-control).

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Modify the configured format by deleting the **Removed** formula from the format element that the validation warning mentions.

#### Option 2

Modify the Word template by [adding](er-design-configuration-word-suppress-controls.md#tag-control) the required tag to the relevant Word content control.

## <a id="i15"></a>No default mapping

When the [Missing binding](#i11) inspection runs, it evaluates the inspected format bindings against the bindings of the relevant model mapping component. You can import [several](./tasks/er-manage-model-mapping-configurations-july-2017.md) ER model mapping configurations to your Finance instance, and each configuration might contain the applicable model mapping component. You must select one configuration as the default configuration. Otherwise, an exception occurs when you try to run, edit, or validate the inspected ER format. You receive the following message: "More than one model mapping exists for the \<model name (root descriptor)\> data model in the configurations \<configuration names separated by comma\>. Set one of the configurations as default."

For an example that shows how this issue might occur and how it can be fixed, see [Manage several derived mappings for a single model root](er-multiple-model-mappings.md).

## <a id="i16"></a>Inconsistent setting of Header or Footer components

When you [configure](er-fillable-excel.md) an ER format component to use an Excel template to generate an outbound document, you can add the **Excel\\Header** component to fill in headers at the top of a worksheet in an Excel workbook. You can also add the **Excel\\Footer** component to fill in footers at the bottom of a worksheet. For every **Excel\\Header** or **Excel\\Footer** component that you add, you must set the **Header/footer appearance** property to specify the pages that the component runs for. Because you can configure several **Excel\\Header** or **Excel\\Footer** components for a single **Sheet** component, and you can generate different headers or footers for different type of pages in an Excel worksheet, you must configure a single **Excel\\Header** or **Excel\\Footer** component for a specific value of the **Header/footer appearance** property. If you configure more than one **Excel\\Header** or **Excel\\Footer** component for a specific value of the **Header/footer appearance** property, a validation error occurs, and you receive the following error message: "Headers/footers (&lt;component type: Header or Footer&gt;) are inconsistent."

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Modify the configured format by deleting one of the inconsistent **Excel\\Header** or **Excel\\Footer** components.

#### Option 2

Modify the value of the **Header/footer appearance** property for one of the inconsistent **Excel\\Header** or **Excel\\Footer** components.

## <a id="i17"></a>Inconsistent setting of Page component

When you [configure](er-fillable-excel.md) an ER format component to use an Excel template to generate an outbound document, you can add the **Excel\\Page** component to paginate a generated document by using ER formulas. For every **Excel\\Page** component that you add, you can add many nested [Range](er-fillable-excel.md#range-component) components and still remain compliant with the following [structure](er-fillable-excel.md#page-component-structure):

- The first nested **Range** component can have the **Replication direction** property set to **No replication**. Use this range to make page headers in generated documents.
- You can add many other nested **Range** components where the **Replication direction** property is set to **Vertical**. Use these ranges to fill in generated documents.
- The last nested **Range** component can have the **Replication direction** property set to **No replication**. Use this range to make page footers in generated documents and to add the required page breaks.

If you don't follow this structure for an ER format in the ER format designer at design time, a validation error occurs, and you receive the following error message: "There are more than two range components without replication. Remove unnecessary components."

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Modify the configured format by changing the **Replication direction** property for all inconsistent **Excel\\Range** components.

## <a id="i18"></a>Executability of an expression with ORDERBY function

Use the built-in [ORDERBY](er-functions-list-orderby.md) ER function to sort the records of an ER data source of the **[Record list](er-formula-supported-data-types-composite.md#record-list)** type. You specify the data source as an argument of the function.

Specify arguments of the `ORDERBY` function to sort records of application tables, views, or data entities. By using this function, you make a single database call to get the sorted data as a list of records. Use a data source of the **Record list** type as an argument of the function to specify the application source for the call.

ER checks whether it can establish a direct database query to a data source that you refer to in the `ORDERBY` function. If ER can't establish a direct query, a validation error occurs in the ER model mapping designer. The message that you receive states that the ER expression that includes the `ORDERBY` function can't be run at runtime.

The following steps show how this issue might occur.

1. Start to configure the ER model mapping component.
1. Add a data source of the **Dynamics 365 for Operations \\ Table records** type.
1. Name the new data source **Vendor**. In the **Table** field, select **VendTable** to specify that this data source requests the **VendTable** table.
1. Add a data source of the **Calculated field** type.
1. Name the new data source **OrderedVendors**, and configure it so that it contains the expression `ORDERBY("Query", Vendor, Vendor.AccountNum)`.

    :::image type="content" source="./media/er-components-inspections-18-1.png" alt-text="Screenshot of configuring data sources on the Model mapping designer page.":::

1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page and verify that the expression in the **OrderedVendors** data source can be queried.
1. Modify the **Vendor** data source by adding a nested field of the **Calculated field** type to get the trimmed vendor account number.
1. Name the new nested field **$AccNumber**, and configure it so that it contains the expression `TRIM(Vendor.AccountNum)`.
1. Select **Validate** to inspect the editable model mapping component on the **Model mapping designer** page and verify that the expression in the **Vendor** data source can be queried.

    :::image type="content" source="./media/er-components-inspections-18-2.png" alt-text="Screenshot of verifying that the expression in the Vendor data source can be queried on the Model mapping designer page.":::

1. Notice that a validation error occurs, because the **Vendor** data source contains a nested field of the **Calculated field** type. This nested field doesn't allow the expression of the **OrderedVendors** data source to be translated to the direct database statement. The same error occurs at runtime if you ignore the validation error and select **Run** to run this model mapping.

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

#### Option 1

Instead of adding a nested field of the **Calculated field** type to the **Vendor** data source, add the **$AccNumber** nested field to the **FilteredVendors** data source, and configure the field so that it contains the expression `TRIM(FilteredVendor.AccountNum)`. By using this approach, you can run the `ORDERBY("Query", Vendor, Vendor.AccountNum)` expression at the database level, and you can calculate the **$AccNumber** nested field after.

#### Option 2

Change the expression of the **FilteredVendors** data source from `ORDERBY("Query", Vendor, Vendor.AccountNum)` to `ORDERBY("InMemory", Vendor, Vendor.AccountNum)`. Don't change the expression for a table that has a large volume of data (transactional table), because this change fetches all records and orders the required records in memory. Therefore, this approach can cause poor performance.

## <a id="i19"></a>Obsolete application artifact

When you design an ER model mapping component or an ER format component, you can configure an ER expression to call an application artifact in ER, such as a database table, a method of a class, and more. In Finance version 10.0.30 and later, you can configure ER to warn you when the referred application artifact is marked in source code as obsolete. This warning is useful because usually, obsolete artifacts are eventually removed from source code. Being informed about an artifact’s status can stop you from using the obsolete artifact in the editable ER component before its removal from the source code. This action helps prevent errors of calling non-existing application artifacts from an ER component at runtime.

To start evaluating the obsolete attribute of application artifacts during the inspection of an editable ER component, enable the **Validate obsolete elements of Electronic Reporting data sources** feature in the **Feature management** workspace. The obsolete attribute is currently evaluated for the following types of application artifacts:

- Database table
  - Field of a table
  - Method of a table
- Application class
  - Method of a class

> [!NOTE]
> A warning occurs during the inspection of the editable ER component for a data source that refers to an obsolete artifact only when this data source is used in at least one binding of this ER component.

> [!TIP]
> When the [SysObsoleteAttribute](../dev-ref/xpp-attribute-classes.md#sysobsoleteattribute) class is used to notify the compiler to issue warning messages instead of errors, the inspection warning presents the specified in source code warning at design time in the **Details** FastTab on the **Model mapping designer** or **Format designer** page.

The following illustration shows the validation warning that occurs when the obsolete `DEL_Email` field of the `CompanyInfo` application table is bound to a data model field by using the configured `company` data source.

:::image type="content" source="./media/er-components-inspections-19a.png" alt-text="Screenshot of review the validation warnings in the Details FastTab on the Model mapping designer page.":::

### Automatic resolution

No option to automatically fix this issue is available.

### Manual resolution

Modify the configured model mapping or format by removing all bindings to a data source that refers to an obsolete application artifact.

## Additional resources

[ALLITEMS ER function](er-functions-list-allitems.md)

[ALLITEMSQUERY ER function](er-functions-list-allitemsquery.md)

[INT64VALUE ER function](er-functions-conversion-int64value.md)

[INTVALUE ER function](er-functions-conversion-intvalue.md)

[FILTER ER function](er-functions-list-filter.md)

[WHERE ER function](er-functions-list-where.md)

[Use JOIN data sources to get data from multiple application tables in ER model mappings](er-join-data-sources.md)

[Trace the execution of ER formats to troubleshoot performance issues](trace-execution-er-troubleshoot-perf.md)

[Business document management overview](er-business-document-management.md)

- [Suppress Word content controls in generated reports](er-design-configuration-word-suppress-controls.md)

- [Manage several derived mappings for a single model root](er-multiple-model-mappings.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
