---
# required metadata

title: Intercompany accounting setup
description: This article explains how to set up intercompany accounting so that you can use intercompany journals for ledger allocations and financial journals, such as daily journals, vendor invoice journals, and payment journals.
author: kweekley
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerInterCompany
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 1362297b-7a51-4930-b822-2b204a2e3c37
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Intercompany accounting setup

[!include [banner](../includes/banner.md)]

This article explains how to set up intercompany accounting so that you can use intercompany journals for ledger allocations and financial journals, such as daily journals, vendor invoice journals, and payment journals.

Intercompany journals can be created in various scenarios, such as for daily journals, vendor invoice journals, ledger allocations, and centralized payments. To enable these scenarios, you must set up intercompany accounting.

## Define main accounts
First, you must create the intercompany main accounts to use for the Due to and Due from accounting entries. It's a good idea to use unique main accounts for each company, to simplify the reconciliation and elimination of intercompany accounting entries. If you're using a trading partner or counterpart dimension to identify the intercompany party, you can define this dimension as a fixed dimension on the main account that is defined in Intercompany accounting. When you set up the main accounts, you should set the **Main account type** field to **Balance sheet** on the **Main accounts** page.

## Define journal names
Next, you must define a journal name. Set the **Journal type** field to **Daily** on the **Journal names** page. It's a good idea to use a specific journal name for intercompany accounting.

## Define intercompany accounting setup
The **Intercompany accounting** page is used to create the pairs of legal entities that can transact with each other. The Intercompany accounting setup is shared, so the setup is visible from within all legal entities. When creating a new legal entity pair, ensure that you are aware of which legal entity is defined as the originating company versus the destination company. When entering intercompany transactions, the transaction determines which legal entity is initiating or originating the transaction. For example, the intercompany accounting is setup for USMF (originating) and USSI (destination). If a user is active in USSI and enters an intercompany transaction with USMF, the transaction will not post because the intercompany accounting is only defined for USMF being the originator. If either company can originate a transaction, you will need to create a second legal entity pair for the reciprocal setup. 

Select the **Debit account (Due from)** and **Credit account (Due to)** for both the originating and destination legal entity. Define which **Journal name** will be used when the transaction is created in the destination company. The journal for the originating company is already known because it's selected by the user when creating the intercompany transaction. 

Finally, select which legal entity will receive the accounting for supporting amounts, such as cash discount or realized gains/losses for centralized payments. 

A reciprocal relationship can easily be set up on the **Intercompany accounting** page by using the **Create reciprocal relationship** button after the first legal entity pair is created. When the reciprocal pair is created, the information for the destination company is copied to the originating company and vice versa. The journal defined for the destination company will remain. Most organizations use the same naming convention for their journal names, so that the journal name is the same. If the journal name is different, a warning will appear on the field to notify you that the journal doesn't exist and a different journal can be selected.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
