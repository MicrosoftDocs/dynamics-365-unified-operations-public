---
title: Low-cost fixed assets
description: Learn about low-cost fixed assets for Hungary, including overviews on setting up low-cost asset thresholds and books for low-cost fixed assets.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: article
ms.date: 10/31/2017
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Hungary
ms.search.validFrom: 2016-11-30
ms.search.form: AssetParameters
ms.dyn365.ops.version: Version 1611
---

# Low-cost fixed assets

[!include [banner](../../includes/banner.md)]

This article provides information about low-cost fixed assets for Hungary.

A low-cost asset is an asset for which the acquisition cost doesn't exceed a predefined amount. Hungarian tax law defines the limit (threshold) for low-cost assets. These assets can be fully depreciated at the same time that they are acquired.

## Set up the low-cost asset threshold

To set up the limit for low-cost assets, click **Fixed assets** &gt; **Setup** &gt; **Fixed assets parameters**. Then, in the **Low-cost asset threshold** field, enter the value limit for low-cost assets.

## Set up books for low-cost fixed assets

When you create an acquisition transaction for an asset that uses the book for low-cost assets, depreciation is generated automatically.

1.  Click **Fixed assets** &gt; **Setup** &gt; **Books**.
2.  Select the book for low-cost assets, and select the **Low-cost asset** check box.

**Note:** Only value models that use the "Manual" or "Straight line service life" depreciation profiles/global methods, or the Hungary-specific "Straight line (Hu)" method, are available for low-cost depreciation.

## Generate acquisition and depreciation transactions for low-cost fixed assets

When you acquire an asset, you create an acquisition transaction from the pre-acquisition transaction. When you post the acquisition transaction for a low-cost asset, the depreciation transaction is generated automatically.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]