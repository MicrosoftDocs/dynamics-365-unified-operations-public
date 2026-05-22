---
title: Derogatory depreciation for France
description: This article provides information about derogatory depreciation for France and how to set it up.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/11/2026
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2016-02-28
ms.search.form: AssetPosting, AssetBook, AssetBookTable
---

# Derogatory depreciation for France

[!include [banner](../../includes/banner.md)]

This article provides information about derogatory depreciation for France and how to set it up. In derogatory depreciation, you calculate an extra amount of depreciation as the difference between the depreciation amount on the tax book and the depreciation amount on the accounting book during the life of a fixed asset.

You post this extra amount of depreciation as the **Derogatory increase** transaction type on the accounting book if the depreciation amount on the tax book is higher than the depreciation amount on the accounting book. Alternatively, you post this extra amount of depreciation as the **Derogatory decrease** transaction type. For example, a fixed asset that has acquisition amount of EUR 1,000 is depreciated in the accounting book for five years and in the tax book for three years. In the first year, the accounting depreciation is EUR 200 (1,000 ÷ 5), and the tax depreciation is EUR 333.33 (1,000 ÷ 3). Therefore, the extra amount is EUR 133.33 (\[1,000 ÷ 3\] – \[1,000 ÷ 5\], or 333.33 – 200.00) and is posted as a derogatory increase. After the third year of the life cycle, the accounting depreciation is EUR 200 (1,000 ÷ 5), and the tax depreciation is 0 (zero). Therefore, the extra amount is EUR 200 (0.00 – \[1,000 ÷ 5\], or 0.00 – 200.00) and is posted as a derogatory decrease. To use derogatory depreciation, you first create and set up accounting and derogatory tax books, and assign them to an asset. For the derogatory tax model, you enable the **Derogatory tax model** field on the **Books** page. For the accounting model, you select the derogatory tax model in the **Derogatory calculation** field. The following conditions must be met:

- Both books must have the **Depreciation** field enabled.
- **Allow negative net book value** is disabled in both books.
- Both books have the same value in the **Calendar** field.
- Both books must have the same posting layer set to **Current**.
- The depreciation profile that you select on the derogatory book must have full depreciation activated if the depreciation method is of the **Reducing Balance** type.
- The depreciation profiles that you select on both value models must have the same settings for **Depreciation Year** and **Period Frequency**.
- Both books must have the same setting in the **Depreciation convention** field on the **Books** page (**Fixed assets** > **Fixed assets** > **Fixed assets** > Select a fixed asset and then click **Books**).
- The **Placed in service** dates must be the same in both books as soon as you assign the books to a specific asset.

On the **Fixed asset posting profiles** page, you set up general ledger accounts for **Derogatory increase** and **Derogatory decrease** transactions in the accounting book. On the **Disposal parameters** page, you can complete the setup to post derogatory increase amounts or derogatory decrease amounts to specific general ledger accounts during disposal. You can review the derogatory depreciation amounts for the accounting book on the **Fixed asset balances** page, the **Fixed asset note** report, or the **Fixed asset movement** report.

## Additional resources

[Fixed asset value model and depreciation book merge](../../fixed-assets/fixed-asset-value-model-depreciation-book-merge.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
