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

This topic describes the method that's used in Fixed assets to calculate depreciation after an has been split asset using the reduce balance method, the depreciation year is the fiscal year. For more information see [Reduce balance depreciation](reduce-balance-depreciation.md) and [Split a fixed asset](https://docs.microsoft.com/en-us/dynamics365/finance/fixed-assets/tasks/split-fixed-asset).

https://docs.microsoft.com/en-us/dynamics365/finance/fixed-assets/

When you split a fixed asset in a following fiscal period of the acquisition
period, the reduce balance depreciation will consider the asset net book value
of the prior year as well as the acquisition and depreciation adjustments
transactions of which generated from the split transaction.

Assumes the asset acquired in a fiscal year and split in the second fiscal year.
And amount to depreciate for the original asset after split is considering the
asset NBV before splitting as well as the acquisition and depreciation
adjustment of which posted during split transaction.

For example, the fiscal period is from June 30th to July 1st, the reducing
balance percentage is 18% and there is an asset is acquired in June 2019 with
acquisition price \$10,000 the depreciation of the first fiscal year equals
\$18,000 and monthly depreciation equals \$150, then depreciated till Nov 2019
which equals \$738.75. Split 80% of this asset in Nov 2019 to another fixed
asset.

[![Reduce balance depreciation after split](./media/Reduce_balance_depreciation_after_split.png)](./media/Reduce_balance_depreciation_after_split.png)

The amount to depreciate for the original asset equals \$1,822.25, NBV before
posting split transaction 9,111.25 + the generated acquisition adjustment during
posting split transaction \$(-8,000) + the generated depreciation adjustment
during split transaction \$711. Hence the second-year depreciation of the second
year is (1,822.25\*18%)/12 = 27.33.

The amount to depreciate for the new fixed asset in the first year equals
(8,000\*18%)/12 = \$120.
