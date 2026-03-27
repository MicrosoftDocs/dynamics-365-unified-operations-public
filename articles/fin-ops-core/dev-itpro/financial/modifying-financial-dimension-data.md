---
title: Modifying financial dimension data
description: Learn why financial dimension data is immutable, which tables can't be modified, and what to do instead when dimension values are incorrect on posted documents.
author: ethanrimes
ms.author: ethankallett
ms.topic: conceptual
ms.date: 03/02/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-01-16
ms.dyn365.ops.version: AX 7.0.0
---

# Modifying financial dimension data

[!include [banner](../includes/banner.md)]

This article explains why financial dimension data is immutable, which dimension framework tables you must not modify, and what to do when dimension values are incorrect on a posted document.

## Immutability of financial dimension data

Financial dimension data is **insert-only on first reference**. Once a record is inserted into a financial dimension table, it exists there permanently. The only modifications that are ever permitted are limited property adjustments such as a rename operation. Records in these tables are never updated or deleted through normal application operations.

This design exists because dimension data is shared. Multiple documents across many modules can reference the same dimension records. A single foreign key into a dimension table can represent data that records across many different tables reference. Changing a single row of data under that foreign key changes the data for **every holder of that foreign key**, not just the one document you intend to fix.

The dimension framework can't determine how many tables and records hold a reference to any individual value without checking every table and every row, which can be a multihour process.

### Tables that you must not modify

Don't directly modify the following dimension framework tables through SQL statements (DELETE, UPDATE, or INSERT). Treat any table whose name starts with "Dimension" and doesn't contain the word "Status" as immutable.

- **DimensionAttribute**
- **DimensionAttributeSet**
- **DimensionAttributeSetItem**
- **DimensionAttributeValue**
- **DimensionAttributeValueSet**
- **DimensionAttributeValueSetItem**
- **DimensionAttributeValueCombination**
- **DimensionAttributeValueGroup**
- **DimensionAttributeValueGroupCombination**
- **DimensionAttributeLevelValue**

Because the dimension framework is insert-only and never deletes records, these tables can grow very large when financial dimensions are misused to track highly variable data such as serial numbers, dates, or document numbers. These values are rarely reused across transactions, which prevents the framework's deduplication from working as designed. For guidance on identifying and addressing this pattern, see [Highly variable dimensions](/dynamics365/finance/general-ledger/high-var-dimensions).

The **DimensionAttributeValueCombinationStatus** and **DimensionAttributeValueGroupStatus** tables are exceptions. These tables are validation cache tables that exist only for performance reasons. You can truncate them without causing data corruption. Truncating them only affects the time it takes to validate combinations against the account structure until the cache is rebuilt.

The **DimensionValueDeleteAudit** table is another special case. A row is written to this table each time you delete a record that serves as a source of financial dimension values from its backing table. Because each row captures approximately 2,000 bytes of call stack data, the table can grow rapidly if you mass-delete records from backing tables.

> [!WARNING]
> Frequently deleting records from tables that serve as dimension sources is strongly discouraged. The dimension framework is designed for write-once, reuse-many data. Mass deletes can create data growth and produce duplication in dimension data that affects reporting.

### Impact on balances and reporting

Modifying posted dimension data alters that data for all posted transactions that reference it, not just the current document. This change can cause balance discrepancies and reporting problems that are difficult to identify and clean up after the fact. Because the dimension framework doesn't maintain reference counts, there's no straightforward way to assess the full scope of the impact before it occurs.

## Risks of changing data directly

Don't directly modify data outside the application framework. For example, don't use Microsoft SQL Server Management Studio or perform direct SQL write operations. This guideline applies to the modification of data in *any* column of the table, not just the columns discussed in this article. It also applies to the replication of data from one row to another, and to attempts to create "new" sets or combinations outside the dimension framework storage classes.

Understand this guideline when considering backups and partial restorations of data that might affect referential and hash integrity. For example, if you back up only the Ledger Dimension related records and import them into another partition, you might cause problems unless you also import all the other records in the dimension framework, in addition to all the backing entity records, such as records from the CustTable table or other table that were used to create any combinations. Any attempt to modify the data in these tables, or to synthesize GUIDs or hashes, corrupts data and requires complex, time-consuming analysis to find the source of the corruption and try to fix it.

Renaming a backing entity value directly in the database (for example, renaming a customer account or department code through SQL) bypasses the `.update()` and `.renamePrimaryKey()` methods on the backing table that contain synchronization code for the dimension framework. This action can result in inconsistent, contradictory names where the backing entity shows the new name but dimension records still reference the old one. For further guidance on this issue, see [Dimension value shows a wrongly named or cased natural key](/dynamics-365/finance/general-ledger/dim-value-name-wrong-or-incorrect-case).

If dimension display values are already out of sync with the backing record, you can resynchronize them in one of two ways.

**Option 1: Use the Data Maintenance portal (version 10.0.18 and later)**

1. Go to the **Data Maintenance portal**.
1. Select **Rebuild dimension data from source records**.
1. Select **Run**.
1. Wait for the batch job to complete. When the status shows **Complete**, the dimension display values are resynchronized with the underlying backing records.

**Option 2: Rename the backing record through the application**

For a single record, you can trigger resynchronization without running a batch job by renaming the backing entity value through the application UI:

1. Open the backing entity record (for example, the customer or department).
1. Rename the value to a temporary name (for example, prepend an underscore: `_DEPT001`).
1. Save the record. This action triggers the `.renamePrimaryKey()` method, which synchronizes the dimension display values to the temporary name.
1. Rename the value back to its original name and save again. This action triggers a second synchronization, leaving dimension display values consistent with the correct original name.

This approach works because each save through the application invokes the synchronization hooks that a direct SQL rename bypasses.

For more information about how the dimension framework uses hashes internally and why modifications break data integrity, see [Ledger account combinations](/dynamics365/fin-ops-core/dev-itpro/financial/LedgerAccountCombinations).

## What to do instead

When dimension values on a posted document are incorrect, fix the document reference, not the dimension data. This approach is no different from how you handle any other shared reference in the system.

Consider this example: if you print a check (document) to the wrong vendor (dimension), you don't change the vendor record to be a different ID, because that change affects all other checks already made against that vendor. Instead, you change the check record to point to a different vendor.

The same principle applies to financial dimension data, but with a larger impact because a single dimension foreign key can be shared across records in many tables and modules.

If one or more dimension values within a set are incorrect for any reason (values not entered, not required, cleared on entry, or otherwise wrong), the proper fix is:

1. Create the correct set of dimension values through the application by using a new temporary document.
1. Copy the foreign key reference from that document back to the original document that has the problem.

This approach ensures that the new dimension data is properly created through the framework's storage classes with correct hashes and referential integrity, while the incorrect document is repointed to the correct data without affecting any other documents in the system.

> [!IMPORTANT]
> You can delete a financial dimension only if no references to any of its values exist in the dimension tables. If a dimension is referenced, you can't delete it. To hide a dimension that is no longer in use, rename it (for example, to "___DONOTUSE_DIMNAME") so that it doesn't appear alongside active dimensions.
