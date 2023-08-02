---
# required metadata

title: Posting definition examples
description: This article provides examples that show how posting definitions are used for purchase order encumbrances and budget appropriations.
author: kweekley
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: JournalizingDefinition, JournalizingDefinitionTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 3864e4da-853f-403d-b906-79631d80b363
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Posting definition examples

[!include [banner](../includes/banner.md)]

This article provides examples that show how posting definitions are used for purchase order encumbrances and budget appropriations.

Before you read this article, you should be familiar with posting definitions and transaction posting definitions. For information, see [Posting definitions](posting-definitions.md). The following examples can be set up on the **Posting definitions** page. Each example contains these sections:

-   Posting definition – Match criteria
-   Posting definition – Generated entries
-   Transactions with the accounts, dimension values, and amounts
-   Ledger entries generated from the posting definition

When a match occurs between the accounts and dimension values in the **Match criteria** pane for the posting definition and the accounts and dimension values on the transaction, ledger entries are generated based on the **Generated entries** pane for the posting definition. 
> [!NOTE]
> To associate a posting definition with a specific transaction type, use the **Transaction posting definitions** page. After you associate a posting definition with a transaction type and select **Use posting definitions** on the **General ledger parameters** page, all transactions of the selected transaction type must use posting definitions.

## Example: Purchase order encumbrances
When you enable encumbrance processing by selecting **Enable encumbrance process** on the **General ledger parameters** page, posting definitions must be used to record encumbrances to the general ledger for any accounts that should be reserved. In most cases, all expense accounts are reserved on the balance sheet. 

Posting definitions for encumbrances are set up for the **Purchasing** module on the **Posting definitions** page. Then, in the **Purchasing** area of the **Transaction posting definitions** page, you can select the **Purchase order** transaction type to associate the posting definition with purchase orders. 

All voucher transactions for purchase order encumbrances must balance (that is, debits must equal credits) in each unique dimension on a voucher.

### Posting definition – Match criteria

| Account structure       | Match account number | Priority |
|-------------------------|----------------------|----------|
| Account Structure - P&L | \*                   | 1        |

<em>A blank value in the **Match account number</em>* field means that all matching accounts in the defined account structure are part of the matching rule.

### Posting definition – Generated entries

| Account structure | Generated account number                    | Generated debit/credit |
|-------------------|---------------------------------------------|------------------------|
| Balance           | 300143 - -(Encumbrance account)             | Same                   |
| Balance           | 300144 - -(Reserve for encumbrance account) | Balancing              |

### Transactions with the accounts, dimension values, and amounts

The accounts and dimension values come either from the accounting distributions that you enter for a purchase order line, or from the accounts and dimensions that are automatically generated based on the default settings for vendors, items, categories, and dimension templates.

| Account + dimensions           | Debit  | Credit | Comment |
|--------------------------------|--------|--------|---------|
| 606400-OU\_1-OU\_3566-Training | 250.00 |        |         |

### Ledger entries generated from the posting definition

Generated ledger entries are created to record the encumbrances.

| Account + dimensions           | Debit  | Credit | Comment |
|--------------------------------|--------|--------|---------|
| 300143-OU\_1-OU\_3566-Training | 250.00 |        |         |
| 300144-OU\_1-OU\_3566-Training |        | 250.00 |         |

In this example, any account that is part of Account Structure - P&L matches the posting definition criteria. Therefore, when 606500-OU\_1-OU\_3566-Training is evaluated, generated entries are created for the accounts that are defined in the **Generated entries** pane for the posting definition.

## Example: Budget appropriations
When you enable budget appropriation by selecting **Enable budget appropriation** on the **General ledger parameters** page, posting definitions must be used to record budget register entries to the general ledger. When a budget control configuration is active and is turned on, posting definitions and transaction posting definitions can be used to support the recording of entries for appropriations, revisions, transfers, projects, fixed assets, and supply and demand forecasts to the general ledger. 

To set up a posting definition for budget register entries that has a budget type of **Original budget**, and that has appropriations enabled, select the **Budget** module on the **Posting definitions** page. Then, in the **Budget** area of the **Transaction posting definitions** page, you can use budget codes to associate the posting definition with budget register entries that have a budget type of **Original budget**. 

When budget appropriations and posting definitions are enabled, the budget register entries are recorded for budget control and in the general ledger.

### Posting definition – Match criteria

| Account structure       | Match account number | Priority |
|-------------------------|----------------------|----------|
| Account Structure - P&L | \*                   | 1        |

<em>A blank value in the **Match account number</em>* field means that all matching accounts in the defined account structure are part of the matching rule.

### Posting definition – Generated entries

| Account structure | Generated account number              | Generated debit/credit |
|-------------------|---------------------------------------|------------------------|
| Account structure | 300145 - -(Estimated revenue account) | Same                   |
| Account structure | 300146 - -(Appropriation account)     | Balancing              |

### Transactions with the accounts, dimension values, and amounts

You enter the accounts, dimension values, and amounts for the budget account entry on the **Budget register entry** page.

| Account + dimensions           | Debit | Credit | Comment |
|--------------------------------|-------|--------|---------|
| 606400-OU\_1-OU\_3566-Training |       | 250.00 |         |

### Ledger entries generated from the posting definition

Generated ledger entries are created to record the original budget in each dimension.

| Account + dimensions           | Debit  | Credit | Comment |
|--------------------------------|--------|--------|---------|
| 300145-OU\_1-OU\_3566-Training |        | 250.00 |         |
| 300146-OU\_1-OU\_3566-Training | 250.00 |        |         |

In this example, any account that is part of Account Structure - P&L matches the posting definition criteria. Therefore, when 606400-OU\_1-OU\_3566-Training is evaluated, the generated ledger entries are created.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
