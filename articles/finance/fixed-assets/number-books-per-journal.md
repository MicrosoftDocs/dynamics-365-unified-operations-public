---
# required metadata

title: Number of books per journal
description: This topic describes the relationship between journals and asset books when you create a fixed asset acquisition or depreciation proposal through a batch job. You can define the maximum number of books to be included per acquisition and for depreciation using the Number of books per journal parameter group. 
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

This topic describes the relationship between journals and asset books when you create a fixed asset acquisition or depreciation proposal through a batch job. You can define the maximum number of books to be included per acquisition and for depreciation using the **Number of books per journal** parameter group. The **Number of books per journal** parameter lets you distribute the number of asset books per acquisition and depreciation journal. You can access this parameter by in the **General** tab of the Fixed Assets parameters page (**Fixed assets > Setup > Fixed assets parameters**).

The default value are for an acquisition proposal is at least 10,000 books, and for a depreciation proposal, at least 2,000 books.

If there are 4,000 fixed assets and each asset has two associated books, one book will post to the current layer, and the other book will post to the tax layer. If you acquire 4,000 fixed assets thru batch processing, the batch job that creates one fixed asset acquisition journal will contain 4,000 asset books.

> [!NOTE] 
> The created journal will remain in use until the batch job finishes.

> [!NOTE] 
> The derived books are not included in the maximum number of books per journal.

You can run depreciation for the same set of acquired assets thru batch processing. The batch job creates two depreciation journals. Each journal consists of 2,000 asset books.
The first journal will contain books that are associated with fixed assets, numbered from 1 to 2,000. The second journal will contain books that are associated with fixed assets, numbered from 2,001 to 4,000.

The batch processing job excludes closed books. For example, assume that there are 10 closed books within the first 2,000, in a batch job for depreciation. The first journal will contain books that are associated with fixed assets, numbered from 1 to 2011. The second journal will contain books that are associated with fixed assets numbered 2012 through 4000. 

The limit on the number of books is applied if duplicate asset IDs don't exist in the same journal. But if the asset ID is same the as the book ID, the number of books per journal could be exceeded to keep the asset ID in the same journal.

If there are 5,001 fixed asset IDs along with three books that are associated to each fixed asset ID. Also assume that each asset book posts to the same posting layer, and that you run depreciation for three consecutive months without summarization. The depreciation journal will be created thru a batch job, and the system will create seven journals with 667 fixed asset IDs and three books for each fixed asset ID. This results in 2,001 books. In three months, this results in 6,003 journal lines to maintain the same asset IDs in the same journal. One journal with 332 fixed asset IDs and three books for each fixed asset ID and 3 months this result 2,988 lines.

 
