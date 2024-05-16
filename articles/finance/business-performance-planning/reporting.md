---
title: Reporting visual
description: Learn how to use the Reporting visual in the Business performance planning application, including outlines on benefits, prerequisites, and installation.
author: ShielaSogge
ms.author: twheeloc
ms.date: 12/08/2023
ms.topic: article
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Reporting visual

This article describes how to use the **Reporting** visual in the Business performance planning application. To fully use this application, you must install Microsoft Power BI visuals. For information about how to install Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

The **Reporting** visual is a powerful tool for seamlessly generating professional-looking financial reports in Power BI. You can use this visual to create comprehensive financial statements that offer advanced row and column formatting capabilities. Examples include cash flow statements, income statements, and balance sheets.

## Benefits

- **Tailored financial reports** – Create detailed financial reports with precision by using advanced row and column formatting options.
- **Custom calculations integration** – Seamlessly integrate custom calculations and subtotals at any point on the report to ensure accuracy and tailored insights.
- **Professional data presentation** – Enhance the presentation of financial data by using advanced formatting features to give the reports a polished and professional appearance.
- **Insightful variance views** – Gain deeper insights into financial data through variance views that are included on the reports. Then use these insights to help with comprehensive financial analysis and decision-making.

## Prerequisites and installation

For more information about prerequisites and installation, see [Install business performance planning visuals](powerBI-visual-install.md).

> [!NOTE]
> Because the **Reporting** visual doesn't write data back to Dataverse, it doesn't require that you enter API details.

## Use the Reporting visual

You can use the **Reporting** visual to add subtotals and custom calculations to the financial report. The enhanced formatting options let you create a professional and polished presentation of financial data. You can also include variance views on the reports to facilitate deeper understanding and analysis of financial data.

### Initial setup

To begin to use the **Reporting** visual, put the **Amount** column from your cube into the **Values** field in the **Visualizations** pane. Then populate your row and column data. For a financial report, the rows are typically populated with an account name, and the columns are populated with a time period, such as month, quarter, or year.

> [!TIP]
> To find the **Amount** column, expand your cube in the **Data** pane, and look for a field that has a **Sum** symbol next to it. A **Sum** symbol next to numeric fields indicates that they're measures.

### Custom calculations

To add custom calculations, select **Edit** or the ellipsis (**&hellip;**) in **Visual settings** in the upper-right corner of the visual.

#### Row calculations

In the **Edit** section, add new rows by selecting and holding (or right-clicking) in the place where you want to add them.

#### Column calculations

Select and hold (or right-click) the column header where you want to add a calculation, and then select **Before** or **After**. Then select the column header items to use in the calculation. The editor shows a list of all the row and column calculations. To edit the calculations, select the item that you want to work with.

### Supported operators

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

### Precedence

The operators have the following precedence, from highest to lowest.

| Operators                               | Description                                                                     |
|-----------------------------------------|---------------------------------------------------------------------------------|
| (&hellip;), \[&hellip;\], \{&hellip;\}  | Grouping matrix object                                                          |
| x(&hellip;), x\[&hellip;\], obj.prop, : | Function call, matrix index, property accessor, key/value separator             |
| '                                       | Matrix transpose                                                                |
| !                                       | Factorial                                                                       |
| \^, .\^                                 | Exponentiation                                                                  |
| +, -, \~, not                           | Unary plus, unary minus, bitwise not, logical not                               |
| See the next section                    | Implicit multiplication                                                         |
| \*, /, .\*, ./, %, mod                  | Multiply, divide, modulus                                                       |
| +, -                                    | Add, subtract                                                                   |
| :                                       | Range                                                                           |
| to, in                                  | Unit conversion                                                                 |
| \<\<, \>\>, \>\>\>                      | Bitwise left shift, bitwise right arithmetic shift, bitwise right logical shift |
| ==, !=, \<, \>, \<=, \>=                | Relational                                                                      |
| &                                       | Bitwise and                                                                     |
| \^\|                                    | Bitwise xor                                                                     |
| \|                                      | Bitwise or                                                                      |
| and                                     | Logical and                                                                     |
| xor                                     | Logical xor                                                                     |
| or                                      | Logical or                                                                      |
| ?, :                                    | Conditional expression                                                          |
| =                                       | Assignment                                                                      |
| ,                                       | Parameter and column separator                                                  |
| ;                                       | Row separator                                                                   |
| \\n, ,, ;                               | Statement separator                                                            |

For each row and column, you can assign a style that you set in the visual properties. Alternatively, select **Measure** to specify that the measure format should be used.

### Formatting

The following options are available on the **Format** tab of the **Visualizations** pane in Power BI:

- **Row and column styles** – In the **Row/Column Style** section, you can define row and column styles for any row that this style is assigned to. By assigning these styles to the calculations, you can achieve a format option that applies to all items that use this style. Examples include text formats such as font weight, color, underlines, and overlines. After the style is set, enter edit mode, select the row in the visual, and then select the style on the header of the report.
- **Conditional formatting** – In the **Conditional formatting** property of the visual, you can set up three flexible rules for conditional formatting. You set up a rule by using the **Val** keyword to refer to the value of the specific measure in the visual. You can use all the mathematical options that are outlined in the [Supported operators](#supported-operators) section. For example, the rule **Val \> 2000** formats all values above 2,000 by using the format for that measure.

#### Row/column spacing

You can increase the space between a row/column by selecting and holding (or right-clicking) the column header.

#### Variance visualization according to IBCS

Use the **Reporting** visual to add a variance visualization according to International Business Communication Standards (IBCS) principles. To add the variance visualization to your reporting, use the **Variance** section in the visual properties. You can flexibly set the value and comparison columns by pointing to the column number. Alternatively, you can set the calculation in the visual by selecting and holding (or right-clicking) the **Variance** column. In this case, you can reference the columns in the nested dimension section, or you can select the **Absolute Indexing** checkbox to use an **Absolute** reference to any column in the visual.

You can switch between absolute and relative variance displays by selecting the delta symbol (**&Delta;**) or the percentage sign (**%**), as appropriate.

#### Comments

The **Reporting** visual supports the display of cell-based comments that can be formatted in HTML. To activate these comments, turn on **Comments** in the properties. You can also specify the width of the comment box.

#### Measure header

In the **Measure** header section, in the visual properties, you can set the format for a measure underline to clearly identify a specific scenario type according to the IBCS guide.

#### Data-driven styles

Automatically apply format styles. Here are some examples:

- **Number Formats** – Use .NET number format conventions.
- **Color** – Enter a hex code or color name.
- **FontSize** – Enter an integer.
- **Font-weight** – Specify **bold**, **n**, or **italic**, or enter an integer.
- **FontStyle** – Specify **italic**, **oblique**, or **normal**.
- **LineFormat** – Specify **u** for a single underline, **u2** for a double underline, **o** for a single overline, or **o2** for a double overline.

In the table that contains the row members, add a column that contains the format style that you want to apply. Use the following format:

\{"numberFormat": "\#,0,.0;(\#,0,.0)","FontSize": 8,"color": "blue","FontWeight": "bold","FontStyle": "","LineFormat": "n","LineColor": "blue"\}

### Refresh button

Turn on the **Refresh** option in the **Visualization** section to make the **Refresh** button available on the visual.

### Export data

You can export data in Excel or comma-separate values (CSV) format.

### Cell setting and autowidth

You can dynamically adjust the column width for every column.

### Rows header/flatten

You can use the **Flatten** feature to change the layout of the visual.
