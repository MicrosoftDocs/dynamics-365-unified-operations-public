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

# Choosing the Correct Extended Data Type (EDT) for Financial Dimension Foreign Keys

[!include [banner](../includes/banner.md)]

When creating fields with foreign keys to financial dimension tables, you must select the correct extended data type (EDT). Both the foreign key relation and the correct EDT are necessary for the dimension framework to function properly. Using the incorrect EDT can result in data corruption and cause unintended behavioral differences within the application.

The dimension framework contains reference scanners and data maintenance actions that identify dimension usage. Using the incorrect EDT prevents these scanners from detecting the dimension usage.

## EDT reference guide

There are five main EDTs used in the dimension framework.

### DimensionDefault

- **Foreign key to:** DimensionAttributeValueSet
- **Use for:** Unordered set of dimension name/value pairs, primarily used in master data and header records.
- **Examples:** Customer/vendor default dimensions, project templates.

### LedgerDimensionAccount

- **Foreign key to:** DimensionAttributeValueCombination
- **Use for:** Multi-segment ledger accounts that include the main account plus financial dimensions.
- **Examples:** Journal lines where you need the full ledger account combination (main account plus all dimensions resolved).

### LedgerDimensionDefaultAccount

- **Foreign key to:** DimensionAttributeValueCombination
- **Use for:** Posting profiles or setup tables where only the main account is stored.
- **Examples:** Accounts payable/receivable posting profiles, parameters where you define a single main account for a process.

### DimensionDynamicAccount

- **Foreign key to:** DimensionAttributeValueCombination
- **Use for:** Non-ledger account types where a companion account type enum (typically `LedgerJournalACType`) determines the backing entity. The value is a single-segment DAVC referencing an entity such as Customer, Vendor, Bank, Fixed Asset, or Project.
- **Examples:** LedgerDimension and OffsetLedgerDimension on the general journal. If you select Ledger as the account type, you can enter a full ledger account. But if you select Customer or Vendor, you can select a customer or vendor for the LedgerDimension.

### DimensionDynamicDefaultAccount

- **Foreign key to:** DimensionAttributeValueCombination
- **Use for:** Scenarios where the dimension value could come from a default account or a non-ledger account such as Customer or Vendor.
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
> Module-specific scenarios that do not fall into any of the above categories should not be stored in dimension tables.

## Impact of incorrect EDT usage

- **Dimension reference scanners** can't correctly identify dimension usage on fields with the wrong EDT.
- **Data maintenance actions** fail to process dimension data correctly, which can lead to data corruption during cleanup.

## See also

- [Make backing tables consumable as financial dimensions](/dynamics365/fin-ops-core/dev-itpro/financial/dimensionable-entities)
- [Modifying financial dimension data](/dynamics365/fin-ops-core/dev-itpro/financial/modifying-financial-dimension-data)
