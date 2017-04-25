---
# required metadata

title: Post fixed asset transactions to posting layers
description: This article gives an overview of posting layer functionality for fixed asset transactions.
author: twheeloc
manager: AnnBe
ms.date: 04/25/2017
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

[!include[banner](../includes/banner.md)]


This article gives an overview of posting layer functionality for fixed asset transactions.

A fixed asset is often depreciated in different ways for different purposes. Depreciation for tax purposes is calculated by using current tax rules to achieve the highest possible depreciation before taxes, but depreciation for reporting purposes is calculated according to accounting laws and standards. The various kinds of depreciation are calculated and recorded separately in the posting layers.

Each book that is attached to a fixed asset is set up for a particular posting layer that has an overall depreciation objective. There are ten posting layers: Current, Operations, Tax, and seven Custom layers. You can also disable posting to the general ledger for the book by setting the Post to general ledger field to No. The Posting layer field is then automatically set to None. Typically, books that don’t post to the general ledger are used for tax reporting purposes. This approach gives you the additional flexibility to delete historical transactions for the asset book, because they haven’t been committed to the general ledger.

Fixed asset journals are defined by using the Journal names page at General ledger > Journal setup > Journal names. Each journal that you can post depreciations in is defined by its journal name for only one posting layer. The posting layer in the journal can’t be changed. This restriction helps guarantee that transactions for each posting layer are kept separate. At least one journal name must be created for each posting layer. If you’re using books that don’t post to the general ledger, you must also create a journal where the posting layer is set to None.

You can designate ledger accounts for fixed asset transactions on the Fixed asset posting profiles page. For each posting profile, you must select the relevant transaction type and book, and then designate the ledger accounts. Set up a posting profile record for each book that will post to the general ledger.

> [!NOTE] 
> By using derived books, you can post transactions to different posting layers at the same time. You create the transactions of the primary book in a journal where the posting layer corresponds to the book posting layer. During posting, the derived book transactions are posted to the appropriate posting layers.

For more information see, [Derived books](derived-books.md) and [Posting with derived books](post-derived-value-models.md).



