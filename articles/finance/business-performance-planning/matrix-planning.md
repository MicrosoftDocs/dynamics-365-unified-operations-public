---
title: Matrix planning visual
description: Learn how to use the Matrix planning visual in the Business performance planning application, including outlines on benefits, prerequisites, and installation.
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

# Matrix planning visual

This article describes how to use the **Matrix planning** visual in the Business performance planning application.

The **Matrix planning** visual is a custom Microsoft Power BI visual that's built to transform the planning experience. It offers a seamless and powerful approach to planning processes such as managing forecasts and budgets. Unlike traditional methods that involve data downloads, manual Excel-based budgeting, and intricate data consolidation, the **Matrix planning** visual streamlines operations on your Power BI dashboard.

## Benefits

- **Streamlined planning process** – The **Matrix planning** visual eliminates the complexities of traditional methods by enabling users to enter and manage forecasted values directly in the Power BI environment. This purpose-driven functionality streamlines the planning process and therefore saves time and effort.
- **Real-time visualization and decision-making** – Users get dynamic real-time visualizations of forecasted values. By overlaying forecast dimensions onto existing actual data, users can make agile, data-driven decisions across diverse business sectors.
- **Enhanced efficiency and collaboration** – The **Matrix planning** visual significantly enhances efficiency. By empowering teams to access and use real-time visualizations, it fosters informed, collaborative decision-making.
- **Seamless integration and accessibility** – Because the **Matrix planning** visual seamlessly integrates with Power BI dashboards, it's a critical Dynamics 365 Finance business performance planning visual. Its purpose is to ensure easy accessibility and usage in the familiar Power BI environment.
- **Optimized planning experience** – Redefine your planning processes by empowering users to efficiently manage forecasts, instantly visualize data, and optimize decision-making. In this way, you foster a more efficient and data-centric planning experience.

## Prerequisites and installation

For more information about prerequisites and installation, see [Install business performance planning visuals](powerBI-visual-install.md).

### Installation

1. Open the Power BI application, and access the workspace or report where you plan to configure the Matrix Planner.
2. Download the **Matrix planning** visual from AppSource. 
3. Drag the **Matrix planning** visual onto the report canvas.
4. Select the visual on the report canvas, and then select the **Format visual** tab on the report canvas. In the **API Details** window for the visual, add your API base URL and cube name. This information provides the details that business performance planning requires to read data from the cube and write data to it. The API base URL is the URL of the environment where business performance planning is installed. The environment URL must be preceded by **https://** (for example, `https://environment.d365.com`). For more information, see [Find your environment and organization ID and name](/power-platform/admin/determine-org-id-name).

    > [!NOTE]
    > The **Format visual** tab is available only when a visual is selected on the report canvas.

5. Select the visual, and find the visualization pane for it. In the visualization pane, enter names for the rows, columns, and filter fields. These columns provide the structure (x-axis and y-axis) for your matrix. 
6. Arrange the fields in the rows and columns of the matrix to define its visual structure. Fields that are put in rows and columns define the matrix's axes. Any fields that aren't put in rows and columns are used as filter context and should be added to the **Filters** field in the visualization pane.
7. Define the shape of the matrix by putting values in the rows and columns. Any dimensions that are intended only as filter context (that is, they aren't part of the x-axis or y-axis) should be added to the **Filters** field in the visualization pane.
8. Provide dimensions and variables to enable the **Matrix planning** visual to establish the write-back coordinates that are required to effectively build planning and budgeting models.
9. Assign the **Amount** column from your cube to the values variable in the visualization pane. This step ensures that the **Matrix planning** visual includes specific data values.
10. Verify the configuration setup in the visualization pane to ensure that all necessary fields, dimensions, and variables are correctly assigned and placed in the row, column, filter, and value sections.
11. Save the changes that you made to the configuration. Then apply the settings to activate the **Matrix planning** visual on your Power BI dashboard or report.

> [!NOTE]
> Add all dimensions to the visual.

An attribute from every dimension of the cube that's specified in the visual settings should be used in the visual (in the row section, the column section, or the filter section). Otherwise, the write-back is applied at the "All" level to all dimensions that aren't used in the visual. As a result, excessive numbers of records are written to the database.

## Enter data

To enable data entry, select **Edit** in the upper left to enter edit mode. Then enter values in a field, or select and hold (or right-click).

### Aggregation cells

To enter data in an aggregation cell in the **Matrix planning** visual, go to the visual properties, expand the **Grid UI** section, and set the **Splashing at parent** attribute to **On**.

### Prerequisites for entering or editing data on aggregations

The relevant hierarchy should be collapsed, and the children should not be visible. Multiple allocation options are available. For more information, see [Allocation visual](allocation.md).

> [!IMPORTANT]
> Values that are entered at a base level and dimension coordinates that don't contain aggregations are saved after you select **Save**. Values that are entered on aggregations are immediately saved.

Changes from base-level entries are immediately visible in the matrix. To view the results of allocation or the effects on other elements of the report, refresh the report page. Because of limitations in Power BI Desktop, **Refresh** in the visual doesn't work in Power BI Desktop.

## Export to Excel

Select **Export to excel** to export a formatted report of the content that's shown in the matrix visual to Excel.

## Copy and paste

In edit mode, you can paste cells that you've copied to the clipboard into the matrix. Select the place in the matrix where you want to paste the content, select and hold (or right-click), and then select **Paste**.

## Enter or edit comments

You can directly enter comments by selecting and holding (or right-clicking) a base-level cell. In read mode, hover over a cell to view comments that have been entered at base levels and underlying levels on an aggregated level.

### Configuration options

- **Grid properties** – In the **Format** pane in Power BI, set different design parameters, such as the font size, colors, and layout.
- **Show comment markers** – Comments are stored in the **TEXT\_VAL** value of the cube. You can either use the same cube that contains your values or store them in a separate comments cube. We recommend that you use a separate comments cube if you want to store comments at a different granularity than your cube. For comments in the same cube, you can show comment markers in the **Matrix planning** visual. For this approach, your cube must have a column that returns **1** if there's a comment for the record. Here's an example: **Comment Count = if(VW\_GL\[TEXT\_VAL\]\<\>BLANK(),1,0)**. This calculated column measure for the comment count must be added to the **Comment count** field in the visual. Markers are shown for the coordinates where the comment count is above 0 (zero).
- **Lock measure or value columns for entry** – The **Measure uneditable** property lets you prevent edits for specific value fields by specifying one or more columns, where the first value starts with **0**. For example, to prevent entry in the second value field you can set the property to **1**. To prevent entry in the second and third value fields, set the property to **1,2**.
- **Disable entry on empty parents** – The **Allow entry on empty parent** property lets you prevent users from entering data in empty aggregated cells. Data entry in these cells lead to a large number of unintentional write-back transactions.

### Conditional formatting

Use the **Conditional formatting** section of the **Format** pane in Power BI to configure conditional formatting for the background and font colors for each value measure in the **Matrix planning** visual.

The definition of conditional formatting criteria uses the **Val** variable. You can use any mathematical operation to set up conditional formatting as you require:

- **Val \> 10** applies the formatting set for the specific measure to all values above 10.
- **Val \>=0** or **Val \<=0** applies the format to all values in the measure.

### Custom totals

Use the **Values calculation** section of the **Format** pane in Power BI to specify custom calculations other than the default aggregation.

### Custom calculations

Use the **Custom** option in the **Values calculation** section to define the calculation that's applied to a placeholder value field or measure.

Here's an example.

1. In Power BI, create a measure that has a calculation and any definition. For this example, use **PY AC % = 1**.
2. Drag the measure into the value field of the visual.
3. In the Power BI **Values calculation** section of the **Matrix planning** visual in the **Formatting** pane, select **Custom**.
4. Define the calculation by using any of the supported operators. Use the references **val1** through **val*n*** to refer to the corresponding value fields in the visual. For this example, the first field (**Amount**) is referred to as **val1**, and the second field (**PY AC**) is referred to as **val2**.

For this example, you add the **Amount** and **PY AC** fields, and define the placeholder calculation **PY AC %** as **val1/val2**. Here, **val1** refers to the **Amount** field, **val2** refers to the **PY AC** field, and the relative percentage is calculated.

#### Supported operators

| Operator | Name                   | Syntax       | Associativity | Example                 | Result              |
|----------|------------------------|--------------|---------------|-------------------------|---------------------|
| (, )     | Grouping               | (x)          | None          | 2 \* (3 + 4)            | 14                  |
| \[, \]   | Matrix, Index          | \[&hellip;\] | None          | \[\[1,2\],\[3,4\]\]     | \[\[1,2\],\[3,4\]\] |
| \{, \}   | Object                 | \{&hellip;\} | None          | \{a: 1, b: 2\}          | \{a: 1, b: 2\}      |
| ,        | Parameter separator    | x, y         | Left to right | max(2, 1, 5)            | 5                   |
| .        | Property accessor      | obj.prop     | Left to right | obj=\{a: 12\}; obj.a    | 12                  |
| ;        | Statement separator    | x; y         | Left to right | a=2; b=3; a\*b          | \[6\]               |
| ;        | Row separator          | \[x; y\]     | Left to right | \[1,2;3,4\]             | \[\[1,2\],\[3,4\]\] |
| \\n      | Statement separator    | x \\n y      | Left to right | a=2 \\n b=3 \\n a\*b    | \[2,3,6\]           |
| +        | Add                    | x + y        | Left to right | 4 + 5                   | 9                   |
| +        | Unary plus             | +y           | Right to left | +4                      | 4                   |
| \-       | Subtract               | x - y        | Left to right | 7 - 3                   | 4                   |
| \-       | Unary minus            | \-y          | Right to left | \-4                     | \-4                 |
| \*       | Multiply               | x \* y       | Left to right | 2 \* 3                  | 6                   |
| .\*      | Element-wise multiply  | x.\* y       | Left to right | \[1,2,3\] .\* \[1,2,3\] | \[1,4,9\]           |
| /        | Divide                 | x / y        | Left to right | 6 / 2                   | 3                   |
| ./       | Element-wise divide    | x ./ y       | Left to right | \[9,6,4\] ./ \[3,2,2\]  | \[3,3,2\]           |
| %, mod   | Modulus                | x % y        | Left to right | 8 % 3                   | 2                   |
| \^       | Power                  | x \^ y       | Right to left | 2 \^ 3                  | 8                   |
| .\^      | Element-wise power     | x .\^ y      | Right to left | \[2,3\] .\^ \[3,3\]     | \[8,27\]            |
| '        | Transpose              | y'           | Left to right | \[\[1,2\],\[3,4\]\]'    | \[\[1,3\],\[2,4\]\] |
| !        | Factorial              | y!           | Left to right | 5!                      | 120                 |
| &        | Bitwise and            | x & y        | Left to right | 5 & 3                   | 1                   |
| \~       | Bitwise not            | \~x          | Right to left | \~2                     | \-3                 |
| \|       | Bitwise or             | x \| y       | Left to right | 5 \| 3                  | 7                   |
| \^\|     | Bitwise xor            | x \^\| y     | Left to right | 5 \^\| 2                | 7                   |
| \<\<     | Left shift             | x \<\< y     | Left to right | 4 \<\< 1                | 8                   |
| \>\>     | Right arithmetic shift | x \>\> y     | Left to right | 8 \>\> 1                | 4                   |
| \>\>\>   | Right logical shift    | x \>\>\> y   | Left to right | \-8 \>\>\> 1            | 2147483644          |
| and      | Logical and            | x and y      | Left to right | true and false          | false               |
| not      | Logical not            | not y        | Right to left | not true                | false               |
| or       | Logical or             | x or y       | Left to right | true or false           | true                |
| xor      | Logical xor            | x xor y      | Left to right | true xor true           | false               |
| =        | Assignment             | x = y        | Right to left | a = 5                   | 5                   |
| ? :      | Conditional expression | x ? y : z    | Right to left | 15 \> 100 ? 1 : -1      | \-1                 |
| :        | Range                  | x : y        | Right to left | 1:4                     | \[1,2,3,4\]         |
| to, in   | Unit conversion        | x to y       | Left to right | 2 inch to cm            | 5.08 cm             |
| ==       | Equal                  | x == y       | Left to right | 2 == 4 - 2              | true                |
| !=       | Unequal                | x != y       | Left to right | 2 != 3                  | true                |
| \<       | Smaller                | x \< y       | Left to right | 2 \< 3                  | true                |
| \>       | Larger                 | x \> y       | Left to right | 2 \> 3                  | false               |
| \<=      | Smallereq              | x \<= y      | Left to right | 4 \<= 3                 | false               |
| \>=      | Largereq               | x \>= y      | Left to right | 2 + 4 \>= 6             | true                |

If statements are also supported, the syntax resembles the following example:

val2 != 0 ? val1 / val2 : null

Here:

- **!=** is the "not equal" operator.
- **?** is the "if" operator.
- **:** is the "then" operator.

### Column measure override

In scenarios where you write back on different measures that aren't part of a measure dimension, set the coordinates for the column that should be used when a value is written back in that column.

1. Select **Edit** in the upper right of the visual.
2. Select the measure to override metadata for. Set the dimension coordinates that should be used when a value is written in that column.
3. Select **Sync settings** to apply your changes.

> [!TIP]
> It's easier to add a simple DAX measure, **\[Units\]=0**, to apply the measure format and use it as the placeholder for the column override.

### Multi-select mode

Multi-select mode lets you edit multiple cells at the same time.

- To write the same value to every selected cell, select **Multiselect**.
- To distribute the value across the selected cells according to their current distribution, use the **s** prefix. For example, enter **s15000** to distribute 15,000 across three selected cells. The total value of the selected cells is shown to the right of the **Save** button.

## Subtotal formatting

You can have different formats for each level of subtotal rows in the **Matrix planning** visual.

- One-level subtotal
- Two-level subtotals

### DAX-based subtotal

You can use DAX measures for rollups and subtotals. The subtotal format for the lowest level of the hierarchy can't be changed.

### Grand total conditional formatting

You can use the **Grid UI** setting to change the background color of the grand total column.

By default, the **Grid UI** option sets the color green for columns. However, you can use the **GT conditional formatting** option to set a new format.

- **Amount GT format formula**

    - **Val = Val** – Use this formula to set the new format for all the grand total rows.
    - **Val \< Val** – Use this formula to set the new format for a specific range of values.
    - **Val \> Val** – Use this formula to set the new format for a specific range of values.

- **Amount suffix icon** – You can use ASCII or HTML code.
- **Amount GT format formula priority level** – Amount GT format formula 1 has higher priority than the others.

    - **Same formulas** – In this example, two formulas are the same, but only the first formula is applied.
    - **Different formulas** – In this example, two different formulas are applied to the amount.
    - **Three formulas added** – In this example, three formulas are added.

### Undo

You can undo data entry changes before you select **Save**. To undo data entry changes, select and hold (or right-click) the appropriate cell, and then select **Undo**. The previous value is shown at the top of the shortcut menu.

### Dynamic locking

You can dynamically lock edits to cells that meet a specific condition. In the **Editing lock** section of the visual properties, set the condition for the measure where you want to apply the lock. The condition uses the **Val** variable. This variable works just as it works in the **Conditional formatting** and **Edit validation** sections.

## Edit validation

You can define validation rules that apply to a measure in the matrix. The rules support the same operator syntax (**Val** variable) as the **Conditional formatting** and **Edit lock** sections. In addition, you can use math.js functions. For more information, see [Math library for JavaScript and node.js](https://mathjs.org/docs/reference/functions.html).
