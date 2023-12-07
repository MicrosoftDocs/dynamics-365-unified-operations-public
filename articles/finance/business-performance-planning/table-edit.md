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
# Table edit

This article describes how to use the table edit visual in the Business performance planning application. You must also install Power BI visuals to fully use the planning application. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals/).

## Overview

The Table Edit Visual is a powerful feature within D365 Finance business performance planning Power BI that enables direct dimension editing. This functionality offers a multitude of possibilities to modify and manage data directly within your financial planning Power BI reports. It enables:

-   Creating New Scenarios and Versions - allows creation of new forecasting scenarios or versions (e.g., "Forecast," "Version 3").
-   Updating Static Values - allows easy updates to fixed values like 401K match contributions (e.g., 5%).
-   Managing Planning Process Status - enables updates to the status of different planning stages (e.g., "In Review," "Approved").
-   Modifying Drivers in Planning Solutions - Provides the ability to update drivers in driver-based planning solutions (e.g., "Units Sold").

## Benefits

-   **Enhanced Planning Workflow**

    Empowers users to establish a standardized and controlled workflow in the planning process, ensuring efficiency and consistency.

    -   **Streamlined Functionality**

        Enables diverse functionalities within a single visual tool, facilitating tasks like managing approval statuses and manipulating static business drivers directly in Power BI.

# Getting Started

## Prerequisites

1.  Import business performance planning visuals from AppSource. Learn More.
2.  Connect PowerBI to your Dataverse environment. Learn More.
3.  Understanding Allocation. Learn More.
4.  

## Installation Guide

1.  Open Power BI: Launch the Power BI application and access your desired workspace or report where you intend to configure the Matrix Planner.
2.  Position the visual: Drag the Matrix Planning visual to the report canvas.
3.  Add your **API Base URL** and optionally **Table name** to edit directly or leave it blank for dynamic selection within the Table Edit Visual, to the API Details window of the visual.

## Compatibility

Info on PBI versions where the visual is compatible.

# Using the Visual

## Functionality

**Editing Capabilities**

-   Provides an interface for direct editing of dimensions within Power BI.
    -   Enables users to add, modify, or delete rows in selected dimensions.

**Scenario Creation and Management**

-   Facilitates the addition of new scenarios within the scenario dimension.

    To create additional scenarios within the scenario dimension:

    -   Click on the ellipses icon at the top of the Table Edit Visual.
        -   Select Add a row.
        -   Input Forecast Upside and repeat to add Forecast Downside.
        -   Click the ellipses icon again and choose Save changes
        -   Allows users to create various scenarios for "what-if" analyses and exploration.
    -   Utilizing Created Scenarios

        The newly added scenarios (**Forecast Upside**, **Forecast Downside**) can be utilized for **what-if** **analyses** and exploration within D365 Finance business performance planning and Power BI. Examples include modeling sales forecasts based on various economic environments or creating different budget versions and approval statuses.

**Workflow Enhancement**

-   Empowers teams to explore diverse scenarios and plan strategies efficiently within Power BI and BPP.
    -   Facilitates the creation of different versions of forecasts, budgets, and approval statuses.

## Configuration Options

**Selecting Tables:**  
Choose the table from the dropdown menu at the top of the Table Editor to initiate configuration.

**Editing Modes:**  
It has three editing modes—Grid, Row, and Form. These can be selected via the visual properties in the Toolbar actions.

-   **Grid Mode**
    -   Allows immediate editing of any record on a page.
        -   Save changes via the button at the top-right of the visual.
-   **Row Mode**
    -   Enables editing of a specific row with buttons for saving changes or deleting the record.
-   **Form Mode**
    -   Displays records vertically upon clicking the edit button, showing more attributes at once.

**Adding New Records**  
Use the "plus" button in any editing mode to add new records.

**Bulk Edit**  
Select attributes, input values, and use bulk update to edit multiple records. Toggle this feature in the Power BI Format section of the visual.

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
Filter rows using the inverse triangle icon on columns to select filter elements.

**Ext Editor / Notes**  
Provides a Notes Column option for entering extensive formatted/unformatted text.

**Changing Column Width**  
Adjust column widths by dragging field separators. Save new widths using the **Save Settings** button.

**Visual Formatting / Toolbar**

-   **Toolbar Actions:**  
    Admins can specify available functions for users, such as batch update, filtering options, adding/editing/deleting records, and editing modes.
-   **Visual UI:**  
    Configure formatting options (e.g., font, background details, column types) for the visual.
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

-   **Date Format**

    Configure how dates are displayed in specific columns.

-   **Drill-Through**

    Enable drill-through to another report page using Power BI dataset fields.

-   **Inbound Filters**

    Set up inbound filters, supporting server-side and client-side filtering.

-   **Filter with Different Data Type**

    Improved filter options for integer, date, and date/time data types within the Table Editor visual. Adjust settings accordingly for effective filtering based on data types.
