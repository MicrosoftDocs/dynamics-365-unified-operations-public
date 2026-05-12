---
title: Intercompany accounting setup
description: Learn how to set up intercompany accounting so that you can use intercompany journals for ledger allocations and financial journals, such as daily journals.
author: kweekley
ms.author: kweekley
ms.topic: install-set-up-deploy
ms.date: 04/01/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerInterCompany
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 1362297b-7a51-4930-b822-2b204a2e3c37
---

# Intercompany accounting setup

[!include [banner](../includes/banner.md)]

This article explains how to set up intercompany accounting so that you can use intercompany journals for ledger allocations and financial journals, such as daily journals, vendor invoice journals, and payment journals.

Intercompany journals can be created in various scenarios, such as for daily journals, vendor invoice journals, ledger allocations, and centralized payments. To enable these scenarios, you must set up intercompany accounting.

## Define main accounts

First, create the intercompany main accounts to use for the **Due to** and **Due from** accounting entries. Use unique main accounts for each company to simplify the reconciliation and elimination of intercompany accounting entries. If you use a trading partner or counterpart dimension to identify the intercompany party, define this dimension as a fixed dimension on the main account that you define in Intercompany accounting. When you set up the main accounts, set the **Main account type** field to **Balance sheet** on the **Main accounts** page.

## Define journal names

Next, you must define a journal name. Set the **Journal type** field to **Daily** on the **Journal names** page. It's a good idea to use a specific journal name for intercompany accounting.

## Define intercompany accounting setup

Use the **Intercompany accounting** page to create the pairs of legal entities that can transact with each other. The Intercompany accounting setup is shared, so all legal entities can see the setup. When you create a new legal entity pair, be aware of which legal entity is the originating company versus the destination company. When entering intercompany transactions, the transaction determines which legal entity initiates or originates the transaction. For example, the intercompany accounting is set up for USMF (originating) and USSI (destination). If a user is active in USSI and enters an intercompany transaction with USMF, the transaction doesn't post because the intercompany accounting is only defined for USMF being the originator. If either company can originate a transaction, create a second legal entity pair for the reciprocal setup.

Select the **Debit account (Due from)** and **Credit account (Due to)** for both the originating and destination legal entity. Define which **Journal name** to use when the transaction is created in the destination company. The journal for the originating company is already known because the user selects it when creating the intercompany transaction.

Finally, select which legal entity receives the accounting for supporting amounts, such as cash discount or realized gains and losses for centralized payments.

You can easily set up a reciprocal relationship on the **Intercompany accounting** page by using the **Create reciprocal relationship** button after you create the first legal entity pair. When you create the reciprocal pair, the information for the destination company is copied to the originating company and vice versa. The journal defined for the destination company remains. Most organizations use the same naming convention for their journal names, so the journal name is the same. If the journal name is different, a warning appears on the field to notify you that the journal doesn't exist and a different journal can be selected.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
