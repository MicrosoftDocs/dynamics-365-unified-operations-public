---
# required metadata

title: Currency revaluation posting profiles
description: This article describes the Currency revaluation posting profiles.
author: moaamer
ms.date: 01/10/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerClosingSheet
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 14091
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2022-11-28
ms.dyn365.ops.version: AX 10.0.0

---

# Currency revaluation posting profiles

The currency revaluation posting profile allows you post currency revaluation adjustment to different accounts per module (General ledger, Accounts payable, Accounts 
receivable and Bank), it also gives you the ability to configure the posting to lower granular level on each module where you can define currency revaluation posting 
account per currency code and to the lowest level of ledger account, vendor, customer and bank. The differentiation could be for unrealized gain or loss for all modules,
the realized gain or loss only available for accounts payable and accounts receivable.  

The currency revaluation posting profile is under General ledger| Currencies| Currency revaluation posting profile to create a new record select New or Ctrl+N. You’ll 
need to select the gain or loss posting.

In the currency code you can select All currencies or define specific currency by selecting Table in the currency code. In the Account code you can select All, Group or
Table to be able to identify account or main account depending on the module page you already selected. The Main account is a mandatory field where you select the 
currency revaluation posting account that will be used during the currency revaluation adjustment. 


As an example, the Unrealized gain for General ledger post the currency revaluation of EUR transactions on main account 600120 to adjustment account 801602. To post 
currency revaluation of all currencies on accounts that belongs to Travel and Expense (TANDEEXP) main category to adjustment account 801601. To post currency 
revaluation of all currencies on all accounts to adjustment account 801600.
