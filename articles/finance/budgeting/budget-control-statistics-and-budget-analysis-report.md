---
title: Budget control statistics by period vs. Budget analysis report
description: This article provides information about **Budget control statistics** and **Budget analysis** reports that are available in the **Budgeting** module.
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

# Budget control statistics by period vs. Budget analysis report

[!include [banner](../includes/banner.md)]

This article provides information about **Budget control statistics** and **Budget analysis** reports that are available in the **Budgeting** module.

The **Budget control statistics** page provides detailed insights into budget availability and reservations for selected budget control dimension combinations. This report is used to monitor and control budget usage over specific periods. It provides detailed statistics on budget consumption, helping ensure that expenditures do not exceed allocated budgets. This page is useful when a user wants to analyze a single budget account or a combination or group of accounts by period and budget control dimension. The report displays the available budget for each period, helping user to track how much budget remains.

The **Budget analysis** page allows users to query any dimension order across the chart of accounts or to query a subset of an account. For example, a user could view a list of year-to-date fund totals, drill down to a specific fund to view department totals, and then drill down to a specific department to view account totals. It's useful to check summary amounts compared to budgeted amounts to actual expenses and revenue, review overall budget performance and identify variances.

The following transaction details are available on the **Budget analysis** page: 
- **Revised budget** amounts - the sum of original budget, revision, transfer, and carry-forward amounts.
- **Actual expenditures** - the sum of the debits and credits posted for the financial dimension values.
- **Encumbrances** and **Pre-encumbrances** - including original and relieving transactions.

The table describes differences between the two reports:

| Budget control statistics |	Budget analysis|
|-----|-----|
|Displays the budget balances for a budget cycle and a budget model for a single financial dimension value or budget group.|Displays the combined budget amounts for multiple financial dimension values at the same time.|
|Includes data from both confirmed and unconfirmed encumbrances and includes draft transactions.| Includes data from confirmed encumbrances only and displays only posted transactions.|
|Includes data from expense accounts only.	| Includes data from both revenue and expense accounts, and details for revenue accounts that aren't budget controlled.|

> [!NOTE] 
> The **Budget analysis** page doesn't distinguish between operating periods and closing periods.

## Troubleshooting budget control issues

### Budget control data maintenance

**Budget control data maintenance** tool is a good place to start when encountering data inconsistencies with a specific budget controlled documents. This tool allows users to delete and recreate existing source document budget data. It checks the budget for documents that weren't budget checked previously, but should be checked now either due to configuration changes or turning budget control on/off. The tool uses the accounting distributions to determine the correct budget amounts. If there are issues with the distributions, the budget data is incorrect.

To run **Budget control data maintenance**, follow these steps:
1. go to **Budgeting** > **Periodic** > **Budget control data maintenance**.
2. Define a date range, click **Select scenarios**, select **Source document reprocessing provider**.
3. A new dialog appears that lets the user to choose which document type and document number to specify.
4. The **Document number** field allows for wildcards or you can specify a comma-separate list to retrieve multiple documents at a time.
The tool finds all documents that relieve each other. If the user chooses, for example, PO00123 which relieves PR005678, then you see both of those documents in the grid and they get processed as a group. To process the document(s), click **Process document**.
5. Follow the remaining dialogs.

![Budget control data maintenance](./media/budget-control-data-maintenance.png)

### Budget control dimension values provider

The **Budget control dimension values provider** is a scenario in a **Budget control data maintenance** that allows users to adjust dimension values used in budget data. This is typically used when a new segment has been added to the ledger account structure. The scenario finds all dimension values currently used by budget data and transfers them to match the current account structure. If a customer wants to preserve historical data (keep the previous account structure), the date range can be adjusted so that only data in the specified range will be updated.

To run **Budget control dimension values provider**, follow these steps:
1. Go to **Budgeting** > **Periodic** > **Budget control data maintenance**.
2. Entere a date range. It can be set to years before go-live or several years in the future.
3. Click **Select scenarios**, select **Budget control dimension values provider**. If there are documents to process, the grid populates with the records that need to be updated.
4. Select the records to update and click **Process documents**. Depending on the number of records that need to process, this could take some time.
The records displayed are only the unique combinations of budget control dimension values that need to be updated. There could be one or many transactions for each combination.

> [!NOTE] 
> **Document Status** field defaults to **Confirmed**. If there's budget data in a draft state, users need to perform steps again and select **Draft**.

### Budget control check fails

If users experience an issue with budget checks, or budget check fails from one of the following:
 - Not enough funds available, but the **Budget control statistics by period** page shows available funds for the given dimension combination


If the above mentioned steps don't apply or yield expected results, the follow these steps:
- **Budget control threshold** - defines the level of a budget usage at which system prevents posting or displays warnings. If a budget threshold in the **Budget control configuration** page is set to, for example, 80%, and **Display a message when exeeding budget threshold* is set to **Yes**, the user is shown a message about exceeding the threshold defined. 
- **Budget groups** - if a dimension combination runs out of budget, it may try to use funds from the budget group. There might be scenarios where a dimension combination is overbudget and the budget could be pulled from the budget group.
- **Overbudget permissions** - if there are any over budget permissions, there might be an overbudget scenario, but the user won't get a failure on the budget check.
- **Budget control interval** setup on the **Budget control configuration** groups - if the budget control interval is set to **Fiscal year to date** in the **Budget control configuration**, funds validation end date might be different than the date defined in the **Budget control statistics by period** page.
