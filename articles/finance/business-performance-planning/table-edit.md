---
title: Table edit visual
description: Learn how to use the Table edit visual in the Business performance planning application, including an example and an outline on configuration settings.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 12/07/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Table edit visual

This article describes how to use the **Table edit** visual in the Business performance planning application. To fully use this application, you must install Microsoft Power BI visuals. For information about how to install Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

The **Table edit** visual in the Business performance planning application is a powerful custom visual that lets you directly edit dimensions. This functionality gives you many possibilities for modifying and managing data directly on your financial planning Power BI reports:

- Create new forecasting scenarios or versions.
- Easily update static (fixed) values, such as 401(K) match contributions.
- Update the status of the different stages in the planning process.

## Use the Table edit visual

The **Table edit** visual provides an interface for direct edits to dimensions in Power BI. This interface lets users add, modify, or delete rows in selected dimensions.
 
> [!IMPORTANT]
> Any user who has the **Update dimension data** privilege can edit dimension values. The out-of-box **Administrator**, **Power user**, and **Contributor** roles include this privilege.

### Example

This example show how the **Table edit** visual facilitates the addition of new scenarios in the scenario dimension.

To add scenarios in the scenario dimension, follow these steps.

1. In the dropdown list at the top of the **Table edit** visual, select a dimension. For this example, select the **Scenario** dimension.
2. At the top of the page, select **(+)** to add a row.
3. In the **Name** field, enter a name for the new scenario.
4. In the **Description** field, enter a description.
5. Repeat steps 2 through 4 to add the **Forecast downside** scenario.
6. Select **Save**.

The newly added scenarios can be used for what-if analysis and exploration in Dynamics 365 Finance business performance planning and Power BI.
Here are some examples of possible uses:

- Model sales forecasts based on different economic environments.
- Create different budget versions and approval statuses.

### Configuration options

To initiate configuration, select a table on the dropdown menu at the top of the **Table edit** visual.

- **Editing modes** – To update the editing mode, select the visual properties button, expand the **Toolbar actions** section, and then update the **Edit mode** value. There are three editing modes:

    - **Grid** – You can immediately edit any record on a page. Save your changes by using the button in the upper right of the visual.
    - **Row** – You can edit a specific row. Buttons are provided so that you can save your changes or delete the record. In **Row** mode, you must save the new dimension value before you can add a new dimension value.
    - **Form** – After you select the **Edit** button, records are shown vertically, and more attributes immediately appear.

- **Add a new record** – In any editing mode, select the plus sign (**+**) to add new records.
- **Bulk edit** – Select a column, enter a new or updated value, and then select **Batch update**. The values in the selected column are updated for all rows that are shown. To update this setting, select the visual properties button, expand the **Toolbar actions** section, and then update the **Enable batch update** selection.
- **Grouping** – Select and hold (or right-click) column titles to group records. An expand/collapse option is available for the grouped records.
- **Fix column** – To ensure that a column is always visible in the grid, regardless of horizontal scrollbar movements, select and hold (or right-click).
- **Validate data** – Automatically restrict the entries in linked columns to available fields, and apply data validations based on column types.
- **Date picker** – Automatically show a date picker when the date format is set for the column.
- **Boolean/checkbox** – Show a checkbox for Boolean/bit data columns, so that users can set a true or false value.
- **Number column types** – Enforce data types, so that only specific entries are allowed.
- **Column filters and search** – Filter rows by selecting the down arrow on columns and then selecting filter elements.
- **Changing column width** – Adjust column widths by dragging field separators. To save the new widths, select **Save settings**.
- **Visual formatting and toolbar** – Admins can specify available functions for users, such as batch update, filtering options, adding/editing/deleting records, and editing modes. To update any of these settings, select the visual properties button, and expand the **Visual UI** section.
- **Enable lookup cascade** – Specify filtering behavior for users by using the linked columns of a dimension.
- **Hide columns** – Hide columns by name. To hide multiple columns, use commas to separate the names.
- **Lock column edit** – Prevent users from changing a specific column at the visual level.
- **Required columns** – Define columns as mandatory fields when records are edited.
- **URL columns** – Add link behavior to HTTP links.
- **Image column** – Show images instead of links, and configure the image size.
- **Note column** – Enter the names of the columns that you want to add notes to.

> [!IMPORTANT]
> When you reference the name of any column in the preceding settings, you must use the technical name of the column (for example, **msdyn\_description**). You can find the technical name in the **Data** column of Power BI.
