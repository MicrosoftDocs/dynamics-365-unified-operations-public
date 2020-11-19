---
# required metadata

title: Reduce balance depreciation after split
description: This topic describes the method that is used in fixed assets to calculate depreciation after splitting an asset using reduce balance method.
author: moaamer
manager: Ann Beebe
ms.date: 11/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-11-17
ms.dyn365.ops.version: 10.0.14
---

# Reduce balance depreciation after split

This topic describes the method that's used in Fixed assets to calculate depreciation after an asset has been split to another asset using the reduce balance method, the configured depreciation year in asset book is the fiscal year. For more information, see [Reduce balance depreciation](reduce-balance-depreciation.md) and [Split a fixed asset](tasks/split-fixed-asset.md). 

When you split a fixed asset in fiscal period that's later than the period that the asset was acquired in, the reduced balance depreciation will account for the asset net book value (NBV) of the prior year, as well as the acquisition and depreciation adjustment transactions that were generated from the transaction that split the asset. 

This description assumes the asset was acquired in one fiscal year and split in a later fiscal year. The amount to depreciate for the original asset after the split takes into account the asset's NBV before it was split, as well as the acquisition and depreciation adjustment transaction that was posted for the split.

For example, assume that the following conditions are in effect. 

 - The fiscal period is from June 30 to July 1
 - The reducing balance percentage is 18% and there is an asset is acquired in June 2019 at an acquisition price of $10,000 
 - The depreciation of the first fiscal year equals $18,000 and monthly depreciation equals $150, and then depreciated until November 2019, which equals $738.75
 - 80 percent of the asset is split to another fixed asset in November 2019

[![Reduce balance depreciation after split](./media/reduce-balance-depreciation-after-split.png)](./media/reduce-balance-depreciation-after-split.png)

The amount to depreciate for the original asset equals $1,822.25, NBV before posting split transaction 9,111.25 + the generated acquisition adjustment during posting split transaction $(-8,000) plus the generated depreciation adjustment during split transaction of $711. Therefore, the second-year depreciation of the second year is (1,822.25\*18%)/12 = 27.33.

The amount to depreciate for the new fixed asset in the first year equals (8,000\*18%)/12 = $120.
