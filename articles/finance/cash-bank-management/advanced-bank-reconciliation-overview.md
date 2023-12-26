---
# required metadata

title: Advanced bank reconciliation overview
description: This article describes the flow for the advanced bank reconciliation process. The advanced bank reconciliation feature lets you import bank statements that can be automatically reconciled from within bank transactions.
author: angelad116
ms.date: 10/24/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankReconciliationMatchRule
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: b0705653-1fa6-4d94-9728-bcf9fb387ad1
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Advanced bank reconciliation overview

[!include [banner](../includes/banner.md)]

This article describes the flow for the advanced bank reconciliation process. The advanced bank reconciliation feature lets you import bank statements that can be automatically reconciled from within bank transactions.

The advanced bank reconciliation feature lets you import bank statements. The imported bank statement can then be automatically reconciled from within bank transactions. Here are the steps in the advanced bank reconciliation flow.

1.  Set up a bank statement import.
    -   Import bank statements through the data entity framework.
    -   Three typical bank statement formats are built in: ISO20022, BAI2, and MT940.
    -   The functionality can be extended to any format.

2.  Set up a number sequence to use for advanced bank reconciliation, and define the bank reconciliation matching rules.
    -   A reconciliation matching rule is a set of criteria that are used to filter bank statement lines and Microsoft Dynamics 365 Finance bank transaction lines during the reconciliation process. Depending on your business practice, you can set up more than one matching rule to automate and optimize your reconciliation process.

3.  Reconcile bank statements with Finance bank transactions.
    -   Perform automatic matching and creation of reconciliation journals.
    -   View bank statements and Finance bank transactions side by side.
    -   Automatically post Finance bank transactions if they appear on a bank statement but don't appear in the Finance app.
    -   Generate a reconciliation statement.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
