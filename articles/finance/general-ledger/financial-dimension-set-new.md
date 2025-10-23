---
title: New financial dimension sets
description: Learn about the updated functionality for financial dimension sets, including outlines on viewing balance statuses, enable balances, and deleting dimension sets.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 04/14/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-10-16
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage
ms.dyn365.ops.version: 10.0.38
---

# New financial dimension sets

[!include [banner](../includes/banner.md)]

The **Performance enhancement for general ledger dimension set balance calculation** feature initiates the process of creating new balances. This process might take several hours if the amount of transactional data is large. Reports and inquiries that use dimension sets won't be available until the processing is completed. You can view the status on the **Dimension set** page.

This feature enables the **Trial balance inquiry** page and reports that use financial dimension sets to run more efficiently. The financial dimension sets store data more efficiently and use less space. Therefore, the trial balance can show current balance data more quickly. The feature uses process automation to keep the balance amounts up to date. You can find the background process automation named **General ledger balance process** that runs every 5 minutes by default. The process automation background task creates a new, single occurrence batch every 5 minutes. When you view the individual batch task, the occurrence displays 10 minutes because that's the default for any batch. The background task creates a new balance process batch every 5 minutes. This time can be changed on the **Background process** tab in **Process automation**.

>[!IMPORTANT]
> We recommend that you review all customizations that might require the previous balance data and test the feature in an UAT environment before enabling the feature in your PROD environment.
>
> After the feature is enabled in PROD, the prior balance data is immediately queued for deletion to reduce storage costs. This change can't be undone once started, and must be allowed to fully complete before reverting back from the enhancement feature if needed.

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

If you no longer require a dimension set, use the **Delete** button to remove it. Don't delete and recreate dimension sets as a workaround for potential issues with the balance data for a specific dimension set. Recreation of a dimension set is costly. For help with issues, contact support.

## Trial balance and reporting
After the feature is on you notice small changes to the trial balance page and reports such as the **Dimension statement** report that utilize dimension sets to display ledger balance data. Each of these notify the user how current the balance data is. By default, this is a number between 0 and 5 minutes since background process has run. 

## Technical information 
The below table describes the old data model and the new data model used for this feature. The outcome is less data to store resulting in faster performance for some queries such as ones used for the trial balance inquiry page. 

> [!IMPORTANT]
> Any customizations that are dependent on the old data model won't work as soon as the performance feature is enabled. Testing in an UAT environment first is highly recommended. It's not possible to switch between the new and old models efficiently.


| New Table | Old Table | Description |
|-----------|-----------|-------------|
| GeneralLedgerBalance, GeneralLedgerMainAccountBalance | DimensionFocusBalance | FocusDimensionHierarchy and FocusLedgerDimension are removed from the balance tables. The data is now aggregated by the original GeneralJournalAccountEntry.LedgerDimension value (no new DimensionAttributeValueCombination records created for balances any longer). <br> The GeneralLedgerMainAccountBalance stores balances at the main account level only as a performance optimization as the primary use case scenario. |
| GeneralLedgerBalanceReportingDimension | DimensionAttributeValueCombination, DimensionAttributeValueGroupCombination, DimensionAttributeValueGroup, DimensionAttributeValue, DimensionAttributeLevelValue, etc. | New tables store segment values of the dimension attribute value natural key values in hierarchical order based on the dimension set. **NOTE**: The change to no longer use the DimensionAttributeValueCombination and other Dim* tables is only in the context of dimensions set storage. These tables are still used and linked to for transaction entry and all voucher data found in the general ledger (LedgerJournalTrans, GeneralJournalAccountEntry)|
| GeneralLedgerBalanceReportingDimensionReference | DimensionFocusLedgerDimensionReference | The new table is the link between the original ledger account and reporting account structure per dimension set. |
| GeneralLedgerBalanceUnprocessedTransactions | DimensionFocusUnprocessedTransactions | Records to perform incremental update of balances no longer created per dimension set. |


For more information, see [Financial dimensions](financial-dimensions.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]





