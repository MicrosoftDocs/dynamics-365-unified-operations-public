--- 
# required metadata 
 
title: Enter an addition to a fixed asset
description: This procedure shows how to add an addition to an existing fixed asset. 
author: moaamer
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetTable, AssetAddition   
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
# Enter an addition to a fixed asset

[!include [banner](../../includes/banner.md)]

This procedure shows how to add an addition to an existing fixed asset. The purpose of Fixed asset additions is to track item additions, maintenance, or improvements for an asset, and is informational only. Any changes to the fixed asset value or service life must be made separately.   

The procedure uses the Accountant role and demo data for the USMF legal entity.

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
2. In the list, find and select the fixed asset for the addition.
3. In the list, click the link in the selected row.
4. On the Action Pane, click **Fixed asset**.
5. Click **Fixed asset additions**.
6. Click **New**.
7. In the **Name** field, type a value.
8. In the **Acquisition date** field, set the date of the addition purchase or service.
9. In the **Unit cost** field, enter the cost of the item, maintenance, or other improvement for the asset.
10. In the **Quantity** field, enter a number. The total cost will have no impact on the value of the fixed asset and is for tracking and informational purposes only. If the cost will be capitalized, then a write-up adjustment transaction must be posted separately.  
11. Click the **General** tab.

    * Set **Increases service life** to **Yes** if the addition increases the service life of the asset.  
    * This field is informational only. To increase the service life, modify the **Service life** on the **Value models** and/or **Depreciation books** for the asset.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
