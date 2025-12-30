---
title: Ledger, subledger, and subledger journal accounting entries overview
description: Learn about ledgers and subledgers in Dynamics 365 finance and operations apps.
author: prasungoel
ms.author: prasungoel
ms.topic: concept-article
ms.date: 03/10/2025
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-09
ms.search.form: Ledger
ms.dyn365.ops.version: 8.1
---

# Ledger and subledger accounting overview

[!include [banner](../includes/banner.md)]

## What is a ledger?

A *ledger* captures the collection of main accounts in a defined structure. It represents the general ledger for a legal entity, where all the financial transactions are summarized and posted. Therefore, it serves as the basis for the preparation of statutory finance reports (balance sheets and profit and loss statements). Each legal entity can have only one ledger. However, up to 10 posting layers can be used to track the deltas for additional accounting standards.

## Set up a ledger

For each legal entity in Microsoft Dynamics 365 Finance, details about the ledger must be configured. To configure ledger settings, go to **General ledger** \> **Ledger setup** \> **Ledger**.

A ledger has the following main components:

- **Chart of accounts** – Determines the main accounts that are used for all accounting entries that are posted to the ledger.

    Account structures determine which financial dimensions are used with the main accounts. (Financial dimensions can be different for each main account or group of accounts.) Account structures also determine which combination of financial dimension values is valid when entries are posted to the ledger.

- **Calendar** – Defines the fiscal year and periods of the ledger.
- **Currency** – Defines the accounting currency, or home currency, of the ledger. The reporting currency is considered a second accounting currency and is optional. The exchange rate types determine which exchange rate tables are used for transaction entry.

Learn more about how to configure a ledger in [Configure ledgers](configure-ledger.md).

## What is a subledger?

Most documents that are posted affect a *subledger* or a *module*. Examples of subledgers in Dynamics 365 finance and operations apps include Accounts payable, Accounts receivable, Inventory, Fixed assets, Tax, and Production. Each subledger captures the document details that are relevant to it. For example, when a customer invoice is posted, the customer's balance is captured in the **Accounts receivable** module, the tax codes and amounts are captured in the **Tax** module, and the cost of inventory that was sold is captured in the **Inventory**/**Costing** modules.


## What are subledger journal account entries? 
Each source document maintains the subledger journal account entries, which represent the detailed accounting entries of the document. The subledger journal account entries are ultimately transferred to the ledger.  

The subledger journal account entries are created through accounting rules that are defined through the posting profile for each module. Posting profiles use the main accounts from the chart of accounts that is defined in the ledger setup.

To set up posting profiles in finance and operations apps, follow these steps:

- **Accounts payable:** Go to **Accounts payable** > **Setup** > **Vendor posting profile**.
- **Accounts receivable:** Go to **Accounts receivable** \> **Setup** \> **Customer posting profile**.
- **Inventory:** Go to **Inventory management** >  **Setup** \> **Posting** \> **Posting**.
- **Production groups:** Go to **Production control** > **Setup** \> **Production** \> **Production groups**.

Additional posting profiles exist for other modules.

Learn more about posting profiles in [Posting profiles overview](pstg-prfles-ovrvw.md).

## Link between a subledger and a ledger

When a source document is posted, the subledger journal account entry captures the accounting impact of that document. This subledger accounting contains the affected ledger accounts and the corresponding debit and credit amounts. The ledger accounts in the subledger journal account entries are created by using the posting profiles for the main accounts and the financial dimensions from the document. The resulting ledger account (main account &plus; financial dimension values) adheres to the chart of accounts and account structures that are defined in the ledger.

The total debit and credit amounts must be balanced. According to the requirements of the double-entry bookkeeping principle, every transaction that is posted to an account must have an equal and opposite entry in another account. For example, a product receipt for $100 in purchases results in a $100 debit to the Inventory account and an equivalent credit of $100 to the Purchase accrual account.

The balanced accounting entry in the subledger journal account entry is then transferred to the ledger, either in detail or summary, depending on the setup in General ledger parameters.

To view transactions that are posted to the main account, go to **General ledger** \> **Inquiries and reports** \> **Voucher transactions**. Alternatively, open the **Trial balance** list page by going to **General ledger** \> **Inquiries and reports** \> **Trial balance**. Drill down to the transaction details.

The voucher is used as the shared reference between the subledger document and the accounting entries in the ledger.

## Example: Product receipt subledger and ledger postings

After a product receipt is posted for a purchase order, you can view the product receipt journal that was created during posting. From the **Product receipt** journal, select **Vouchers** to view the ledger accounting entry for the product receipt.

In the **Voucher transactions** view, select the **View subledger journal** tab to view the subledger details. Because summarization can occur during the transfer to the ledger, more account entries might be shown in the subledger journal account entry.
