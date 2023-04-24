---
title: Change the depreciation method during the asset life for book
description: In Japan, you can change the depreciation method during the service life of a fixed asset.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - AssetBookTable, AssetGroupBookSetup, AssetDepProfileChangeApply_JP
  - AssetUndepreciatedBalancedSchedule_JP
---
# Change the depreciation method during the asset life for book

[!include [banner](../../includes/banner.md)]

In Japan, you can change the depreciation method during the service life of a fixed asset.



This procedure walks you through changing a depreciation profile for the fixed assets under a fixed asset group and book.



In order to complete this procedure, the Fixed Assets configuration key must be selected. Also, the Undepreciated balance schedule or Years passed schedule has to be configure before you can complete this procedure.

This procedure was created using the demo data company JPMF.


## Change a depreciation profile
1. Go to Fixed assets > Setup > Books.
2. Use the Quick Filter to find records. For example, filter on the Book field with a value of '250NDB_CUR'.
3. Click Fixed asset groups.
4. Use the Quick Filter to find records. For example, filter on the Fixed asset group field with a value of 'STRU-A'.
5. Click Change depreciation profile.
6. In the To depreciation profile field, type a value.
7. In the Start date field, enter a date.
    * The date has to be the start date of a fiscal year in the current fiscal calendar.  
8. Select Yes in the Update service life field.
    * You can add an idle period if you need to  
9. Click Apply.
10. Click Yes.

## View the years passed schedule
1. Go to Fixed assets > Setup > Depreciation rate schedules > Years passed schedules.
    * The corresponding data has to exist for the depreciation profile update.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
