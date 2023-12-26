---
title: Allocate carrying amount of shared asset and goodwill to cash generating units
description: This procedure walks you through allocating the carrying amount of shared asset and goodwill to each of the cash generating units.
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
ms.search.form: AssetImpairmentSharedAssetAlloc_JP, AssetImpairmentPopulateAllocation_JP
---
# Allocate carrying amount of shared asset and goodwill to cash generating units

[!include [banner](../../includes/banner.md)]

This procedure walks you through allocating the carrying amount of shared asset and goodwill to each of the cash generating units. The allocation must be done before activating the CGU group.



In Japan, impairment accounting for shared assets and goodwill is permitted for the following two methods: 

Method 1: On a bigger unit than cash generating unit (CGU). 

Method 2: Allocate carrying amount of shared asset/goodwill to CGUs. 

This procedure applies to only the CGU groups that use method 2. 



Before you can complete this procedure, you must select the Fixed Asset configuration key.



This procedure was completed using the demo data company JPMF.



1. Go to Fixed assets > Setup > Impairment > Allocation of net book value of shared assets and  goodwill.
    * The allocation of goodwill and shared assets is applicable only to the CGU groups with method 2, and the allocation has to be done before activating the CGU group.  
2. In the Proportion field, enter a number.
3. Select the next cash generating unit
4. In the Proportion field, enter a number.
5. Click Populate allocation.
    * You can also choose to repeat the previous steps to configure the proportions individually.  
6. In the list, mark or unmark all rows.
7. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
