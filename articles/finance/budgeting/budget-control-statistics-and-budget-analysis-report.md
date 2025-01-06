---
title: Budget control statistics report vs. Budget analysis report
description: Learn about the Budget control statistics and Budget analysis reports that are available in the Budgeting module.
author: music727
ms.author: mibeinar
ms.topic: article
ms.date: 01/03/2025
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

The **Budget control statistics** report provides detailed insights into budget availability and reservations for selected combinations of budget control dimensions. This report is used to monitor and control budget use over specific periods. It provides detailed statistics about budget consumption to help ensure that expenditures don't exceed allocated budgets. This report is useful when you want to analyze either a single budget account or a combination or group of accounts by period and budget control dimension. It shows the available budget for each period and therefore helps track the amount of budget that remains.

You can use the **Budget analysis** report to query any dimension order across the chart of accounts. You can also query a subset of an account. For example, you can view a list of year-to-date fund totals, drill down to a specific fund to view department totals, and then drill down to a specific department to view account totals. This report is useful for checking summary amounts to compare budgeted amounts to actual expenses and revenue, review overall budget performance, and identify variances.

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

## Troubleshoot budget control issues

### Budget control data maintenance

If you experience data inconsistency with a specific budget-controlled document, the **Budget control data maintenance** tool is a good place to start. You can use this tool to delete and re-create existing budget data from a source document. The tool reviews the budget to find documents that weren't previously budget-checked but that should be checked now, either because the configuration changes occurred or because budget control was turned on or off. The tool uses the accounting distributions to determine the correct budget amounts. If there are issues with the distributions, the budget data is incorrect.

To run the **Budget control data maintenance** tool, follow these steps.

1. Go to **Budgeting** \> **Periodic** \> **Budget control data maintenance**.
1. Define a date range.
1. Select **Select scenarios**, and then select **Source document reprocessing provider**.
1. In the dialog box that appears, you can specify the document type and document number. To retrieve multiple documents at the same time, you can use wildcard characters in the **Document number** field. Alternatively, you can specify a comma-separated list of document numbers.

    The tool finds all documents that relieve each other. For example, you specify document PO00123, which relieves document PR005678. In this case, both documents appear in the grid, and they are processed as a group.

1. To process the documents that are found, select **Process document**.
1. Complete the remaining dialog boxes.

![Screenshot that shows the Budget control data maintenance tool.](./media/budget-control-data-maintenance.png)

### Budget control dimension values provider

The **Budget control data maintenance** tool includes a **Budget control dimension values provider** scenario that lets you adjust the dimension values that are used in budget data. This scenario is typically used when a new segment is added to the ledger account structure. It finds all dimension values that are currently used in budget data and transfers them to match the current account structure.

A customer might want to preserve historical data (that is, keep the previous account structure). In this case, the date range can be adjusted so that only data in the specified range is updated.

To run the **Budget control dimension values provider** scenario, follow these steps.

1. Go to **Budgeting** \> **Periodic** > **Budget control data maintenance**.
1. Enter a date range. The date range can be set to years before go-live or several years in the future.
1. Select **Select scenarios**, and then select **Budget control dimension values provider**.

    If there are documents to process, the grid is populated with the records that must be updated. The records that appear in the grid are only the unique combinations of budget control dimension values that must be updated. For each combination, there might be one transaction or many transactions.

1. Select the records to update, and then select **Process documents**. The operation might take some time, depending on the number of records that must be processed.

> [!NOTE]
> By default, the **Document Status** field is set to **Confirmed**. If there is budget data in a draft state, you must complete the steps again and select **Draft**.

### Budget control check failure

You might experience an issue with budget checks. Alternatively, budget checks might fail because not enough funds are available, but the **Budget control statistics by period** page shows available funds for the dimension combination.

If the previously mentioned steps don't apply, or if they produce unexpected results, review the following configurations:

- **Budget control threshold** – If budget use exceeds the defined threshold, the system either prevents posting or shows warnings. For example, the budget threshold on the **Budget control configuration** page is set to 80%, and the **Display a message when exceeding budget threshold** option is set to **Yes**. In this case, you receive a warning message if budget use exceeds 80%.
- **Budget group** – If a dimension combination runs out of budget, it might try to use funds from the budget group. In some scenarios, an overbudget dimension combination might be able to pull budget from the budget group.
- **Overbudget permissions** – If there are any overbudget permissions, an overbudget scenario might occur, but you don't experience a failure on the budget check.
- **Budget control interval setup on Budget control configuration groups** – If the budget control interval on the **Budget control configuration** page is set to **Fiscal year to date**, the end date for funds validation might differ from the date that is defined on the **Budget control statistics by period** page.
