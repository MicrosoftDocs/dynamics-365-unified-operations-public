---
title: Ledger and subledger accounting overview
description: Learn about ledgers and subledgers in Dynamics 365 finance and operations apps.
author: prasungoel
ms.author: prasungoel
ms.topic: article
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

A *ledger* captures the collection of main accounts in a defined structure. It represents the general ledger for a legal entity, where all the financial transactions are summarized and posted. Therefore, it serves as the basis for the preparation of statutory finance reports (balance sheets and profit and loss statements). Each legal entity can have one ledger, with the option of utilizing up to 10 posting layers to track the deltas for additional accounting standards.  

## Set up a ledger

For each legal entity in Microsoft Dynamics 365 Finance, details about the ledger must be configured. To configure ledger settings, go to **General ledger** \> **Ledger setup** \> **Ledger**.

A ledger has the following main components:

- Chart of accounts - Determines the main accounts used for all accounting entries posted to the ledger.
    -  Account structures determine which financial dimensions are used with the main accounts (can be different per main account or group of accounts) and which combination of financial dimension values are valid when posting into the ledger.  
- Calendar - Defines the fiscal year and periods of the ledger.   
- Currency - The accounting currency, or home currency, of the ledger. The reporting currency, which is considered a second accounting currency, is optional. The exchange rate types determine which exchange rate tables to use for transaction entry. When you set up a ledger, review the components before you defining them. The chart of accounts and the currencies can't be changed later. However, the fiscal calendar and account structure can be changed.

Learn more about how to configure a ledger in [Configure ledgers](configure-ledger.md).

## What is a subledger?

Most documents posted impact a subledger or a module. A subledger captures detailed accounting impact arising from the document posting. Examples of subledgers in Dynamics 365 finance and operations include Accounts payable, Accounts receivable, Inventory, Fixed assets, Tax and Production. Each subledger captures the document details relevant to that subledger. For example, when a customer invoice is posted, the customer’s balance is captured in the Accounts receivable module, the tax codes and amounts are captured in the Tax module, the cost of inventory sold is captured in the Inventory/Costing modules. In addition, each source document maintains the subledger journal account entries, which represent the detailed accounting entries of the document. The subledger journal account entries are ultimately transferred to the ledger.  

## Set up subledger postings

The subledger journal account entries are created through accounting rules defined through posting profile for each module. Posting profiles use the main accounts from the Chart of accounts defined in the Ledger setup. 

To set up posting profiles in finance and operations apps, follow these steps.

- **Accounts payable:** Go to **Accounts payable** > **Setup** > **Vendor posting profile**.
- **Accounts receivable:** Go to **Accounts receivable** \> **Setup** \> **Customer posting profile**.
- **Inventory:** Go to **Inventory management** \> **Posting** \> **Posting**.
- **Production groups:** Go to **Production control** > **Setup**  \> **Production** \> **Production groups**.

Additional posting profiles exist for other modules. 

Learn more about posting profiles in [Posting profiles overview](pstg-prfles-ovrvw.md).

## Link between a subledger and a ledger
When a source document is posted, the subledger journal account entry captures the accounting impact of that document. This subledger accounting contains the affected ledger accounts and the corresponding debit and credit amounts. The ledger accounts within the subledger journal account entries are created using the posting profiles for the main accounts, and financial dimensions from the document. The resulting ledger account (main account + financial dimension values) adheres to the chart of accounts and account structures defined within the ledger.  

The total debit and credit amounts must be balanced. The double entry bookkeeping principle requires that every transaction posted to an account has an equal and opposite entry to another account. For example, a product receipt for $100 in purchases results in a $100 debit to the Inventory account and an equivalent credit of $100 to the Purchase accrual account.  

The balanced accounting entry within the subledger journal account entry is then transferred to the ledger, either in detail or summary, depending on setup within General ledger parameters. 

To view transactions that are posted to the main account, go to **General ledger** > **Inquiries and reports** > **Voucher transactions** or go to the **Trial balance** list page from **General ledger** > **Inquiries and reports** > **Trial balance**. Drill down to the transaction details. 

The voucher is used as the shared reference between the subledger document and the accounting entries within the ledger. 

## Example: Product receipt subledger and ledger postings

After a **Product receipt** is posted for a purchase order, you can view the product receipt journal created during posting. From the **Product receipt** journal, click **Vouchers** to view the ledger accounting entry for the product receipt. 

In the **Voucher transactions** view, go to the **View subledger journal** tab to view the subledger details. More account entries may be shown in the subledger journal account entry because summarization may occur during the transfer to the ledger. 


