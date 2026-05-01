---
title: Low-cost fixed assets
description: Learn about low-cost fixed assets for Hungary, including overviews on setting up low-cost asset thresholds and books for low-cost fixed assets.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/20/2026
ms.reviewer: johnmichalak
ms.search.region: Hungary
ms.search.validFrom: 2016-11-30
ms.search.form: AssetParameters
ms.custom: 
  - bap-template
---

# Low-cost fixed assets

[!include [banner](../../includes/banner.md)]

This article provides information about low-cost fixed assets for Hungary.

A low-cost asset is an asset for which the acquisition cost doesn't exceed a predefined amount. Hungarian tax law defines the limit (threshold) for low-cost assets. You can fully depreciate these assets at the same time that you acquire them.

## Set up the low-cost asset threshold

To set up the limit for low-cost assets, select **Fixed assets** > **Setup** > **Fixed assets parameters**. Then, in the **Low-cost asset threshold** field, enter the value limit for low-cost assets.

## Set up books for low-cost fixed assets

When you create an acquisition transaction for an asset that uses the book for low-cost assets, the system automatically generates depreciation.

1.  Select **Fixed assets** > **Setup** > **Books**.
1.  Select the book for low-cost assets, and select the **Low-cost asset** check box.

> [!NOTE]
> Only value models that use the "Manual" or "Straight line service life" depreciation profiles/global methods, or the Hungary-specific "Straight line (Hu)" method, are available for low-cost depreciation.

## Generate acquisition and depreciation transactions for low-cost fixed assets

When you acquire an asset, you create an acquisition transaction from the pre-acquisition transaction. When you post the acquisition transaction for a low-cost asset, the system automatically generates the depreciation transaction.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]