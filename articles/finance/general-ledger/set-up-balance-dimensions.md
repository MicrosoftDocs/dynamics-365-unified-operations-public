---
# required metadata

title: How do I set up balancing financial dimensions?
description: This article describes the options for setting up and using the Balancing financial dimension feature.
author: kweekley
ms.date: 07/25/2024
ms.topic: article

# optional metadata

ms.search.form: DimensionDetails
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2021-08-17
ms.dyn365.ops.version: 10.0.210
---

# How do I set up balancing financial dimensions?

[!include [banner](../includes/banner.md)]

This article describes the options for setting up and using the Balancing financial dimension feature.

## Symptom

There are two options for setting up balancing financial dimensions. The first option is to use the **Balancing financial dimension** field on the **Ledger** setup page (**General ledger \> Ledger setup \> Ledger**).
The second option is to use the **Require the dimension to be balanced** field on the **Financial dimensions** page (**General ledger > Chart of accounts \> Dimensions \> Financial dimensions**). This article 
explains the difference between these two options.

## Resolution

Organizations typically use balancing dimensions to generate a balance sheet that's in balance at the financial dimension level. Enabling either feature will not bring posted, unbalanced dimensions into balance.
You must first enter adjusting entries manually to bring the balance sheet into balance before enabling either feature.

The two options are mutually exclusive. The option that your organization uses should be based on your business requirements. We often hear about customers who define the balancing dimension in both the ledger 
setup and the financial dimension setup, and then complete some or all of the additional setup that is required. However, they still can't post because of an imbalance at the financial dimension level.

The following sections describe the two options and explain how to set them up.

### Ledger – Balancing financial dimension

The balancing dimension on the **Ledger** setup page is used to enable interunit accounting. Follow these steps to turn on the functionality.

1. Determine which financial dimension is the balancing dimension.

    - This functionality lets you select only one financial dimension as the balancing dimension.
    - Don't yet select the dimension on the **Ledger** setup page.
    - Make sure that your balance sheet is already balanced for the selected financial dimension.

2. Update the account structure for the balancing financial dimension.

    - The balancing financial dimension must be included in all account structures that are assigned to the ledger.
    - The financial dimension must not allow blanks in the account structure. This restriction ensures that every accounting entry that is posted to General ledger contains a financial dimension value. A blank  dimension isn't valid when balancing dimensions are used.

3. On the **Accounts for automatic transactions** page (**General ledger \> Posting setup \> Accounts for automatic transactions**), define the interunit debit and credit main accounts.
4. On the **Ledger** setup page (**General ledger \> Ledger setup \> Ledger**), in the **Balancing financial dimension** field, select a financial dimension to use for balancing.

If the selected financial dimension isn't balanced as transactions are entered and posted, debit or credit entries are automatically added that are required to balance the accounting entry during 
posting. The debit and credit ledger accounts for the interunit transaction are shown on the posted voucher in General ledger. However, they won't be shown on the journals or source documents that the accounting 
entries were posted for.

### Financial dimensions – Require the dimension to be balanced

Although the balancing dimension on the **Financial dimensions** page is typically used by public sector companies, the functionality isn't linked to any public sector configuration key. Because there's no 
limitation in the system, you can use this functionality even if your organization isn't a public sector entity.

This functionality is typically used in the public sector customer base because it requires that posting definitions be used to automatically balance each transaction. It doesn't use the interunit debit and credit accounts that are defined on the **Accounts for automatic transactions** page to automatically balance the accounting entries. If an accounting entry isn't balanced at the dimension level after the posting definitions are applied, the transaction won't be posted, even if the interunit debit and credit accounts are defined.

We often hear about customers who define the balancing dimension in both the ledger setup and the financial dimension setup. In this case, the system uses the financial dimensions functionality. The setup for 
balancing dimensions at the financial dimension level takes precedence during posting. Posting will fail if the posting definition doesn't create a balanced accounting entry at the financial dimension level.

Follow these steps to turn on the use of a balancing dimension at the financial dimension level.

1. Determine which financial dimensions is the balancing dimensions.

    - You can set more than one financial dimension as a balancing dimension.
    - Don't yet set the financial dimensions that will be required to balance a transaction on the **Financial dimensions** page.

2. Define the posting definitions for each type of journal or source document used by your organization. Posting definitions consume the ledger accounts from an unposted journal or source document as ‘match criteria’. The posting definition then returns the ‘generated entries’ which become the accounting entry. If the posting definition is correctly set up, the generated entry includes the match criteria ledger accounts, plus additional accounts to balance the accounting entry at the dimension level. For more information, see [Posting definitions](posting-definitions.md). 

   Posting definitions aren’t supported on every type of transaction. For example, posting definitions can't be defined for any transactions entered through the General journal or the Fixed asset journal. If a
   posting definition can’t be defined for a journal or source document, the transaction must be manually balanced at the financial dimension value. For example, if a general journal entry is made and the
   Department dimension is the balancing dimension, you must ensure that each department value is in balance. If the dimension isn’t balanced for each department value, the voucher won’t post until the imbalance
    is corrected by manually adding an interunit debit or credit to the voucher. 

    > [!IMPORTANT]
    > If an excessive number of transactions must be manually balanced, you should **not** use the balancing dimension functionality on the **Financial dimensions** page. Instead, use the balancing dimension
    > functionality on the **Ledger** setup page.
3. After posting definitions are defined, the financial dimensions can be marked as required for balancing.

As you enter and post transactions, the posting definitions are called during posting to determine the accounting entries. If the financial dimensions are balanced, validation occurs after the accounting entries 
have been determined. If the financial dimensions aren't balanced, the transaction won't be posted, and you will receive a message that states that the debits don't equal the credits for a specific dimension.
