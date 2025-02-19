---
title: Ledger and subledger overview
description: Learn about ledgers and subledgers in Dynamics 365 finance and operations apps.
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

# Ledger and subledger overview

[!include [banner](../includes/banner.md)]

## What is a ledger?

A *ledger* captures the collection of main accounts in a defined structure. It represents the general ledger for a legal entity, where all the financial transactions are summarized and posted. Therefore, it serves as the basis for the preparation of statutory finance reports (balance sheets and profit and loss statements) and tax reporting.

## Set up a ledger

For each legal entity in Microsoft Dynamics 365 Finance, details about the ledger must be configured. To configure ledger settings, go to **General ledger** \> **Ledger setup** \> **Ledger**.

A ledger has the following the main components:

- The chart of accounts, fiscal calendar, and financial dimensions.
- The *account structure* that is applicable to the ledger. An account structure is a collection of main accounts by type and reporting requirements. For example, the balance sheet account structure contains a list of main accounts that are relevant to assets, liabilities, and owner equity.
- The accounting currency, reporting currency, and exchange rate type.

When you set up a ledger, it's important that you do a thorough review before you define these components. The chart of accounts and the currency can't be changed later. However, the fiscal calendar and account structure can be changed.

Learn more about how to configure a ledger in [Configure ledgers](configure-ledger.md).

## What is a subledger?

A *subledger* captures the detailed financial postings of any document that is created in a module. The subledger postings are summarized and eventually posted to the general ledger. Examples of subledgers in Dynamics 365 finance and operations apps include Accounts payable, Accounts receivable, Inventory, Fixed assets, and Production.

## Set up subledger postings

Subledger postings in an area are defined in the *posting profile* for the module.

To set up posting profiles in finance and operations apps, follow these steps.

- **Accounts payable:** Go to **Accounts payable** \> **Setup ** \> **Vendor posting profile**.
- **Accounts receivable:** Go to **Accounts receivable** \> **Setup** \> **Customer posting profile**.
- **Inventory:** Go to **Inventory management** \> **Posting** \> **Posting**.
- **Production groups:** Go to **Production control** \> **Production** \> **Production groups**.

Learn more about posting profiles in [Posting profiles overview](pstg-prfles-ovrvw.md).

## Link between a subledger and a ledger

When a transaction is posted in a module, a subledger journal is created to capture the accounting impact of that transaction. This subledger journal contains a list of all affected ledger accounts and the corresponding posting amount by debit and credit entries.

The total debit and credit amounts must be balanced. This principle requires that every transaction to an account has an equal and opposite entry to another account. For example, a product receipt for $100 in purchases results in a $100 debit to the Inventory account and an equivalent credit of $100 to the Purchase accrual account. In this way, every transaction that is posted in a module and has an accounting impact is recorded to the general ledger.

General ledger postings follow the ledger's account structure, fiscal calendar, and posting rules. When transactions are posted in the general ledger, only accounts from the chart of accounts that is defined in the ledger are used.

To view transactions that are posted to the main account, go to **General ledger** \> **Inquiries and reports** \> **Voucher transactions**.

The net of all postings to the general ledger is aggregated by using main account types:

- Asset
- Liability
- Revenue
- Expense
- Cost of goods sold

By account structure, either balance sheet or profit and loss. When financial reports are generated, they show transactions by legal entity.

## Product receipt subledger and ledger postings

After a Product receipt journal is created for a purchase order in finance and operations apps, the **Vouchers** tab shows the ledger account postings for the product receipt.

In the **Voucher transactions** view, the **View subledger journal** tab can be used to view the subledger details. Here are some examples of these details:

- Subledger journal number
- Posting type
- Ledger accounts
- Debit or credit amounts
- Currency

The total debit and credit amounts must be equal for the subledger.

The **Voucher transactions** view includes a **Transaction** list that shows all the documents that were posted to the selected main account.
