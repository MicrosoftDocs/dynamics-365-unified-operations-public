---
title: Financial tag rule reference
description: Learn about financial tags rules with PowerFx formulas
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 10/27/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-03-23
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage, FinTagRule, FinancialTags
ms.dyn365.ops.version: 10.0.42
---

[!include [banner](../includes/banner.md)]

# Additional reference information for Financial tag rules. 

## PowerFx formula reference for Financial tag rules

| Formula   | Description | Example     |
|-----------|-------------|-------------|
| If | Returns one value if a condition is true and another value if not. | <c>If( doc.AccountType = LedgerJournalACType.Cust, doc.Customer.Name, Blank() )</c> | 
| | | |
|*not sure what we want to put here actually. | .. | .. |

## Supported list of fields for all Journals

| Field name | PowerFx | Description |
|-----------|-------------|-------------|
| Account Type | doc.AccountType | refers to the account type value in the journal line | 
