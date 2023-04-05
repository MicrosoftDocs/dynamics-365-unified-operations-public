---
title: Column definitions in financial reports
description: This article provides information about column definitions. A column definition is a report component that defines the contents of columns on a report.
author: aprilolson
ms.date: 10/10/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: aolson
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 106601
ms.assetid: 66e72a48-edab-4e9d-815f-596a1623c258
ms.search.form: FinancialReports
---

# Column definitions in financial reports

[!include [banner](../includes/banner.md)]

This article provides information about column definitions. A column definition is a report component, or building block, that defines the contents of columns on a report. Like row definitions, basic column definitions can be used on multiple reports.

## Create and modify a column definition

A column definition can contain two to 255 columns.

### Create a column definition

1. In Report designer, in the navigation pane, click **Column definitions**.
2. On the **File** menu, click **New**, and then click **Column definition**.
3. Add the contents of the column definition.

### Open a column definition

1. In Report designer, in the navigation pane, click **Column definitions**.
2. Double-click a column definition to open it.

### Add a column to a column definition

1. In Report designer, click **Column definitions**, and then open the column definition to modify.
2. Select the column where a new column should be inserted.
3. On the **Edit** menu, click **Insert column**. The new column appears to the left of the column that you selected.

### Delete a column from a column definition

1. In Report designer, click **Column definitions**, and then open the column definition to modify.
2. Select the column to delete.
3. On the **Edit** menu, click **Delete column**.

## Contents of a column definition
A column definition includes the following information:

- A column of the descriptions for the row definition
- Amount columns that show data from the financial data or calculations that are based on other data in the column definition
- Formatting columns
- Attribute columns

This information appears in the following areas in the column definition:

- The headers area of the column definition contains the heading text and formatting that appears in the report. A header can apply to a single column of data, can span multiple columns, or can apply to columns on a conditional basis. The column definition can include as many column header rows as you require.

    > [!NOTE]
    > Column headers apply to each column of data on the report. Report headers apply to the whole report. You define report headers on the **Headers and footers** tab of the report definition.

- Column detail rows are the rows under the header rows in the column definition. Column detail rows define the information that is included on the report. The following table lists and describes the column detail rows.

    | Column detail row name                                                | Description                                                    |
    |-----------------------------------------------------------------------|-------------------------------------------------------------------------|
    | Column Type                                                           | (Required) Specify the type of data in the column.                                      |
    | Book Code/Attribute Category                                          | Specify financial data information for columns of the **FD** and **ATTR** types.     |
    | Fiscal Year Period Periods Covered                                    | Specify financial data information for columns of the **FD** type.              |
    | Formula                                                               | Specify a calculation formula for columns of the **CALC** type.                  |
    | Column Width Extra Spaces Before Column Format Override Print Control | Specify special format options.                                               |
    | Column Restrictions                                                   | Restrict data.                                                                        |
    | Reporting Unit                                                        | Restrict the column, so that it shows data only for the specified reporting unit.      |
    | Currency Display Currency Filter                                      | Format currency.                                                                      |
    | Dimension Filter                                                      | Specify a filter to restrict data to certain financial data reporting units.           |
    | Attribute Filter                                                      | Specify a filter to restrict the financial data.                                      |
    | Start Date End Date                                                   | Restrict the financial data to specific dates.                                    |
    | Justification                                                         | Left-align, center-align, or right-align the description text that is specified in the row definition. |

## Column restrictions in a column definition
You can use column restrictions to specify how a column definition uses data or calculates information. You can also restrict a report column to a specific unit or for specific dates.

> [!NOTE]
> A **Column restriction** code overrides any conflicting setting that is assigned in the row definition.

### Column restrictions cell

The **Column restrictions** cell can include codes that restrict or suppress information, such as row formatting, details, and amounts, for that column.

#### Add a column restriction in a column definition

1. In Report designer, open the column definition to modify.
2. Double-click the **Column restrictions** cell for the column to restrict.
3. In the **Column restrictions** dialog box, select one or more codes in the list, and then click **OK**.

### Column restriction codes

The following table describes the column restriction codes.

| Column restriction code | Description |
|-------------------------|-------------|
| SU                      | Suppress the underscore for a column where either an underscore command (**---**) or a double underscore command (**===**) is entered in the row definition. For example, you might not want to underline amounts that are produced by a percentage calculation. |
| ST                      | Suppress totals, so that only details are shown in the column (for example, a statistical column). |
| SD                      | Suppress details, so that only **TOT** and **CAL** rows (from the row definition) are shown in the column. |
| DR                      | Restrict the amounts in an **FD** column to debit amounts. |
| CR                      | Restrict the amounts in an **FD** column to credit amounts. |
| ADJ                     | Restrict the amounts in the column to period adjustment amounts, if these amounts are available. |
| XAD                     | Restrict the amounts in the column, so that period adjustment amounts are excluded. |
| PT                      | Restrict the amounts in the column, so that only posted transactions are included, if these transactions are available. |
| UPT                     | Restrict the amounts in the column, so that only unposted transactions are included, if these transactions are available.<p><strong>Note:</strong> Not all data providers support unposted transactions. </p> |

### Restrict a column to a reporting unit

1. In Report designer, open the column definition to modify.
2. Double-click the **Reporting unit** cell for the column to restrict.
3. In the **Reporting unit selection** dialog box, in the **Reporting tree** list, select a tree.
4. Expand or collapse the list of units, select a reporting unit, and then click **OK**.

## Format column headers
You can add, modify, and delete the headers that appear at the top of the columns on a report. You can also configure conditional spanning column headers, based on the **Period** field from column definitions and the **Base period** field from report definitions. The base period feature helps save you time when you create rolling forecast reports.

### Create and manage column headers

You can use the **Column header** dialog box to add, modify, and delete the headers that appear at the top of the columns on a report. The following table describes the fields in the **Column header** dialog box.

| Field                 | Description |
|-----------------------|-------------|
| Column header text    | This text appears in the column header. You can type text directly in this field, or click **Insert autoText** to select an option that updates the column header every time that the report is generated. To include multiple autotext codes, click **Insert autoText** again, and then click another code in the list. |
| Format options        | Apply formatting to a column header, such as box or underline. |
| Spread from Spread to | Define the column or columns that the header text applies to. |
| Justification         | Specify how the column header text should be aligned for the column or range of columns that is specified in the **Spread from** and **Spread to** fields. |

### Create a column header

1. In Report designer, open the column definition to modify.
2. Double-click a header cell.
3. In the **Column header** dialog box, enter the column header text. Alternatively, click **Insert autoText**, and select an option.
4. In the **Format options** field, select a format for the header.
5. In the **Spread from** field, enter the letter of the column that the column header should start over. In the **Spread to** field, enter the letter of the column that the column header should end over.
6. Under **Justification**, select whether the column header text to should be left-justified, center-justified, or right-justified.
7. Click **OK**.

### Add a column header row

1. In Report designer, open the column definition to modify.
2. Select a cell in the header row.
3. On the **Edit** menu, click **Insert row**. The new row is inserted above the row that you selected in step 2.

> [!NOTE]
> If you have four or more rows of report headers on a report, the headers will overlap when the report is exported to an Excel worksheet. To view all headers on the report, increase the top margin in the report definition.

### Delete a column header row

1. In Report designer, open the column definition to modify.
2. In the header row, select the cell to delete.
3. On the **Edit** menu, click **Delete row**.

### Create an automatically generated header

Report designer can automatically generate column headers, based on autotext codes. Autotext codes are variables that are updated every time that a report is generated. Any column header can include these codes to specify report information that can vary, such as dates or period numbers. Therefore, you can use one column definition for multiple report definitions, time periods, and reporting trees. Because autotext codes rely on the calendar information from the detail rows of the column definition, they are supported only for **CALC** and **FD** columns. The way that an autotext code appears in the column header cell affects how that information appears on the report. In the **Column Header** dialog box, the autotext codes appear in mixed case. Therefore, the text appears in mixed case on the report. For example, in a standard calendar year, **\@CalMonthLong** resolves month **7** to **July**. If the name of the month should be uppercase (for example **JULY**), enter the autotext code in uppercase characters in the **Column header text** field. For example, enter **\@CALMONTHLONG**. You can mix codes and text. For example, you enter the following header text: **Period \@FiscalPeriod-\@FiscalYear from \@StartDate to \@EndDate**. The report heading that is generated resembles the following text: **Period 1-02 from 01/01/02 to 01/31/02**.

> [!NOTE]
> The format of some of the text, such as the long date, depends on your regional settings on the server. To change these settings, click the **Start** button, click **Control Panel**, and then click **Region and Language**. The following table lists the available autotext options for column headers.


| Autotext option and code                | Description |
|-----------------------------------------|-------------|
| Month name (@CalMonthLong)              | Print the name of the current month in the column heading. If you decide to round the amounts in the report to thousands, millions, or billions, or if you set the column width on the report to fewer than nine characters, the name of the month is abbreviated to the first three characters. |
| Abbreviated month name (@CalMonthShort) | Print the abbreviated name of the month for the selected fiscal period. |
| Period number (@FiscalPeriod)           | Print the numeric form of the fiscal period that is identified for that column. If the column spans multiple periods, the last period in the range is printed. |
| Period description (@FiscalPeriodName)  | Print the fiscal period description that is identified in the financial data. |
| Fiscal year (@FiscalYear)               | Print the fiscal year for the column in numeric form. |
| Calendar year (@CalYear)                | Print the calendar year for the column in numeric form. |
| Start date (@StartDate)                 | Print the start date for the column. |
| End Date (@EndDate)                     | Print the end date for the column. |
| Unit name from tree (@UnitName)         | If you restrict a column to a specific unit of the reporting tree, print the unit name in the column header. |
| Unit description (@UnitDesc)            | If you restrict a column to a specific unit of the reporting tree, print the unit description in the column header. |
| Book Code (@BookCode)                   | Print the book code that is specified in the column. |
| Blank line (@Blank)                     | Insert an empty line in the column header. |

### Create a conditional spanning header

Conditional spanning headers can span multiple columns that are based on specific period data. For example, if you have a budget report for the fiscal year and want to display the actual budgets of past months together with the projected budgets of future months, you can use a conditional spanning header to automatically update the report header. Be aware of the following situations when you create a conditional spanning header:

- Any stop condition (**Spread to** field) that is matched before a start condition (**Spread from** field) is ignored. For example, column B has the spread condition defined as BASE+1 to BASE, BASE is in column C, and BASE+1 is in column D. In this case, the stop condition in column C is ignored, and the printing of the header starts at column D.
- If you specify column headers that overlap, they overlap when they are printed on the report. The report is generated, but the following warning appears in the **Report queue status** field: "Column headers using Base intersect with other column headers and may cause overlapping text." For example, the header definition on column B is B to BASE+1, and the header definition on column D is BASE+1 to F. In this case, the headers are printed on top of each other and are unreadable. Whenever BASE is used in a **Spread from/Spread to** definition, be sure to view the report that is generated, to see whether the headers overlap.
- If you specify BASE in the spread definition in a No Print (**NP**) column, it's ignored, regardless of what is defined in the column definition. Essentially, this scenario is the same as not creating a column header definition.
- For conditional printing columns (**P&lt;B**, **P&gt;=B**), conditional spanning headers behave like any regular column header definition. For example, if the condition is false, any subsequent column matching for the spread condition starts the printing of the header.

#### Create a conditional spanning header

1. In Report designer, open the column definition to modify.
2. Double-click a header cell.
3. In the **Column header** dialog box, enter the column header text. Alternatively, click **Insert autoText**, and select an option.
4. In the **Format options** field, select a formatting style for the header.
5. Specify a period relative to the base period that is specified when the report is generated. In the **Spread from** and **Spread to** fields, enter one of the following values: **BASE**, **BASE-X** or **BASE+X**, where X is the number of periods from the base period. For example, if you enter **BASE** in the **Spread from** field, the conditional spanning column header text starts in the column header where the report definition's **Base period** value equals the column definition's **Period** value. It ends in the column that is indicated in the **Spread to** field. Therefore, if the spread is BASE to M, and the report definition's **Base period** value is **4**, the header starts in the column where the period is set to **4** and ends at column M. Headers stop and start on printing columns only.
6. Under **Justification**, select whether the column header text should be left-justified, center-justified, or right justified.
7. Click **OK**.

#### Example of a conditional spanning header

A user is creating a report for a dynamic six-month forecast. The user wants the word "Actual" to be printed over the columns that contain actual data, and the word "Budget" to be printed over the columns that contain budget forecasts. Each month that the report is run, there is one more actual column and one less budget column. Although the user can modify the column definition manually each time that the report is generated to adjust the headers, to save time and effort, the user decides to create conditional spanning headers that will automatically create headers over the appropriate columns each time that the report is run. The user opens Report Designer, clicks **Column Definition** in the navigation pane, and opens the column definition for the report. The user then enters the following information. The base period in the report definition is 4.

|  Format   |  A   | B     | C      | D       | E        | F       | G       | H      | I             | J             | K             | L             | M             |
|-----------|------|-------|--------|---------|----------|---------|---------|---------|-------------|---------------|---------------|---------------|---------------|
| Header 1   |    | Actual    | Budget        |         |         |        |       |          |        |               |               |               |               |
| Header 2   |      | @CalMonthLong | @CalMonthLong | @CalMonthLong | @CalMonthLong | @CalMonthLong | @CalMonthLong | @CalMonthLong | @CalMonthLong | @CalMonthLong | @CalMonthLong | @CalMonthLong | @CalMonthLong |
| Header 3    |      |       |        |        |        |         |        |          |               |               |               |               |               |
| Column Type  | DESC | FD   | FD     | FD    | FD   | FD    | FD      | FD            | FD            | FD            | FD            | FD            | FD            |
| Book Code/Attribute |      | ACTUAL        | BUDGET2012    | ACTUAL        | BUDGET2012    | ACTUAL        | BUDGET2012    | ACTUAL        | BUDGET2012    | ACTUAL        | BUDGET2012    | ACTUAL        | BUDGET2012    |
| Fiscal Year |  | BASE   | BASE   | BASE   | BASE   | BASE    | BASE    | BASE     | BASE          | BASE          | BASE          | BASE          | BASE          |
| Period  |     | 1      | 1       | 2      | 2      | 3       | 3       | 4        | 4             | 5             | 5             | 6             | 6             |
| Periods Covered     |      | PERIODIC      | PERIODIC      | PERIODIC      | PERIODIC      | PERIODIC      | PERIODIC      | PERIODIC      | PERIODIC      | PERIODIC      | PERIODIC      | PERIODIC      | PERIODIC      |
| Column Width   | 30   | 10    | 10     | 10     | 10    | 10    | 10    | 10     | 10            | 10            | 10            | 10            | 10            |
| Print Control  |    | P&lt;=B    | P&gt;B   | P&lt;=B  | P&gt;B   | P&lt;=B   | P&gt;B   | P&lt;=B  | P&gt;B   | P&lt;=B  | P&gt;B   | P&lt;=B       | P&gt;B        |

The user double-clicks a column header cell in column B to open the **Column header** dialog box, and enters the following information.

| Field              | Value                 |
|--------------------|-----------------------|
| Column header text | Actual                |
| Insert AutoText    | No selection is made. |
| Format options     | Box                   |
| Justification      | No selection is made. |
| Spread from        | B                     |
| Spread to          | BASE                  |

After entering information, the user clicks **OK**. The user then double-clicks the column header cell in column C to open the **Column header** dialog box, and enters the following information.

| Field              | Value                 |
|--------------------|-----------------------|
| Column header text | Budget                |
| Insert AutoText    | No selection is made. |
| Format options     | Box                   |
| Justification      | No selection is made. |
| Spread from        | BASE+1                |
| Spread to          | M                     |

Now, every time that this report is generated, the word "Actual" will be printed over the columns that contain actual data, and the word "Budget" will be printed over the columns that contain budget forecasts. Additionally, the number of columns will be adjusted each month.

## Apply column justification
The **Justification** cell is used to apply justification formatting to a description column in a report. This option affects only the column descriptions, not the actual values.

1. In Report designer, open the column definition to modify.
2. Double-click the **Justification** cell.
3. Select one of the following values in the list:

    - **None** – No justification is applied.
    - **Left** – Left-align the column descriptions.
    - **Center** – Center-align the column descriptions.
    - **Right** – Right-align the column descriptions.

## Add special formatting options
In the column definition, the formatting column detail rows apply special formatting to selected columns. Although some of the **Print control** options and **Column restrictions** options are specific to **FD** columns, most of the options apply to all column types. The formatting that is specified in the column definition overrides the formatting that is specified in the report definition. However, the formatting that is specified in the row definition overrides the formatting that is specified in the column definition. The following rows are considered formatting rows:

- Column Width
- Extra Spaces Before Column
- Format/Currency Override
- Print Control

### Changing the column width

The **Column width** cell specifies the number of characters to use for the width of this column on the printed report. Column width is important for columns that contain amounts (columns of the **CALC**, **WKS**, or **FD** type), descriptions (columns of the **DESC** type), or fill (columns of the **FILL** type). By default, the **AutoFit** option is selected, so that the width of each column is automatically adjusted to fit the contents.

#### Specify the width of a column on a report

1. In Report designer, open the column definition to modify.
2. In the **Column width** cell, enter the number of spaces for the width of the column. The maximum width of any column is 255 characters (this number includes cents, commas, and parentheses). Alternatively, to enable report designer to select the appropriate width for the column, based on the cell content, double-click the **Column width** cell, and then click **AutoFit**.

### Add space between columns

The **Extra spaces before column** cell specifies the width of the separator between one column and adjacent columns in the column definition. The **Extra spaces before column** setting affects all column detail rows for the column, but not the column header rows. Use this option to separate groups of columns or to add a few spaces before the description, so that the description column is indented from the left-aligned titles on the report. The default number of spaces between each column is two. You can change this setting on the **Settings** tab in the report definition.

#### Specify the space between columns

1. In Report designer, open the column definition to modify.
2. In the **Extra spaces before column** cell, enter the number of spaces to insert between columns.

### Specify a format currency override

The **Format/Currency override** cell specifies the formatting of the decimal, currency, and percentage amounts in the column. This formatting overrides any formatting that is specified in the report definition or system defaults.

#### Assign a format currency override to a report column

1. In Report designer, open the column definition to modify.
2. Double-click a **Format/Currency override** cell in an amount column.
3. In the **Format override** dialog box, select formatting options.

### Add a print control code

The **Print control** cell can contain codes that adjust the display or the printing characteristics of a column. There are two types of print control codes: regular print control codes and conditional print control codes.

#### Regular print control codes

| Print control code | Translation                                     | Description |
|--------------------|-------------------------------------------------|-------------|
| NP                 | Nonprinting                                     | Exclude the amounts in this column from the report that is printed and from calculations. To include a non-printing column in a calculation, refer to the column directly in the calculation formula. For example, the non-printing column C is included in the following calculation: **B+C+D**. However, the non-printing column C isn't included in the following calculation: **B:D**. |
| XCR                | Change sign if typical balance of row is credit | Create a budget or comparative report where any unfavorable variance (such as a revenue shortfall or an expense overrun) is always negative. Apply this code to a **CALC** column to reverse the sign of the column amount if the typical balance of a given row is a credit (as identified by a **C** in the **Normal Balance** column of the row definition).<p><strong>Note:</strong> For <strong>TOT</strong> rows and </strong>CAL</strong> rows that typically carry a credit balance, be sure to enter a <strong>C</strong> in the <strong>Normal Balance</strong> column in the row definition.</p> |
| X0            | Suppress column if all zeros or blanks   | Exclude an **FD** column from the report if all cells in that column are either empty or contain zeros. |
| SR                 | Suppress rounding                               | Prevent the amounts in this column from being rounded. |
| XR                 | Suppress rollup                                 | Suppress a rollup. If the report uses a reporting tree, the amounts in this column aren't rolled up into subsequent parent nodes. |
| RP                 | Repeat column on each page                      | Repeat a specified column on each page of a report. For example, you can use the **RP** print control code to include a column of the **ROW** type that pulls in row codes on every page. |
| WT                 |  Wrap text                                      |  If the text in a column is too long to fit the space, wrap the text to keep all the text in the column. |

#### Conditional print control codes

| Conditional print control code | Description                                                                             |
|--------------------------------|-----------------------------------------------------------------------------------------|
| (none)                         | Clear the conditional print selection.                                                  |
| P&lt;B                         | Display a specified column only if the period is less than the base period.             |
| P&gt;B                         | Display a specified column only if the period is more than the base period.             |
| P=B                            | Display a specified column only if the period is equal to the base period.              |
| P&lt;=B                        | Display a specified column only if the period is less than or equal to the base period. |
| P&gt;=B                        | Display a specified column only if the period is more than or equal to the base period. |

#### Add print control codes to a report column

1. In Report designer, open the column definition to modify.
2. Double-click the **Print control** cell.
3. In the **Print control** dialog box, select a code in the **Select print control options** list. To select more than one code, hold down the Ctrl key while you select the codes.
4. Select an option in the **Conditional print options** field. By default, **(none)** is selected. You can select only one conditional print code at a time.
5. Click **OK**.

> [!TIP]
> You can also enter the print codes directly in the **Print control** cell. Separate multiple print control codes with a comma.

## Column types
The type of information that each column on a report includes is specified by the value in the **Column Type** row in the column definition. Each column definition must contain at least one description (**DESC**) column and one amount (**FD**, **WKS**, or **CALC**) column.

> [!NOTE]
> The column type codes don't apply to all accounting systems. If you select a type that isn't valid for your accounting system, that column is blank on the report.

### Specify a column type

1. In Report designer, open the column definition to modify.
2. In the appropriate column, double-click a cell in the **Column type** row.
3. Select a column type in the list. The following table describes the various column types.

    <table>
    <thead>
    <tr>
    <th>Column type code</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>FD</td>
    <td>Display financial data when you use a <strong>Link to Financial Dimensions</strong> column in the row definition. When you select the <strong>FD</strong> column type, default settings are automatically specified for the following rows:
    <ul>
    <li><strong>Book Code/Attribute Category:</strong> ACTUAL</li>
    <li><strong>Book Code/Attribute Category:</strong> ACTUAL</li>
    <li><strong>Fiscal Year:</strong> BASE</li>
    <li><strong>Period:</strong> BASE</li>
    <li><strong>Periods Covered:</strong> PERIODIC</li>
    <li><strong>Column Width:</strong> 14</li>
    </ul>
    You can change these default settings.</td>
    </tr>
    <tr>
    <td>CALC</td>
    <td>Display the result of a simple or complex calculation that is specified in the <strong>Formula</strong> cell. For more information, see <a href="advanced-formatting-options-financial-reporting.md">Advanced formatting options in financial reporting</a>.</td>
    </tr>
    <tr>
    <td>DESC</td>
    <td>Display the row description from the row definition. Although the description column is often the first column on the report, it can be in any position.</td>
    </tr>
    <tr>
    <td>ROW</td>
    <td>Display the individual row codes for financial rows from the <strong>Row Code</strong> column in the row definition. For more information, see <a href="row-definitions-financial-reporting.md">Row definitions in financial reporting</a>.</td>
    </tr>
    <tr>
    <td>ACCT (Account codes)</td>
    <td>Display the financial data segment values or dimension values that apply to each row. For account and transaction detail reports, the fully qualified account is printed (for example, <strong>110140-070-0101</strong>). If ranges have been specified in the <strong>Link to Financial Dimensions</strong> column in an associated row definition, the range is enclosed in square brackets and is treated as a single value (for example, <strong>[110140:110700]-070-[0101:0200]</strong>). For financial reports and high-level reports that are a combination of several accounts, the financial data link from the row definition is printed (for example, <strong>1100:1200</strong>).</td>
    </tr>
    <tr>
    <td>FILL</td>
    <td>Fill the cell with a character that you enclose in single quotation marks. If you don't enter a character, the column is empty. For example, to fill a column with an ellipsis (...), enter <strong>FILL</strong> <strong>'.'</strong>.</td>
    </tr>
    <tr>
    <td>PAGE</td>
    <td>Insert a vertical page break in the report. The columns that are to the right of the <strong>PAGE</strong> column appear on a different page.</td>
    </tr>
    <tr>
    <td>ATTR</td>
    <td>If your accounting system supports attributes, display an account or transaction attribute in the column. An attribute, which must apply to a single full account, extracts underlying account or transaction information from the financial data. Account-level attributes display data from the account, and transaction-level attributes display data that occurred at the time that the transaction was posted. If you select <strong>ATTR</strong> as the column type, specify the attribute category in the <strong>Book Code/Attribute Category</strong> detail row of the column definition.</td>
    </tr>
    </tbody>
    </table>

### Financial Dimensions column

The following **Column definition** row definitions apply to columns that have a column type of **FD** (Amounts from financial dimensions).

#### Book Code/Attribute Category cell

The **Book code/Attribute category** cell identifies the book code for the data in the **FD** column. A column definition can include multiple actual, budget, and statistical columns. A column definition can also display different periods, such as current or year-to-date, and different amounts. The list of book codes reflects the actual, budget, and statistical (non-financial) options that have been established in your financial data.

#### Fiscal year cell

The **Fiscal year** cell identifies the fiscal year that the column should include. The year can be relative to the base year that is specified when the report is generated. The following options are available.

| Option  | Description                                                                                                                  |
|---------|------------------------------------------------------------------------------------------------------------------------------|
| BASE    | Use the base year that is specified at report time.                                                                          |
| BASE+\# | Use the year that is \# years after the base year. For example, to use the third year after the base year, enter **BASE+3**. |
| BASE-\# | Use the year that is \# years before the base year. For example, to use the previous year, enter **BASE-1**.                 |
| \#      | Enter the actual fiscal year.                                                                                                |

#### Period cell

The **Period** cell identifies the fiscal periods that the column should include. The period can be relative to the base period that is specified when the report is generated. The following options are available.

| Option          | Description |
|-----------------|-------------|
| BASE            | Use the base period. |
| BASE+\#         | Use the period that is \# periods after the base period. For example, to use the third period after the base period, enter **BASE+3**. |
| BASE-\#         | Use the period that is \# periods before the base period. For example, to use the previous period, enter **BASE-1**. |
| BASE-\#:BASE    | Use multiple periods, from several periods before the base period through the base period. For example, to use the three previous periods and the base period, enter **BASE-3:BASE**. |
| BASE:BASE+\#    | Use multiple periods, from the base period through several periods after the base period. For example, to use the base period and the following two periods, enter **BASE:BASE+2**. |
| BASE-\#:BASE+\# | Use multiple periods, from several periods before the base period to several periods after the base period. For example, to use the three previous periods, the base period, and the following two periods, enter **BASE-3:BASE+2**. |
| 1:BASE          | Use multiple periods, from the first period through the base period. |
| \#              | Always use a specific period number. We don't recommend that you use this option, because it reduces the flexibility of the column definition. |
| \#:\#           | Always use a specific range of periods. We don't recommend that you use this option, because it reduces the flexibility of the column definition. |

You can go beyond fiscal year boundaries in any of the period specifications, and you can mix years in a range of periods. For example, you specify the periods as **BASE-5** (to represent the past six periods) and run a report that has a base period of 2. In this case, the report shows data for the first two periods of the specified fiscal year and the last four periods of the previous fiscal year.

### Specify the periods for an FD column

1. In Report designer, open the column definition to modify.
2. In an **FD** column, double-click the cell in the **Period** row, and then select an option in the list.
3. In the formula bar above the navigation pane, or in the **Period** cell, complete the formula. Replace any number sign (\#) with the appropriate value.

#### Periods covered cell

The **Periods covered** cell identifies the amount that the column should display. This amount is relative to the value in the **Fiscal year** and **Period** cells for the column. The following options are available.

| Option      | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| PERIODIC    | Display the sum of the activity for the current period or range of periods. |
| PERIODIC/BB | Display the beginning balance for the current period or range of periods.   |
| YTD         | Display the sum of the year-to-date activity.                               |
| YTD/BB      | Display the beginning balance for the year.                                 |

### Specify the periods that are covered for an FD column

1. In Report designer, open the column definition to modify.
2. In an **FD** column, double-click the cell in the **Periods covered** row, and select an option in the list.

### Attribute filter in a column definition

Attributes are financial data values that further define an account or transaction. The account attributes include **Asset**, **Liability**, **Revenue**, and **Expense**. The transaction attributes include **Transaction description** and **Transaction apply date**. Attribute support might differ between Microsoft Dynamics 365 Finanace. The **Attribute filter** cell restricts the data in **FD** columns to specific values or ranges for attribute categories. Although this feature can be used together with an **ATTR** column, the **ATTR** column isn't required. In an **FD** column, there is a limit on the accounts or transactions that the report will include from the attribute filter.

> [!NOTE]
> To see which attributes your ERP system supports, see the integration guide for your system.

#### Apply an attribute filter for an FD column on a report

1. In Report designer, open the column definition to modify.
2. Double-click the **Attribute filter** cell for an **FD** column.
3. In the **Attribute filter** dialog box, double-click a cell in the **Attribute** column, and then select the filter type.
4. To further limit the results, enter a range in the **From** and **To** columns. The **From** cell must contain a value.
5. Click **OK**.

#### Example of an attribute filter

The following example shows part of a column description that has an account attribute in the **Book code/Attribute category** row. The attribute filter for this column specifies the range of values to include in the report.

|      Filter                  | A    | B                   |
|------------------------------|------|---------------------|
| Column Type                  | DESC | FD                  |
| Book Code/Attribute Category |      | ACTUAL              |
| Fiscal Year                  |      | BASE                |
| Period                       |      | 1:BASE              |
| Periods Covered              |      | PERIODIC            |
| ...                          |      |                     |
| Column Width                 | 30   |                     |
| ...                          |      |                     |
| Attribute Filter             |      | Reference=\[01:10\] |

### Dimension filter in a column definition

A dimension filter is used to restrict the **FD** column to specific dimension values. The filter can include a single dimension, a range of dimensions, or a group of dimensions. The filter can also include dimension value sets. Because dimension values can vary, a ..\\financial-dimensions\\dimension-based system doesn't have to correspond to an exact length. The filter is applied, regardless of whether the report includes a reporting tree. You can use a wildcard character (\* or ?) in any position. When you specify multiple accounts, put a comma between accounts, as in the following example: +Account=\[1200\], +Account=\[1100\], Department=\[01?\] To receive all departments for a specific account, you can exclude the Department dimension from the dimension filter. For example, both of the following dimension filters are handled in the same way:

- +Account=\[1100\],Department
- +Account=\[1100\]

You can also use any combination of alphanumeric characters for exact matching, and you can define partial dimensions. For example, **Location = \[10\*\]** includes all location dimension values that begin with 10.

#### Apply a dimension filter for a column on a report

1. In Report designer, open the column definition to modify.
2. Double-click the **Dimension filter** cell for an **FD** column.
3. In the **Dimensions** dialog box, enter the filters to apply.
4. Click **OK**.

### Format a multiple-currency report in a column definition

A multiple-currency report can display amounts in the ledger's accounting currency, the ledger's reporting, the originating transaction currency, or the translated reporting currency. A company's accounting currency is defined in the Ledgers setup. Don't confuse this setting with the operating system's regional options setting, where you can configure the default currency symbols that are used on reports. The following currency-related cells are available in the column definition:

- **Currency display** – Specify the type of currency (accounting, reporting, transaction, or translated reporting) that the transactions are displayed in. Translated to a reporting currency functionality is sometimes referred to as currency translation. Currency translation is the ability to report general ledger amounts in a currency that might not be the functional or reporting currency of the company or the currency that the transaction was entered in.
- **Currency filter** – Specify a currency filter. Only transactions that are entered in the selected currency are displayed on the report.


To determine a company's accounting currency, follow these steps.

1. In Report designer, on the **Company** menu, click **Companies**.
2. In the **Companies** dialog box, select a company, and then click **View**.
3. In the **View company** dialog box, under **Regional options**, you can view the currency that is defined for the selected company.

#### Specify the currency on a multiple-currency report

1. In Report designer, open the column definition to modify.
2. Double-click the **Currency cisplay** cell in the appropriate **FD** column, and then select the option for displaying currency information: **Ledger accounting currency**, **Ledger reporting**, transaction currency, or select to translate to a different reporting currency.
3. Double-click the **Currency Filter** cell in the appropriate **FD** column, and then select the appropriate currency code in the list. Only transactions that are entered in this currency are displayed on the report.


### Example for currency display and currency filter cells

A user has made the following currency selections in their column definition:

- **Currency filter:** Yen
- **Currency display:** Accounting currency from Ledger (U.S. dollars)

Because of the currency filter that is selected, the report includes only transactions that were entered in Japanese yen (JPY). Because of the currency display that is selected, the report displays those transactions in the accounting currency, U.S. dollars (USD).

#### Currency filter and currency display combinations

The following table shows the report results that can occur for various combinations of the options in **Currency display** and **Currency filter** cells because of the selections that were made. The functional currency is USD.


| Currency Display cell                        | Currency Filter cell | Report result |
|----------------------------------------------|----------------------|---------------|
| Transaction currency                 | **YEN**              | **Y6,000** – The result shows only transactions that were entered in JPY. |
| Accounting currency from ledger | **YEN**              |**$60** – The result shows only transactions that were entered in JPY and displays those transactions in USD.<p><strong>Note:</strong> The conversion rate is approximately 100 JPY per USD.</p> |
| Accounting currency from ledger | Empty                | **$2,310** – The result shows all data in the accounting currency that is specified in the Ledger.<p><strong>Note:</strong> This amount is the sum of all transactions in accounting currency.</p> |
| Transaction currency                 | Empty                | **$2,250** – The result shows all amounts in the currency that the transaction was performed in. This means the total is adding together amounts from different currencies. |

### Calculation column in a column definition

A column type of **CALC** in a column definition supports complex calculations in the **Formula** cell, and can include the **+**, **-**, **\***, and **/** operators, and also **IF/THEN/ELSE** statements. A calculation column can also refer to any other column, even subsequent columns. Additionally, a calculation column can also include the fiscal year and period to support headers for the column. The calculation formula can be up to 1,024 characters long. To express the calculation result as a percentage, use a special format override.

> [!NOTE]
> The results of calculation formulas don't include the values in non-printing column ranges. For example, **A:D** prints **0** (zero), whereas **A+B+C** for non-printing values calculates the value.

#### Operators in calculation columns

To add, subtract, multiply, or divide columns, enter the column letters in the order of computation, and then use the appropriate operator to separate each column letter. The following table explains the operators that you can use in a calculation column.

| Operator | Example calculation | Description |
|----------|---------------------|-------------|
| +        | A+C                 | Add the amount in column A to the amount in column C. |
| :        | A:C A:C-D           | Add a range of consecutive columns. For example, the formula **A:C** adds the sums of columns A through C, and the formula **A:C-D** adds the sums of columns A through C, and then subtracts the amount in column D. |
| -        | A-C                 | Subtract the amount in column A from the amount in column C.<p><strong>Note:</strong> You can also use the minus sign (-) to reverse the signs in a column. For example, use <strong>-A+B</strong> to add the reverse of the amount in column A to the amount in column B.</p> |
| \*       | A\*C                | Multiply the amount in column A by the amount in column C. |
| /        | A/C                 | Divide the amount in column A by the amount in column C. |

#### Use a calculation formula in a column definition

1. In Report designer, open the column definition to modify.
2. In the appropriate **CALC** column, enter a formula in the **Formula** cell.

#### Complex calculations

A complex calculation can contain any combination of cell references, operators, values, and levels of nested parentheses. For example, to compute the average of columns A and B, use the calculation formula **((A+B)/2)**.

#### Specify report cells in a column calculation

You can refer to a specific report cell by entering a column letter and a row code. For example, **B.100** refers to row code 100 in column B. You can divide a whole column by a specific report cell amount that is in the same column. For example, the calculation **B/B.100** means that the amount in column B should be divided by the value in row code 100 in column B. If the calculation refers to a column that depends on another column, the dependent column is resolved first. If you refer a column to another column that refers back to the first column, you will cause a circular reference error.

> [!NOTE]
> The calculation might be incorrect if you change the calculation priority for the report. You can set the calculation priority on the **Settings** tab of the report definition.

#### Multiply or divide a column by a base row

You can create a column that displays all the values in a specified column as a percentage of a base number. Therefore, you can show relationships between rows, such as a percentage of a sales row or a percentage of a total expenses row. To multiply or divide each row in a specific column by a base row, enter the column to use in the calculation, and then enter **\*BASEROW** or **/BASEROW**. For example, enter **C\*BASEROW** or **C/BASEROW**.

> [!NOTE]
> When you use a base row calculation in a column definition, make sure that each row definition that is used with this column definition contains at least one base row for calculations.

#### Divide the amount in a column by the number of periods

You can divide the amount in a column by a specified number of periods. For example, the formula **B/Periods** divides the value in column B by the number of periods in column B. If the calculation spans multiple columns, specify the number of periods to use in the calculation. For example, the formula **(B+C)/Periods** adds the amounts in column B and column C, and then divides the result by the period value.

## Additional resources

[Row definitions in financial report designer](row-definitions-financial-reporting.md)

[Advanced formatting options in financial reporting](advanced-formatting-options-financial-reporting.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
