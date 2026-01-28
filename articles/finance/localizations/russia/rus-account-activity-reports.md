---
title: Account activity reports
description: Learn how to work with activity reports for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/08/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
---

# Account activity reports

[!include [banner](../../includes/banner.md)]

This article explains how to work with activity reports for Russia in Microsoft Dynamics 365 Finance.

## Turnover sheet with correspondence

The *turnover sheet with correspondence* is a basic component of the accounting reports. It's a multirow, multicolumn table that contains information about the activity for all accounts during the accounting period. The number of rows and columns in the table is determined by the number of account numbers from the chart of accounts that you set up on the **Query** page.

The top row and the leftmost column of the table contain the account numbers from the chart of accounts. The intersection of rows and columns shows the total of all transactions for the period. The correspondence of those transactions is determined by the account numbers in the top row and the leftmost column that correspond to the selected cell.

For each row and column in the table, the totals are summarized. The summary for each row is recorded in the bottom row of the table, and the summary for each column is recorded in the rightmost column. The total amount of debit and credit turnover is shown in the cell at the intersection of the bottom row and the rightmost column.

To configure and generate the turnover sheet with correspondence, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Inquires and reports** \> **Account activity** \> **Turnover sheet with correspondence**.
1. On the **General** tab, in the **Date interval code** field, select the date interval code from the date interval directory.
1. In the **From date** and **To date** fields, select the start and end of the report generation period.

    > [!NOTE]
    > If you don't manually set these fields, values are entered based on the selected date interval code.

1. In the **Currency type** field, select the currency type for the report: **Accounting currency**, **Reporting currency**, or **Indicated currency**.
1. In the **Currency** field, select the transaction currency.

    > [!NOTE]
    > This field is available only if you select **Indicated currency** in the **Currency type** field.

1. Set the **To debit accounts** option to **Yes** if you want the debit for the selected accounts to appear as a header line. If this option is set to **No**, the debit for the selected accounts appears in the column.
1. In the **Dimension** section, in the **Agreement**, **ExpenseAndIncomeCode**, and **Worker** fields, specify dimension codes if you want to select transactions that have specific codes for the report.

    > [!NOTE]
    > If you leave these fields blank, the system will select transactions that have *any* dimension code for the report.

1. In the **Posting layer** field, select the posting layer.
1. Set the **Print ranges** option to **Yes** to view the query terms when you print the report.
1. Set the **Delete zero line** option to **Yes** if you don't want to print lines or columns that have 0 (zero) values.
1. Set the **Total accounts** option to **Yes** to total the accounts.
1. Set the **Totals only** option to **Yes** to view only total accounts.

    > [!NOTE]
    > This option is available only if you set the **Total accounts** option to **Yes**.

    ![Turnover sheet with correspondence page, General tab.](../media/1_Turnover_sheet_with_correspondence.jpg)

1. Select **ОК** to generate the report.

    ![Turnover sheet with correspondence report.](../media/2_Activity_of_account.jpg)

    > [!NOTE]
    > - Select **Voucher** to view the ledger transactions that generated the activity.
    > - Select **Select** to change the report generation parameters.
    > - Select **Print** to print the report in Microsoft Excel.

   ![Turnover sheet with correspondence generated report.](../media/3_Activity_of_account.jpg)

## General ledger report

The *general ledger* report contains information about the balances and activity for a specified account that is in correspondence with all accounts in the chart of accounts for a specified date interval. The report is broken down by reporting periods (for example, months). A separate page is generated for each account in the chart of accounts.

To configure and generate the general ledger report, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Inquires and reports** \> **Account activity** \> **General ledger**.
1. On the **General** tab, in the **Date interval code** field, select the date interval code from the date interval directory.
1. In the **From date** and **To date** fields, select the start and end of the report generation period.

    > [!NOTE]
    > If you don't manually set these fields, values are entered based on the selected date interval code.

1. In the **Currency type** field, select the currency type for the report: **Accounting currency**, **Reporting currency**, or **Indicated currency**.
1. In the **Currency** field, select the transaction currency.

    > [!NOTE]
    > This field is available only if you select **Indicated currency** in the **Currency type** field.

1. In the **From main account** and **To main account** fields, specify the range of accounts to generate the report for.
1. In the **Dimension** section, in the **Agreement**, **ExpenseAndIncomeCode**, and **Worker** fields, specify dimension codes if you want to select transactions that have specific codes for the report.

    > [!NOTE]
    > If you leave these fields blank, the system will select transactions that have *any* dimension code for the report.

1. Set the **Print ranges** option to **Yes** to view the query terms when you print the report.
1. Set the **Delete zero line** option to **Yes** if you don't want to print lines or columns that have 0 (zero) values.
1. Set the **Total accounts** option to **Yes** to total the accounts.
1. Set the **Totals only** option to **Yes** to view only total accounts.

    > [!NOTE]
    > This option is available only if you set the **Total accounts** option to **Yes**.

1. Set the **Debit activity** option to **Yes** to print the detailed account turnovers in debit correspondence.
1. Set the **Credit activity** option to **Yes** to print the detailed account turnovers in credit correspondence.
1. Set the **Use periods** option to **Yes** to print the report by interval, according to the reporting period. Set this option to **No** to print the report by months.

    ![General ledger account activity report page, General tab.](../media/4_General_ledger.jpg)

1. Select **ОК** to generate the report.

    ![General ledger account activity report.](../media/5_Account_activity.jpg)

> [!NOTE]
>
> - Select **Voucher** to view the ledger transactions that generated the activity.
> - Select the total account cell to open the transactions on all accounts that are included in the range of the specified total account, and that generated activity on the total account.
> - Select **Select** to change the report generation parameters.
> - Select **Print** to print the report in Excel.

   ![Generated General ledger account activity report .](../media/6_Account_activity.jpg)

## Review of account report

The rows on the *review of account* report contain information about the balances and activity of a specified account that is in debit and credit correspondence for the period that is under review. The final line of the report summarizes the activity. The first row of the report shows the balance at the beginning of the period, and the last row shows the balance at the end of the period.

To configure and generate the review of account report, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Inquires and reports** \> **Account activity** \> **Review of account**.
1. On the **General** tab, in the **Date interval code** field, select the date interval code from the date interval directory.
1. In the **From date** and **To date** fields, select the start and end of the report generation period.

    > [!NOTE]
    > If you don't manually set these fields, values are entered based on the selected date interval code.

1. In the **Currency type** field, select the currency type for the report: **Accounting currency**, **Reporting currency**, or **Indicated currency**.
1. In the **Currency** field, select the transaction currency.

    > [!NOTE]
    > This field is available only if you select **Indicated currency** in the **Currency type** field.

1. In the **Main account** field, select the account to generate the report for.
1. In the **Dimension** section, in the **Agreement**, **ExpenseAndIncomeCode**, and **Worker** fields, specify dimension codes if you want to select transactions that have specific codes for the report.

    > [!NOTE]
    > If you leave these fields blank, the system will select transactions that have *any* dimension code for the report.

1. Set the **Print ranges** option to **Yes** to view the query terms when you print the report.
1. Set the **Total accounts** option to **Yes** to total the accounts.
1. Set the **Totals only** option to **Yes** to view only total accounts.

    > [!NOTE]
    > This option is available only if you set the **Total accounts** option to **Yes**.

1. Set the **Main accounts only** option to **Yes** to view only main accounts.

    ![Review of account report, General tab.](../media/7_Review_of_account.jpg)

1. On the **Records to include** tab, you can select **Filter** to specify filter criteria.
1. Select **ОК** to generate the report.

![Review of account report.](../media/8_Review_of_account.jpg)

> [!NOTE]
>
> - Select **Voucher** to view the ledger transactions that generated the activity.
> - Select **Select** to change the report generation parameters.
> - Select **Print** to print the report in Excel.

   ![Generated Review of account report.](../media/9_Review_of_account.jpg)

## Journal order/account activity report

You can use the *Journal order/account activity* report to review movement on a specified account in the context of transactions. You can also review the recalculation of the balance for each transaction.

To configure and generate the journal order/account activity report, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger \> Inquires and reports \> Account activity \> Journal order/account activity**.
1. On the **General** tab, in the **Date interval code** field, select the date interval code from the date interval directory.
1. In the **From date** and **To date** fields, select the start and end of the report generation period.

    > [!NOTE]
    > If you don't manually set these fields, values are entered based on the selected date interval code.

1. In the **Currency type** field, select the currency type for the report: **Accounting currency**, **Reporting currency**, or **Indicated currency**.
1. In the **Currency** field, select the transaction currency.

    > [!NOTE]
    > This field is available only if you select **Indicated currency** in the **Currency type** field.

1. In the **Main account** field, select the account to generate the report for. If you select a total account, the report will be generated for the transactions of all accounts that are included in the total.
1. In the **Dimension** section, in the **Agreement**, **ExpenseAndIncomeCode**, and **Worker** fields, specify dimension codes if you want to select transactions that have specific codes for the report.

    > [!NOTE]
    > If you leave these fields blank, the system will select transactions that have *any* dimension code for the report.

1.  Set the **Print ranges** option to **Yes** to view the query terms when you print the report.
1.  Set the **Total accounts** option to **Yes** to total the accounts.
1. Set the **Totals only** option to **Yes** to view only total accounts.

    > [!NOTE]
    > This option is available only if you set the **Total accounts** option to **Yes**.

1. Set the **Debit activity** option to **Yes** to print the detailed account turnovers in debit correspondence.
1. Set the **Credit activity** option to **Yes** to print the detailed account turnovers in credit correspondence.

    ![Journal order/account activity report, General tab.](../media/10_Journal_order_account_activity.jpg)

1. On the **Records to include** tab, you can select **Filter** to specifyfilter criteria.
1. Select **ОК** to generate the report in Excel.

![Generated Journal order/account activity report.](../media/11_Journal_order_and_account_activity.jpg)

> [!NOTE]
>   
> - Select **Voucher** to view the ledger transactions that generated the activity.
> - Select the total account cell to open the transactions on all accounts that are included in the range of the specified total account, and that generated activity on the total account.
> - Select **Select** to change the report generation parameters.
> - Select **Print** to print the report in Excel.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
