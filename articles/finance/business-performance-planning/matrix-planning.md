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
This article describes how to use the matrix planning visual in the business performance planning application.

## Overview

The matrix planning visual is a custom Power BI visual built to transform the planning experience, offering a seamless and powerful approach to planning processes such as managing forecasts and budgets. Unlike traditional methods involving data downloads, manual Excel-based budgeting, and intricate data consolidation, it streamlines operations within your Power BI dashboard.

### Benefits

 - Streamlined planning process - The matrix planning visual eliminates the complexities of traditional methods by enabling users to directly input and manage forecasted values within the Power BI environment. This purpose-driven functionality streamlines the planning process, saving time and effort.
 - Real-time visualization and decision making - Provides users with dynamic real-time visualizations of forecasted values. By overlaying forecast dimensions onto existing actual data, users can make agile, data-driven decisions across diverse business sectors.
 - Enhanced efficiency and collaboration - The matrix planning visual significantly enhances efficiency, fostering collaborative decision-making by empowering teams to access and utilize real-time visualizations for informed, collective decisions.
 - Seamless integration and accessibility - This visual seamlessly integrates with Power BI dashboards, becoming a critical Dynamics 365 finance business performance planning visual. Its purpose is to ensure easy accessibility and usage within the familiar Power BI environment.
 - Optimized planning experience - Redefine your planning processes by empowering users to efficiently manage forecasts, visualize data instantly, and optimize decision-making, fostering a more efficient and data-centric planning experience.


### Prerequisites

1.  Import business performance planning visuals from AppSource. [Microsoft AppSource]([https://appsource.microsoft.com]). To learn more about importing visuals, see [Importing visuals](/power-bi/developer/visuals/import-visual).
2.  Connect PowerBI to your Dataverse environment. For more information see, [Connect to Dataverse using a Connector](/power-apps/maker/data-platform/data-platform-powerbi-connector?tabs=Dataverse#connect-to-dataverse-using-a-connector) or [Use DirectQuery in Power BI Desktop](/power-bi/connect-data/desktop-use-directquery).
3.  Understanding data model and cube - The matrix planning visual writes back to the data model defined in the business performance planning app when creating the cube. This cube consolidates all dimensions at their intersections. To enable writing back to this data model, it's crucial to provide the primary keys of each dimension to the matrix planning visual during configuration.
4.  Understanding allocation. For more information, see [Allocation](allocation.md). 
  
>[!Tip]
>It's recommended to connect using direct query. When using direct query, after the cube is selected, there's a **Load selected tables** option. Select this option automatically selects dimension tables that are used in the cube.


### Installation Guide

1.  Open Power BI: Launch the Power BI application and access your desired workspace or report where you intend to configure the Matrix Planner.
2.  Confirm that the matrix visual has been downloaded from AppSource. See prerequisite step 1 above.  
3.  Position the visual - Drag the matrix planning visual to the report canvas.
4.  Add your API base URL and cube name to the API Details window of the visual. This provides the business performance planning app the details it needs to read and write data from the Cube.
5.  To add API details, select the **Format visual** tab in the report canvas. The API base URL is the environment URL where planning has been installed. The environment URL must be preceded by https://. For example: https://environment.d365.com. For more information, see [Find your environment and organization ID and name](/power-platform/admin/determine-org-id-name).

>[!Note]
>The visual must be selected in the report canvas for the **Format visual** tab to display.

6.  Access visualization pane - Select and locate the visualization pane for the visual. Enter names for the rows, columns, and filters fields in the visualization pane. These columns provides the structure (X and Y axis) for your matrix. 
7.  Structure the matrix - Arrange the fields in the rows and columns of the matrix to define its visual structure. Fields placed in rows and columns define the matrix's axis. Any fields not utilized in these sections are used as filter context and should be added to the **Filters** field in the visualization pane.
8.  Define the matrix shape - Determine the shape of the matrix table by placing values in the rows and columns. For dimensions intended solely as filter context (not part of the X or Y axis), add these to the **Filters** parameter in the visualization pane.
9. Set the write back coordinates - Provide dimensions and variables to allow the matrix planning visual to establish write back coordinates necessary for building planning and budgeting models effectively.
10. Assign values variable - Assign the **Amount** column from your cube to the values variable in the visualization pane. This step ensures the inclusion of specific data values within the matrix planning visual.
11. Verify the configuration - Confirm the configuration setup in the visualization pane to ensure all necessary fields, dimensions, and variables are correctly assigned and placed within the rows, columns, filters, and values sections.
12. Save and apply changes - Save the changes made to the configuration. Apply the settings will activate the matrix planning visual within your Power BI dashboard or report.

>[!Note]
>Add all dimensions to the visual.

It's recommended that an attribute from every dimension of the cube that you have specified in the visual settings is used in the visual (either in the row, column or filters section). Otherwise, the write back will be applied on the "All" level to all dimensions not used in the visual. This will result in writing excessive numbers of records into the database.


### Entering data

To enable data entry, click **Edit** button on the top left. After the edit mode is active (indicated by the green color of the edit button), type in the field or use the right-click context menu.

#### Aggregation cells

To enter data on an aggregation cell in the matrix planning visual, set **Splashing at parent** attribute in the visual properties in the grid UI section to **On**. Go to visual properties, expand the **Grid UI** section. Set **Splashing at parent level** to **On**.

#### Prerequisites for entering or editing data on aggregations

The relevant hierarchy should be collapsed, and the children should not be visible. There are multiple allocation pptions available. For more information, see [Allocations](allocation.md).

>[!Important]
>A value entered on a base level, dimension coordinates that don't contain aggregations, will be saved after you press **Save**. Values entered on aggregations are immediately saved.

Changes from base-level entries are immediately visible in the matrix. To see results of allocation or effects on other elements of the report, refresh the report page with the standard Power BI function or press **Refresh** in the matrix visual when using the Power BI service.

Due to limitations in Power BI Desktop, **Refresh** in the visual doesn't work in Power BI Desktop.

### Export To Excel

**Export to Excel** exports a formatted report of the content displayed in the matrix visual to Excel.

### Copy and paste

In **Edit** mode, copy cells from the clipboard using right-click. Choose **Paste** or CTRL p in the dialog box to paste content into the matrix at the selected position.

### Entering or editing comments

You can directly enter comments by right-clicking on a base-level cell. Hovering over a cell in read mode displays entered comments on base levels and underlying levels on an aggregated level.

#### Configuration options

 - Grid properties - In the format pane in Power BI, set various design parameters like font size, colors, and layout.
 - Show comment markers - Comments are stored in the TEXT_VAL of the cube. You can either use the cube that contains your values or store them in a separate comments cube. We recommend a separate comments cube if you want to store comments on a different granularity than your cube. For comments in the same cube, you can display of comment markers in the matrix planning visual. This requires to have a column in your cube that returns a "1" if there is a comment for the record, for example: 
Comment Count = if(VW_GL[TEXT_VAL]\<\>BLANK(),1,0)
This comment count calculated column measure needs to be added to the **Comment count** field in the visual. Markers will be shown for the coordinates where the Comment count is greater than 0.
 - Lock measure or value columns for entry - **Measure uneditable** property prevents edits for specific value fields by specifying one or more columns where the first value starts with **0**. For example, if you want to prevent entry in the second value field you can set the property to **1**. If you want to prevent entry in the second and 3rd you set it to **1,2**.
 - Disable entry on empty parents - **Allow entry on empty parent** property prevents users from entering data on empty, aggregated cells that can lead to a large number of unintentional write-back transactions.

#### Conditional formatting

The Conditional formatting section in the Power BI **Format pane** configures conditional formatting for background and font color for each value measure in the Matrix planning visual.
The definition of the conditional format criteria uses the **Val** variable. You can use any mathematical operation to set up conditional format as required:
-   Val \> 10; will apply the formatting set for the specific measure for all values greater than 10,
-   Val \>=0 or Val \<=0; will apply the format for all values in the measure, etc. You can use any operators. Learn More.


#### Custom totals

**Values calculation** section in the Power BI format pane specifies custom calculations other than the default aggregation.

#### Custom calculations

**Custom** option in the **Values calculation** section allows you to define your own calculation that is applied to a placeholder value field or measure.

For example:

1.  Create a measure with a calculation and any definition e.g. "PY AC % = 1" in Power BI.
2.  Drag that measure into the value field of the visual.
3.  Go to the Power BI **Values calculation** section of the matrix planning visual in the **Formatting** pane and choose **Custom**.
4.  Define calculation using any of the supported operators and the references **val1** to **valn**. Val1 to valn refers to the respective value field in the visual. For example, the first field amount is referred to as **val1,** the second field **PY AC** is referred to as **val2**.
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

If statements are also supported, the syntax looks like:

val2 != 0 ? val1 / val2 : null

Here:

**! =** is the not equal operator.

**?** is the "if”.

**:** is "then" operator

#### Column measure override 

In scenarios where you need to write back on different measures that aren't part of a measure dimension, you can set the coordinates for the column that should be used when a value is written back on that column.

-   Click **Edit** on the top right of the visual.
-   Click on the measure where you want to apply to override metadata. Set the dimension coordinates that should be used when a value is written on that column.
-   Click **Sync settings** to apply the changes.

>[!Note]
>It's easier to add a simple DAX measure, [Units]=0 , to apply the measure format and use that as the placeholder for the column override.

#### Multi-select mode

The multi select mode enables you to edit multiple cells at the same time.
-   To write the same value to every selected cell. Click **Multiselect**.
-   To distribute (**Allocation**) the value across the selected cells according to their current distribution. To use this mode, use the **s** prefix. For example, s15000 will distribute 15000 across the three selected cells. On the right side of the **Save** button, you can see the total value of the selected cells.

### Subtotals formatting

It is possible to have different formats for each level of subtotal rows in the matrix planning visual.

-   One level subtotal
-   Two level subtotals

#### DAX-based subtotal

It is possible to use DAX measures for rollups and subtotals. The subtotal format for the lowest level of the hierarchy can't be changed.

#### Grand total conditional formatting

Using the Grid UI setting, change the background color of the grand total column.
Default green color that has been set for the columns from the Grid UI option, you can use the **GT conditional formatting** option and set a new format.

*Amount GT Format Formula*

-   Val = Val; Use this formula to set the new format for all the grand total rows.
-   Val \< Val; Set the format for a specific range of values.
-   Val \> Val; Set the format for a specific range of values.

*Amount Suffix icon*

It allows you to put an ASCII or HTML code.

*Amount GT format formula Priority level*

It's important to know that the priority of the Amount GT format formula 1 is higher than others.

-   Same formulas - In this example, two formulas are the same but only the first one has been applied.
-   Different formulas - In this example, two different formulas have been applied for the amount.
-   Three formulas added - In this example, three formulas have been added.

#### Undo
You can undo data entry changes before clicking **Save**. Undo data entry changes by right clicking on the respective cell and select the undo option. This shows the previous value at the top of the context menu. 

#### Dynamic locking

You can dynamically lock editing cells that fulfill a specific condition. In the **Editing lock** section of the **visual properties**, set the condition for the respective measure where you want to apply the lock. The condition is using the **val** variable that work in the same way as in the **Conditional formatting** and **Edit validation** sections.

### Edit validation

You can define validation rules that apply to a measure in the matrix. The rules support the same operators syntax (**val** variable) as **Conditional formatting** and **Edit lock**. In addition, you can use Math js functions. For more information, see [Math library for JavaScript and node.js](https://mathjs.org/docs/reference/functions.html).
