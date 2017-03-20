---
# required metadata

title: Post fixed asset transactions to posting layers
description: This article gives an overview of posting layer functionality for fixed asset transactions.
author: twheeloc
manager: AnnBe
ms.date: 2015-09-10 20 - 18 - 26
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetBookTable, LedgerJournalTransAsset
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 3001
ms.assetid: 7dabde57-0843-47c3-85ef-f36b6f472e30
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Post fixed asset transactions to posting layers

This article gives an overview of posting layer functionality for fixed asset transactions.

A fixed asset is often depreciated in different ways for different purposes. Depreciation for tax purposes is calculated by current tax rules to achieve the highest possible depreciation before taxes, but depreciation for reporting purposes is calculated according to accounting laws and standards. The various kinds of depreciation are calculated and recorded separately in the posting layers. 

Each value model that is attached to a fixed asset is set up for a particular posting layer that has an overall depreciation objective. There are three types of posting layers. Current and Operations are used for accounting purposes, and Tax is used for tax depreciation. You can use depreciation books instead of the tax layer, if you prefer. 

Each journal that you can post depreciations in is defined by its journal name for only one posting layer. The posting layer in the journal cannot be changed, which helps make sure that transactions for each posting layer are kept separate. At least one journal name must be created for each posting layer. 

You can designate ledger accounts for fixed asset transactions in the Fixed asset posting profiles page. For each posting profile, you must select the relevant transaction type and value model, with the relevant posting layer, and then designate the ledger accounts. If special accounts for tax depreciation are created, they are often put at the end of the chart of accounts and have account numbers that differ from the account numbers for usual business.

> [!NOTE] 
> Using derived value models lets you post transactions to different posting layers at the same time. You create the transactions of the primary value model in a journal with the posting layer that corresponds to the value model posting layer. During posting, the derived value model transactions are posted to their respective posting layers.

For more information see, [Derived books](derived-books.md) and [Posting with derived books](post-derived-value-models.md).

