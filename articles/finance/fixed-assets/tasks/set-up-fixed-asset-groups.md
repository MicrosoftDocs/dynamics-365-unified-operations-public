--- 
# required metadata 
 
title: Set up fixed asset groups
description: This article explains how to create a new fixed asset group. 
author: moaamer
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetGroup, AssetGroupBookSetup   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up fixed asset groups

[!include [banner](../../includes/banner.md)]

This article explains how to create a new fixed asset group. It uses the Accountant role and demo data for the USMF legal entity.

1. Go to **Fixed assets > Setup > Fixed asset groups**.
2. Select **New**.
3. In the **Fixed asset group** field, type a value.
4. In the **Name** field, type a value. Autonumber fixed assets and Number sequence code on the **Fixed asset** group will override the settings on the **Fixed assets parameters**. You can change it here if the assets in this fixed asset group will have different numbering from other groups.  
5. Select **Books**.
6. In the **Book** field, enter or select a value. The **Calculate depreciation** field is set to **Yes**, so the asset book will be included in depreciation proposals. If **Calculate depreciation** is set to **No**, the asset will not be automatically depreciated.  
7. Set the Service life of the asset, in years. Note that the **Depreciation periods** field value is calculated after setting the Service life.  
8. In the **Depreciation convention** field, select an option.
9. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
