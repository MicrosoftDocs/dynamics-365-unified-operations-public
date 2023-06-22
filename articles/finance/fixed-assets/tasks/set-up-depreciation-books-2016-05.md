--- 
# required metadata 
 
title: Set up depreciation books
description: This procedure walks through the process of creating a new depreciation book and associate it with a fixed asset group. 
author: moaamer
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetDepBookTable, AssetGroupDepBookSetup   
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
# Set up depreciation books 

[!include [banner](../../includes/banner.md)]

This procedure walks through the process of creating a new depreciation book and associate it with a fixed asset group. 

## Create a depreciation book
1. Go to **Fixed assets > Setup > Depreciation books**.
2. Click **New**.
3. In the **Depreciation book** field, type a value.
4. In the **Description** field, type a value.
5. Select or clear the **Calculate depreciation** checkbox.
6. In the **Depreciation profile** field, click the drop-down button to open the lookup.
7. In the list, find and select the desired depreciation profile.
8. In the list, click the link in the selected row.
9. In the **Alternative depreciation profile** field, click the drop-down button to open the lookup.
10. In the list, select the desired depreciation profile.
11. In the list, click the link in the selected row.
    * The **Extraordinary depreciation profile** is used for additional depreciation of an asset in unusual circumstances. For example, you might use this to record depreciation that results from a natural disaster.  
12. Select or clear the **Create depreciation adjustments with basis adjustments** checkbox.
13. In the **Calendar** field, click the drop-down button to open the lookup.
14. In the list, click the link in the selected row.

## Associate the depreciation book with a fixed asset group
1. Click **Fixed asset groups**.
2. In the **Fixed asset group** field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the **Depreciation convention** field, select an option.
6. In the **Service life** field, enter a number.
    * Note the **Depreciation periods** field value is calculated after setting the Service life.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
