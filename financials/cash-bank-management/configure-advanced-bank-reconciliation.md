---
# required metadata

title: Advanced bank reconciliation overview
description: Advanced bank reconciliation allows you to import electronic bank statements and automatically reconcile with bank transactions in Microsoft Dynamics 365 for Operations.  This article will explain the set up processes for reconciliation.  
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 101
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 98303
ms.assetid: ae071f04-f038-4b17-812d-0a241ed15521
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Advanced bank reconciliation overview

Advanced bank reconciliation allows you to import electronic bank statements and automatically reconcile with bank transactions in Microsoft Dynamics 365 for Operations.  This article will explain the set up processes for reconciliation.  

There are a number of pieces that must be set up before using the advanced bank reconciliation functionality. For more information about setting up bank statement import, see [Set up the bank statement import process](set-up-advanced-bank-reconciliation-import-process.md).  Requirements for set up of the reconciliation process are detailed below.

## Transaction codes
Transaction codes can be used as part of the bank reconciliation matching rules.  Transaction codes will help to match only the same types of transactions between Dynamics 365 for Operations and your bank statement.  In order to do this type of matching, you must first define transaction types used for bank transactions from Dynamics 365 for Operations, then map those types to statement transaction codes used by your bank.  Transaction types for Dynamics 365 for Operations bank transactions are defined on the **Bank transaction type** page.  This is also where you define the main account to be used for postings associated with that transaction type. 

Once your Dynamics 365 for Operations bank transaction codes are defined, you then map those to the transaction codes used in your electronic bank statements.  This mapping process is done using the **Transaction code mapping** page.  Transaction code mapping is completed separately for each bank account.

## Matching rules and matching rule sets
Matching rules allow you to define criteria for automatic reconciliation between Dynamics 365 for Operations bank transactions and bank statement transactions.  Set up of matching rules is done on **Reconciliation matching rules** page.  For more information, see [Set up bank reconciliation matching rules](set-up-bank-reconciliation-matching-rules.md). 

Matching rule sets are used to define a group of matching rules that are run in sequence during the bank reconciliation process.  Matching rule sets are configured on the **Reconciliation matching rule sets** page.

## Cash and bank management parameters
There are a number of parameters specific to the advanced bank reconciliation process on the **Cash and bank management parameters** page.  The **Show statement line amount in debit/credit** changes the view of amounts on the **Bank statement** page.  If this option is selected, the bank statement transaction amounts will be shown in separate debit and credit columns.  If not selected, the bank statement transaction amounts will be shown in a single amount column with the appropriate sign. 

The validation options set on the parameters page override the selections set on matching rules.  For example, you cannot manually or automatically match documents beyond the date difference set on the parameters page.  Also, if the option to **Validate transaction type mapping** is selected, the transaction types must be mapped between the Dynamics 365 for Operations bank transaction and bank statement transaction in order for the transactions to be manually or automatically matched. 

You also must configure the necessary number sequences on the **Cash and bank management parameters** page.  On the **Number sequences** tab, set number sequence codes for the Download **ID, Statement ID, Reconcile ID, and Bank reconciliation** references.

## Bank account reconciliation options
You must first enable Advanced bank reconciliation for the bank account.  A number of additional options are available on the **Bank account** page once the Advanced bank reconciliation functionality is enabled. 

**Use bank statements as confirmation of electronic payment** functionality integrates the bank reconciliation functionality with electronic payment statuses.  When this is enabled, a bank document will automatically be created for the electronic payment status is set to **Sent**.  In addition, the status of an electronic payment will be updated from **Sent** to **Received** after the payment is matched, reconciled, and posted. 

The **Bank account name in statements** field is the name used for the bank account on your electronic bank statements.  This name is used when determining what transactions to import for a bank account from a statement that may contain information for multiple bank accounts. 

The option to **Reconcile after import** will automatically validate the bank statement, create a new bank reconciliation and worksheet, and run the Default matching rule set.  This functionality automates the process up to the point of the transactions that must be manually matched.  The setting on the bank account will default when importing.

