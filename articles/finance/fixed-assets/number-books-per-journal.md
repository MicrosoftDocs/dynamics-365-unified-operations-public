---
# required metadata

title: Number of books per journal
description: 
author: moaamer
manager: Ann Beebe
ms.date: 11/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-11-19
ms.dyn365.ops.version: 10.0.14
---

# Number of books per journal

[!include [banner](../includes/banner.md)]

This topic describes the relationship between journal and asset books when you create a depreciation proposal. You can define the maximum nunmber of books to be included per acquisition and for depreciation using the **Number of books per journal** parameter group. You can also define the maximum number of books to be included per acquisition and depreciation journal using the same parameter group. Aquisition and depreciation journals are created in a batch job. The **Number of books per journal** parameter helps you to distribute the number of asset books per acquisition and depreciation journal. You can access this parameter by in the **General** tab of the Fixed Assets parameters page (**Fixed assets > Setup > Fixed assets parameters**).

The default values are for an acquisition proposal is at least 10,000 books, and for a depreciation proposal, at least 2,000 books.

Assume that there are 4000 fixed assets, and each asset has two associated books, one book is posting to the current layer and the other book is posting to tax layer.

Acquiring 4000 fixed assets thru batch processing. The batch job creates one fixed asset acquisition journal contains 10,000 asset books.

> [!NOTE] 
> The created journal will remain as in use till the batch job finish.

Run depreciation for the same set of acquired assets thru batch processing. The batch job creates two depreciation journals, each journal consists of 2000 asset book.

The batch processing excludes the closed books. Assumes there are 10 books within the first 2000 books have been closed, while running the batch job for depreciation the first journal will contain associated books to fixed assets from 1 to 2011, and the second journal will contain associated book to fixed asset 2012 till 4000.

> [!NOTE] 
> The derived books are not considered in the maximum number of books per journal.

The limit on the number of books is applied if duplicate asset IDs aren't don't exist in the same journal. But if the asset ID is the as the book ID, the number of books per journal could be exceeded to keep the asset ID in the same journal.

Assumes, you have 5,001 fixed asset IDs along with three books that are associated to each fixed asset ID. Also assume that each asset ID posts to the same posting layer, and that you run depreciation for three consecutive months without summarization. The depreciation journal will be created thru a batch job, and the system will create seven journals with 667 fixed asset IDs and three books for each fixed asset ID. This results in 2,001 books. In three months, this results in 6,003 journal lines to maintain the same asset IDs in the same journal. One journal with 332 fixed asset IDs and three books for each fixed asset ID and 3 months this result 2988 lines.

 
