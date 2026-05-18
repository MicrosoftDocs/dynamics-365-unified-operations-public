---
title: Advanced bank reconciliation setup process
description: Advanced bank reconciliation allows you to import electronic bank statements and automatically reconcile with bank transactions in Microsoft Dynamics 365 Finance.
author: EricWangChen
ms.author: wangchen
ms.topic: install-set-up-deploy
ms.date: 04/01/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:  BankReconciliationMatchRule, BankReconciliationMatchRuleSet
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: ae071f04-f038-4b17-812d-0a241ed15521
---

# Advanced bank reconciliation setup process

[!include [banner](../includes/banner.md)]

Advanced bank reconciliation enables you to import electronic bank statements and automatically reconcile them with bank transactions in Microsoft Dynamics 365 Finance. This article explains the setup processes for reconciliation.  

There are a number of pieces that must be set up before using the advanced bank reconciliation functionality. For more information about setting up bank statement import, see [Set up the advanced bank reconciliation import using Electronic reporting](../accounts-payable/import-bai2-er.md). Requirements for set up of the reconciliation process are detailed below.

## Transaction codes

Use transaction codes as part of the bank reconciliation matching rules. Transaction codes help you match only the same types of transactions between Finance and your bank statement. To use this type of matching, first define transaction types for bank transactions from Finance, and then map those types to statement transaction codes that your bank uses. Define transaction types for bank transactions on the **Bank transaction type** page. This page is also where you define the main account to use for postings associated with that transaction type.

After you define your bank transaction codes, map them to the transaction codes used in your electronic bank statements. Use the **Transaction code mapping** page for this mapping process. Complete transaction code mapping separately for each bank account.

## Matching rules and matching rule sets

Matching rules allow you to define criteria for automatic reconciliation between Finance bank transactions and bank statement transactions. Setup of matching rules is done on the **Reconciliation matching rules** page. For more information, see [Set up bank reconciliation matching rules](set-up-bank-reconciliation-matching-rules.md).

Use matching rule sets to define a group of matching rules that run in sequence during the bank reconciliation process.  Configure matching rule sets on the **Reconciliation matching rule sets** page.

## Cash and bank management parameters

The **Cash and bank management parameters** page contains parameters specific to the advanced bank reconciliation process. The **Show statement line amount in debit/credit** parameter changes the view of amounts on the **Bank statement** page. If you select this option, the bank statement transaction amounts appear in separate debit and credit columns. If you don't select it, the bank statement transaction amounts appear in a single amount column with the appropriate sign.

The validation options that you set on the **Cash and bank managment parameters** page override the selections set on matching rules. For example, you can't manually or automatically match documents beyond the date difference set on the parameters page. Also, if you select the option to **Validate transaction type mapping**, you must map the transaction types between the Finance bank transaction and bank statement transaction in order to manually or automatically match the transactions.  

You also must configure the necessary number sequences on the **Cash and bank management parameters** page.  On the **Number sequences** tab, set number sequence codes for the Download **ID, Statement ID, Reconcile ID, and Bank reconciliation** references.

## Bank account reconciliation options

You must first enable Advanced bank reconciliation for the bank account. A number of additional options are available on the **Bank account** page once the Advanced bank reconciliation functionality is enabled.

**Use bank statements as confirmation of electronic payment** functionality integrates the bank reconciliation functionality with electronic payment statuses. When this is enabled, a bank document will automatically be created for the electronic payment status is set to **Sent**. In addition, the status of an electronic payment will be updated from **Sent** to **Received** after the payment is matched, reconciled, and posted.

The **Bank account name in statements** field is the name you use for the bank account on your electronic bank statements. This name is used when determining what transactions to import for a bank account from a statement that might contain information for multiple bank accounts.

The option to **Reconcile after import** automatically validates the bank statement, creates a new bank reconciliation and worksheet, and runs the default matching rule set. This functionality automates the process up to the point of the transactions that you must manually match. The setting on the bank account defaults when importing.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
