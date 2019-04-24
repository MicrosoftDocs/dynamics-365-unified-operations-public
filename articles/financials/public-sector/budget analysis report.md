---
# required metadata

title:  Budget analysis report 
description: Use the Budget analysis report to generate a summarized report comparing budgeted amounts to actual expenses and revenue activity during a time period you specify. 
author: velofog
manager: AnnBe
ms.date: 04/24/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: public sector
ms.author: v-alpavk
ms.search.validFrom: 2019-6-30
ms.dyn365.ops.version: 10.0.3

---

# Budget analysis report 
!include[banner](../includes/banner.md)]

Use the Budget analysis report to generate a summarized report comparing budgeted amounts to actual expenses and revenue activity during a time period you specify. For each account, the report lists budgeted amounts, actual expenses or revenues, encumbrance amounts from purchase orders, and pre-encumbrance amounts from purchase requisitions. Additionally, the report lists the remaining budget amount for each account and fund. The report can be sorted by fund and then account number and displays subtotals within each fund based on the financial dimension set you selected to group by. The grouping determines how the Navigation Pane, a tool helpful for reviewing activity, displays activity.

The report includes all accounts that have activity in the date range for either revenue or expenditure account types. The report does not include net totals (revenue – expense = net).

To see more information about an account, click the account name or number to open the Budget analysis inquiry form. You can view all the transactions that contribute to the amount on the report. To view the transactions, display drilldown report links in the report. Click a link to open a drilldown report with transaction detail for revised budget, actual expenses or revenues, encumbrances, or  pre-encumbrances. The drilldown reports can optionally include pending transactions.

## How to filter the data on this report
When you generate this report, the following default parameters are displayed. You can use these parameters to filter the data that will be displayed on the report. For more information, see 'How to work with reports' in this topic.

| Field | Description |
|-|-|
| Financial dimension set | Select the dimension group for ledger accounts to list in the report. A financial dimension set is a named group of accounts or dimensions that contains either account values for the account or dimension values for a single dimension. For example, a set can include main accounts, departments, and cost centers, or combinations such as a cost center and main account, or a department and cost center. For more information, see the 'Create a financial dimension set' topic. |
| Budget model | Select a budget model from which to report budget amounts. |
| Budget cycle time span | Specify the budget cycle to create the report for. For more information, see the 'Define budget cycles' topic on TechNet.|
| Account type | Indicate whether to report budget and actual amounts for expense or revenue accounts. By default, expense accounts are reported on.  If you change the account type after you select accounts or enter a selection query, you must select a new group of accounts in the Main accounts  fields and enter a new query by clicking Select . |
| Group main accounts by category | Select this check box to group accounts by main account category after grouping by the financial dimensions in a ledger account. The lowest level of grouping displays, regardless of the financial dimension you have selected. The main account categories are sorted by the alphanumeric codes. All accounts that are not assigned to a main account category are grouped at the end.    Main account categories are set up using the Main account categories  form.|
| Suppress accounts with zeroes| Select this check box to display only accounts with nonzero actual and budget amounts. |
| Show drilldown report links| Select this check box to display links to click to open a drilldown report with transaction detail for revised budget, actual expenses or revenues, encumbrances, or pre-encumbrances.  |
| Show pending transactions in drilldown reports | If the Show drilldown report links  field is selected, you can select this check box to include pending transactions in a drilldown report. Select this check box to include pending transaction details in drilldown reports for revised budget, actual expenses or revenues, encumbrances, or pre-encumbrances. Note If you choose to show pending transactions in the drilldown reports, the displayed balances might differ from the amounts displayed on the Budget Analysis report. |
| Dates to include| Specify whether to report amounts for an entire budget cycle or a range of dates. When you run this report for a previous year, the year-to-date columns are suppressed. If you selected Budget cycle, select the name of a budget cycle. This option uses the dates that were set up for the selected budget cycle in the  Budget cycle time spans form. For more information, see the 'Create a financial dimension set ' topic.    If you selected  Date range, select the starting and ending dates for the budget and actual entries to include in the report. You can enter different ranges for the budget and actual amounts. For example, if your organization budgets biennially, you can report budget amounts for a two-year date range, and include only the current year of      actual expenditure or revenue amounts.<br><br>**Note:** The date range you enter must be in one or more of the fiscal years that are included in the   fiscal calendar that was selected when the budget cycle time span was set up. For example, a fiscal calendar for a budget cycle includes fiscal years with dates from January 1, 2010 to December 31, 2014. The From date  cannot be before January 1, 2010. |
| Budget  | Enter or select the date range for the budget entries to include in the report.  |
| Actuals   | Enter or select the date range for the actual entries to include in the report. |
| Group by  | Select a dimension set to use to show subtotals by group. The report groups ledger accounts that share the same value for the financial dimensions you specify in the set. You can create new dimension sets by which to group accounts. For more information, see the 'Create a financial dimension set' topic.  |
| Page break by | Select a financial dimension set that includes the dimensions on which to start a new page for a change in the dimension value. You can only insert a page break on dimensions in the dimension set that are selected in the Group by  field. For example, when grouping by Fund-Department, you should choose to insert the page on Fund and Department, or only Fund. You can create new dimension sets by which to group accounts. For more information, see the 'Create a financial dimension set' topic on TechNet.  |
| Main accounts | Enter the range of main account numbers to list in the report. Leave the fields blank to run the report for all accounts.  |

## Reviewing the report
The report includes the following information:
- Account number
- Account name
- Revised budget (Original + Budget adjustments)
- Current actuals (for revenues or expenditures depending on the account type)
- Current percent of budget (actuals/revised budget)
- Year-to-date actuals (Only posted transactions for current year)
- Encumbrances (Only posted transactions for current year)
- Pre-encumbrances (Only posted transactions for current year)
- Budget remaining (Original + Budget adjustments – Actuals – Encumbrances – Pre-encumbrances) (Only posted transactions are considered in this calculation.)
- Year-to-date percent of budget remaining (Budget remaining/Revised budget) (Only posted transactions for current year)
The report also includes totals for each fund, department, and main account category, if included.

The drilldown report includes the following information:
- Name of category for drilldown: revised budget, actual expense or revenues, YTD encumbrances, or YTD pre-encumbrances
- Legal entity name
- Ledger account number
- Date for the transaction
- Voucher number
- Document information for the transaction
- Description for the voucher transaction date
- Voucher details
- Debit and credit detail for the actuals voucher
- Positive and negative amounts for budget, encumbrance, and pre-encumbrance voucher
- Opening/closing and running balance for the ledger account
