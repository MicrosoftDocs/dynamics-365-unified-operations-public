--- 
title: DE-00002 Depreciation adjustments for additional acquisitions in the second year
description: Learn how to set up the calculation of depreciation for additional acquisitions, including a step-by-step process on setting up depreciation profiles. 
author: mrolecki
ms.author: mrolecki
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: johnmichalak   
audience: Application User 
ms.search.region: Germany
ms.search.validFrom: 2016-06-30
ms.search.form: AssetParameters, AssetDepreciationProfile
ms.dyn365.ops.version: Version 7.0.0 
---

# DE-00002 Depreciation adjustments for additional acquisitions in the second year

[!include [banner](../../includes/banner.md)]

This guide demonstrates how to set up the calculation of depreciation for additional acquisitions. The demo data company used to create this procedure is DEMF.


## Allow multiple acquisitions
1. Go to Fixed assets > Setup > Fixed assets parameters.
2. Check the Allow multiple acquisitions checkbox.
3. Click Save.

## Set up depreciation profile
1. Go to Fixed assets > Setup > Depreciation profiles.
2. Click New.
3. In the Depreciation profile field, type a value.
4. In the Name field, type a value.
5. In the Method field, select 'Straight line life remaining'.
6. In the Period frequency field, select 'Monthly'.
7. Check the Full year depreciation on additional acquisitions checkbox.
8. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]