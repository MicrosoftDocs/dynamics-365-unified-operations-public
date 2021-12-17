---
# required metadata

title: Accounts for automatic transactions
description: This topic describes how accounts for automatic transactions are used for posting through Dynamics 365 and provides examples for key accounts for automatic transactions.
author: rachel-profitt
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerSystemAccounts
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2022-01-03
ms.dyn365.ops.version: AX 7.0.0

---
# Accounts for automatic transactions

The **Accounts for automatic transactions** page is used to define the default main account to be used for each posting type in the system. While most posting types can be configured in a module- or feature-specific page, some posting types can only be configured on the **Accounts for automatic transactions** page.

For example, you can configure the main account to be used for the Customer balance **Posting type** in **Summary** field on the **Customer posting profile** page and use a different main account for each customer profile. This allows you to have more granular control of the postings. On the other hand, the **Error account** can only be specified on the **Accounts for automatic transactions** page.

In a new legal entity, when you open **General ledger &gt; Setup &gt; Accounts for automatic transactions**, the list will be empty. You can add the most common posting types that should be configured on the page by clicking the **Create default types** button. Then for each row, you can select the main account in the **Main account** field to be used in the grid.

If the **Main account** field is left blank for a posting type and you haven't configured a main account in a module-specific or feature-specific page, an error will be received when you post a transaction that uses the posting type. The message will typically read "The account for \[Posting type\] cannot be found."

## Default posting types

The following table shows examples of the default posting types that are created when you click **Create default types.** The table shows sample main accounts and descriptions. The **Debit/Credit** column indicates whether the transaction typically Debit or Credit, or in some cases can post A either. The **Clearing account** column indicates whether the posting type is a clearing account. This means the amount posted in this account is automatically reversed when a later transaction is posted.

| Posting type                            | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | Description                                                                                                                                               |
|-----------------------------------------|----------------------|---------------------------|--------------|----------------|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Penny difference in reporting currency  | 618160               | Miscellaneous Expense     | Expense      | Both           | No               | Used when there is a penny difference when translating a foreign currency transaction amount to the reporting currency.                                   |
| Penny difference in accounting currency | 618160               | Miscellaneous Expense     | Expense      | Both           | No               | Used when there is a penny difference when translating a foreign currency transaction amount to the accounting currency.                                  |
| Error account                           | 999999               | Error Account             | Expense      | Both           | No               | Used when there is an error in the system. This account should be validated each period and any errors resolved.                                          |
| Year-end result                         | 300160               | Retained Earnings         | Equity       | Both           | No               | Used when running the year-end close process to move the balance of Profit-and-loss type accounts into the main account selected for the Year-end result. |
| Customer cash discount                  | NA                   | NA                        | NA           | NA             | No               | The accounts for automatic transactions posting type is not used. A main account is required when configuring Cash discounts in Accounts receivable.|
| Vendor cash discount                    | NA                   | NA                        | NA           | NA             | No               | The accounts for automatic transactions posting type is not used. A main account is required when configuring Cash discounts in Accounts payable.                                                                |

## Additional posting types

The following table shows examples of additional posting types that must be configured if you plan to use the related features. These posting types do not have posting profile configuration available in another module. The Debit/Credit column indicates if the transaction typically Debit or Credit, or in some cases can post either. The Clearing account column indicates whether the posting type is a clearing account. This means the amount posted in this account is automatically reversed when a later transaction is posted.

| Posting type                                          | Main account example | Main account name example   | Account type | Debit/ Credit? | Clearing account | Description                                                                                                                         |
|-------------------------------------------------------|----------------------|-----------------------------|--------------|----------------|------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Balance account for consolidation difference          | 801200               | Gain and Loss - Revaluation | Expense      | Both           | No               | Used when you perform a consolidation with a currency revaluation and there are penny differences during the revaluation.           |
| Profit and loss account for consolidation differences | 801200               | Gain and Loss - Revaluation | Expense      | Both           | No               | Used when you perform a consolidation with a currency revaluation and there are penny differences during the revaluation.           |
| Interunit – debit                                     | 133500               | Interunit Receivable        | Asset        | Debit          | No               | Used when you select a balancing dimension in the **Ledger** page and a transaction is posted where the dimension does not balance. |
| Interunit - credit                                    | 233500               | Interunit Payable           | Liability    | Credit         | No               | Used when you select a balancing dimension on the **Ledger** page and a transaction is posted where the dimension does not balance. |
