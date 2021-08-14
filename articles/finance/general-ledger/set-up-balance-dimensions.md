---
# required metadata

title: How do I set up balancing financial dimensions?
description: This topic describes the options for setting up and using the Balancing financial dimension feature.
author: kweekley
ms.date: 08/17/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DimensionDetails
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2021-08-17
ms.dyn365.ops.version: 10.0.210
---

#  How do I set up balancing financial dimensions?

[!include [banner](../includes/banner.md)]

This topic describes the options for setting up and using the Balancing financial dimension feature.  

## Symptom

There are two options to setup balancing financial dimensions.  The first option is found on the **Ledger** setup page (**General ledger > Ledger setup > Ledger**), which contains the **Balancing financial dimension** field.  The second option is found on the **Financial dimensions** page (**General ledger > Chart of accounts > Dimensions > Financial dimensions**), which contains the **Require the dimension to be balanced** field. 
What is the difference between the two? 

## Resolution

Typically, balancing dimensions are used by an organization to generate a balance sheet that’s in balance at the financial dimension level. Before either of these fields is set to **Yes**, you’ll need to determine whether or not enabling these features will change any posted transactions.  If the balance sheet isn’t balanced at the selected financial dimension already, it still won’t be in balance even if you set either field to Yes. You might need to enter adjusting entries manually to bring the balance sheet into balance before setting either of the fields to Yes. 

The two referenced options are mutually exclusive; the option your organization uses should be based on your business requirements.  We often hear of customers marking the balancing dimension option on both the Ledger and Financial dimensions, completing some or all of the additional setup required, but still aren’t able to post due to an imbalance at the financial dimension level. The following information explains each option, along with an overview of how to set up each one. 

### Ledger – Balancing financial dimension

The balancing dimension on the **Ledger ** setup page s used to enable interunit accounting. Complete the following steps to turn on the feature:

- Determine which financial dimension will be the balancing dimension

  - This feature permits only one financial dimension to be selected as the balancing dimension.

  - Don’t select the dimension yet in the **Ledger setup** page yet

  - Be sure that your balance sheet is already balanced for the selected financial dimension

- Update the account structure for the balancing financial dimension

  - The balancing financial dimension must be included in all account structures assigned to the ledger.  

  - The financial dimension must not allow blanks in the account structure. This is to ensure that every accounting entry posted to general ledger contains a financial dimension value.  A blank dimension isn’t valid using balancing dimensions. 

- Define the interunit - debit and interunit - credit main accounts on the **Accounts for automatic transactions** page (**General ledger > Posting setup > Accounts for automatic transactions**).

- Set the financial dimension on **Balancing financial dimension** the field on the **Ledger** setup page (**General ledger > Ledger setup > Ledger**).

As transactions are entered and posted, if the selected financial dimension value isn’t balanced, the system will automatically add the interunit debit and interunit credit during posting to balance the accounting entry.  The interunit debit and interunit credit ledger accounts are shown on the posted voucher in General ledger, but they won’t be shown on the journals or source documents for which the accounting entries were posted. 
### Financial dimensions – Require the dimension to be balanced
The balancing dimension on the **Financial dimensions** page is typically used by public sector companies, but there isn’t a limitation within the system.  The functionality isn’t tied to any public sector configuration key, you can use the functionality regardless of whether your organization is a public sector entity or not.

The feature is typically used within the public sector customer base because it requires the use of posting definitions to automatically balance each transaction.  **This feature *doesn’t* automatically balance the accounting entries using the interunit debit and interunit credit defined accounts in the Accounts for automatic transactions.  If the accounting entry isn’t balanced at the dimension level after applying the posting definitions, the transaction will not post, even if the interunit debit and credit accounts are defined. They’re never used by this feature.  

We often see customers defining the balancing dimension at both the ledger setup and at the financial dimension setup.  If this is done, the system ultimately uses the financial dimensions functionality. The setup for the balancing dimensions at the financial dimension level takes precedence during posting. Posting will fail if the posting definition doesn’t create a balanced accounting entry at the financial dimension level. 
Complete the following to enable the feature:

- Determine which financial dimensions will be the balancing dimensions. 

  - You can set more than one financial dimension to be selected as balancing.

  - Don’tset the financial dimensions that will be needed  to balance a transaction on the **Financial dimensions** page yet.

- Define the posting definitions for each type of journal or source document used by your organization. Posting definitions consume the ledger accounts from an unposted journal or source document as ‘match criteria’.  It then returns the ‘generated entries’ which becomes the accounting entry.  If the posting definition is correctly setup, the generated entry includes the match criteria ledger accounts, plus additional accounts to balance the accounting entry at the dimension level. For more information, see [Posting definitions](posting-definitions.md). Posting definitions aren’t supported on every type of transaction. If a posting definition can’t be defined for a journal or source document, there are two options:

  - The transaction must be balanced at the financial dimension value by entering the transaction manually.  For example, if a general journal is entry is made and the Department dimension is the balancing dimension, you must ensure that each Department value is in balance.  If the dimension isn’t balanced for each department value, the voucher won’t post until the imbalance corrected. Correcting the imbalance requires manually adding an interunit debit or interunit credit to the voucher.

  - You shouldn’t use posting definition, which means can’t use the Balancing financial dimension feature when you set up financial dimensions. If you used posting definitions, you’ll be required to use balancing dimensions in the ledger setup. 

- After posting definitions are defined, the financial dimensions can be marked as needed to balance. 

As you enter and post transactions, the posting definitions are called during posting to determine the accounting entry. Validation occurs after the accounting entries have been determined if the financial dimension(s) are balanced.  If financial dimensions aren’t, the transaction won’t post and you’ll receive a message that the debits don’t equal the credits for a specific dimension. 

