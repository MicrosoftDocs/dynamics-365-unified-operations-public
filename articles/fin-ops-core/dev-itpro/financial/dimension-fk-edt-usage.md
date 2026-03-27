---
title: Dimension foreign key reference EDT usage
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

# Choosing the correct extended data type (EDT) for financial dimension foreign keys

[!include [banner](../includes/banner.md)]

When you create fields with foreign keys to financial dimension tables, select the correct extended data type (EDT). The dimension framework needs both the foreign key relation and the correct EDT to work properly. If you use the wrong EDT, you can cause data corruption and unintended behavioral differences within the application.

The dimension framework includes reference scanners and data maintenance actions that identify dimension usage. If you use the wrong EDT, these scanners can't detect the dimension usage.

## EDT reference guide

The dimension framework uses five main EDTs.

### DimensionDefault

- **Foreign key to:** DimensionAttributeValueSet
- **Use for:** Unordered set of dimension name/value pairs, primarily used in master data and header records.
- **Examples:** Customer and vendor default dimensions, project templates.

### LedgerDimensionAccount

- **Foreign key to:** DimensionAttributeValueCombination
- **Use for:** Multisegment ledger accounts that include the main account plus financial dimensions.
- **Examples:** Journal lines where you need the full ledger account combination (main account plus all dimensions resolved).

### LedgerDimensionDefaultAccount

- **Foreign key to:** DimensionAttributeValueCombination
- **Use for:** Posting profiles or setup tables where you store only the main account.
- **Examples:** Accounts payable and receivable posting profiles, parameters where you define a single main account for a process.

### DimensionDynamicAccount

- **Foreign key to:** DimensionAttributeValueCombination
- **Use for:** Scenarios where the dimension value comes from ledger accounts or a non-ledger account such as Customer and Vendor
- **Examples:** LedgerDimension and OffsetLedgerDimension on the general journal. If you select Ledger as the account type, you can enter a full ledger account. But if you select Customer or Vendor, you can select a customer or vendor for the LedgerDimension.

### DimensionDynamicDefaultAccount

- **Foreign key to:** DimensionAttributeValueCombination
- **Use for:** Scenarios where the dimension value comes from a default account or a non-ledger account such as Customer or Vendor.
- **Examples:** The Travel and Expense payment method, where you set a default offset account based on the payment method. You can select Ledger, Worker, Bank, or Vendor as the account type and then set the offset account accordingly. It's similar to DimensionDynamicAccount, but instead of being the foreign key on the line itself, it's on the settings table that defines a default value.

## Decision matrix

| Scenario | EDT | Target table |
|----------|-----|-------------|
| Dimensions only, no main account | DimensionDefault | DimensionAttributeValueSet |
| Multi-segment accounts | LedgerDimensionAccount | DimensionAttributeValueCombination |
| Posting profile accounts only | LedgerDimensionDefaultAccount | DimensionAttributeValueCombination |
| Journal lines using `LedgerJournalACType` to determine the account type | DimensionDynamicAccount | DimensionAttributeValueCombination |
| Default main accounts or non-ledger accounts | DimensionDynamicDefaultAccount | DimensionAttributeValueCombination |

> [!NOTE]
> Don't store module-specific scenarios that don't fall into any of the preceding categories in dimension tables.

## Impact of incorrect EDT usage

- **Dimension reference scanners** can't correctly identify dimension usage on fields with the wrong EDT.
- **Data maintenance actions** fail to process dimension data correctly, which can lead to data corruption during cleanup.

## See also

- [Make backing tables consumable as financial dimensions](/dynamics365/fin-ops-core/dev-itpro/financial/dimensionable-entities)
- [Modifying financial dimension data](/dynamics365/fin-ops-core/dev-itpro/financial/modifying-financial-dimension-data)
