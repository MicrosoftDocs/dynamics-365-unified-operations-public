---
title: Create lump sum depreciation assets using equally divided method
description: Learn how to create lump sum depreciation assets using the equally divided method for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 04/18/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetBook, AssetDepreciationProfile
ms.custom: 
  - bap-template
---

# Create lump sum depreciation assets using equally divided method

[!include [banner](../../includes/banner.md)]

This article explains how to create lump sum depreciation assets using the equally divided method for Japan in Microsoft Dynamics 365 Finance.

In Japan, the following three types of fixed assets are depreciated with equal amounts in each year of service life.
- Lump sum assets
- Deferred assets
- Low-value assets


The following procedures use the JPMF demo company data.

Before you complete the procedures, you must first select the **Fixed Asset** configuration key.

## Create a lump sum fixed asset

To create a lump sum fixed asset, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select **New**.
1. In the **Fixed asset group** field, enter a value.
1. In the **Name** field, enter a value.
    * Confirm that the **Type** is defaulted from the **Fixed asset** group.   
    * Set the **Type** to **Deferred for Deferred asset**.  
    * Confirm that the **Asset classification** is set to **Lump sum**. 
    * Set **Asset classification** to **Low-value** for low-value assets.  
5. Select **Save**.
6. Select **Books**.
7. Expand the **Depreciation** section and confirm that the method is equally divided.  

## Confirm the depreciation profile

To confirm the depreciation profile, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Setup \> Depreciation profiles**.
2. Use the Quick Filter to filter on the **Depreciation profile** field with a value of "LUMPSUM".
    1. Confirm that the method is equally divided.  
    1. Confirm that the number of years to equally divide depreciation is "3". The value varies depending on the type of fixed asset is lump sum, deferred asset, or low-value asset.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
