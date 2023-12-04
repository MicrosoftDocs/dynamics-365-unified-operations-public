---
# required metadata

title: Budget analysis report
description: This article describes the Budget analysis report, which is used to generate a summarized report that compares budgeted amounts to actual expenses and revenue activity during a period that you specify.
author: v-kiarnd
ms.date: 07/08/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: public sector
ms.author: twheeloc
ms.search.validFrom: 2019-6-30
ms.dyn365.ops.version: 10.0.3

---

# Budget analysis report

[!include[banner](../includes/banner.md)]

You can use the **Budget analysis** report to generate a summarized report that compares budgeted amounts to actual expenses and revenue activity during a period that you specify. For each account, the report lists budgeted amounts, actual expenses or revenue, encumbrance amounts from purchase orders, and pre-encumbrance amounts from purchase requisitions. Additionally, the report lists the remaining budget amount for each account and fund.

The report can be sorted by fund and then account number. Within each fund, the report shows subtotals, based on the financial dimension set that you selected to group by. When you use the navigation pane to review activity, the grouping determines how activity is shown there.

The report includes all accounts that have activity in the date range for either revenue or expenditure account types. Any account marked as a Profit and Loss account type won't be included in the report. The report also doesn't include net totals. (Net totals are calculated as revenue minus expenses.)

To view more information about an account, select the account name or number to open the **Budget analysis inquiry** page. You can view all the transactions that contribute to the amount on the report. To view the transactions, you can show drill-down report links on the report. Select a link to open a drill-down report that has transaction details for revised budget, actual expenses or revenue, encumbrances, or pre-encumbrances. The drill-down reports can optionally include pending transactions.

## Filter the data on this report

When you generate the report, the following default parameters are shown. You can use these parameters to filter the data that appears on the report. For more information, see the "How to work with reports" section of this article.

| Field | Description |
|---|---|
| Financial dimension set | Select the dimension group for the ledger accounts that should be listed on the report.<p>A financial dimension set is a named group of accounts or dimensions that contains either account values for the account or dimension values for a single dimension. For example, a set can include main accounts, departments, and cost centers. Alternatively, it can contain combinations, such as a cost center and a main account, or a department and a cost center.  |
| Budget model | Select the budget model to report budget amounts from. |
| Budget cycle time span | Specify the budget cycle to create the report for. |
| Account type | Specify whether budget and actual amounts should be reported for expense accounts or revenue accounts. By default, expense accounts are reported on. If you change the account type after you select accounts or enter a selection query, you must select a new group of accounts in the **Main accounts** fields and select **Select** to enter a new query. |
| Group main accounts by category | Select this check box to group accounts by main account category after they are grouped by financial dimensions in a ledger account. The lowest level of grouping is shown, regardless of the financial dimension that you selected. The main account categories are sorted by their alphanumeric codes. All accounts that aren't assigned to a main account category are grouped at the end. You set up main account categories by using the **Main account categories** page. |
| Suppress accounts with zeroes | Select this check box to show only accounts that have non-zero actual and budget amounts. |
| Show drilldown report links | Select this check box to show links that can be used to open a drill-down report that has transaction details for revised budget, actual expenses or revenue, encumbrances, or pre-encumbrances. |
| Show pending transactions in drilldown reports | If the **Show drilldown report links** check box is selected, you can select this check box to include pending transaction details on a drill-down report for revised budget, actual expenses or revenue, encumbrances, or pre-encumbrances.<blockquote> **NOTE:**  If you select this check box, the balances that are shown might differ from the amounts that are shown on the **Budget analysis** report. |
| Dates to include | Specify whether amounts should be reported for a whole budget cycle or a range of dates. When you run this report for a previous year, the year-to-date (YTD) columns are suppressed.<br>- If you select **Budget cycle**, select the name of a budget cycle. This option uses the dates that were set up for the selected budget cycle on the **Budget cycle time spans** page.<br>- If you select **Date range**, select the start and end dates for the budget and actual entries that should be included on the report. You can enter different ranges for the budget amounts and actual amounts. For example, if your organization budgets biennially, you can report budget amounts for a two-year date range, but include only the current year of actual expenditure or revenue amounts. **NOTE:**  The date range that you specify must be in one or more of the fiscal years that are included in the fiscal calendar that was selected when the budget cycle time span was set up. For example, a fiscal calendar for a budget cycle includes fiscal years that have dates from January 1, 2010, to December 31, 2014. In this case, the "from" date can't be before January 1, 2010.<br> |
| Budget | Specify the date range for the budget entries that should be included on the report. |
| Actuals | Specify the date range for the actual entries that should be included on the report. |
| Group by | Select the dimension set that is used to show subtotals by group. Ledger accounts that have the same value for the financial dimensions that you specify in the dimension set are grouped on the report. You can create new dimension sets to group accounts by. |
| Page break by | Select a financial dimension set that includes the dimensions where you want to insert a new report page if the dimension value changes. You can insert a page break only for dimensions in the dimension set that you selected in the **Group by** field. For example, if you group by Fund-Department, you should insert the page for Fund and Department, or just for Fund. You can create new dimension sets to group accounts by.  |
| Main accounts | Enter the range of main account numbers that should be listed on the report. Leave the fields blank to run the report for all accounts. |

## Review the report

The report includes the following information:

- Account number
- Account name
- Revised budget (= Original budget + Budget adjustments)
- Current actuals (for either revenue or expenditures, depending on the account type)
- Current percentage of budget (actuals/revised budget)
- YTD actuals (Only posted transactions for the current year are considered.)
- Encumbrances (Only posted transactions for the current year are considered.)
- Pre-encumbrances (Only posted transactions for the current year are considered.)
- Budget remaining (= Original budget + Budget adjustments – Actuals – Encumbrances – Pre-encumbrances) (Only posted transactions are considered in this calculation.)
- YTD percentage of budget remaining (= Budget remaining ÷ Revised budget) (Only posted transactions for the current year are considered in this calculation.)

The report also includes totals for each fund, department, and main account category, if they are included.

The drill-down report includes the following information:

- Name of the category for drill-down: revised budget, actual expense or revenue, YTD encumbrances, or YTD pre-encumbrances
- Name of the legal entity
- Ledger account number
- Date of the transaction
- Voucher number
- Document information for the transaction
- Description of the voucher transaction date
- Voucher details
- Debit and credit details for the actuals voucher
- Positive and negative amounts for the budget, encumbrance, and pre-encumbrance voucher
- Opening, closing, and running balances for the ledger account


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
