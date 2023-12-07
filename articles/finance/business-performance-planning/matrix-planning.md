---
# required metadata

title: Business performance planning application matrix planning visual
description: This article describes how to use the matrix planning visual in the Business performance planning application.
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
# Matrix planning visual
This article describes how to use the matrix planning visual in the Business performance planning application

## Overview

The Matrix Planning visual is a custom Power BI visual built to transform the planning experience, offering a seamless and powerful approach to planning processes such as managing forecasts and budgets. Unlike traditional methods involving data downloads, manual Excel-based budgeting, and intricate data consolidation, it streamlines these operations within your Power BI dashboard.

## Benefits

-   **Streamlined Planning Process**: The Matrix Planning visual eliminates the complexities of traditional methods by enabling users to directly input and manage forecasted values within the Power BI environment. This purpose-driven functionality streamlines the planning process, saving time and effort.
-   **Real-time Visualization and Decision-making:** Its purpose is to provide users with dynamic real-time visualizations of forecasted values. By overlaying forecast dimensions onto existing actual data, users can make agile, data-driven decisions across diverse business sectors.
-   **Enhanced Efficiency and Collaboration:** By bypassing manual planning cycles, the Matrix Planning visual significantly enhances efficiency. Its purpose is to foster collaborative decision-making by empowering teams to access and utilize real-time visualizations for informed, collective decisions.
-   **Seamless Integration and Accessibility:** The Matrix Planning visual seamlessly integrates with Power BI dashboards, becoming a critical D365 Finance business performance planning (BPP) visual. Its purpose is to ensure easy accessibility and usage within the familiar Power BI environment.
-   **Optimized Planning Experience:** The Matrix Planning visual will redefine your planning processes by empowering users to efficiently manage forecasts, visualize data instantly, and optimize decision-making, fostering a more efficient and data-centric planning experience.

    Matrix Planning visual’s purpose is to empower Power BI users with enhanced planning capabilities, real-time visualization, and collaborative decision-making, revolutionizing the way forecasts are managed and utilized within business contexts.

## Prerequisites

1.  Import business performance planning visuals from AppSource. [Microsoft AppSource]([https://appsource.microsoft.com])  Learn more about importing visuals [Importing visuals](/power-bi/developer/visuals/import-visual)
2.  Connect PowerBI to your Dataverse environment. [Connect to Dataverse using a Connector](/power-apps/maker/data-platform/data-platform-powerbi-connector?tabs=Dataverse#connect-to-dataverse-using-a-connector) or [Use DirectQuery in Power BI Desktop](/power-bi/connect-data/desktop-use-directquery)
3.  Understanding Data Model and Cube: The Matrix Planning visual writes back to the data model defined in the business performance planning app when creating the cube. This cube consolidates all dimensions at their intersections. To enable writing back to this data model, it's crucial to provide the primary keys of each dimension to the Matrix Planning visual during configuration.
4.  Understanding Allocation. **This needs to link to the Allocation topic**
  
[!Tip]  
It is recommended to connect using **Direct Query**.  When using direct query, after the cube is selected, there is an option to **Load selected tables**.  Selecting this option will auto-select any dimension tables that are used in the cube.


## Installation Guide

1.  Open Power BI: Launch the Power BI application and access your desired workspace or report where you intend to configure the Matrix Planner.
2.  Ensure that the Matrix visual has been downloaded from AppSource.  See Pre-requisite step 1 above.  
3.  Position the visual: Drag the Matrix Planning visual to the report canvas.
4.  Add your **API Base URL** and **Cube name** to the API Details window of the visual. This will provide business performance planning app the details it needs to read and write data from the Cube. To add the API details, select the **Format visual** tab in the report canvas.  The API base URL will be the Environment URL where planning has been installed.  The environment URL must be preceded by https://.  For example:  https://environment.d365.com.  Learn more [Find your environment and organization ID and name](/power-platform/admin/determine-org-id-name)  Note:The visual must be selected in the report canvas for the Format visual tab to display.
5.  Access Visualization Pane: Select the visual, locate the Visualization pane for the visual. Add all the "Name" columns from each dimension to the Rows, Columns, or Filters fields in the Visualization pane. These columns will provide the structure (X and Y axis) for your matrix. 
6.  Structuring the Matrix: Arrange the fields in the rows and columns of the matrix to define its visual structure. Fields placed in rows and columns define the matrix's axis. Any fields not utilized in these sections are used as filter context and should be added to the Filters field in the Visualization pane.
7.  Defining Matrix Shape: Determine the shape of the matrix table by placing values in the rows and columns. For dimensions intended solely as filter context (not part of the X or Y axis), add these to the Filters parameter in the Visualization pane.
8.  Setting Write-Back Coordinates: Providing these dimensions and variables allows the Matrix Planning visual to establish the "write-back coordinates" necessary for building planning and budgeting models effectively.
9.  Assigning Values Variable: Lastly, take the "Amount" column from your Cube and assign it to the Values variable in the Visualization pane. This step ensures the inclusion of specific data values within the Matrix Planning visual.
10.  Verify Configuration: Double-check the configuration setup in the Visualization pane to ensure all necessary fields, dimensions, and variables are correctly assigned and placed within the Rows, Columns, Filters, and Values sections.
11. Save and Apply Changes: Save the changes made to the configuration. Apply the settings to activate the Matrix Planning visual within your Power BI dashboard or report.

Note: Add All Dimensions to the Visual

It is recommended that an attribute from every dimension of the cube that you have specified in the visual settings is used in the visual (either in the row, column or filters section). Otherwise, the writeback will be applied on the "All" level to all dimensions not used in the visual which will result in writing excessive numbers of records into the database.

## Compatibility

Info on PBI versions where the visual is compatible.

## Using the Visual

## Functionality

### Entering Data

To enable data entry, click the "Edit" button on the top left. Once the edit mode is active (indicated by the green color of the edit button), you can simply type in the field or use the right-click context menu.  There is also a help menu in the upper right corner of the visual that supplies keyboard shortcuts for entering data.  This can be found under the '?' icon.

### Entering data on Aggregation cells

To enter data on an aggregation cell in the matrix planning visual, set the **Splashing at Parent** attribute in the visual properties in the **Grid UI** section to **On**.  (Navigate to Visual properties, expand the Grid UI section, and set 'Splashing at Parent Level' to On)

#### Prerequisite for entering/editing data on aggregations

-   The relevant hierarchy should be collapsed, and the children should not be visible

There are multiple Allocation Options available. Learn More.  **This needs a link to the allocations doc**

[!Important] 
A value entered on a base level (i.e., dimension coordinates that DO NOT contain aggregations) will only be saved if you press the "Save" button. Values entered on aggregations are immediately saved.

Changes from base-level entries are immediately visible in the Matrix. To see results of Allocation or effects on other elements of the report you have to refresh the report page with the standard Power BI function or press the "Refresh" Button in the Matrix visual when using the Power BI Service.

Due to limitations in Power BI Desktop, the "Refresh" button in the visual does NOT work in Power BI Desktop.

### Export To Excel

The **Export to Excel** button allows exporting a formatted report of the content displayed in the matrix visual to Excel.

### Copy and Paste

In **Edit** mode, copy cells from the clipboard using the right-click context menu. Choose **Paste** in the context menu or \<CTRL p\> in the dialog box to paste content into the matrix at the selected position.

### Entering/Editing Comments

You can directly enter comments by right-clicking on a base-level cell. Hovering over a cell in read mode displays entered comments on base levels and underlying levels on an aggregated level.

## Configuration options

### Grid Properties

In the Format pane in Power BI, set various design parameters like font size, colors, and layout.

#### Showing comment markers

Comments are stored in the TEXT_VAL of the cube. You can either use the cube that contains your values or store them in a separate comments cube. We recommend a separate comments cube if you want to store comments on a different granularity than your cube.

For comments in the same cube, you can activate the display of comment markers in the Matrix Planning visual. This requires having a column in your cube that returns a "1" if there is a comment for the record e.g.:

Comment Count = if(VW_GL[TEXT_VAL]\<\>BLANK(),1,0)

This comment count calculated column measure needs to be added to the Comment Count field in the visual.

Markers will be shown for the coordinates where the Comment Count is greater than 0.

#### Locking Measure/Value Columns For Entry

**Measure Un-editable** property enables you to prevent edits for specific value fields by specifying one or more columns where the first value starts with **0**. For example, if you want to prevent entry in the second value field you can set the property to **1**. If you want to prevent entry in the second and 3rd you set it to **1,2**.

#### Disable Entry on Empty Parents

**Allow entry on empty parent** property helps the admin user prevent users from entering data on empty, aggregated cells that can lead to a large number of unintentional write-back transactions.

#### Conditional formatting

**Conditional Formatting** section in the Power BI **Format pane** helps configure conditional formatting for background and font color for each value measure in the Matrix planning visual.

The definition of the conditional format criteria uses the **Val** variable. You can use any mathematical operation to set up conditional format as required e.g.:

-   Val \> 10; will apply the formatting set for the specific measure for all values greater than 10,
-   Val \>=0 or Val \<=0; will apply the format for all values in the measure, etc. You can use any operators. Learn More.

#### Custom totals

**Values Calculation** section in the Power BI "Format" pane lets you specify custom calculations other than the default aggregation.

##### Custom calculations

**Custom** option in the **Values Calculation** section allows you to define your own calculation that is applied to a "placeholder" value field or measure.

For example:

1.  Create a measure with a calculation and any definition e.g. "PY AC % = 1" in Power BI
2.  Drag that measure into the value field of the visual
3.  Go to the Power BI **Values Calculation** section of the Matrix Planning visual in the **Formatting** pane and choose **Custom.**
4.  Define calculation using any of the supported operators and the references **val1** to **valn**. Val1 to Valn refers to the respective value field in the visual e.g. the first field **amount** is referred to as **val1,** the second field **PY AC** is referred to as **val2** and so forth**.**

    For example, if you have added Amount, PY AC and the placeholder calculation PY AC % as **val1/val2** (val1 referring to "Amount" and val2 to "PY AC"); will calculate the relative percentage.

##### Supported Operators

| **Operator** | **Name**               | **Syntax** | **Associativity** | **Example**          | **Result**    |
|--------------|------------------------|------------|-------------------|----------------------|---------------|
| (, )         | Grouping               | (x)        | None              | 2 \* (3 + 4)         | 14            |
| [, ]         | Matrix, Index          | [...]      | None              | [[1,2],[3,4]]        | [[1,2],[3,4]] |
| {, }         | Object                 | {...}      | None              | {a: 1, b: 2}         | {a: 1, b: 2}  |
| ,            | Parameter separator    | x, y       | Left to right     | max(2, 1, 5)         | 5             |
| .            | Property accessor      | obj.prop   | Left to right     | obj={a: 12}; obj.a   | 12            |
| ;            | Statement separator    | x; y       | Left to right     | a=2; b=3; a\*b       | [6]           |
| ;            | Row separator          | [x; y]     | Left to right     | [1,2;3,4]            | [[1,2],[3,4]] |
| \\n          | Statement separator    | x \\n y    | Left to right     | a=2 \\n b=3 \\n a\*b | [2,3,6]       |
| +            | Add                    | x + y      | Left to right     | 4 + 5                | 9             |
| +            | Unary plus             | +y         | Right to left     | +4                   | 4             |
| -            | Subtract               | x - y      | Left to right     | 7 - 3                | 4             |
| -            | Unary minus            | -y         | Right to left     | -4                   | -4            |
| \*           | Multiply               | x \* y     | Left to right     | 2 \* 3               | 6             |
| .\*          | Element-wise multiply  | x.\* y     | Left to right     | [1,2,3] .\* [1,2,3]  | [1,4,9]       |
| /            | Divide                 | x / y      | Left to right     | 6 / 2                | 3             |
| ./           | Element-wise divide    | x ./ y     | Left to right     | [9,6,4] ./ [3,2,2]   | [3,3,2]       |
| %, mod       | Modulus                | x % y      | Left to right     | 8 % 3                | 2             |
| \^           | Power                  | x \^ y     | Right to left     | 2 \^ 3               | 8             |
| .\^          | Element-wise power     | x .\^ y    | Right to left     | [2,3] .\^ [3,3]      | [8,27]        |
| '            | Transpose              | y'         | Left to right     | [[1,2],[3,4]]'       | [[1,3],[2,4]] |
| !            | Factorial              | y!         | Left to right     | 5!                   | 120           |
| &            | Bitwise and            | x & y      | Left to right     | 5 & 3                | 1             |
| \~           | Bitwise not            | \~x        | Right to left     | \~2                  | -3            |
| \|           | Bitwise or             | x \| y     | Left to right     | 5 \| 3               | 7             |
| \^\|         | Bitwise xor            | x \^\| y   | Left to right     | 5 \^\| 2             | 7             |
| \<\<         | Left shift             | x \<\< y   | Left to right     | 4 \<\< 1             | 8             |
| \>\>         | Right arithmetic shift | x \>\> y   | Left to right     | 8 \>\> 1             | 4             |
| \>\>\>       | Right logical shift    | x \>\>\> y | Left to right     | -8 \>\>\> 1          | 2147483644    |
| and          | Logical and            | x and y    | Left to right     | true and false       | false         |
| not          | Logical not            | not y      | Right to left     | not true             | false         |
| or           | Logical or             | x or y     | Left to right     | true or false        | true          |
| xor          | Logical xor            | x xor y    | Left to right     | true xor true        | false         |
| =            | Assignment             | x = y      | Right to left     | a = 5                | 5             |
| ? :          | Conditional expression | x ? y : z  | Right to left     | 15 \> 100 ? 1 : -1   | -1            |
| :            | Range                  | x : y      | Right to left     | 1:4                  | [1,2,3,4]     |
| to, in       | Unit conversion        | x to y     | Left to right     | 2 inch to cm         | 5.08 cm       |
| ==           | Equal                  | x == y     | Left to right     | 2 == 4 - 2           | true          |
| !=           | Unequal                | x != y     | Left to right     | 2 != 3               | true          |
| \<           | Smaller                | x \< y     | Left to right     | 2 \< 3               | true          |
| \>           | Larger                 | x \> y     | Left to right     | 2 \> 3               | false         |
| \<=          | Smallereq              | x \<= y    | Left to right     | 4 \<= 3              | false         |
| \>=          | Largereq               | x \>= y    | Left to right     | 2 + 4 \>= 6          | true          |

If statements are also supported. The syntax looks like below:

val2 != 0 ? val1 / val2 : null

Here:

**! =** is the not equal operator.

**?** is the "if”.

**:** is "then" operator

### Column Measure Override / Edit Column Meta Data

In scenarios where you need to write back on different measures that are not part of a measure dimension, you can set the coordinates for the column that should be used when a value is written back on that column.

-   Click **Edit** menu on the top right of the visual
-   Click on the measure where you want to apply to override metadata. Now you can set the dimension coordinates that should be used when a value is written on that column
-   Apply the changes with the “Sync Settings” button

Note: It is easier to add a simple DAX measure e.g. [Units]=0 apply the measure format as per normal Power BI functionality and use that as the placeholder for the column override.

### Multi-Select Mode

This enables you to edit multiple cells at the same time.

-   Either write the same value to every selected cell. Turn it on by pressing the **Multiselect** button located to the right of the **Edit** button.
-   or distribute (**Allocation**) the value across the selected cells according to their current distribution. To use this mode, use the **s** prefix. For example, s15000 will distribute 15000 across the three selected cells. On the right side of the **Save** button, you can see the total value of the selected cells.

### Subtotals formatting

It is possible to have different formats for each level of subtotal rows in the Matrix planning visual.

-   One level subtotal
-   Two level subtotals

#### DAX-based subtotal

It is possible to use DAX measures for rollups and subtotals.

Note: subtotal format for the lowest level of the hierarchy cannot be changed.

### Grand total conditional formatting

Using a Grid UI setting, you can change the background color of the grand total column.

Default green color that has been set for the columns from the Grid UI option, you can use the **GT Conditional Formatting** option and set a new format.

*Amount GT Format Formula*

-   Val = Val; Use this formula to set the new format for all the grand total rows.
-   Val \< Val; Set the format for a specific range of values.
-   Val \> Val; Set the format for a specific range of values.

*Amount Suffix icon*

It allows you to put an ASCII or HTML code.

*Amount GT format formula Priority level*

It is important to know that the priority of the Amount GT Format Formula 1 is higher than others.

-   Same Formulas - In this example, two formulas are the same but only the first one has been applied
-   Different Formulas - In this example, two different formulas have been applied for the amount.
-   Three Formulas Added - In this example, three formulas have been added.

### Undo

You can undo data entry changes before clicking on the save button by right clicking on the respective cell and choosing the undo option that shows the previous value at the top of the context menu

Dynamic Locking

You can dynamically lock editing cells that fulfill a specific condition. In the **Editing Lock** section of the **visual properties**, you can set the condition for the respective measure where you want to apply the lock. The condition is using the **val** variable that work in the same way as in the **Conditional Formatting** and **Edit Validation** sections.

In the example below we specify that if the value in the second measure is greater than 0 editing should be locked.

Edit Validation

You can define validation rules that apply to a measure in the matrix. The rules support the same operators syntax (**val** variable) as **Conditional Formatting** and **Edit Lock**. In addition, you can use Math js Functions ([math.js \| an extensive math library for JavaScript and Node.js (mathjs.org)](https://mathjs.org/docs/reference/functions.html)).
