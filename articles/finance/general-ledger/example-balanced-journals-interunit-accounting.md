---
# required metadata

title: Balanced journals for interunit accounting
description: This article shows how a journal is automatically balanced when a balancing financial dimension is selected on the Ledger page. 
author: kweekley
ms.date: 07/19/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 301bd80e-f8b1-4f12-8194-e6d7de736084
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Balanced journals for interunit accounting

[!include [banner](../includes/banner.md)]

This article shows how a journal is automatically balanced when a balancing financial dimension is selected on the Ledger page. 

If account entries don't balance at the detail level of the financial dimension values, additional account entries are created automatically to balance the journal. These account entries use the **Interunit - debit** and **Interunit - credit** posting types on the **Accounts for automatic transactions** page to determine the main account. For example, Business Unit, which is the second segment of the ledger account, is selected as the balancing financial dimension, and the following accounting entries are about to be created.

| &nbsp;               | &nbsp;    |
|----------------------|-----------|
| 6100 – MSP – OU\_256 | 100.00 DR |
| 6100 – NY – OU\_249  | 100.00 DR |
| 2100 – MSP – OU\_256 | 200.00 CR |

In this case, the following balances are determined:

-   For Business Unit MSP = 100.00 CR
-   For Business Unit NY = 100.00 DR
-   For Business Unit MSP = 200.00 DR

Therefore, the following accounting entries are created automatically to balance the  journal at the level of the financial dimension values.

| &nbsp;                            | &nbsp;    |
|-----------------------------------|-----------|
| (Interunit Debit) – MSP – OU\_256 | 100.00 DR |
| (Interunit Credit) – NY – OU\_249 | 100.00 CR |
| (Interunit Debit) - MSP - OU\_256 | 200.00 DR |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
