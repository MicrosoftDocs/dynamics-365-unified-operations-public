---
title: Budget control maintenance tool
description: Learn about the budget control maintenance tool in Dynamics 365 Finance.
author: music727
ms.author: mibeinar
ms.topic: how-to
ms.date: 04/17/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: global
ms.search.validFrom: 
ms.search.form: 
ms.dyn365.ops.version: 
ms.assetid: 
---

# Budget control data maintenance tool

If you experience data inconsistency with a specific budget-controlled document, start with the **Budget control data maintenance** tool.
The **Budget control data maintenance** tool can:

- delete and recreate existing budget data from a source document
- review the budget to find documents that weren't previously budget-checked but should be checked now, either because of configuration changes or because budget control was turned on or off.
- use the accounting distributions to determine the correct budget amounts. If there are problems with the distributions, the budget data is incorrect.

To run the **Budget control data maintenance** tool, follow these steps:

1. Go to **Budgeting** > **Periodic** > **Budget control data maintenance**.
1. Define a date range.
1. Select **Select scenarios**, and then select **Source document reprocessing provider**.
1. In the dialog box that appears, specify the document type and document number. To retrieve multiple documents at the same time, use wildcard characters in the **Document number** field. Alternatively, specify a comma-separated list of document numbers.

    The tool finds all documents that relieve each other. For example, you specify document PO00123, which relieves document PR005678. In this case, both documents appear in the grid, and they're processed as a group.

1. To process the documents that the tool finds, select **Process documents**.
1. Complete the remaining dialog boxes.

### Budget control dimension values provider

The **Budget control data maintenance** tool includes a **Budget control dimension values provider** scenario that adjusts the dimension values in budget data. Typically, use this scenario when you add a new segment to the ledger account structure. It finds all dimension values that are currently used in budget data and transfers them to match the current account structure.

If you want to preserve historical data and keep the previous account structure, adjust the date range so that only data in the specified range is updated.

To run the **Budget control dimension values provider** scenario, follow these steps:

1. Go to **Budgeting** > **Periodic** > **Budget control data maintenance**.
1. Enter a date range. You can set the date range to years before go-live or several years in the future.
1. Select **Select scenarios**, and then select **Budget control dimension values provider**.

    If there are documents to process, the grid is populated with the records that must be updated. The records that appear in the grid are only the unique combinations of budget control dimension values that must be updated. For each combination, there might be one or many transactions.

1. Select the records to update, and then select **Process documents**. The operation might take some time, depending on the number of records that must be processed.

> [!NOTE]
> By default, the **Document status** field is set to **Confirmed**. If there's budget data in a draft state, complete the steps again and select **Draft**.

For more information about troubleshooting budget control issues, see [Common budget control troubleshooting scenarios](/troubleshoot/dynamics-365/finance/budgeting/budget-control-troubleshooting).

