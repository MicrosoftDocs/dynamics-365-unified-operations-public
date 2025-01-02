---
title: New financial dimension sets
description: Learn about the updated functionality for financial dimension sets, including outlines on viewing balance statuses, enable balances, and deleting dimension sets.
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 10/16/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-10-16
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage
ms.dyn365.ops.version: 10.0.38
---

# New financial dimension sets

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Finance version 10.0.38, a new feature **Performance enhancement for general ledger dimension set balance calculation** is available. When you turn on this feature, the process of creating new balances is initiated. This process might take several hours if the amount of transactional data is large. Reports and inquiries that use dimension sets won't be available until the processing is completed. You can view the status on the **Dimension set** page.

This feature enables the **Trial balance inquiry** page and reports that use financial dimension sets to run more efficiently. The financial dimension sets store data more efficiently and use less space. Therefore, the trial balance can show current balance data more quickly. The feature uses process automation to keep the balance amounts up to date.

## View balance status

Use the **Balance status** button to view the current calculation state of the financial dimension set. The page that appears shows the status of the dimension set balance for each legal entity. It also shows the date and time when the dimension set was last updated by the automatic background process.

## Enable balances

Use the **Enable balances** button to initialize and start to track balances for a dimension set that doesn't currently have balances.

> [!NOTE]
> We recommend that you limit the number of dimension sets that have balances, because balance updates affect all General ledger posting activities.

## Disable balances

Use the **Disable balances** button to turn off balance tracking for a given dimension set.

## Rebuild balances

Use the **Rebuild balances** button on the balance status page to re-create balances from the General ledger transactional data. This functionality helps ensure that the balances match the data in General ledger. A rebuild of balances requires lots of processing and should rarely be required.

## Delete a dimension set

If you no longer require a dimension set, you can use the **Delete** button to remove it. Don't delete and re-create dimension sets as a workaround for potential issues with the balance data for a specific dimension set. Re-creation of a dimension set is costly. For help with issues, contact support.

## Techincal information 
The below table describes the old data model and the new data model used for this feature. The outcome is less data to store resulting in faster performance for some queries such as ones used for the trial balance inquiry page. 

| New Table | Old Table | Description |
|-----------|-----------|-------------|
| GeneralLedgerBalance, GeneralLedgerMainAccountBalance | DimensionFocusBalance | FocusDimensionHierarchy and FocusLedgerDimension are removed from the balance tables. The data is now aggregated by the original GeneralJournalAccountEntry.LedgerDimension value (no new DimensionAttributeValueCombination records created for balances any longer). <br> The GeneralLedgerMainAccountBalance stores balances at the main account level only as a performance optimization as the primary use case scenario. |
| GeneralLedgerBalanceReportingDimension | DimensionAttributeValueCombination, DimensionAttributeValueGroupCombination, DimensionAttributeValueGroup, DimensionAttributeValue, DimensionAttributeLevelValue, etc. | New tables store segment values of the dimension attribute value natural key values in hierarchical order based on the dimension set. |
| GeneralLedgerBalanceReportingDimensionReference | DimensionFocusLedgerDimensionReference | The new table is the link between the original ledger account and reporting account structure per dimension set. |
| GeneralLedgerBalanceUnprocessedTransactions | DimensionFocusUnprocessedTransactions | Records to perform incremental update of balances no longer created per dimension set. |


For more information, see [Financial dimensions](financial-dimensions.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
