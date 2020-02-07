Account activity reports
========================

Turnover sheet with correspondence
----------------------------------

The turnover sheet with correspondence is a basic component of the accounting
reports. It's a multirow, multicolumn table that contains information about the
activity for all accounts during the accounting period. The number of rows and
columns in the table is determined by the number of account numbers from the
chart of accounts that you set up on the **Query** page.

The top row and the leftmost column of the table contain the account numbers
from the chart of accounts. The intersection of rows and columns shows the total
of all transactions for the period. The correspondence of those transactions is
determined by the account numbers in the top row and the leftmost column that
correspond to the selected cell.

For each row and column in the table, the totals are summarized. The summary for
each row is recorded in the bottom row of the table, and the summary for each
column is recorded in the rightmost column. The total amount of debit and credit
turnover is shown in the cell at the intersection of the bottom row and the
rightmost column.

1.  Go to **General ledger \> Inquires and reports \> Account activity \>
    Turnover sheet with correspondence**.

2.  On the **General** tab, in the **Date interval code** field, select the date
    interval code from the date interval directory.

3.  In the **From date** and **To date** fields, select the start and end of the
    report generation period.

    *Note.* If you don't manually set these fields, values are entered based on
    the selected date interval code.

4.  In the **Currency type** field, select the currency type for the report:
    **Accounting currency**, **Reporting currency**, or **Indicated currency**.

5.  In the **Currency** field, select the transaction currency.

    *Note.* This field is available only if you select **Indicated currency** in
    the **Currency type** field.

6.  Set the **To debit accounts** option to **Yes** if you want the debit for
    the selected accounts to appear as a header line. If this option is set to
    **No**, the debit for the selected accounts appears in the column.

7.  In the **Dimension** section, in the **Agreement**,
    **ExpenseAndIncomeCode**, and **Worker** fields, specify dimension codes if
    you want to select transactions that have specific codes for the report.

>   *Note.* If you leave these fields blank, the system will select transactions
>   that have *any* dimension code for the report.

1.  In the **Posting layer** field, select the posting layer.

2.  Set the **Print ranges** option to **Yes** to view the query terms when you
    print the report.

3.  Set the **Delete zero line** option to **Yes** if you don't want to print
    lines or columns that have 0 (zero) values.

4.  Set the **Total accounts** option to **Yes** to total the accounts.

5.  Set the **Totals only** option to **Yes** to view only total accounts.

    *Note.* This option is available only if you set the **Total accounts**
    option to **Yes**.

![](media/563c2c2bbdd7de3c3b7e7081dc77eb2b.jpg)

>   A screenshot of a cell phone Description automatically generated

1.  Select **ОК** to generate the report.

![A screenshot of a cell phone Description automatically generated](media/22c10c915243ad3481f298882919ac8b.jpg)

*Note.*

-   Select **Voucher** to view the ledger transactions that generated the
    activity.

-   Select **Select** to change the report generation parameters.

-   Select **Print** to print the report in Microsoft Excel.

![](media/9d58c015900d677aa04440e9ef9f92a9.jpg)

>   A screenshot of a cell phone Description automatically generated

General ledger report
---------------------

The **General ledger** report contains information about the balances and
activity for a specified account that is in correspondence with all accounts in
the chart of accounts for a specified date interval. The report is broken down
by reporting periods (for example, months). A separate page is generated for
each account in the chart of accounts.

1.  Go to **General ledger \> Inquires and reports \> Account activity \>
    General ledger**.

2.  On the **General** tab, in the **Date interval code** field, select the date
    interval code from the date interval directory.

3.  In the **From date** and **To date** fields, select the start and end of the
    report generation period.

    *Note.* If you don't manually set these fields, values are entered based on
    the selected date interval code.

4.  In the **Currency type** field, select the currency type for the report:
    **Accounting currency**, **Reporting currency**, or **Indicated currency**.

5.  In the **Currency** field, select the transaction currency.

    *Note.* This field is available only if you select **Indicated currency** in
    the **Currency type** field.

6.  In the **From main account** and **To main account** fields, specify the
    range of accounts to generate the report for.

7.  In the **Dimension** section, in the **Agreement**,
    **ExpenseAndIncomeCode**, and **Worker** fields, specify dimension codes if
    you want to select transactions that have specific codes for the report.

>   *Note.* If you leave these fields blank, the system will select transactions
>   that have *any* dimension code for the report.

1.  Set the **Print ranges** option to **Yes** to view the query terms when you
    print the report.

2.  Set the **Delete zero line** option to **Yes** if you don't want to print
    lines or columns that have 0 (zero) values.

3.  Set the **Total accounts** option to **Yes** to total the accounts.

4.  Set the **Totals only** option to **Yes** to view only total accounts.

    *Note.* This option is available only if you set the **Total accounts**
    option to **Yes**.

5.  Set the **Debit activity** option to **Yes** to print the detailed account
    turnovers in debit correspondence.

6.  Set the **Credit activity** option to **Yes** to print the detailed account
    turnovers in credit correspondence.

7.  Set the **Use periods** option to **Yes** to print the report by interval,
    according to the reporting period. Set this option to **No** to print the
    report by months.

![](media/94b924117049ce4f9a2a7c763c283397.jpg)

>   A screenshot of a cell phone Description automatically generated

1.  Select **ОК** to generate the report.

![A screenshot of a cell phone Description automatically generated](media/afd55046015024a62dce369c1ff05e0a.jpg)

*Note.*

-   Select **Voucher** to view the ledger transactions that generated the
    activity.

-   Select the total account cell to open the transactions on all accounts that
    are included in the range of the specified total account, and that generated
    activity on the total account.

-   Select **Select** to change the report generation parameters.

-   Select **Print** to print the report in Excel.

![](media/6506da8b69f9459ea0983a773c9ce7a7.jpg)

>   A screenshot of a cell phone Description automatically generated

Review of account report
------------------------

The rows on the **Review of account** report contain information about the
balances and activity of a specified account that is in debit and credit
correspondence for the period that is under review. The final line of the report
summarizes the activity. The first row of the report shows the balance at the
beginning of the period, and the last row shows the balance at the end of the
period.

1.  Go to **General ledger \> Inquires and reports \> Account activity \> Review
    of account**.

2.  On the **General** tab, in the **Date interval code** field, select the date
    interval code from the date interval directory.

3.  In the **From date** and **To date** fields, select the start and end of the
    report generation period.

    *Note.* If you don't manually set these fields, values are entered based on
    the selected date interval code.

4.  In the **Currency type** field, select the currency type for the report:
    **Accounting currency**, **Reporting currency**, or **Indicated currency**.

5.  In the **Currency** field, select the transaction currency.

    *Note.* This field is available only if you select **Indicated currency** in
    the **Currency type** field.

6.  In the **Main account** field, select the account to generate the report
    for.

7.  In the **Dimension** section, in the **Agreement**,
    **ExpenseAndIncomeCode**, and **Worker** fields, specify dimension codes if
    you want to select transactions that have specific codes for the report.

>   *Note.* If you leave these fields blank, the system will select transactions
>   that have *any* dimension code for the report.

1.  Set the **Print ranges** option to **Yes** to view the query terms when you
    print the report.

2.  Set the **Total accounts** option to **Yes** to total the accounts.

3.  Set the **Totals only** option to **Yes** to view only total accounts.

    *Note.* This option is available only if you set the **Total accounts**
    option to **Yes**.

4.  Set the **Main accounts only** option to **Yes** to view only main accounts.

![](media/c17d3005d0db44ce7adcfffabd2e5d0c.jpg)

>   A screenshot of a cell phone Description automatically generated

1.  On the **Records to include** tab, you can select **Filter** to specify
    filter criteria.

2.  Select **ОК** to generate the report.

![A screenshot of a cell phone Description automatically generated](media/9f2cfb7ea76aae2ad3387672e0f22138.jpg)

*Note.*

-   Select **Voucher** to view the ledger transactions that generated the
    activity.

-   Select **Select** to change the report generation parameters.

-   Select **Print** to print the report in Excel.

![](media/8ef1ddaa38e46933d06df803ec1639b6.jpg)

>   A screenshot of a cell phone Description automatically generated

Journal order/account activity report
-------------------------------------

You can use the **Journal order/account activity** report to review movement on
a specified account in the context of transactions. You can also review the
recalculation of the balance for each transaction.

1.  Go to **General ledger \> Inquires and reports \> Account activity \>
    Journal order/account activity**.

2.  On the **General** tab, in the **Date interval code** field, select the date
    interval code from the date interval directory.

3.  In the **From date** and **To date** fields, select the start and end of the
    report generation period.

    *Note.* If you don't manually set these fields, values are entered based on
    the selected date interval code.

4.  In the **Currency type** field, select the currency type for the report:
    **Accounting currency**, **Reporting currency**, or **Indicated currency**.

5.  In the **Currency** field, select the transaction currency.

    *Note.* This field is available only if you select **Indicated currency** in
    the **Currency type** field.

6.  In the **Main account** field, select the account to generate the report
    for. If you select a total account, the report will be generated for the
    transactions of all accounts that are included in the total.

7.  In the **Dimension** section, in the **Agreement**,
    **ExpenseAndIncomeCode**, and **Worker** fields, specify dimension codes if
    you want to select transactions that have specific codes for the report.

>   *Note.* If you leave these fields blank, the system will select transactions
>   that have *any* dimension code for the report.

1.  Set the **Print ranges** option to **Yes** to view the query terms when you
    print the report.

2.  Set the **Total accounts** option to **Yes** to total the accounts.

3.  Set the **Totals only** option to **Yes** to view only total accounts.

    *Note.* This option is available only if you set the **Total accounts**
    option to **Yes**.

4.  Set the **Debit activity** option to **Yes** to print the detailed account
    turnovers in debit correspondence.

5.  Set the **Credit activity** option to **Yes** to print the detailed account
    turnovers in credit correspondence.

![](media/a94c873da1ee2aaca1f72a4216edfd8e.jpg)

>   A screenshot of a cell phone Description automatically generated

1.  On the **Records to include** tab, you can select **Filter** to specify
    filter criteria.

2.  Select **ОК** to generate the report in Excel.

![A screenshot of a cell phone Description automatically generated](media/b191594c22459a225a8074a581d75662.jpg)

*Note.*

-   Select **Voucher** to view the ledger transactions that generated the
    activity.

-   Select the total account cell to open the transactions on all accounts that
    are included in the range of the specified total account, and that generated
    activity on the total account.

-   Select **Select** to change the report generation parameters.

-   Select **Print** to print the report in Excel.
