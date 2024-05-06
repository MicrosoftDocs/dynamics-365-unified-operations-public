--- 
title: Set up fixed asset groups
description: Learn how to create a new fixed asset group, including a step-by-step process for creating a new fixed asset group using the Accountant role.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 03/28/2023
ms.custom:
ms.reviewer: twheeloc   
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: AssetGroup, AssetGroupBookSetup
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
