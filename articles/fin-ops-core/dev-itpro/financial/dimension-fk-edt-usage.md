---
title: Dimension FK reference EDT usage
description: Learn which extended data types (EDTs) to use for foreign key fields that reference financial dimension tables, and the impact of using the wrong EDT.
author: ethanrimes
ms.author: ethanrimes
ms.topic: conceptual
ms.date: 03/02/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-01-16
ms.dyn365.ops.version: AX 7.0.0
---

# Dimension FK reference EDT usage

[!include [banner](../includes/banner.md)]

When creating fields with foreign keys to financial dimension tables, you must select the correct extended data type (EDT). Both the foreign key relation and the correct EDT are necessary for the dimension framework to function properly. Using the incorrect EDT can result in data corruption and cause unintended behavioral differences within the application.

The dimension framework contains reference scanners and data maintenance actions that identify dimension usage and clean up corrupt data. This cleanup works by creating new dimension records and updating FK references to point to the corrected records, because the old data in dimension tables may be valid in other contexts and can't be altered. Using the incorrect EDT prevents these scanners from detecting the dimension usage. Additionally, these scanners are used to support conversion of financial dimensions to financial tags for improved performance, and incorrect EDTs can prevent that conversion from detecting all references.

## EDT reference guide

There are five main EDTs used in the dimension framework.

### DimensionDefault

- **FK to:** DimensionAttributeValueSet
- **Use for:** Unordered set of dimension name/value pairs, primarily used in master data and header records.
- **Examples:** Customer/vendor default dimensions, project templates.

### LedgerDimensionAccount

- **FK to:** DimensionAttributeValueCombination
- **Use for:** Multi-segment ledger accounts that include the main account plus financial dimensions.
- **Examples:** Journal lines where you need the full ledger account combination, transactions that post to the ledger and require all dimensions resolved.

### LedgerDimensionDefaultAccount

- **FK to:** DimensionAttributeValueCombination
- **Use for:** Posting profiles or setup tables where only the main account is stored.
- **Examples:** Accounts payable/receivable posting profiles, parameters where you define a single main account for a process.

### DimensionDynamicAccount

- **FK to:** DimensionAttributeValueCombination
- **Use for:** Scenarios where the dimension value could come from ledger accounts or a non-ledger account such as Customer or Vendor.
- **Examples:** Journal lines where dimensions can be dynamic and include non-ledger accounts. The account type for the line should be determined by a field that uses the `LedgerJournalACType` enum.

### DimensionDynamicDefaultAccount

- **FK to:** DimensionAttributeValueCombination
- **Use for:** Scenarios where the dimension value could come from a default account or a non-ledger account such as Customer or Vendor.
- **Examples:** Default offset accounts defined on header tables that are defaulted to all lines on the document/journal, default offset accounts for project expenses.

## Decision matrix

| Scenario | EDT | Target table |
|----------|-----|-------------|
| Dimensions only, no main account | DimensionDefault | DimensionAttributeValueSet |
| Multi-segment accounts | LedgerDimensionAccount | DimensionAttributeValueCombination |
| Posting profile accounts only | LedgerDimensionDefaultAccount | DimensionAttributeValueCombination |
| Journal lines using `LedgerJournalACType` to determine the account type | DimensionDynamicAccount | DimensionAttributeValueCombination |
| Default main accounts or non-ledger accounts | DimensionDynamicDefaultAccount | DimensionAttributeValueCombination |

> [!NOTE]
> There are a few EDTs extending `LedgerDimensionBudget` that are used only in special cases related to Budget. These EDTs have been approved by the dimensions team. In most cases, the five standard EDTs should be sufficient. For anything module-specific that doesn't fall into the categories above, contact the dimensions framework team to discuss the scenario.

## Impact of incorrect EDT usage

- **Dimension reference scanners** can't correctly identify dimension usage on fields with the wrong EDT.
- **Data maintenance actions** fail to process dimension data correctly, which can lead to data corruption during cleanup.
- **Financial tags migration** can be prevented from detecting all references, because the scanners that support converting financial dimensions to financial tags rely on correct EDT usage.

## See also

- [Make backing tables consumable as financial dimensions](dimensionable-entities.md)
- [Modifying financial dimension data](modifying-financial-dimension-data.md)
