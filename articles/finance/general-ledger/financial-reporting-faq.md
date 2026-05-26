---
title: Financial reporting FAQ
description: Access answers to some frequently asked questions about Financial reporting, including questions about restricting access and error messages.
author: jinniew
ms.author: jiwo
ms.topic: faq
ms.date: 05/26/2026
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-01-13
ms.search.form: 
ms.dyn365.ops.version: 10.0.14
---

# Financial reporting FAQ

This article provides answers to frequently asked questions about Financial reporting.

## How do I restrict access to a report by using tree security?

The following example shows how to restrict access to a report by using tree security.

The USMF demo company has a **Balance sheet** report that not all Financial reporting users should access. Use tree security to restrict access to a single report so that only specific users can access it.

1. Sign in to Financial reporter report designer.
1. Go to **File** > **New** > **Tree Definition** to create a new tree definition.
1. Double-tap (or double-click) the **Summary** line in the **Unit Security** column.
1. Select **Users and Groups**.
1. Select the users or groups that require access to the report.
1. Select **Save**.
1. In the report definition, add your new tree definition.
1. In the report definition, select **Setting**. Then, under **Reporting unit selection**, select **Include all units**.

## How do I identify which accounts don't match my balances?

If you have a report that doesn't have matching balances, use the following procedures to identify each account and variance:

1. Go to financial reporter report designer.
1. Create a new row definition.
1. Select **Edit \> Insert Rows from Dimensions**.
1. Select **MainAccount**.
1. Select **OK**.
1. Save the row definition.
1. Create a new column definition.
1. Create a new report definition.
1. Select **Settings** and unmark this option.
1. Generate the report.
1. Export the report to Microsoft Excel.

In Dynamics 365 Finance, follow these steps:

1. Go to **General ledger \> Inquiries and reports \> Trial balance**.
1. Set the following fields:

    - **From Date** – Enter the start date of the fiscal year.
    - **To Date** – Enter the date that you're generating the report for.
    - **Financial Dimension** – Set this field to **Main Account set**.

1. Select **Calculate**.
1. Export the report to Excel.

You can now copy the data from the Financial reporter Excel report to the **Trial Balance** report, so that you can compare the **Closing Balance** columns.

## Why does my report show "No data is available on this report" when I filter by a financial dimension other than the main account?

If a report returns data when you don't apply a filter or when you filter by main account, but shows **"No data is available on this report"** as soon as you filter by another dimension - such as Department or Cost center - the cause is usually the filter value, the posted data, or the report definition. Work through the following checks in order:

1. **Confirm that the filter value matches the format of the posted data.** On the Action Pane of the generated report, select **Report options** > **Add a dimension filter**. Select the dimension. Then enter the dimension ID exactly as it's stored on the posted transactions, or select a value from the list. A mistyped value or a value in the wrong format returns no data. For more information, see [View financial reports](view-financial-reports.md#change-report-options).
1. **Confirm that posted transactions contain a value for the dimension.** Go to **General ledger** > **Inquiries and reports** > **Trial balance**, and select a **Financial dimension set** that includes the dimension. If the trial balance shows blank values for the dimension, no posted transactions have a value to filter on. This situation often occurs when the dimension is optional in the account structure and isn't entered when transactions are posted. To inspect individual postings, go to **General ledger** > **Inquiries and reports** > **Voucher transactions**.
1. **Confirm that the row or column definition doesn't conflict with the filter.** If the row definition or column definition restricts results to specific accounts or dimension values, and your filter doesn't match data within those restrictions, the report returns no rows. To show a row for each dimension value instead of filtering at runtime, use **Edit** > **Insert rows from dimensions** in the row definition. This command isn't limited to **Main account**. For an example, see [Trial balance financial reports](trial-balance-financial-reports.md#row-definition).

## When I design a report in Report designer, or when I generate a financial report, I receive the following message: "The operation couldn't be completed due to a problem in the data provider framework." How should I respond?

The message indicates that an issue occurred when the system tried to retrieve financial metadata from the data mart while you were using Financial reporting. There are two ways to respond to this issue:

- Review the integration status of the data by going to **Tools \> Integration status** in Report designer. If the integration is incomplete, wait for it to complete. Then retry what you were doing when you received the message.
- Contact Support to identify and work through the issue. There might be inconsistent data in the system. Support engineers can help identify the issue on the server and find the specific data that might require an update.

## How does the selection of historical rate translation affect report performance?

The historical rate is typically used with retained earnings, property, plant and equipment, and equity accounts. The historical rate might be required, based on guidelines of the Financial Accounting Standards Board (FASB) or generally accepted accounting principles (GAAP). For more information, see [Currency capabilities in financial reporting](../dev-itpro/financial-reporting-currency-capability.md).

## How many types of currency rate are there?

There are three types:

- **Current rate** – This type is typically used with balance sheet accounts. It's known as the *spot exchange rate* and can be the rate on the last day of the month or another predetermined date.
- **Average rate** – This type is typically used with income statement (profit/loss) accounts. You can set up the average rate to do either a simple average or a weighted average.
- **Historical rate** – This type is typically used with retained earnings, property, plant and equipment, and equity accounts. These accounts might be required, based on FASB or GAAP guidelines.

## How does historical currency translation work?

Rates are specific to the transaction date. Therefore, each transaction is individually translated, based on the closest exchange rate.

For historical currency translation, you can use the precalculated period balances instead of individual transaction details. This behavior differs from the behavior for current rate translation.

## How does historical currency translation affect performance?

When you update data that is presented on the reports, there might be a delay because the system must recalculate amounts by checking transaction details. This delay occurs every time that the system updates the rates or posts more transactions. For example, if you set up thousands of accounts for historical translation a couple times per day, there might be a delay of up to an hour before the data on the report is updated. On the other hand, if there's a smaller number of specific accounts, you can reduce the processing times for updates to the report data to minutes or less.

Likewise, when you generate reports by using currency translation for historical type accounts, there are extra per-transaction calculations. Depending on the number of accounts, report generation time can more than double.

## What should I do if my beginning or opening balances in the multi-company consolidation report don't match the Trial Balance after running year-end close without transferring dimensions?

This discrepancy occurs because financial reporting doesn't support year-end close without transferring balance sheet dimensions, which is a recommended best practice. If you run year-end close without transferring these dimensions, the beginning balance posts to a different dimension than the previous year’s balances, leading to discrepancies.

## What are the limitations of financial reporting in accessing and reporting on archived data, and how does it affect currency translation?

Financial reporting can't access archived data. You must use other data explorers for this purpose. Reports generated for archived years don't return any data. You can view previously generated reports without the ability to drill down into transaction details. It's advisable to export or print these reports with transaction details before archiving. Regarding currency translation, it disregards the opening amount carried forward from archived years, affecting translated retained earnings. This limitation isn't a concern if you aren't using currency translation or if the opening amount is already zero.

## What are the estimated Data mart integration intervals?

Financial reporter uses 16 tasks to copy data from Dynamics 365 Finance to the financial reporter database. The following table lists these 16 tasks and shows the interval that specifies how often each task runs. You can't change the intervals.

| Name                                                       | Interval | Interval timing |
|------------------------------------------------------------|----------|-----------------|
| AX 2012 Account Categories to Account Category            | 41       | Minutes         |
| AX 2012 Accounts to Account                                | 7        | Minutes         |
| AX 2012 Companies to Company                               | 300      | Seconds         |
| AX 2012 Companies to Organization                          | 23       | Minutes         |
| AX 2012 Dimension Combinations to Dimension Combination    | 1        | Minutes         |
| AX 2012 Dimension Values to Dimension Value                | 11       | Minutes         |
| AX 2012 Dimensions to Dimension                            | 31       | Minutes         |
| AX 2012 Exchange Rates to Exchange Rate                    | 17       | Minutes         |
| AX 2012 Fiscal Years to Fiscal Year                        | 13       | Minutes         |
| AX 2012 General Ledger Transactions to Fact                | 1        | Minutes         |
| AX 2012 Organization Hierarchies to Tree                   | 3,600    | Seconds         |
| AX 2012 Scenarios to Scenario                              | 29       | Minutes         |
| AX 2012 Transaction Type Qualifiers to Fact Type Qualifier | 19       | Minutes         |
| Maintenance Task                                           | 1        | Minutes         |
| MR Report Definitions to AX7 Financial Reports             | 45       | Seconds         |
| MR Report Versions to AX Financial Report Versions         | 45       | Seconds         |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
