---
title: Configure ledgers and subledgers 
description: Learn about ledgers and subledgers in Dynamics 365 finance and operations 
author: kweekley
ms.author: kweekley
ms.topic: article
ms.date: 02/18/2025
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-09
ms.search.form: Ledger
ms.dyn365.ops.version: 8.1
---

# Configure ledgers and subledgers

[!include [banner](../includes/banner.md)]

## What is a ledger? 

A ledger captures the collection of main accounts in a defined structure. It represents the General ledger for a legal entity where all the financial transactions are summarized and posted. This is the basis for statutory finance reports (Balance sheet, Profit and loss statements) preparation and tax reporting. 

## Set up a ledger 

For each legal entity in Microsoft Dynamics 365 Finance, details about the ledger must be configured. To set up ledger settings, go to **General ledger** > **Ledger setup** > **Ledger**.  

The main components of the ledger are: 
 - Chart of accounts, fiscal calendar, and financial dimension.
 - Account structure applicable for the ledger. An Account structure is a collection of main accounts by type and reporting requirements. For example, the Balance sheet account structure contains list of main
accounts pertaining to assets, liabilities, and owners equity.
 - Accounting currency, reporting currency, and exchange rate type.  

When setting up a ledger, it's important to define the above components after thorough review as it's not possible to change chart of accounts and the currency. The Fiscal calendar and Account structure can be 
modified. 

For more information on configuring the ledger, see [Configure ledgers](configure-ledger.md).  
 
## What is a subledger? 

A subledger captures the detailed financial postings of any document created in a module. The subledger postings are summarized and eventually posted to the General ledger. Examples of subledgers in Dynamics 365 finance and operations apps are Accounts payable, Accounts receivable, Inventory, Fixed assets, and Production. 

## Set up subledger postings 

Subledger postings in an area are defined in the **Posting profile** for the module. 
To set up posting profiles in Dynamics 365 finance and operations apps, follow these steps: 
 - Account payable: **Account payable** > **Setup **> **Vendor posting profile**. 
 - Account receivable: **Account receivable** > **Setup** > **Customer posting profile**.
 - Inventory: **Inventory management** > **Posting** > **Posting**.
 - Production groups: **Production control** > **Production** > **Production groups**. 

For more information on Posting profiles, see [Posting profiles overview](pstg-prfles-ovrvw.md).   

## Link between a subledger and a ledger 

When a transaction is posted within a particular module, it creates a subledger journal to capture the accounting impact of the transaction. The subledger journal contains list of all affected ledger accounts, 
and the respective posting amount by debit and credit entries. 

The total debit and credit amounts must be balanced. This principle states that every transaction to an account has an equal and opposite entry to another account. 
For example, a product receipt for $100 in purchase, results in a $100 debit to Inventory account and an equivalent credit of $100 to the Purchase accrual account. In this way, each transaction posted in a module
with accounting impact is recorded to the General ledger. 

General ledger postings follow the ledger's account structure, fiscal calendar, and posting rules. When posting transactions in the General ledger, only accounts from the chart of accounts defined in the
ledger are used.  

To view transactions posted to the main account, go to **General ledger** > **Inquiries and reports** > **Voucher transactions**.   

The net of all postings to the General ledger is aggregated using main account types: 
 - asset
 - liability
 - revenue
 - expense
 - cost of goods sold
 
By account structure, either balance sheet or profit and loss. When generating financial reports, transactions are displayed per legal entity. 

## Product receipt subledger and ledger postings  

After a **Product receipt journal** is created for a **Purchase order** in Dynamics 365 finance and operations, the **Vouchers** tab displays the **Ledger account postings** for the **Product receipt**. 
In the **Voucher transactions** view, the **View subledger journal** tab can be used to show the subledger details including:
 - subledger journal number
 - posting type
 - ledger accounts
 - Debit or credit amounts
 - currency

The total Debit and Credit amounts must be equal for the subledger. 

**Voucher transactions** includes a **Transaction** list that displays all the documents posted to the selected main account. 
