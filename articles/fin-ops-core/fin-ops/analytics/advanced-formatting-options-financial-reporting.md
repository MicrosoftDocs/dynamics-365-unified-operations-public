---
title: Advanced formatting options in financial reporting
description: Learn about advanced formatting functions, including filters, restrictions, nonprinting rows, and conditional statements in calculations.
author: panolte
ms.author: johnmichalak
ms.topic: article
ms.date: 12/02/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.search.form: FinancialReports
ms.dyn365.ops.version: Version 1611
ms.assetid: 895b5127-01d6-4495-b127-343387b743aa
---

# Advanced formatting options in financial reporting

[!include [banner](../../../finance/includes/banner.md)]

When you create a report in financial reporting, you can use extra formatting functions. These functions include filters for dimensions, restrictions for columns and reporting units, nonprinting rows, and IF/THEN/ELSE statements in calculations.

The following table explains the advanced formatting functions that you can use when you design reports.

| Function                   | Description |
|----------------------------|-------------|
| Dimension filter           | To access specific sets of data, use dimensions in the row definition and column definition. Many reports use only the natural segment in the row format. However, you can modify rows so that they include dimension values. Use dimension filters in the column definition to access specific dimension values. |
| Reporting unit restriction | Set up a report row so that it shows only information that's linked to a specific reporting unit. |
| Nonprinting (NP) rows     | Nonprinting rows are useful on many reports. If several calculations are required to obtain a value, you can hide these calculations on the printed report. Nonprinting rows are also useful for troubleshooting report designs and for advanced cell placement. |
| Column restriction         | The column restriction in the row definition is useful for hiding values that are relevant only on some rows of the report. When percentage calculations are performed on a row, the column restriction prevents total columns or other columns from being printed when those numbers don't apply. |
| Column break               | Add column breaks in a row definition to show report information side by side. You can add multiple column breaks in a single row definition, and column headers are repeated at the top of each column after the column break. Comments for a report are shown between the column breaks. |
| IF/THEN/ELSE statement     | Modify calculations in a row definition or a column definition. |
| Use single quotes ('') and an ampersand (&) for dimension values | Use dimension values, including the ampersand character for report design. |

## Advanced cell placement

Advanced cell placement, or *forcing*, involves placing specific values into specific cells. For example, use forcing to move the correct balance in a cash flow statement. Use forcing for the following purposes:

- Move values from Microsoft Excel into specific cells.
- Hard-code specific values into a report.
- Modify signs by copying a value from a previous cell and multiplying that value by -1.

> [!NOTE]
> In many cases, you must configure your report definition so that column calculations are done before row calculations. To complete this configuration, follow these steps.
>
> 1. In Report Designer, open the report definition.
> 1. On the **Settings** tab, under **Calculation priority**, select **Perform column calculation first and then row**.

## Designing the report

When you design a report, create all the detail rows first to make sure that values are pulled in as expected. Then add **NP** (No Print) format overrides to suppress the detail that includes the final values.

> [!IMPORTANT]
> When you use the **CAL** format code in the row definition, you can't drill down into transaction detail.

For forcing, formulas use the following format: &lt;destination column&gt;=&lt;originating column&gt;.&lt;row code&gt; Separate any other placements for a row by a comma and a space. Here's an example: D=C.190,E=C.100

## Examples of advanced formatting options

The following examples show how to format the row definition and column definition to force a basic cash flow report (example 1) and a statistical report (example 2).

### Example 1: Basic forcing

The following table shows an example of a row definition that uses basic forcing.

| Row Code |           Description            | Format Code | Related Formulas/Rows/Units |        Row Modifier        | Link to Financial Dimensions |
|----------|----------------------------------|-------------|-----------------------------|----------------------------|------------------------------|
| 100      | Cash at Beginning of Period (NP) |             |                             | Account Modifier = \[/BB\] | +Segment2 = \[1100\]         |
| 130      | Cash at Beginning of Period      | CAL         | C=C.100,F=D.100             |                            |                              |
| 160      |                                  |             |                             |                            |                              |
| 190      |                                  |             |                             |                            |                              |

> [!NOTE]
> The previous table doesn't show empty columns: Format Overrides, Normal Balance, Print Control, and Column Restriction.

The following table shows an example of column definition that uses basic forcing in the row.

|           Format             | A   | B    | C        | D      | E      | F    |
|------------------------------|-----|------|----------|--------|--------|------|
| Header 1                     |     |      |          |        |        |      |
| Header 2                     | A   | B    | C        | D      | E      | F    |
| Header 3                     |     |      |          |        |        |      |
| Column Type                  | ROW | DESC | FD       | FD     | FD     | CALC |
| Book Code/Attribute Category |     |      | ACTUAL   | ACTUAL | ACTUAL |      |
| Fiscal Year                  |     |      | BASE     | BASE   | BASE   |      |
| Period                       |     |      | BASE     | BASE   | BASE   |      |
| Periods Covered              |     |      | PERIODIC | YTD/BB | YTD    |      |
| Formula                      |     |      |          |        |        | E-D  |
| Column Width                 | 5   | 30   | 14       | 14     | 14     | 14   |

### Example 2: Statistical reports

The following table shows an example of a row definition that uses forcing for a statistical report.

| Row Code | Description               | Format Code | Related Formulas/Rows/Units     | Format Override      | Normal Balance | Link to Financial Dimensions               |
|----------|---------------------------|-------------|---------------------------------|----------------------|----------------|--------------------------------------------|
| 50       | Statistical Information   | REM         |                                 |                      |                |                                            |
| 100      | Headcount - US            | CAL         | 4                               | \#\#\#0.;($\#\#\#0.) |                |                                            |
| 115      | Headcount - International | CAL         | 11                              | \#\#\#0.;($\#\#\#0.) |                |                                            |
| 130      |                           |             |                                 |                      |                |                                            |
| 190      | US Sales                  |             |                                 |                      | C              | +Segment2 = \[41\*\], Segment3 = \[00\]    |
| 220      | International Sales       |             |                                 |                      | C              | +Segment2 = \[41\*\], Segment3 = \[01:99\] |
| 250      |                           |             |                                 |                      |                |                                            |
| 280      |                           |             |                                 |                      |                |                                            |
| 310      | US Sales                  | CAL         | D=C.190,E=C.100,F=(C.100/C.190) |                      |                |                                            |
| 340      | International Sales       | CAL         | D=C.220,E=C115,F=(C.220/C.115)  |                      |                |                                            |

> [!NOTE]
> The previous table doesn't show the Print Control, Column Restriction, and Row Modifier columns.

The following table shows an example of a column definition that uses forcing for a statistical report.

|    Format                    | A   | B    | C      | D            | E     | F            |
|------------------------------|-----|------|--------|--------------|-------|--------------|
| Header 1                     | A   | B    | C      | D            | E     | F            |
| Header 2                     | -   | -    | YTD    | Yearly Sales | Staff | $ Per Person |
| Header 3                     |     |      |        |              |       |              |
| Column Type                  | ROW | DESC | FD     | CALC         | CALC  | CALC         |
| Book Code/Attribute Category |     |      | ACTUAL |              |       |              |
| Fiscal Year                  |     |      | BASE   |              |       |              |
| Period                       |     |      | BASE   |              |       |              |
| Periods Covered              |     |      | YTD    |              |       |              |
| Formula                      |     |      |        |              |       | E-D          |
| Column Width                 | 5   | 30   | 14     | 14           | 14    | 14           |

## Restricting a row to a specific reporting unit

When you restrict a report row to a specific reporting unit, that row shows the linked data only for the named reporting unit and ignores the data for other reporting units in the reporting tree. For example, you can create a row that provides details for the total operating expenses for a specific department. Your report might contain duplicate data if the report contains both a reporting tree and a row definition that has more than just the natural account. For example, you have a reporting tree that lists the six departments in your organization, and you also have a row definition that lists a specific combination of an account and a department in the row. When you generate the report, the specific combination of an account and a department is printed on every level of the reporting tree, even though that department might not match what is in the tree. This behavior occurs because the row overrides what the report definition typically filters out. One way that you can avoid duplication of data is by restricting a row to a specific reporting unit.

> [!NOTE]
> If a row includes dimensions, and you restrict that row to a child reporting unit, the row amount is included for that child unit and for its parent units, but no duplication occurs.

### Restrict a row to a reporting unit

1. In Report Designer, select **Row Definitions**, then select a row definition to modify.
1. Double-click the appropriate **Related Formulas/Rows/Units** cell.
1. In the **Reporting Unit Selection** dialog box, in the **Reporting tree** field, select the tree that you assigned in the report definition.
1. Select a reporting unit, then select **OK**. The restriction appears in the cell of the row definition.
1. Double-click the cell in the **Link to Financial Dimensions** column of the restricted row, then enter a link to the financial data system.

## Selecting print control in a row definition

You can specify print control codes for each column by using the **Print Control** cell.

### Add print control codes to a report row

1. In Report Designer, open the row definition to modify.
1. Double-click the **Print Control** cell.
1. In the **Print Control** dialog box, select a print control code, or press and hold the Ctrl key to select multiple codes. You can also type print control codes directly in the **Print Control** cell. Use commas to separate multiple print control codes.
1. Select any conditional print options.
1. Select **OK**.

### Regular print control codes

The following table describes the regular print control codes for a row definition.

| Print control code | Interpretation of the print control code         | Description |
|--------------------|--------------------------------------------------|-------------|
| NP                 | Nonprinting row                                 | Prevent the amounts in the row from being printed on the report, and exclude the amounts from calculations. To include a nonprinting column in a calculation, refer to the column directly in the calculation formula. For example, nonprinting row 240 is included in the following calculation: **230+240+250**. However, nonprinting row 240 isn't included in the following calculation: **230:250**. |
| CS                 | Currency symbol; use currency format in this row | Include the currency symbol in all nonpercentage amounts. Percentage values never receive a currency symbol. |
| XD                 | Suppress row in account detail report            | Suppress the display of accounts on account detail reports and transaction detail reports. This print control is useful when a row includes multiple accounts that shouldn't be listed on the account detail report or transaction detail report. |
| X0                 | Suppress row if all zeros                        | Exclude a row from the report if all cells in that row are either empty or contain zeros. This print control is meaningful only when the option to suppress zero balance isn't selected in the report definition. |
| B0                 | Leave zero columns blank                         | Leave columns empty in a row that contain zero amounts. |
| XR                 | Suppress rollup                                  | Suppress a rollup. If the report uses a reporting tree, the amounts in this row aren't rolled up into subsequent parent nodes. |
| SR                 | Suppress rounding                                | Prevent the amounts in this row from being rounded. |
| XT                 | Suppress row in transaction detail report        | Suppress the display of transactions on transaction detail reports. This print control is useful when a row includes multiple accounts that shouldn't be listed on a transaction detail report. |

### Conditional print control codes

The following table describes the conditional print control codes for a row definition.

| Print control code | Description                                  |
|--------------------|----------------------------------------------|
| (none)             | Clear the conditional print selection.       |
| DR                 | Print only the debit balances for this row.  |
| CR                 | Print only the credit balances for this row. |

## Column Restriction cell in a row definition

The **Column Restriction** cell in a row definition serves multiple purposes. Depending on the type of row, you can use the **Column Restriction** cell to specify one of the following functions:

- Limit the printing of row amounts to a specific column. This function is useful if you're creating a tabular balance sheet.
- Specify the column of amounts to sort.

## Using a calculation formula in a row definition

A calculation formula in a row definition can include the **+**, **-**, **\***, and **/** operators, and also **IF/THEN/ELSE** statements. Additionally, a calculation can involve individual cells and absolute amounts (actual numbers that are included in the formula). The formula can contain up to 1,024 characters. You can't apply calculations to rows that contain cells of the **Link to Financial Dimensions** (FD) type. However, you can include calculations on consecutive rows, suppress the printing of those rows, and then total the calculation rows.

### Operators in a calculation formula

A calculation formula uses more complex operators than a row total formula. You can use the **\*** and **/** operators together with the other operators to multiply (\*) and divide (/) amounts. To use a range or sum in a calculation formula, you must use an at sign (@) in front of any row code, unless you're using a column in the row definition. For example, to add the amount in row 100 to the amount in row 330, you can use the row total formula **100+330** or the calculation formula **@100+@330**.

> [!NOTE]
> You must use an at sign (@) before every row code that you use in a calculation formula. Otherwise, the number is read as an absolute amount. For example, the formula **@100+330** adds USD 330 to the amount in row 100. When you reference a column in a calculation formula, an at sign (@) isn't required.

### Create a calculation formula

1. In Report Designer, select **Row Definitions**, then open the row definition to modify.
1. Double-click the **Format Code** cell, then select **CAL**.
1. In the **Related Formulas/Rows/Units** cell, type the calculation formula.

### Example of a calculation formula for specific rows

In this example, the calculation formula **@100+@330** adds the amount in row 100 to the amount in row 330. The row total formula **340+370** adds the amount in row 340 to the amount in row 370. (The amount in row 370 comes from the calculation formula.)

| Row Code | Description                 | Format Code | Related Formulas/Rows/Unit | Print Control | Row Modifier | Link to Financial Dimensions |
|----------|-----------------------------|-------------|----------------------------|---------------|--------------|------------------------------|
| 340      | Cash at Beginning of Period |             |                            | NP            | BB           | +Account=\[1100:1110\]       |
| 370      | Cash at Beginning of Year   | CAL         | @100+@330                  | NP            |              |                              |
| 400      | Cash at Beginning of Period | TOT         | 340+370                    |               |              |                              |

When you assign the format code **CAL** to a row in a row definition and enter a mathematical calculation in the **Related Formulas/Rows/Units** cell, you must also enter the letter of the associated column and row on the report. For example, enter **A.120** to represent column A, row 120. Alternatively, you can use an at sign (@) to indicate all columns. For example, enter **@120** to represent all columns in row 120. Any mathematical calculation that doesn't include a column letter or an at sign (@) is assumed to be a real number.

> [!NOTE]
> If you use a label row code to reference a row, you must use a period (.) as a separator between the column letter and the label (for example, **A.GROSS\_MARGIN/A.SALES**). If you use an at sign (@), a separator isn't required (for example, **\@GROSS\_MARGIN/@SALES**).

### Example of a calculation formula for a specific column

In this example, the calculation formula **E=C.340** means that the calculation in the cell in column C, row 340, is performed only on column E.

> [!NOTE]
> When you reference a column in a calculation formula, an at sign (@) isn't required.

| Row Code | Description                 | Format Code | Related Formulas/Rows/Unit | Print Control | Row Modifier | Link to Financial Dimensions |
|----------|-----------------------------|-------------|----------------------------|---------------|--------------|------------------------------|
| 340      | Cash at Beginning of Period |             |                            | NP            | BB           | +Account=\[1100:1110\]       |
| 370      | Cash at Beginning of Year   | CAL         | E=C.340                    | NP            |              |                              |
| 400      | Cash at Beginning of Period | TOT         | 340+370                    |               |              |                              |

### Modifying a number in selected columns

When you modify a number or calculation in one column of a particular row but don't want to affect other columns on the report, specify **CAL** (Calculation) in the **Format Code** column of the row definition.

- To perform a calculation on all report (**FD**) columns, don't enter a column assignment.
- To restrict a formula to specific columns, enter the column letter, an equal sign (**=**), and then the formula.
- You can specify multiple columns. When you use an at sign (@) with specific column placement, the at sign (@) is related to the row.
- You can enter multiple column formulas in one row. Separate the formulas by using commas.

### Calculation examples

| Calculation            | Action that is created                                                                                                   |
|------------------------|--------------------------------------------------------------------------------------------------------------------------|
| @130\*.75              | For every column, the value in row 130 is multiplied by 0.75. The result is then put in the current row of every column. |
| B=@130\*.75            | The same calculation is performed only on column B.                                                                      |
| A,B,C=(@100/@130)\*.75 | A=(A.100/A.130)\*.75 B=(B.100/B.130)\*.75 C=(C.100/C.130)\*.75                                                           |

### IF/THEN/ELSE statements in a row definition

You can add **IF/THEN/ELSE** statements to any valid calculation and use them with the **CAL** format. Enter **IF/THEN/ELSE** calculation formulas in the cell in the **Related Formulas/Rows/Units** column. **IF/THEN/ELSE** calculation formulas use the following format: IF &lt;true/false statement&gt; THEN &lt;formula&gt; ELSE &lt;formula&gt; The **ELSE &lt;formula&gt;** part of the statement is optional.

#### IF statements

The statement that follows the **IF** statement can be any statement that can be evaluated as true or false. The statement that follows the **IF** statement might involve a simple evaluation, or it might be a complex statement that contains multiple expressions. Here are some examples:

- **IF A.200&gt;0** (Simple evaluation)
- **IF A.200&gt;0 AND A.200&lt;10,000** (Complex statement)
- **IF A.200&gt;10000 OR ((A.340/B.1200)\*2 &lt;1200)** (Complex statement that contains multiple expressions)

The term **Periods** in an **IF** statement represents the number of periods for the report. Use this term to calculate a year-to-date average. For example, when you run a report for period 7 YTD, the statement **B.150/Periods** means that the value in row 150 of column B is divided by 7.

#### THEN and ELSE formulas

The **THEN** and **ELSE** formulas can be any valid calculation, from simple value assignments to complex formulas. For example, the statement **IF A.200&gt;0 THEN A=B.200** means, "If the value in the cell in column A of row 200 is more than 0 (zero), put the value from the cell in column B of row 200 into the cell in column A of the current row." The preceding **IF/THEN** statement puts a value in one column of the current row. However, you can also use an at sign (@) in either true/false evaluations or the formula to represent all columns. Here are some other examples that are described in the following sections:

- **IF A.200 &gt;0 THEN B.200**: If the value in cell A.200 is positive, the value from cell B.200 is put into every column of the current row.
- **IF A.200 &gt;0 THEN @200**: If the value in cell A.200 is positive, the value from each column in row 200 is put into the corresponding column in the current row.
- **IF @200 &gt;0 THEN @200**: If the value in row 200 of the current column is positive, the value from row 200 is put into the same column in the current row.

### Restricting a calculation to a reporting unit in a row definition

To restrict a calculation to a single reporting unit in a reporting tree, so that the resulting amount isn't rolled up to a higher-level unit, use the **\@Unit** code in the **Related Formulas/Rows/Units** cell in the row definition. The **\@Unit** code is listed in column B of the reporting tree, **Unit Name**. When you use the **\@Unit** code, the values aren't rolled up, but the calculation is evaluated at every level of the reporting tree.

> [!NOTE]
> To use this function, a reporting tree must be associated with the row definition.

The calculation row can refer to a calculation row or a financial data row. You record the calculation in the **Related Formulas/Rows/Units** cell of the row definition and the financial data–type restriction. The calculation must use a conditional calculation that starts with an **IF \@Unit** construction. Here's an example: IF @Unit(SALES) THEN @100 ELSE 0 This calculation includes the amount from row 100 in every column of the report, but only for the SALES unit. If multiple units are named SALES, the amount appears in each of those units. Additionally, row 100 can be a financial data row and can be defined as nonprinting. In this case, the amount is prevented from appearing in all units in the tree. You can also limit the amount to a single column of the report, such as column H, by using a column restriction to print the value only in that column of the report. You can include **OR** combinations in an **IF** statement. Here's an example: **IF @Unit(SALES) OR @Unit(SALESWEST) THEN 5 ELSE @100**. You can specify a unit in a calculation-type restriction in one of the following ways:

- Enter a unit name to include units that match. For example, **IF \@Unit(SALES)** enables the calculation for any unit that is named SALES, even if there are several SALES units in the reporting tree.
- Enter the company and unit name to restrict the calculation to specific units in a specific company. For example, enter **IF @Unit (ACME:SALES)** to restrict the calculation to SALES units in the ACME company.
- Enter the full hierarchy code from the reporting tree to restrict the calculation to a specific unit. For example, enter **IF @Unit(SUMMARY^ACME^WEST COAST^SALES)**.

> [!NOTE]
> To find the full hierarchy code, right-click in the reporting tree definition, and then select **Copy Reporting Unit Identifier (H-code)**.

#### Restrict a calculation to a reporting unit

1. In Report Designer, select **Row Definitions**, then open the row definition to modify.
1. Double-click the **Format Code** cell, then select **CAL**.
1. Select the **Related Formulas/Rows/Units** cell, then enter a conditional calculation that starts with an **IF \@Unit** construction.

### IF/THEN/ELSE statements in a column definition

An **IF/THEN/ELSE** statement enables any calculation to depend on the results from any other column. You can refer to other columns, but you can't refer to a report cell in the **IF** statement. You must apply any calculation to the whole column. For example, the statement **IF B&gt;100 THEN B ELSE C\*1.25** means, "If the amount in column B is more than 100, put the value from column B into the **CALC** column. If the amount in column B isn't more than 100, multiply the value in column C by 1.25, and put the result into the **CALC** column." Always follow the **IF** statement with a logic statement that can be evaluated as true or false. The formulas that you use for both the **THEN** statement and the **ELSE** statement can contain references to any number of columns, and these formulas can be as complex as you want to make them.

> [!NOTE]
> You can't put the results of a calculation into any other column. The results must be in the column that contains the formula.

#### Use single quotes and an ampersand for dimension values in a row, column, or tree

You can design reports using dimension values that contain an ampersand (&).

Within any **Link to Financial Dimension** field, you can enter a value such as **'P&L'**. Including single quotes (' ') on both sides of the dimension value indicates that you're using the literal value, such as including the (&) ampersand character.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
