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
Table Edit

# Table edit visual

## Overview

The Table Edit Visual is a powerful custom visual that enables direct dimension editing. This functionality offers a multitude of possibilities to modify and manage data directly within your financial planning Power BI reports. It enables:

-   Creating New Scenarios and Versions - allows creation of new forecasting scenarios or versions (e.g., "Forecast," "Version 3").
-   Updating Static Values - allows easy updates to fixed values like 401K match contributions (e.g., 5%).
-   Managing Planning Process Status - enables updates to the status of different planning stages (e.g., "In Review," "Approved").



## Using the visual

**Editing Capabilities**

-   Provides an interface for direct editing of dimensions within Power BI. This enables users to add, modify, or delete rows in selected dimensions.
 
  [!Important] Any user with the **Update dimension data privilege** can edit dimension values.  The out of the box roles of **Administrator, Power User** and **Contributor** have this privilege by default.



**Example: Scenario creation**

-   Facilitates the addition of new scenarios within the scenario dimension.

    To create additional scenarios within the scenario dimension:

    -   Click on the down arrow at the top of the Table Edit Visual and select a dimensions.
        -   Select the **Scenario** dimension.
        -   Select the **Plus sign** (+) at the top of the form to add a row. 
        -   Input the **Name** of the new scenario.  For example, **Forecast Upside**.
        -   Enter a **Description**.
        -   Repeaat the same steps to add **Forecast Downside**.
        -   Click **Save** icon to save changes.
          
    -   Utilizing Created Scenarios

        The newly added scenarios (**Forecast Upside**, **Forecast Downside**) can be utilized for **what-if** **analyses** and exploration within D365 Finance business performance planning and Power BI. Examples include modeling sales forecasts based on various economic environments or creating different budget versions and approval statuses.


## Configuration Options

**Selecting Tables:**  
Choose the table from the dropdown menu at the top of the Table Editor to initiate configuration.

**Editing Modes:**  
It has three editing modes—Grid, Row, and Form. To update this setting, select the visual properties icon.  Expand the **Toolbar actions** and update the **Edit Mode** selection.   

-   **Grid Mode**
    -   Allows immediate editing of any record on a page.
        -   Save changes via the button at the top-right of the visual.
-   **Row Mode**
    -   Enables editing of a specific row with buttons for saving changes or deleting the record.  When in the row mode, the new dimension value must be saved before a new dimension value can be added.
-   **Form Mode**
    -   Upon selecting the **Edit** button, displays records vertically, showing more attributes at once.

**Adding New Records**  
Use the "plus" button in any editing mode to add new records.

**Bulk Edit**  
Select a column at the top of the visual.  Enter in a new or updated value.  Select Batch update.  All displayed rows will have the selected column values updated.   To update this setting, select the visual properties icon.  Expand the **Toolbar actions** and update the **Enable batch update** selection.   
**Grouping**

Right-click on column titles to group records with an expand/collapse option.

**Fix Column**  
Permanently fix a column on the grid with a right-click, ensuring it's always displayed irrespective of horizontal scrollbar movements.

**Data Validations**  
Automatically restrict entries in linked columns to available fields and apply data validations based on column types:

-   **Date Picker:**
    -   Automatically displays a date picker when the date format is set for the column.
        -   Set desired display formats via the visual properties.
-   **Boolean / Check Box**
    -   Shows a tick box for Boolean/Bit data columns, allowing users to set true or false.
-   **Number Column Types**
    -   Enforces data types, allowing only specific entries (e.g., integers for "integer" type).

**Column Filters / Search**  
Filter rows using the **inverse triangle** icon on columns to select filter elements.


**Changing Column Width**  
Adjust column widths by dragging field separators. Save new widths using the **Save Settings** button.

**Visual Formatting / Toolbar**

-   **Toolbar Actions:**  
    Admins can specify available functions for users, such as batch update, filtering options, adding/editing/deleting records, and editing modes.  To update any of these settings, select the visual properties icon and expand the **Visual UI** section.
 
-   **Enable Lookup Cascade**

    Specify filtering behavior for users using linked columns of a dimension.

-   **Hiding Columns**

    Hide columns by name or multiple columns using comma separation.

-   **Lock Column**

    Prevent users from changing a specific column on the visual level.

-   **Required Columns**

    Define columns as mandatory fields for editing records.

-   **URL Columns**

    Add link behavior to HTTP links.

-   **Image Column**

    Display images instead of links and configure image size.


