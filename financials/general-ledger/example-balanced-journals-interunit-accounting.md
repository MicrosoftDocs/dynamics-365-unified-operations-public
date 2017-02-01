---
# required metadata

title: Balanced journals for interunit accounting | Microsoft Docs
description: This article shows how a journal is automatically balanced when a balancing financial dimension is selected on the Ledger page. 
author: twheeloc
manager: AnnBe
ms.date: 2015-12-03 20:52:10
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: LedgerParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 15791
ms.assetid: 48cc8971-833c-4760-bc8d-5310f76b1140
ms.region: Global
# ms.industry: 
ms.author: peakerbl

---

# Balanced journals for interunit accounting

This article shows how a journal is automatically balanced when a balancing financial dimension is selected on the Ledger page. 

If account entries don't balance at the level of the financial dimension values, additional account entries are created automatically to balance the journal. These account entries use the **Interunit - debit** and **Interunit - credit** posting types on the **Accounts for automatic transactions** page to determine the main account. For example, Branch, which is the second segment of the ledger account, is selected as the balancing financial dimension, and the following accounting entries are about to be created.

|                      |           |
|----------------------|-----------|
| 6100 – MSP – OU\_256 | 100.00 DR |
| 6100 – NY – OU\_249  | 100.00 DR |
| 2100 – MSP – OU\_256 | 200.00 CR |

In this case, the following balances are determined:

-   For Branch MSP = 100.00 CR
-   For Branch NY = 100.00 DR

Therefore, the following accounting entries are created automatically to balance the  journal at the level of the financial dimension values.

|                                   |           |
|-----------------------------------|-----------|
| (Interunit Debit) – MSP – OU\_256 | 100.00 DR |
| (Interunit Credit) – NY – OU\_249 | 100.00 CR |



