---
title: Create lump-sum depreciation assets using equally divided method
description: In Japan, 3 types of fixed assets are depreciated with equal amount in each year of its service life.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: AssetTable, AssetBook, AssetDepreciationProfile
---
# Create lump-sum depreciation assets using equally divided method

[!include [banner](../../includes/banner.md)]

In Japan, 3 types of fixed assets are depreciated with equal amount in each year of its service life. The 3 types are: lump sum assets, deferred assets and low-value assets. 



Use this task to learn how to create a lump sum fixed asset.



In order to complete this task, the Fixed Assets configuration key must be selected.



This task uses the JPMF demo company data.


## Create a lumpsum fixed asset
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. Click New.
3. In the Fixed asset group field, type a value.
4. In the Name field, type a value.
    * Confirm that the Type is defaulted from the Fixed asset group.   
    * Set the Type to Deferred for Deferred asset.  
    * Confirm that the Asset classification is set to Lump sum  
    * Set Asset classification to Low-value for low-value assets.  
5. Click Save.
6. Click Books.
7. Expand the Depreciation section.
    * Confirm the Method is Equally divided  

## Confirm the depreciation profile
1. Go to Fixed assets > Setup > Depreciation profiles.
2. Use the Quick Filter to filter on the Depreciation profile field with a value of 'LUMPSUM'.
    * Confirm the Method is Equally divided  
    * Confirm that the Number of years to equally divide depreciation is 3  
    * The value varies depending on the type of fixed asset is lump-sum, deferred asset or low-value asset.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
