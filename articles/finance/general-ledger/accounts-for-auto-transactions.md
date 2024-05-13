---
title: Accounts for automatic transactions
description: Learn how accounts for automatic transactions are used for posting through Microsoft Dynamics 365, with examples for key accounts for automatic transactions.
author: jchrist
ms.author: jchrist
ms.topic: article
ms.date: 05/13/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-01-03
ms.search.form: LedgerSystemAccounts
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
---

# Accounts for automatic transactions

The **Accounts for automatic transactions** page (**General ledger &gt; Posting setup &gt; Accounts for automatic transactions**) is used to define the default main account that is used for each posting type in the system. Although most posting types can be configured on a module-specific or feature-specific page, some posting types can only be configured on the **Accounts for automatic transactions** page.

For example, you can specify the main account that is used for the **Customer balance** posting type in the **Summary** field on the **Customer posting profile** page and use a different main account for each customer profile. In this way, you have more granular control over the postings. On the other hand, you can specify the error account only on the **Accounts for automatic transactions** page.

When you open the **Accounts for automatic transactions** page in a new legal entity, the list of accounts will be empty. You can add the most common posting types that should be configured on the page by selecting the **Create default types** button. Then, for each row, you can select the main account in the **Main account** field. If you leave the **Main account** field blank for a posting type, and you haven't configured a main account on a module-specific or feature-specific page, you will receive an error message when you post a transaction that uses the posting type. Typically, the message will be, "The account for \[Posting type\] cannot be found."

## Default posting types

The following table shows examples of the default posting types that are created when you select **Create default types** on the **Accounts for automatic transactions** page. It shows sample main accounts and descriptions. The "Debit/Credit?" column indicates whether the transaction typically posts a debit or credit. In some cases, a transaction can post either a debit or a credit. The "Clearing account" column indicates whether the posting type is a clearing account. If the posting type is a clearing account, the amount that is posted in the account is automatically reversed when a later transaction is posted.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|----------------------|---------------------------|--------------|---------------|------------------|-------------|
| Penny difference in reporting currency | 618160 | Miscellaneous Expense | Expense | Both | No | This posting type is used when a penny difference occurs when a transaction amount in a foreign currency is translated to the reporting currency. |
| Penny difference in accounting currency | 618160 | Miscellaneous Expense | Expense | Both | No | This posting type is used when a penny difference occurs when a transaction amount in a foreign currency is translated to the accounting currency. |
| Error account | 999999 | Error Account | Expense | Both | No | This posting type is used when an error occurs in the system. The account should be validated every period, and any errors should be resolved. |
| Year-end result | 300160 | Retained Earnings | Equity | Both | No | This posting type is used when the year-end close process is run to move the balance of accounts of the **Profit-and-loss** type into the main account that is selected for the year-end result. |
| Customer cash discount | Not applicable | Not applicable | Not applicable | Not applicable | No | The posting type that is defined on the **Accounts for automatic transactions** page isn't used. A main account is required when cash discounts are configured in Accounts receivable.|
| Vendor cash discount | Not applicable | Not applicable | Not applicable | Not applicable | No | The posting type that is defined on the **Accounts for automatic transactions** page isn't used. A main account is required when cash discounts are configured in Accounts payable. |

## Additional posting types

The following table shows examples of additional posting types that must be configured if you plan to use the related features. For these posting types, no posting profile configuration is available in another module. The "Debit/Credit?" column indicates whether the transaction typically posts a debit or credit. In some cases, a transaction can post either a debit or a credit. The "Clearing account" column indicates whether the posting type is a clearing account. If the posting type is a clearing account, the amount that is posted in the account is automatically reversed when a later transaction is posted.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|----------------------|---------------------------|--------------|---------------|------------------|-------------|
| Balance account for consolidation difference | 801200 | Gain and Loss - Revaluation | Expense | Both | No | This posting type is used when you perform a consolidation that involves a currency revaluation, and penny differences occur during the revaluation. |
| Profit and loss account for consolidation differences | 801200 | Gain and Loss - Revaluation | Expense | Both | No | This posting type is used when you perform a consolidation that involves a currency revaluation, and penny differences occur during the revaluation. |
| Interunit – debit | 133500 | Interunit Receivable | Asset | Debit | No | This posting type is used when you select a balancing dimension on the **Ledger** page, and the dimension doesn't balance in a transaction that is posted. |
| Interunit - credit | 233500 | Interunit Payable | Liability | Credit | No | This posting type is used when you select a balancing dimension on the **Ledger** page, and the dimension doesn't balance in a transaction that is posted. |
