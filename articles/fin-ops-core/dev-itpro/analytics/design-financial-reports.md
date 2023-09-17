---
title: View and design financial reports
description: This article provides exercises that walk you through viewing and creating financial reports for Microsoft Dynamics 365 Finance.
author: jcart1106
ms.date: 11/21/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: jcart
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: cd5f6483-c09b-4c2d-9336-d22eb6ab6e4f
ms.search.form: FinancialReportingSetup
---

# View and design financial reports

[!include [banner](../includes/banner.md)]

This article provides exercises that walk you through viewing and creating financial reports for Microsoft Dynamics 365 Finance. Financial reporting consists of a viewing experience within the application and a click-once report designer that lets you create and edit financial reports.

## Exercise 1: Generate and explore a default financial report

For this exercise, you will be generating and exploring an existing default report. This report includes all accounts and also contains account properties (attributes) for the accounts. You'll be drilling into transaction detail, applying dimension filters, changing the currency on the report. First, we'll update the display order of dimensions for financial reporting. This allows you to choose how the dimensions display not only while designing and viewing financial reports.

1. Go to **Financial dimension configuration for integrating applications** under the **Dimensions of Chart of Accounts** in General ledger.
2. Move the dimensions to be in the following order:

    1. Main Account
    2. Business Unit
    3. Cost Center
    4. Department

    > [!NOTE]
    > The other dimensions can remain in the order they are currently in.

3. Save the dimension configuration. Next, we'll generate a report and explore the data in the report.
4. Go to **Financial reports** under **Inquiries and reports** in General ledger.
5. Select the row for the report named **GL Detail – Default**.
6. Select **Edit**.

    > [!NOTE]
    > You'll be prompted to download the click-once report designer and to log in. Use your credentials to log in.

7. Change the base year to 2021 and select **Generate**. When a report is generated from the report designer, it will open in a new browser tab. You can either explorer the report in the new browser tab, or go to your original browser tab and open the report from there by selecting it from the **Financial reports** list.
8. In the opened report, select one of the amounts to drill into the account detail for the report.
9. Once in account detail, select an account with data and **drill to report transaction level**. At the report transaction level, you can see the properties (attributes) that are included in the design of this report. Depending on the transaction and account, some or all of the attributes may be displayed.
10. Close the report transaction level.
11. Select the same or a different account and **open voucher transactions**. Voucher transactions is filtered to the period, year and account + dimension combination of the account selected. From **Voucher transactions**, you can choose to explore other information about the transaction.
12. Close **Voucher transactions**. Within a financial report, you can choose to view the data either for a different period and year or with different attributes and dimensions applied. This is done by using **Report Options**.
13. Select **Report Options**.
14. Select **Add a dimension filter** and choose **Business Unit**.
15. Enter **001** into the field and select **OK**. The report now displays only the data for the 001 Business Unit. This is a personalized view of the report and isn't available for others to view.
16. Close the filtered report. Financial reports can be displayed in any currency that has been added to the application.
17. Select **Currency**, then select **EUR**. The report now displays in Euros. Any currency codes or currency symbols included in the report design now display in the applied currency. If no currency symbol is defined for a currency, the currency symbol is not displayed.
18. Close the **GL Detail** report.
19. Close **Report Designer**.

## Exercise 2: Add additional account properties to a report design
In this exercise, you will be modifying an existing default report. You will be updating both row definition to include all accounts and you'll update the column definition to contain account attributes. Once the updates are complete, you'll generate the newly created report and explore the report. We'll start from the **Financial reports** list.

1. Go to **Financial reports** under **Inquiries and reports** in General ledger.
2. Select the row for the report named **Summary Trial Balance – Default**.
3. Select **Edit**. **Summary Trial Balance – Default** will open in the report designer.
4. Select **File**, then **Save As** and name the report **Detailed Trial Balance with Attributes**.

    > [!NOTE]
    > Any time a new report is created in report designer, the **Financial reports** list is updated.

5. From the report definition, select the row definition icon to open the **Trial Balance – Default row definition**.
6. Save the row definition as **Detailed Trial Balance with Attributes**.
7. With the cursor on row 50, select **Edit**, then **Insert Rows from Dimensions**. Insert rows from dimensions allows you to choose what dimensions you'd like to have in your row definition. For this exercise, we are going to build the row definition using Main Account.
8. Make sure **Main Account** contains all ampersands and select **OK**. The row definition now contains all of the main accounts for legal entity USMF.
9. Scroll down to row 11110 and delete row 11110.
10. In row 11080, select **--- (Underscore amounts)**.
11. In row 11140, type **Total of all accounts** in column B.
12. In column C, select **TOT** from the drop down.
13. Type **50:11080** in column D.
14. **Save** the row definition. The row definition now contains all of the accounts plus a total row to add all of the accounts together. Next, we'll update the column definition to include additional account attributes.
15. From the **Detailed Trial Balance with Attributes** report definition, select the column definition icon to open the **Summary Trial Balance – Default** column definition.
16. Save the column definition as **Detailed Trial Balance with Attributes**. The column definition contains financial data columns, a description column and calculation columns. We are going to add attribute columns to the column definition to provide additional detail about the accounts.
17. The following attributes are going to be added to the column definition:

    - Journal Number
    - Journal Description
    - Transaction Date
    - Created by
    - Last modified by

18. In column I, select **ATTR** as the column type. Then, select **Journal Number** as the attribute category.
19. Continue adding columns for the remaining attributes.
20. In the **Header 2** row, add descriptions for each of the new columns that have been added.
21. Save the column definition. Now that the row definition and column definition have been updated, we'll need to add them to the report definition.
22. From the **Detailed Trial Balance with Attributes** report definition, select Detailed Trial Balance with Attributes for both the row definition and column definition.
23. Change the base year to **2012**.
24. **Save** the report definition and **generate**. Once the report completes generating and opens, you can explore the report as you did in the first exercise. Drill down on different accounts to see how the additional attributes are displayed.
25. Close the **Detailed Trial Balance with Attributes** report.
26. Close **Report Designer**.

## Exercise 3: Create a multidimensional report using a reporting tree
For this exercise, you will be modifying an existing default report. You will be creating a reporting tree and adding to a report definition to produce a **Cost Center/Divisional Income Statement**. Once the updates are complete, you'll generate the **Cost Center/Divisional Income Statement** and explore the report using the reporting tree. We'll start from the **Financial reports** list.

1. Go to **Financial reports** under Inquiries and reports in General ledger.
2. Select the row for the report named **Income Statement – Default**.
3. Select **Edit**. **Income Statement – Default** will open in the report designer.
4. On the **File** menu, point to **New**, and then click **Reporting Tree Definition**.
5. On the **Edit** menu, click **Insert Reporting Units from Dimensions**.
6. Clear checkboxes for all dimensions, except **Cost Center**.
7. Click the **From Dimension** field for the Cost Center dimension, type **007**, and then press the Tab key. In the **To Dimension** field, type **018**.
8. **Save** the resulting tree with the name **Cost Centers by Division**. Now that the reporting tree has been created, you'll modify the reporting tree to contain three new rollup units; Marketing, Operations and Retail.
9. On the **Window** menu, click **Cost Centers by Division**. (If the reporting tree has been closed, select it from the **Reporting Tree Definitions** in the navigation pane.)
10. Click unit number two, **Trade Shows**, and click the **Insert Reporting Unit** icon.
11. Double-click the entity column on the blank row, and select **USMF**.
12. Type **Marketing** in columns B and C.
13. Click unit number five, **Service Operations**, and right-click. **Select Insert Reporting Unit**.
14. Repeat step 11.
15. Type **Operations** in columns B and C.
16. Click unit number twelve, **Outlet**, and right-click. Select **Insert Reporting Unit**.
17. Repeat step 11.
18. Type **Retail** in columns B and C. Notice the Marketing, Operations and Retail units display at the same level as the current rollup units. The new units are organized next. Reporting units are organized through the right-click options; promote and demote, or by drag and drop.
19. Verify unit three, **Trade Shows**, is active and right-click.
20. Select **Demote Reporting Unit**. Notice the unit now displays as a child of **Marketing**.
21. Click unit four, **Marketing Campaign**, and right-click.
22. Select **Demote Reporting Unit**.
23. Click **Service Operations** in the graphical display. Press and hold down the left mouse button while dragging the unit up to **Operations**. Release the left mouse to drop the unit into Operation's rollup. Repeat for **Production**, **Quality Control**, **Logistics**, **Procurement** and **Administration**.
24. Make **Outlet**, **Super**, **Mall**, and **Online** children of **Retail** by either demoting them or dragging and dropping them.
25. Save the resulting re-organization. Now that we have the reporting tree created and organized, it can be added to the report definition.
26. On the **Window** menu, select **Income Statement – Default** to open the report definition.
27. Click the **Tree type** drop-down arrow and select **Reporting tree**.
28. Click the Tree drop-down arrow and select **Cost Centers by Division**.
29. Change the base year to **2021**, **save** the changes and **generate** the report. After the report completes generating and opens, you can explore the report.
30. Select the **Reporting Tree** drop down to view the reporting units. Alternatively, you can drill down on a row of the report to see all the balances for all units of the reporting tree.
31. Close **Income Statement – Default**.
32. Close **Report Designer**.

## Exercise 4: Create a consolidated report using an organization hierarchy
For this exercise, you will be modifying an existing default report. You will be adding an organization hierarchy in the report definition to produce a Consolidated Income Statement and Balance Sheet. Once the updates are complete, you'll generate the consolidated report and explore the report using the reporting tree. We'll start from the Financial reports list.

1. Go to **Financial reports** under **Inquiries and reports** in General ledger.
2. Select the row for the report named **Balance Sheet and Income Statement Side by Side – Default**.
3. Select **Edit**. **Balance Sheet and Income Statement Side by Side – Default** will open in the report designer.
4. Select **File** &gt; **Save As** and name the report **Consolidated Balance Sheet and Income Statement Side by Side**.
5. Change the base year to 2021.
6. Click the Tree type drop-down arrow, and select **Organization Hierarchies**.
7. Click the Tree drop-down arrow and select **Contoso Holdings**.
8. Save the changes and generate the report. If prompted, select all reporting units. After the report completes generating and opens, you can explore the report.
9. Select **Report Options**.
10. Select **Add a dimension filter** and choose **Department**.
11. Type **022** into the field and select **OK**.
12. Close the filtered report.
13. Select the **Reporting Tree** drop down to view the reporting units. Alternatively, you can drill down on a row of the report to see all the balances for all units of the reporting tree.
14. Close **Consolidated Balance Sheet and Income Statement Side by Side**.
15. Close **Report Designer**.

## Exercise 5: Create a side-by-side departmental report
In this exercise, you'll be creating a new report. The report is a side-by-side departmental income statement. You'll use an existing row definition, but create a new report definition and a new column definition that uses dimension filters. We'll start from the **Financial reports** list.

1. Go to **Financial reports** under **Inquiries and reports** in General ledger.
2. Select **New**. Report designer will open with a blank report definition open. Your first task will be creating the column definition.
3. Create a new column definition by clicking **File**, then **New**, and then **Column Definition**.
4. In **Column A**, select **DESC** for the column type.
5. In **Column B**, select **FD** for the column type.
6. Double-click in **the Dimension Filter** field.
7. In the **Dimension** window, double-click the **Department** column.
8. In the **Individual or range** section of the dialog, click the **ellipsis** for the **From** field to display a list of departments.
9. Select department **022**, **Sales & Marketing** and then click **OK**.
10. Repeat steps 5 to 8 for Departments 23-25.
11. On the **Header 2** row for each FD column, type the following department descriptions:

    - Column B – Sales and Marketing
    - Column C – Operations
    - Column D – Finance
    - Column E – IT

12. Save the column definition as Side by Side Departments. Since we are using an existing row definition, the report definition can now be modified to have use the newly created column definition and the existing row definition.
13. On the **Window** menu, select **New Report Definition** to open the report definition.
14. Select **Income Statement – Default** as the row definition and **Side by Side Departments** as the column definition.
15. Save the report definition as **Side by Side Departmental Income Statement**.
16. Change the base year to **2021**.
17. Change the detail level to **Financial, Account and Transaction**.
18. **Save** your changes and **generate**. Once the report completes generating and opens, you can explore the report.

## Additional resources
[Financial reporting](../../../finance/general-ledger/financial-reporting-getting-started.md)

[View financial reports](../../../finance/general-ledger/view-financial-reports.md)

[Dynamics 365 Finance Blog](https://community.dynamics.com/365/financeandoperations/b/dynamics-365-finance-blog)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
