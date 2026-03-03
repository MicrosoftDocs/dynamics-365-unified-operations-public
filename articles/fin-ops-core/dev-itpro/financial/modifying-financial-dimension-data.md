---
title: Modifying financial dimension data
description: Learn why financial dimension data is immutable, which tables can't be modified, and what to do instead when dimension values are incorrect on posted documents.
author: ethanrimes
ms.author: ethanrimes
ms.topic: conceptual
ms.date: 03/02/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-01-16
ms.dyn365.ops.version: AX 7.0.0
---

# Modifying financial dimension data

[!include [banner](../includes/banner.md)]

This article explains why financial dimension data is immutable, which dimension framework tables must not be modified, and what to do instead when dimension values are incorrect on a posted document.

## Immutability of financial dimension data

Financial dimension data is **insert-only on first reference**. Once a record is inserted into a financial dimension table, it exists there permanently. The only modifications that are ever permitted are limited property adjustments such as a rename operation. Records in these tables are never updated or deleted through normal application operations.

This design exists because dimension data is shared. Multiple documents across many modules can reference the same dimension records. A single foreign key into a dimension table can represent data that is referenced by records across many different tables. Changing a single row of data under that foreign key changes the data for **every holder of that foreign key**, not just the one document you intend to fix.

The dimension framework can't determine how many tables and records hold a reference to any individual value without checking every table and every row, which can be a multi-hour process.

### Tables that must not be modified

The following dimension framework tables must not be modified directly through SQL statements (DELETE, UPDATE, or INSERT). Any table whose name starts with "Dimension" and doesn't contain the word "Status" should be treated as immutable.

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

The **DimensionAttributeValueCombinationStatus** and **DimensionAttributeValueGroupStatus** tables are exceptions. These are validation cache tables that exist only for performance reasons. They can be truncated without causing data corruption. Truncating them only affects the time it takes to validate combinations against the account structure until the cache is rebuilt.

### Impact on balances and reporting

Modifying posted dimension data alters that data for all posted transactions that reference it, not just the current document. This can cause balance discrepancies and reporting problems that are difficult to identify and clean up after the fact. Because the dimension framework doesn't maintain reference counts, there's no straightforward way to assess the full scope of the impact before it occurs.

## Risks of changing data directly

It's important that no data be directly modified outside the application framework (for example, in Microsoft SQL Server Management Studio or otherwise performing direct SQL write operations). This guideline applies to the modification of data in *any* column of the table, not just the columns that have been discussed in this article. It also applies to the replication of data from one row to another, and to attempts to create "new" sets or combinations outside the dimension framework storage classes.

It's important that you understand this guideline when you're considering backups and partial restorations of data that might affect referential and hash integrity. For example, if you back up only the Ledger Dimension related records and import them into another partition, you might cause issues unless you also import all the other records in the dimension framework, in addition to all the backing entity records, such as records from the CustTable table or other table that were used to create any combinations. Any attempt to modify the data in these tables, or to synthesize GUIDs or hashes, will cause data to become corrupted, and will require complex, time-consuming analysis to find the source of the corruption and try to fix it.

Renaming a backing entity value directly in the database (for example, renaming a customer account or department code through SQL) bypasses the `.update()` and `.renamePrimaryKey()` methods on the backing table that contain synchronization code for the dimension framework. This can result in inconsistent, contradictory names where the backing entity shows the new name but dimension records still reference the old one. For further guidance on this issue, see [Dimension value shows a wrongly named or cased natural key](/dynamics-365/finance/general-ledger/dim-value-name-wrong-or-incorrect-case.md).

For more information about how the dimension framework uses hashes internally and why modifications break data integrity, see [Ledger account combinations](/dynamics365/fin-ops-core/dev-itpro/financial/LedgerAccountCombinations.md).

## What to do instead

When dimension values on a posted document are incorrect, the correct approach is to fix the document reference, not the dimension data itself. This is no different from how you would handle any other shared reference in the system.

Consider this example: if you print a check (document) to the wrong vendor (dimension), you don't change the vendor record to be a different ID, because that would affect all other checks already made against that vendor. Instead, you change the check record to point to a different vendor.

The same principle applies to financial dimension data, but with a larger impact because a single dimension foreign key can be shared across records in many tables and modules.

If one or more dimension values within a set are incorrect for any reason (values not entered, not required, cleared on entry, or otherwise wrong), the proper fix is:

1. Create the correct set of dimension values through the application by using a new temporary document.
2. Copy the foreign key reference from that document back to the original document that has the problem.

This approach ensures that the new dimension data is properly created through the framework's storage classes with correct hashes and referential integrity, while the incorrect document is repointed to the correct data without affecting any other documents in the system.

> [!IMPORTANT]
> A financial dimension can only be deleted if no references to any of its values have been inserted into the dimension tables. If a dimension has been referenced, it can't be deleted. To hide a dimension that is no longer in use, rename it (for example, to "___DONOTUSE_DIMNAME") so that it doesn't appear alongside active dimensions.
