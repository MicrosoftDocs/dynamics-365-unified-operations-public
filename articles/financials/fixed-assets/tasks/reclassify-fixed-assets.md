--- 
# required metadata 
 
title: Reclassify fixed assets
description: To reclassify a fixed asset, you must transfer it to a new fixed asset group or assign a new fixed asset number to it in the same group. 
author: saraschi2
manager: AnnBe 
ms.date: 10/30/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Reclassify fixed assets

[!include[task guide banner](../../includes/task-guide-banner.md)]

To reclassify a fixed asset, you must transfer it to a new fixed asset group or assign a new fixed asset number to it in the same group. 

When a fixed asset is reclassified:

• All value models for the existing fixed asset are created for the new fixed asset. Any information that was set up for the original fixed asset is copied to the new fixed asset. The status of the value models for the original fixed asset is Closed. 

• The new value models of the new fixed asset contain the date of the reclassification in the Acquisition date field. The date in the Depreciation run date field is copied from the original asset information. If the depreciation has already started, the Date when depreciation was last run field displays the date of the reclassification. 

• The existing fixed asset transactions for the original fixed asset are canceled and regenerated for the new fixed asset.

1. Go to Fixed assets > Periodic tasks > Reclassification.
2. In the Fixed asset group field, select the group to reclassify.
3. In the Fixed asset number field, select the fixed asset to reclassify.
4. In the New fixed asset group field, select a group to transfer the fixed asset to.
    * If the new fixed asset group is attached to a number sequence, the New fixed asset number field is updated with the number from the new fixed asset group number sequence. Otherwise, the New fixed asset number field is updated with the number from the number sequence that is set up in the Fixed asset parameters page. If a number sequence is not set up in the Fixed asset parameters page, enter a number in the New fixed asset number field.  
5. In the Reclassification date field, enter a date.
6. In the Voucher series field, enter or select a value.
7. Click OK.

