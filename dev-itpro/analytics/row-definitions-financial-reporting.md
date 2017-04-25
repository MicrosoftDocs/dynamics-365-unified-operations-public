---
# required metadata

title: Row definitions in financial report designer
description: A row definition is a report component, or building block, that specifies the contents of each row on a financial report. A row definition can be combined with column definitions, reporting tree definitions, and report definitions to create a building block group that can be used by multiple companies.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: FinancialReports
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: Management Reporter, Core
# ms.tgt_pltfrm: 
ms.custom: 68873
ms.assetid: 2fd7b5da-700f-48cb-9003-90c0d82f818f
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Row definitions in financial report designer

[!include[banner](../includes/banner.md)]


A row definition is a report component, or building block, that specifies the contents of each row on a financial report. A row definition can be combined with column definitions, reporting tree definitions, and report definitions to create a building block group that can be used by multiple companies.

Create a row definition
-----------------------

1.  In Report Designer, in the navigation pane, click **Row Definitions**.
2.  On the **File** menu, click **New**, and then click **Row Definition**. For more information about the content of each cell, see [Modify row definition cells](modify-row-definition-cells-financial-reporting.md).

## Open a row definition
1.  In Report Designer, in the navigation pane, click **Row Definitions**.
2.  Double-click the name of the row definition to open.
3.  To view any building blocks that are associated with the row definition, right-click the row definition, and then select **Associations**.

## Contents of a row definition
A row definition can contain up to 20,000 financial dimension rows and can include the following information:

-   Descriptive text that adds meaning to the report by creating section headings, lines, and spaces, such as **Cash** or **Total Revenue**
-   Links to financial data, which can include dimension values in the Microsoft Dynamics 365 for Operations **Note:** You can set up a row definition to pull data from the financial dimensions system every time that the report is generated.
-   Row totals and formulas that are based on the linked financial data

Usually, each row in a row definition contains one of the following types of information:

-   References to the financial dimensions system
-   Totals or calculations that are based on the data
-   Formatting

There are two methods for entering information in a row definition:

-   Manually enter row information in a new row definition. For more information, see [Modify row definition cells](modify-row-definition-cells-financial-reporting.md).
-   Use report designer to pull row information directly from the financial dimensions. For more information, see the "Related formulas/rows/units" section in [Modify row definition cells](modify-row-definition-cells-financial-reporting.md).

## Add dimensions in a row definition
A dimension is an intersection of data and values. You can group data and values in report designer. You can then classify and analyze transactions in more detail. You can use the **Insert Rows from Dimensions** dialog box to add multiple rows to a row definition at the same time. The dialog box displays one column for each dimension. The following table describes the information that you can specify for each dimension.

| Option                | Description                                                                                                                                                                                                                                                                      |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dimension             | The pattern that identifies the dimension to add to the row definition. This pattern contains one ampersand (&) or number sign (\#) for each position in the dimensions. Generally, use all ampersands for the Main Account dimension and all number signs for other dimensions. |
| Dimension Range Start | The first value for this dimension to add to the row definition.                                                                                                                                                                                                                 |
| Dimension Range End   | The last value for this dimension to add to the row definition.                                                                                                                                                                                                                  |

To add dimensions to a row definition, follow these steps.

1.  In Report Designer, click **Row Definitions**, and then open the row definition to modify.
2.  On the **Edit** menu, click **Insert Rows from Dimensions**.
3.  In the **Insert Rows from Dimensions** dialog box, in the **Dimensions** row, select the cell for the dimension to transfer to the row definition, and then click **All &&&**.
4.  To limit the row definition to a specific range of dimension values, enter the starting dimension value in the **Dimension Range Start** cell, and then enter the ending dimension value in the **Dimension Range End** cell. To include all values for the selected dimension, leave these cells empty. **Note:** Wildcard characters (\* or ?) in dimension ranges might not return all the results that you want, depending on how the ERP database collates data.
5.  In the **Starting row code** field, specify the row code for the first dimension value to add to the row definition.
6.  In the **Increment each row by** field, specify the gap between consecutive row codes. For example, if the first row code is 100, and the increment value is 30, the first new rows have the codes 100, 130, 160, 190, and 220. Use an increment value that provides enough space to insert new format and formula rows.
7.  Click **OK**. For each of the selected dimension values, one line is added to the row definition.

## Adjust rounding in a row definition
If you have a balance sheet where the amounts are rounded, the totals might not balance. This issue can occur if, for example, you use the rounding option on a balance sheet report and the report definition also specifies rounding. You can use the **Rounding adjustment** option in the row definition to balance the amounts in the balance sheets. You can turn rounding off or modify it on the **Settings** tab of the report definition. The following table shows how amounts are rounded. In this table, the totals of rows 100 and 200 differ when rounding is turned on.

| Row code | Amounts without rounding | Amount with rounding to whole thousands |
|----------|--------------------------|-----------------------------------------|
| 100      | 3,600                    | 4                                       |
| 200      | 3,700                    | 4                                       |
| Total    | 7,300                    | 8                                       |

To adjust rounding in a balance sheet, follow these steps.

1.  In Report Designer, click **Row Definitions**, and then open the row definition to modify.
2.  On the **Edit** menu, click **Rounding Adjustment**.
3.  In the **Rounding Adjustments** dialog box, enter the following values:
    -   **Rounding adjustment row** – The row code for the row that should be adjusted to balance the balance sheet.
    -   **Total assets row** – The row code for the row in the balance sheet that contains the total assets.
    -   **Total liabilities and equity row** – The row code for the row in the balance sheet that contains the total liabilities and equity.
    -   **Adjustment amount limit** – A positive whole number that specifies the limit on automatic adjustments. This amount is compared with the absolute value of the actual rounding difference.

    **Note:** These row codes must be linked to your financial data. In other words, the row must have a dimension value in its **Link to Financial Dimensions** cell. Do **not** reference a description (**DESC**), calculated (**CALC**), or totaled (**TOT**) row.

The amounts in your balance sheet will now balance evenly when rounding is turned on. **Note:** The adjustment limit is applied based on the **Rounding precision** option that is specified for the report definition. For example, if you round your report to thousands and enter **2** in the **Adjustment amount limit** field, you receive a warning message when the value in the **Rounding adjustment row** field increases or decreases by more than 2,000.

## Format row and column text
You can customize the appearance of your reports by changing fonts and formatting text. The following sections explain how to format the appearance of rows and columns on reports.

### Manage font styles

You can create and modify font styles for your report. You can then apply those styles to the document, or to a specific row or column on a report.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Create a font style</td>
<td><ol>
<li>In Report Designer, on the <strong>Format</strong> menu, click <strong>Styles and Formatting</strong>.</li>
<li>In the <strong>Styles and Formatting</strong> dialog box, click <strong>New</strong>, and then enter a unique name for the new style.</li>
<li>Make your font selections, and then click <strong>OK</strong>.</li>
</ol></td>
</tr>
<tr class="even">
<td>Modify a font style</td>
<td><ol>
<li>In Report Designer, on the <strong>Format</strong> menu, click <strong>Styles and Formatting</strong>.</li>
<li>In the <strong>Styles and Formatting</strong> dialog box, select a style to modify, and then click <strong>Modify</strong>.</li>
<li>Make your font selections, and then click <strong>OK</strong>.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Apply a font style</td>
<td><ol>
<li>In Report Designer, in a definition or column definition, or in headers and footers, select one or more cells.</li>
<li>In the <strong>Style</strong> list on the toolbar, select a font style.</li>
</ol></td>
</tr>
</tbody>
</table>

### Format row text

The formatting that is specified in the row definition overrides any formatting that is specified in the column definition and the report definition. You can modify the text format by using the controls on the formatting toolbar. These controls are standard Microsoft Windows controls.

1.  In Report Designer, open the row definition to modify.
2.  Select the cells to format. To select multiple cells, hold down the Ctrl key while you select the cell.
3.  Click the toolbar button of the format to apply. For example, to indent a row, select the row, and then click **Increase Indent** ![Increase Indent](https://i-technet.sec.s-msft.com/dynimg/IC679497.gif "Increase Indent") on the toolbar.

### Adjust columns while you design reports

To make it easier to view the columns that you're working on in the row definition, you can adjust the width of a column, and can also hide (minimize) or show columns in the view pane. The modifications that you make affect only the on-screen appearance of the columns. They don't affect the column formatting on reports.

### Change the width of a column in the view pane

1.  In Report Designer, open the row definition to modify.
2.  On the **Format** menu, select **Column Width**.
3.  In the **Column Width** dialog box, enter a value, and then click **OK**. Alternatively, you can drag the right boundary of a column heading cell to change the width of the column.

### Hide columns in the view pane

1.  In Report Designer, open the row definition to modify.
2.  Select the column or columns to minimize.
3.  Right-click, and then click **Hide**.

### Show all hidden columns in the view pane

1.  In Report Designer, open the row definition to modify.
2.  Right-click the minimized column to display, and then click **Unhide**.


See also
--------

[Financial reporting](financial-reporting-intro.md)


