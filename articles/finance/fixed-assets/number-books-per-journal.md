---
title: Number of books per journal
description: Learn about the relationship between journals and asset books when you create a fixed asset acquisition or depreciation proposal through a batch job.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/12/2021
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-11-19
ms.search.form: 
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Number of books per journal

[!include [banner](../includes/banner.md)]

This article describes the relationship between journals and asset books when you create a fixed asset acquisition or depreciation proposal through a batch job. You can define the maximum number of books that are included for each acquisition and for depreciation by using the fields in the **Number of books per journal** section on the **General** tab of the **Fixed assets parameters** page (**Fixed assets \> Setup \> Fixed assets parameters**). These fields let you distribute the number of asset books per acquisition journal and depreciation journal.

For an acquisition proposal, the default value is at least 10,000 books. For a depreciation proposal, the default value is at least 2,000 books.

For example, if there are 4,000 fixed assets, and two books are associated with each asset, one book will be posted to the current layer, and the other book will be posted to the tax layer. If you acquire 4,000 fixed assets through batch processing, the batch job that creates one fixed asset acquisition journal will contain 4,000 asset books.

> [!NOTE]
> The journal that is created will continue to be used until the batch job is completed.
>
> The derived books aren't included in the maximum number of books per journal.

You can use  batch processing to run depreciation for the same set of acquired assets. For example, a batch job creates two depreciation journals, each of which consists of 2,000 asset books. The first journal will contain books that are associated with the fixed assets that are numbered 1 through 2,000. The second journal will then contain books that are associated with the fixed assets that are numbered 2,001 through 4,000.

The batch processing job excludes closed books. For example, in a batch job for depreciation, 10 of the first 2,000 books are closed. In this case, the first journal will contain books that are associated with the fixed assets that are numbered 1 through 2,011. The second journal will then contain books that are associated with the fixed assets that are numbered 2,012 through 4,000.

> [!NOTE]
> If you have fixed asset IDs with different separators (such as – or /), and you create fixed asset transactions in batch jobs, you must run a separate batch job for each type of separator. The system can't process different separators within the same batch job.

The limit on the number of books is applied if duplicate asset IDs don't exist in the same journal. However, if the asset ID is the same as the book ID, the number of books per journal can be exceeded to keep the asset ID in the same journal.

For example, there are 5,001 fixed asset IDs, three books are associated with each fixed asset ID, and each asset book is posted to the same posting layer. You run depreciation for three consecutive months, without summarizing.  The depreciation journal will be created through a batch job, and the system will create seven journals that have 667 fixed asset IDs and three books for each fixed asset ID. The result will be 2,001 books. Therefore, in three months, there will be 6,003 journal lines to maintain the same asset IDs in the same journal. The system will also create one journal that has 332 fixed asset IDs and three books for each fixed asset ID. In three months, there will be 2,988 lines.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
