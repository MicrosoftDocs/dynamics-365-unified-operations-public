---
title: Budget control statistics report vs. Budget analysis report
description: Learn about the Budget control statistics and Budget analysis reports that are available in the Budgeting module.
author: music727
ms.author: mibeinar
ms.topic: how-to
ms.date: 04/17/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: global
ms.search.validFrom: 2016-02-28
ms.search.form: BankReconciliationWorksheet
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9df13adf-aa9d-4f6b-bde6-25a214611692
---

# Budget control statistics report vs. Budget analysis report

[!include [banner](../includes/banner.md)]

This article provides information about the **Budget control statistics** and **Budget analysis** reports that are available in the **Budgeting** module.

The **Budget control statistics** report provides detailed insights into budget availability and reservations for selected combinations of budget control dimensions. Use this report to monitor and control budget use over specific periods. It provides detailed statistics about budget consumption to help ensure that expenditures don't exceed allocated budgets. This report is useful when you want to analyze either a single budget account or a combination or group of accounts by period and budget control dimension. It shows the available budget for each period and therefore helps track the amount of budget that remains.

Use the **Budget analysis** report to query any dimension order across the chart of accounts. You can also query a subset of an account. For example, you can view a list of year-to-date fund totals, drill down to a specific fund to view department totals, and then drill down to a specific department to view account totals. This report is useful for checking summary amounts to compare budgeted amounts to actual expenses and revenue, review overall budget performance, and identify variances.

The following transaction details are available on the **Budget analysis** report:

- **Revised budget amounts** – View the sum of original budget, revision, transfer, and carry-forward amounts.
- **Actual expenditures** – View the sum of debits and credits that were posted for the financial dimension values.
- **Encumbrances and pre-encumbrances** – Both original and relieving transactions are included.

The following table describes differences between the two reports.

| Budget control statistics | Budget analysis |
|---|---|
| This report shows the budget balances for a budget cycle and a budget model for a single financial dimension value or budget group. | This report shows the combined budget amounts for multiple financial dimension values at the same time. |
| This report includes data from both confirmed and unconfirmed encumbrances. It shows draft transactions. | This report includes data from confirmed encumbrances only. It shows only posted transactions. |
| This report includes data from expense accounts only. | This report includes data from both revenue and expense accounts, and details for revenue accounts that aren't budget controlled. |

> [!NOTE]
> The **Budget analysis** report doesn't distinguish between operating periods and closing periods.

> [!NOTE]
> The **Display legacy budget analysis inquiry** parameter on the **Budgeting parameters** page controls which version of the **Budget analysis** page is displayed. Enabling this parameter displays the *BudgetAnalysisInquiry* page, which doesn't include profit and loss accounts. If the parameter is disabled, the *BudgetAnalysisDimensionFocusSummary* page is displayed which includes profit and loss accounts.

Budget reports and inquiry pages can display different default exchange rates.
The following pages use either the default exchange rate in Ledger setup or the manually updated exchange rate in the **Total actuals amounts** field:

- **Budget analysis** inquiry
- **Budget analysis** report
- **Actual vs. Budget** page

The following reports use the budget exchange rate defined in Ledger setup when displaying **Actual expenditures**:

- **Budget control statistics**
- **Budget control statistics by period**
- **Budget control account detail history**
