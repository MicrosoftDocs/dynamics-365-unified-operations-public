---
title: View and design financial reports
description: Learn about various exercises that walk you through viewing and creating financial reports for Microsoft Dynamics 365 Finance.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 03/12/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: FinancialReportingSetup
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: cd5f6483-c09b-4c2d-9336-d22eb6ab6e4f
---

# View and design financial reports

[!include [banner](../../../finance/includes/banner.md)]

This article provides exercises that walk you through viewing and creating financial reports for Microsoft Dynamics 365 Finance. Financial reporting includes a viewing experience within the application and a ClickOnce report designer that you use to create and edit financial reports.

## Generate and explore a default financial report

In this exercise, you generate and explore an existing default report. This report includes all accounts and also contains account properties (attributes) for the accounts. You drill into transaction detail, apply dimension filters, and change the currency on the report. First, you update the display order of dimensions for financial reporting. By updating this order, you choose how the dimensions display not only while designing but also when viewing financial reports.

1. Go to **Financial dimension configuration for integrating applications** under the **Dimensions of Chart of Accounts** in General ledger.
2. Move the dimensions to be in the following order:

    1. Main Account
    1. Business Unit
    1. Cost Center
    1. Department

    > [!NOTE]
    > Keep the other dimensions in their current order.

3. Save the dimension configuration. Next, generate a report and explore the data in the report.
1. Go to **Financial reports** under **Inquiries and reports** in General ledger.
1. Select the row for the report named **GL Detail – Default**.
1. Select **Edit**.

    > [!NOTE]
    > You're prompted to download the click-once report designer and to sign in. Use your credentials to sign in.

1. Change the base year to 2021 and select **Generate**. When you generate a report from the report designer, it opens in a new browser tab. You can either explore the report in the new browser tab, or go to your original browser tab and open the report from there by selecting it from the **Financial reports** list.
1. In the opened report, select one of the amounts to drill into the account detail for the report.
1. Once in account detail, select an account with data and **drill to report transaction level**. At the report transaction level, you can see the properties (attributes) that are included in the design of this report. Depending on the transaction and account, some or all of the attributes might display.
1. Close the report transaction level.
1. Select the same or a different account and **open voucher transactions**. Voucher transactions are filtered to the period, year, and account + dimension combination of the account selected. From **Voucher transactions**, you can choose to explore other information about the transaction.
1. Close **Voucher transactions**. Within a financial report, you can choose to view the data either for a different period and year or with different attributes and dimensions applied. Use **Report Options** to make these changes.
1. Select **Report Options**.
1. Select **Add a dimension filter** and choose **Business Unit**.
1. Enter **001** into the field and select **OK**. The report now displays only the data for the 001 Business Unit. This personalized view of the report isn't available for others to view.
1. Close the filtered report. You can display financial reports in any currency that you add to the application.
1. Select **Currency**, and then select **EUR**. The report now displays in euros. Any currency codes or currency symbols included in the report design now display in the applied currency. If no currency symbol is defined for a currency, the currency symbol isn't displayed.
1. Close the **GL Detail** report.
1. Close **Report Designer**.

## Add extra account properties to a report design
In this exercise, you modify an existing default report. You update the row definition to include all accounts and update the column definition to contain account attributes. When you finish the updates, you generate the new report and explore it. Start from the **Financial reports** list.

1. Go to **Financial reports** under **Inquiries and reports** in General ledger.
1. Select the row for the report named **Summary Trial Balance – Default**.
1. Select **Edit**. The report designer opens **Summary Trial Balance – Default**.
1. Select **File**, select **Save As**, and name the report **Detailed Trial Balance with Attributes**.

    > [!NOTE]
    > When you create a new report in report designer, the **Financial reports** list is updated.

1. From the report definition, select the row definition icon to open the **Trial Balance – Default row definition**.
1. Save the row definition as **Detailed Trial Balance with attributes**.
1. With the cursor on row 50, select **Edit**, and then select **Insert row from dimensions**. The **Insert row from dimensions** option lets you choose which dimensions you want in your row definition. For this exercise, build the row definition by using Main Account.
1. Make sure **Main Account** contains all ampersands and select **OK**. The row definition now contains all of the main accounts for legal entity USMF.
1. Scroll down to row 11110 and delete row 11110.
1. In row 11080, select **--- (Underscore amounts)**.
1. In row 11140, type **Total of all accounts** in column B.
1. In column C, select **TOT** from the drop-down.
1. Type **50:11080** in column D.
1. **Save** the row definition. The row definition now contains all of the accounts plus a total row to add all of the accounts together. Next, update the column definition to include extra account attributes.
1. From the **Detailed Trial Balance with attributes** report definition, select the column definition icon to open the **Summary Trial Balance – Default** column definition.
1. Save the column definition as **Detailed Trial Balance with attributes**. The column definition contains financial data columns, a description column, and calculation columns. Add attribute columns to the column definition to provide extra detail about the accounts.
1. Add the following attributes to the column definition:

    - Journal Number
    - Journal Description
    - Transaction Date
    - Created by
    - Last modified by

1. In column I, select **ATTR** as the column type. Then, select **Journal Number** as the attribute category.
1. Continue adding columns for the remaining attributes.
1. In the **Header 2** row, add descriptions for each of the new columns that you added.
1. Save the column definition. Now that you updated the row definition and column definition, add them to the report definition.
1. From the **Detailed Trial Balance with attributes** report definition, select **Detailed Trial Balance with attributes** for both the row definition and column definition.
1. Change the base year to **2012**.
1. **Save** the report definition and **generate** it. When the report finishes generating and opens, you can explore the report as you did in the first exercise. Drill down on different accounts to see how the extra attributes are displayed.
1. Close the **Detailed Trial Balance with Attributes** report.
1. Close **Report Designer**.

## Create a multidimensional report using a reporting tree
In this exercise, you modify an existing default report. You create a reporting tree and add it to a report definition to produce a **Cost Center/Divisional Income Statement**. When you finish the updates, you generate the **Cost Center/Divisional Income Statement** and explore the report by using the reporting tree. Start from the **Financial reports** list.

1. Go to **Financial reports** under Inquiries and reports in General ledger.
1. Select the row for the report named **Income Statement – Default**.
1. Select **Edit**. **Income Statement – Default** opens in the report designer.
1. On the **File** menu, point to **New**, and then select **Reporting Tree Definition**.
1. On the **Edit** menu, select **Insert Reporting Units from Dimensions**.
1. Clear checkboxes for all dimensions, except **Cost Center**.
1. Select the **From Dimension** field for the Cost Center dimension, type **007**, and then press the Tab key. In the **To Dimension** field, type **018**.
1. **Save** the resulting tree with the name **Cost Centers by Division**. After you create the reporting tree, modify it to contain three new rollup units: Marketing, Operations, and Retail.
1. On the **Window** menu, select **Cost Centers by Division**. (If you closed the reporting tree, select it from the **Reporting Tree Definitions** in the navigation pane.)
1. Select unit number two, **Trade Shows**, and select the **Insert Reporting Unit** icon.
1. Double-click the entity column on the blank row, and select **USMF**.
1. Type **Marketing** in columns B and C.
1. Select unit number five, **Service Operations**, and right-click. **Select Insert Reporting Unit**.
1. Repeat step 11.
1. Type **Operations** in columns B and C.
1. Select unit number 12, **Outlet**, and right-click. Select **Insert Reporting Unit**.
1. Repeat step 11.
1. Type **Retail** in columns B and C. The Marketing, Operations, and Retail units display at the same level as the current rollup units. The new units are organized next. You organize reporting units through the right-click options; promote and demote, or by drag and drop.
1. Verify unit 3, **Trade Shows**, is active and right-click.
1. Select **Demote Reporting Unit**. The unit now displays as a child of **Marketing**.
1. Select unit 4, **Marketing Campaign**, and right-click.
1. Select **Demote Reporting Unit**.
1. Select **Service Operations** in the graphical display. Press and hold down the left mouse button while dragging the unit up to **Operations**. Release the left mouse to drop the unit into Operation's rollup. Repeat for **Production**, **Quality Control**, **Logistics**, **Procurement**, and **Administration**.
1. Make **Outlet**, **Super**, **Mall**, and **Online** children of **Retail** by either demoting them or dragging and dropping them.
1. Save the resulting reorganization. After you create and organize the reporting tree, add it to the report definition.
1. On the **Window** menu, select **Income Statement – Default** to open the report definition.
1. Select the **Tree type** drop-down arrow and select **Reporting tree**.
1. Select the Tree drop-down arrow and select **Cost Centers by Division**.
1. Change the base year to **2021**, **save** the changes, and **generate** the report. After the report finishes generating and opens, you can explore the report.
1. Select the **Reporting Tree** drop down to view the reporting units. Alternatively, you can drill down on a row of the report to see all the balances for all units of the reporting tree.
1. Close **Income Statement – Default**.
1. Close **Report Designer**.

## Create a consolidated report using an organization hierarchy
For this exercise, you're modifying an existing default report. You add an organization hierarchy in the report definition to produce a Consolidated Income Statement and Balance Sheet. When you finish the updates, you generate the consolidated report and explore the report using the reporting tree. Start from the Financial reports list.

1. Go to **Financial reports** under **Inquiries and reports** in General ledger.
1. Select the row for the report named **Balance Sheet and Income Statement Side by Side – Default**.
1. Select **Edit**. The report opens in the report designer.
1. Select **File** &gt; **Save As** and name the report **Consolidated Balance Sheet and Income Statement Side by Side**.
1. Change the base year to 2021.
1. Select the **Tree type** drop-down arrow, and select **Organization Hierarchies**.
1. Select the **Tree** drop-down arrow and select **Contoso Holdings**.
1. Save the changes and generate the report. If prompted, select all reporting units. After the report finishes generating and opens, you can explore the report.
1. Select **Report Options**.
1. Select **Add a dimension filter** and choose **Department**.
1. Type **022** into the field and select **OK**.
1. Close the filtered report.
1. Select the **Reporting Tree** drop down to view the reporting units. Alternatively, you can drill down on a row of the report to see all the balances for all units of the reporting tree.
1. Close **Consolidated Balance Sheet and Income Statement Side by Side**.
1. Close **Report Designer**.

## Create a side-by-side departmental report
In this exercise, you create a new report. The report is a side-by-side departmental income statement. You use an existing row definition, but create a new report definition and a new column definition that uses dimension filters. Start from the **Financial reports** list.

1. Go to **Financial reports** under **Inquiries and reports** in General ledger.
1. Select **New**. Report designer opens with a blank report definition open. Your first task is creating the column definition.
1. Create a new column definition by selecting **File**, **New**, and then **Column Definition**.
1. In **Column A**, select **DESC** for the column type.
1. In **Column B**, select **FD** for the column type.
1. Double-click in **the Dimension Filter** field.
1. In the **Dimension** window, double-click the **Department** column.
1. In the **Individual or range** section of the dialog, select the **ellipsis** for the **From** field to display a list of departments.
1. Select department **022**, **Sales & Marketing**, and then select **OK**.
1. Repeat steps 5 through 8 for Departments 23 through 25.
1. On the **Header 2** row for each FD column, type the following department descriptions:

    - Column B – Sales and Marketing
    - Column C – Operations
    - Column D – Finance
    - Column E – IT

1. Save the column definition as Side by Side Departments. Since you're using an existing row definition, modify the report definition to use the newly created column definition and the existing row definition.
1. On the **Window** menu, select **New Report Definition** to open the report definition.
1. Select **Income Statement – Default** as the row definition and **Side by Side Departments** as the column definition.
1. Save the report definition as **Side by Side Departmental Income Statement**.
1. Change the base year to **2021**.
1. Change the detail level to **Financial, Account and Transaction**.
1. **Save** your changes and **generate**. When the report finishes generating and opens, you can explore the report.

## Additional resources
[Financial reporting](../../../finance/general-ledger/financial-reporting-getting-started.md)

[View financial reports](../../../finance/general-ledger/view-financial-reports.md)

[Dynamics 365 Finance Blog](https://community.dynamics.com/365/financeandoperations/b/dynamics-365-finance-blog)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
