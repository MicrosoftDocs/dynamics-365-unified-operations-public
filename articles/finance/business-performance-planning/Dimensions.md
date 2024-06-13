---
title: Business performance planning dimensions
description: Learn about dimensions and how they're used in Microsoft Dynamics 365 Finance business performance planning, including an outline on creating dimensions.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 06/04/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Business performance planning dimensions

This article describes dimensions and how they're used in Microsoft Dynamics 365 Finance business performance planning.

Dimensions are descriptors that define your fact data. A dimension consists of columns that are referred to as attributes of the dimension. These columns can be used to create hierarchical structures in your analysis. For example, a dimension might include columns for the date, the month, and the year. Users can then analyze data by drilling down from the year to the month to the date. Common dimensions are people, product, place, and time.

There are two types of dimensions in planning:

- **Linked dimensions** – Dimensions that are connected to Dataverse tables.
- **Standard dimensions** – Nondynamic dimensions that are manually updated either by adding new rows or by uploading new data from Excel.

## Create dimensions in business performance planning

In business performance planning, dimensions can be created in three ways:

- From the current environment (linked dimensions)
- From Excel
- Manually

### Create a dimension from the current environment

You can create a new dimension in business performance planning from an existing Dataverse table. This type of dimension is referred to as a linked dimension.

To create a linked dimension, follow these steps.

1. Go to **Create dimension**.
1. In the **Dimension** field, enter a name for the dimension. This name can contain spaces and special characters.
1. In the **Table** field, enter a name for the table that's created in Dataverse. This table name is shown in Power BI when you work with visuals.
1. Select to add columns from the current environment. (The current environment is the Microsoft Power Platform environment where you deployed business performance planning.) The **Linked table** list becomes available.

    > [!NOTE]
    > The list shows native Dataverse tables and enabled virtual entity tables. For more information about how to enable virtual entities, see [Enable Microsoft Dataverse virtual entities](../../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md).

1. Select the columns from the Dataverse table to include in the dimension. To select a column, select the circle that appears to the left of the column name when you hover over it.

    The selected columns appear in Power BI and can be used to sort and filter data in the planning visuals. Note that some columns are automatically removed. For example, you select the **Account** table for the dimension. That table includes multiple columns that you might want to filter or sort data on. However, it also includes columns that might not be as useful for your analysis of the data, such as **Created by** and **Modified by**. Therefore, these columns are automatically removed. 

    > [!IMPORTANT]
    > The dimension that you create must have a primary key to ensure that there are unique records in the dimension table. The business performance planning app automatically selects the primary column from the source table. The column that's used as the primary column is shown at the top of the page in the **Select columns** step of the wizard.

1. In the **Adjust columns** step of the wizard, you can update the column name for each column that you selected to include in the dimension. For example, you selected to include the **Address 1: City** column from the entity, but you want the name to appear as just **City**.

After you finish entering the information, you can create the dimension.

### Create a dimension from Excel

You can create a new dimension in business performance planning from an Excel file.

1. Go to **Create dimension**.
1. In the **Dimension** field, enter a name for the dimension. This name can contain spaces and special characters.
1. In the **Table** field, enter a name for the table that's created in Dataverse. This table name is shown in Power BI when you work with visuals.
1. Select to add columns from Excel. The **Upload an Excel** file option becomes available. If your workbook has multiple tabs, select the tab to use when the dimension is created.
1. Select the columns from the Excel file to include in the dimension. To select a column, select the circle that appears to the left of the column name when you hover over it.

    > [!IMPORTANT]
    > The dimension that you create must have a primary key to ensure that there are unique records in the dimension table. Therefore, select the column that will ensure unique records. The column that's used as the primary column is shown at the top of the page in the **Select columns** step of the wizard.

1. In the **Adjust columns** step of the wizard, you can update the column name for each column that you selected to include in the dimension. For example, you selected to include the **Address 1: City** column from the Excel workbook, but you want the name to appear as just **City**.

After you finish entering the information, you can create the dimension.

### Manually create a dimension 

You can manually create a new dimension in business performance planning.

1. Go to **Create dimension**.
1. In the **Dimension** field, enter a name for the dimension. This name can contain spaces and special characters.
1. In the **Table** field, enter a name for the table that's created in Dataverse. This table name is shown in Power BI when you work with visuals.
1. Enter the name of each column that you want to include in the dimension. Use commas to separate the column names.

    For this procedure, the **Select columns** step of the wizard is skipped, because the columns that you just specified are automatically included when the dimension is created.

    > [!IMPORTANT]
    > The dimension that you create must have a primary key to ensure that there are unique records in the dimension table. The business performance planning app automatically creates a **Name** column for manually created dimensions and uses that column as the primary column. The column that's used as the primary column is shown at the top of the page in the **Select columns** step of the wizard.

    For this procedure, the **Adjust columns** step of the wizard is also skipped, because the display name of each column is used when the dimension is created in the **General** section.

After you finish entering the information, you can create the dimension.

## Use dataflows to populate dimensions
Dimension data is a combination of multiple sources or must have some level of transformation done to get data into the proper structure for planning. It's recommended to use dataflows to load production data as this better supports typical production volume and complexity. Dataflows also provide a transform experience, detailed status results when loading data, and the option to schedule refreshes of the data.   

Dataflows are a self-service, cloud-based data preparation technology. Dataflows enable customers to ingest, transform, and load data into Microsoft Dataverse environments, Power BI workspaces, or your organization's Azure Data Lake Storage account. Dataflows are authored using Power Query, a unified data connectivity and preparation experience already featured in many Microsoft products, including Excel and Power BI. Dataflows can be triggered to run either on demand or automatically on a schedule and data is always kept up to date. For more information about dataflows, see [An overview of dataflows across Microsoft Power Platform and Dynamics 365](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365).

Dataflows can populate dimensions and cubes within planning. Linking a dataflow to the dimension or cube, when the data source of the dataflow is updated, planning is updated based on the refresh frequency defined in the dataflow.

For more information about loading data via dataflows, see [Loading data via dataflows](load-data-dataflows.md).


## Maintain dimensions

After you create a dimension, you might want to add more dimension values or add more columns to the dimension. You can make these changes in the business performance planning app, or by using the **Table Edit** visual in Power BI or the Excel add-in (available after GA). For more information about how to maintain dimensions in the **Table Edit** visual, see [link to doc]().

You can make the following changes to dimensions in the business performance planning app:

- Edit data in Excel.
- Add a new row of data.
- Delete a row of data.
- Add a new column of data.
- Delete a column of data.
- Add a linked column.
- Delete the dimension.

### Edit data in Excel

To add new rows of data to a dimension in the business performance planning app, follow these steps.

1. On the **Dimensions** page, select **Edit data in Excel**.
1. Open the workbook, and select **Enable editing**.

When you create a new row, you can add values for all columns in it except **Source Type** and any read-only fields. If data is entered in read-only fields, the fields are reset when the changes are published. Users can also edit specific cells of data in the dimension, except the **Source Type** value and the values of read-only fields.

After you add or edit data, you must publish your changes. If you close Excel before you publish, you're prompted to save your changes.

After you publish your changes from Excel, select **Refresh** on the dimension table to view the updates to the dimension.

> [!IMPORTANT]
> For every dimension, there's a **Source** column. The value can be either **User** or **System**. Rows that have a source type of **System** are updated with the values from the linked Dataverse table when a refresh is done. Rows that were created by using the **Table Edit** visual in Power BI have a source type of **User** and aren't overwritten by any data updates.

After you create a new row of data or edit a cell value, you must select **Refresh** to update your data in Power BI. Otherwise, you can't view the new dimension values, rows, or columns.

### Add a new row of data

To add new rows of data to a dimension, follow these steps.

1. On the **Dimension detail** page, select **New row**.
1. After you finish entering all the new rows of data, save your changes.
1. After you create a new row of data or edit a cell value, you must select **Refresh** to update your data in Power BI. Otherwise, you can't view the new dimension values, rows, or columns.

### Delete a row of data 

To delete a row of data from a dimension, follow these steps.

1. On the **Dimension detail** page, select **Delete row**.
2. When you're prompted, confirm the deletion of the row.

> [!NOTE]
> The dimension value can't be deleted if it's included in a cube.

### Add a new column of data

To add a new column of data to any dimension, follow these steps.

1. On the **Dimensions** page, select **New column**.
1. Enter a name for the column.

The new column is added as the last column in the dimension. If you add a new column to a linked dimension and fill the column with data, that data remains after you refresh the data. New columns that are added to a dimension are automatically saved.

### Delete a column of data

You can delete a column of data in a dimension. When a column of data in a dimension is deleted, the cube isn't updated. However, the Power BI visuals might be affected.

### Add a linked column

A linked column lets you create a restricted list of values that can be used when a new dimension value is created.

For example, you want to have a **Scenario** dimension that you can use to track your various scenarios, such as the **Budget 2025** scenario. You want the **Scenario** dimension to have the following attributes: **Scenario name**, **Scenario description**, and **Status**. For the **Status** attribute, you don't want users to be able to make up their own status values and assign them to the scenarios. Instead, you want users to select from a list of specific status values, such as **Not started**, **In review**, and **Approved**. Therefore, you create a **Scenario** dimension that contains the **Scenario name** and **Description** fields. You then create a secondary **Status** dimension that contains the **Status name** and **Status description** fields. After the **Status** dimension is created and populated with the statuses, you go back to the **Scenario** dimension and add a linked column that points to the **Status** dimension. Then, when you add new scenarios to the **Scenario** dimension, you select the status from a list of status values.

To add a linked column, follow these steps.

1. On the **Dimension detail** page, select **New linked column**.
1. In the **Target column** field, enter the name of the new column that's being added to the dimension. For the preceding example, enter **Status**.
1. In the **Source dimension** field, select the source dimension. For the preceding example, select the **Status** dimension.
1. In the **Source** field, select the source column. For the preceding example, select the **Status name** column.
1. Select **Add**.

### Delete the dimension

You can delete a dimension that isn't being used in a cube.

1. On **Dimensions** page, select the dimension in the left preview pane.
1. Select **Delete**.
