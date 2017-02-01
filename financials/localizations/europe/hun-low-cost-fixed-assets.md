---
# required metadata

title: Low-cost fixed assets | Microsoft Docs
description: This topic provides information about low-cost fixed assets for Hungary.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-19 19:43:08
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 264684
ms.assetid: 6af691a6-9fe8-4124-a60c-680cfd14d37c
ms.region: Hungary
# ms.industry: 
ms.author: epopov

---

# Low-cost fixed assets

This topic provides information about low-cost fixed assets for Hungary.

A low-cost asset is an asset for which the acquisition cost doesn't exceed a predefined amount. Hungarian tax law defines the limit (threshold) for low-cost assets. These assets can be fully depreciated at the same time that they are acquired.

## Set up parameters for lowcost fixed assets
### Set up the low-cost asset threshold

To set up the limit for low-cost assets, click **Fixed assets** &gt; **Setup** &gt; **Fixed assets parameters**. Then, in the **Low-cost asset threshold** field, enter the value limit for low-cost assets.

### Set up books

When you create an acquisition transaction for an asset that uses the book for low-cost assets, depreciation is generated automatically.

1.  Click **Fixed assets** &gt; **Setup** &gt; **Books**.
2.  Select the book for low-cost assets, and select the **Low-cost asset** check box.

**Note:** Only value models that use the "Manual" or "Straight line service life" depreciation profiles/global methods, or the Hungary-specific "Straight line (Hu)" method, are available for low-cost depreciation.

### Generate acquisition and depreciation transactions for low-cost fixed assets

When you acquire an asset, you create an acquisition transaction from the pre-acquisition transaction. When you post the acquisition transaction for a low-cost asset, the depreciation transaction is generated automatically.

