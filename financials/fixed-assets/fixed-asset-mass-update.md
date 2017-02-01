---
# required metadata

title: Fixed asset mass update | Microsoft Docs
description: If you use depreciation books, you can change the depreciation conventions for groups of assets that are part of the same depreciation book.
author: twheeloc
manager: AnnBe
ms.date: 2015-09-10 21:05:14
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 3521
ms.assetid: 7aa4123e-f166-4560-ab9a-ddbe5fa45b07
ms.region: Global
# ms.industry: 
ms.author: saraschi

---

# Fixed asset mass update

If you use depreciation books, you can change the depreciation conventions for groups of assets that are part of the same depreciation book.

For example, if you are in the United States, and you put more than 40 percent of your assets in service during the fourth quarter of the year, you must use the mid-quarter depreciation convention. You can use the process for a mass update to change all assets that require the new depreciation convention. When you update the depreciation convention for assets, you delete all depreciation transactions that exist for those assets. You also delete all transactions for depreciation adjustments, transactions for bonus depreciation, and transactions for extraordinary depreciation for those assets. To update the depreciation convention for assets that have already been disposed of, you must first delete the existing disposal transactions. You must also delete all transactions that were generated because of the disposal process. After you update the depreciation convention for assets, you can process depreciation and extraordinary depreciation for each asset. You can also make manual depreciation adjustments, if any adjustments are required.



