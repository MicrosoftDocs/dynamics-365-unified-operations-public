---
# required metadata

title: Configure account structures
description: This topic provides information about account structures and financial dimensions.
author: aprilolson
manager: AnnBe
ms.date: 04/10/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerEliminationRule
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 13131
ms.assetid: 08fd46ef-2eb8-4942-985d-40fd757b74a8
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure account structures

[!include[banner](../includes/banner.md)]

Account structures use the main account and financial dimensions to create a set of rules that determine the order and values used when entering the account number. You can set up as many account structures as you need for your business. The account structures are assigned to a company’s ledger setup, so they can be shared.

When creating an account structure, the maximum number of segments is 11. If you need more segments than this, thoroughly evaluate your setup and need for this many as it will impact the user experience. Consider if a segment could be derived in a reporting scenario using a hierarchy instead of during data entry, or by using a user defined field. For example, if you want to report on location, but you can figure location by department or cost center, you would not need location as a financial dimension. If after evaluation you do determine more than 11 segments are needed, you can add additional ones using advanced rules.

Account structures require the main account. The main account does not need to be the first segment in the structure, but it does identify what account structure is being used during the account number entry. Because of this, a main account value can only exist in one structure assigned to the ledger so that they do not overlap. Once the account structure is identified, the allowed values list is filtered to guide the user through picking only valid dimension values, decreasing the possibility of an incorrect journal entry.

> [!NOTE] 
> If you plan to budget against a financial dimension, it will need to be part of an account structure. Budgeting does not currently utilize advanced rules.

# Example
To illustrate a best practice for setting up an account structure, lets assume that a company wants to track their balance sheet accounts (100000..399999) at the account and Business unit financial dimension level. For revenue and expense accounts (400000..999999), they track financial dimensions Business Unit, Department, and Cost center. If they make a sale, they also like to track Customer. Using this scenario, it would be recommended to have two account structures assigned to the company’s ledger. One for Balance sheet accounts, and one for Profit and Loss accounts. To optimize the user experience and validation, Customer should be an advanced rule that is only used when a sales account is used.

**Balance sheet account structure**

|Main account          | Business Unit    |
|----------------------|-----------|
|100000..399999 | *;” “|

**Profit and loss account structure**

|Main account          | Business Unit    |Main account          | Business Unit    |
|----------------------|-----------|----------------------|-----------|
|400000..999999 | *;” “|*;” “|*;” “|*;” “|



