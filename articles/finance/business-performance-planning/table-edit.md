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

# Introduction & Purpose

## Overview

The Table Edit Visual is a powerful custom visual that enables direct dimension editing. This functionality offers a multitude of possibilities to modify and manage data directly within your financial planning Power BI reports. It enables:

-   Creating New Scenarios and Versions - allows creation of new forecasting scenarios or versions (e.g., "Forecast," "Version 3").
-   Updating Static Values - allows easy updates to fixed values like 401K match contributions (e.g., 5%).
-   Managing Planning Process Status - enables updates to the status of different planning stages (e.g., "In Review," "Approved").


## Benefits

-   **Enhanced Planning Workflow**

    Empowers users to establish a standardized and controlled workflow in the planning process, ensuring efficiency and consistency.

    -   **Streamlined Functionality**

        Enables diverse functionalities within a single visual tool, facilitating tasks like creating new dimension values or updating existing dimension values.

# Getting Started

## Prerequisites

1.  Import business performance planning visuals from AppSource. [Microsoft AppSource]([https://appsource.microsoft.com])  Learn more about importing visuals [Importing visuals](https://learn.microsoft.com/en-us/power-bi/developer/visuals/import-visual)
2.  Connect PowerBI to your Dataverse environment. [Connect to Dataverse using a Connector](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/data-platform-powerbi-connector?tabs=Dataverse#connect-to-dataverse-using-a-connector) or [Use DirectQuery in Power BI Desktop](https://learn.microsoft.com/en-us/power-bi/connect-data/desktop-use-directquery)


[!Tip]  
It is recommended to connect using **Direct Query**.  When using direct query, after the cube is selected, there is an option to **Load selected tables**.  Selecting this option will auto-select any dimension tables that are used in the cube.

## Installation Guide

1.  Open Power BI: Launch the Power BI application and access your desired workspace or report where you intend to configure the visual.
2.  Ensure that the visual has been downloaded from AppSource.  See Pre-requisite step 1 above.  
3.  Position the visual: Drag the visual to the report canvas.
4.  Add your **API Base URL** to the API Details window of the visual. This will provide business performance planning app the details it needs to read and write data from the Cube. To add the API details, select the **Format visual** tab in the report canvas.  The API base URL will be the Environment URL where planning has been installed.  The environment URL must be preceded by https://.  For example:  https://environment.d365.com.  Learn more [Find your environment and organization ID and name](https://learn.microsoft.com/en-us/power-platform/admin/determine-org-id-name)  Note:The visual must be selected in the report canvas for the Format visual tab to display.




# Using the Visual

## Functionality

**Editing Capabilities**

-   Provides an interface for direct editing of dimensions within Power BI. This enables users to add, modify, or delete rows in selected dimensions.
 
  [!Important] Any user with the **Update dimension data privilege** can edit dimension values.  The out of the box roles of **Administrator, Power User** and **Contributor** have this privilege by default.

**Scenario Creation and Management example**

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


