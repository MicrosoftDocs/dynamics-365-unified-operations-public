---
# required metadata

title: Business performance planning application reporting visual
description: This article describes how to use the reporting visual in the Business performance planning application.
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
# Reporting visual

This article describes how to use the reporting visual in the Business performance planning application.. You must also install Power BI visuals to fully use the planning application. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).Reporting

# Introduction & Purpose

## Overview

## The Reporting visual is a powerful tool designed to craft polished financial reports seamlessly within Power BI. It enables the creation of comprehensive financial statements like cash flow statements, income statements, balance sheets, and more, offering advanced row and column formatting capabilities.

## Purpose and Benefits

-   **Tailored Financial Reports**

    Craft detailed financial reports with precision by leveraging advanced row and column formatting options.

-   **Custom Calculations Integration**

    Seamlessly integrate custom calculations and subtotals at any juncture within the report, ensuring accuracy and tailored insights.

-   **Professional Data Presentation**

    Enhance the presentation of financial data by utilizing advanced formatting features for a polished and professional appearance.

-   **Insightful Variance Views**

    Gain deeper insights into financial data through variance views included within the reports, aiding in comprehensive financial analysis and decision-making.

## Prerequisites and installation

For more information about prerequisites and installation, see [Install Power BI visuals](powerBI-visual-install).


## Compatibility

Info on PBI versions where the visual is compatible.

## Using the Visual

## Functionality

-   **Incorporate Subtotals and Custom Calculations**

    Add subtotals and custom calculations at any point within the financial report.

-   **Format Data Professionally**

    Utilize enhanced formatting options for a professional and refined presentation of financial data.

-   **Visualize Variances**

    Include variance views within the reports, allowing for a deeper understanding and analysis of financial data.

## Configuration Options

### Custom Calculations

To add custom calculations, click on **edit** in the visual settings in the top right-hand corner of the visual

*Row Calculations*  
In the edit section, you can now add new rows by right-click on the position where you want to add

*Column Calculations  
*Right-click on the column header where you want to add your calculation and choose before or after. Then click on the column header items that you want to use in the calculation. In the editor at the top right, you can see a list of all row and column calculation. To edit calculations just click on the item that you want to use.

### *Supported Operators*

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

### *Precedence*

The operators have the following precedence, from highest to lowest

| Operators                | Description                                                                     |
|--------------------------|---------------------------------------------------------------------------------|
| (...) [...] {...}        | Grouping Matrix Object                                                          |
| x(...) x[...] obj.prop : | Function call Matrix index Property accessor Key/value separator                |
| '                        | Matrix transpose                                                                |
| !                        | Factorial                                                                       |
| \^, .\^                  | Exponentiation                                                                  |
| +, -, \~, not            | Unary plus, unary minus, bitwise not, logical not                               |
| See section below        | Implicit multiplication                                                         |
| \*, /, .\*, ./, %, mod   | Multiply, divide, modulus                                                       |
| +, -                     | Add, subtract                                                                   |
| :                        | Range                                                                           |
| to, in                   | Unit conversion                                                                 |
| \<\<, \>\>, \>\>\>       | Bitwise left shift, bitwise right arithmetic shift, bitwise right logical shift |
| ==, !=, \<, \>, \<=, \>= | Relational                                                                      |
| &                        | Bitwise and                                                                     |
| \^\|                     | Bitwise xor                                                                     |
| \|                       | Bitwise or                                                                      |
| and                      | Logical and                                                                     |
| xor                      | Logical xor                                                                     |
| or                       | Logical or                                                                      |
| ?, :                     | Conditional expression                                                          |
| =                        | Assignment                                                                      |
| ,                        | Parameter and column separator                                                  |
| ;                        | Row separator                                                                   |
| \\n , ;                  | Statement separators                                                            |

For each row and column, you can either assign a style that you set in the visual properties or specify that the measure format should be used by selecting **Measure.**

### Formatting

#### Row and Column Styles

In the Row/Column Style section, you can define row and column styles that are set for any row that has been assigned this style. You can assign these to the calculations and achieve a format option applies to all items that use this style e.g. text formats: bold, color, underlines, overlines etc.

#### Conditional Formatting

In the Conditional Formatting property of the visual, you can setup up to three flexible rules for conditional formatting. The rule is set up using the keyword **Val** to refer to the value of the specific measure in the visual with all mathematical options as outlined in **Supported Operators.** For example Val \> 2000 will format all values greater than 2000 with the format for that measure.

#### Row/ Column Spacing

Using a right-click you can increase the space between that row/column.

#### Variance Visualization according to IBCS

This visual allows you to add variance visualization according to IBCS principles. To add it to your reporting you can either use the **Variance section** in the visual properties and flexibly set the value and comparison columns by pointing to the column number or set the calculation in the visual with a right-click on the **Variance** column. For the latter, you can either reference the columns in the nested dimension section or by ticking the **Absolute Indexing** checkbox use an **absolute** reference to any column in the visual.

You can switch between absolute and relative variance display by clicking the respective symbol: Delta symbol **Δ** or **%**

#### Comments

Reporting visual supports the display of cell-based comments that can be formatted in HTML. To activate them, turn on the **Comments** in the properties. Here you can also specify the width of the comment box as well.

#### Measure Header

Using the measure Header section in the visual properties you can set the format for a measure underline to clearly identify a particular scenario type according to the IBCS guide.

#### Data-Driven Styles

Automatically apply format styles that include:

-   Number Formats (.NET number format conventions)
-   Color (Hex Code or color name)
-   FontSize (integer number)
-   font-weight (bold, n, italic or integer)
-   FontStyle (Italic, oblique, normal)
-   LineFormat (u= 1 underline, u2= 2 underlines, o = 1 over line, o2 = 2 over lines)

to the report rows.

In the table that contains the row members just add a column with the format style that you want to apply in the following format:

{"numberFormat": "\#,0,.0;(\#,0,.0)","FontSize": 8,"color": "blue","FontWeight": "bold","FontStyle" : "","LineFormat": "n","LineColor": "blue"}

### Refresh Button

Turn on **Refresh** on the visualization section to get the Refresh button on the visual.

Export Data

Export data with either Excel or CSV.

Cell Setting / Auto width

Adjust the **Column Width** dynamically for every Column.

Rows Header /Flatten

The Flatten Feature changes the layout of the visual.
