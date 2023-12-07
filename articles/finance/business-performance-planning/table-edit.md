---
# required metadata

title: Business performance planning application table edit visual
description: This article describes how to use the table edit visual in the Business performance planning application in Microsoft Dynamics 365 Finance.
author: ShielaSogge
ms.date: 12/07/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2023-12-03
ms.dyn365.ops.version: 

---
# Table edit visual

The table edit visual is a powerful custom visual that enables direct dimension editing. This functionality offers a multitude of possibilities to modify and manage data directly within your financial planning Power BI reports. It enables:
 - Creating new scenarios and versions - allows creation of new forecasting scenarios or versions.
 - Updating static values - allows easy updates to fixed values like 401K match contributions.
 - Managing planning process status - updates the status of different planning stages.


You must install Power BI visuals to fully use the planning application. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

## Using the visual

The table edit visual provides an interface for direct editing of dimensions within Power BI. This enables users to add, modify, or delete rows in selected dimensions.
 
>[!Important]
> Any user with the **Update dimension data** privilege can edit dimension values. The out of the box roles of **Administrator, Power user** and **Contributor** include this privilege.

### Example 

The table edit visual facilitates the addition of new scenarios within the scenario dimension.

To create additional scenarios within the scenario dimension, follow these steps:
1. Click on the down arrow at the top of the Table edit visual and select a dimension.
2. Select the **Scenario** dimension.
3. Select **(+)** at the top of the page to add a row.
4. In the **Name** field, enter the name of the new scenario.
5. Enter a **Description**. Repeaat the same steps to add **Forecast downside**.
6. Click **Save**.


### Use the created scenario

The newly added scenarios can be utilized for what-if analyses and exploration within Dynamics 365 Finance business performance planning and Power BI. 
Examples include:
 - modeling sales forecasts based on various economic environments
 - creating different budget versions and approval statuses


### Configuration options

 - Select tables - Choose the table from the dropdown menu at the top of the Table Editor to initiate configuration.
 - Editing modes - To update the editing setting, select the visual properties icon. Expand the **Toolbar actions**, update **Edit mode**.   
There are three editing modes:    
 - **Grid** - Allows immediate editing of any record on a page. You can save changes using the button at the top-right of the visual.
 - **Row** - Enables editing of a specific row with buttons for saving changes or deleting the record. When in **Row** mode, the new dimension value must be saved before a new dimension value can be added.
 - **Form** - After selecting the **Edit** button, records are displayed vertically and show more attributes at once.

 - Add a new record - Click **+** button in any editing mode to add new records.
 - Bulk edit - Select a column, enter in a new or updated value. Select **Batch update**. All displayed rows will have the selected column values updated. To update this setting, select the visual properties icon and expand the **Toolbar actions**. Update the **Enable batch update** selection.   
 - Grouping - Right-click on column titles to group records with an expand/collapse option.
 - Fix column - Permanently fix a column on the grid with a right-click, ensuring it's always displayed irrespective of horizontal scrollbar movements.
 - Validate data - Automatically restrict entries in linked columns to available fields and apply data validations based on column types.
 - Date picker - Automatically displays a date picker when the date format is set for the column.
 - Boolean/checkbox - Shows a checkbox for Boolean/Bit data columns, allowing users to set true or false.
 - Number column types - Enforces data types, allowing only specific entries.
 - Column filters and search - Filter rows using the inverse triangle icon on columns to select filter elements.
 - Changing column width - Adjust column widths by dragging field separators. Save new widths using **Save settings**.
 - Visual formatting and toolbar - Admins can specify available functions for users, such as batch update, filtering options, adding/editing/deleting records, and editing modes. To update any of these settings, select the visual properties icon and expand the **Visual UI** section.
 - Enable lookup cascade - Specify filtering behavior for users using linked columns of a dimension.
 - Hide columns - Hide columns by name or multiple columns using comma separation.
 - Lock column edit - Prevents users from changing a specific column on the visual level.
 - Required columns - Define columns as mandatory fields for editing records.
 - URL columns - Add link behavior to HTTP links.
 - Image column - Display images instead of links and configure image size.
 - Note column - Enter the column names of the columns that you want to add notes to.

>[!Important]
> When referencing any of the column names in the settings listed above, the name of the column must be the technical name. For example: msdyn_description. You can find this in the **Data** column of Power BI.

