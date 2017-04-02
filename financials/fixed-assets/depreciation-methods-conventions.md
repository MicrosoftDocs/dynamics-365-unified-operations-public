---
# required metadata

title: Depreciation methods and conventions
description: This article provides an overview of the depreciation conventions and depreciation methods that are supported by Microsoft Dynamics AX.
author: twheeloc
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetDepreciationProfile, AssetGroupBookSetup, AssetGroupDepBookSetup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 3441
ms.assetid: 1d8267b1-86a8-44bf-8814-f56b5d45a0ae
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Depreciation methods and conventions

This article provides an overview of the depreciation conventions and depreciation methods that are supported by Microsoft Dynamics AX.

You can select various depreciation methods and conventions. The purpose of the methods is to allocate the depreciable value of the fixed asset into fiscal periods. The depreciable value of the fixed asset is the acquisition price, reduced by a scrap value, if any. 

If you are using depreciation conventions and you modify the last depreciation run date for an asset, which then causes some depreciations to be skipped, the depreciation for the last year might be more than or less than is expected. The depreciation is adjusted by the number of depreciation periods affected by the modification of the last depreciation run date.

For example, if you are using the Half year depreciation convention over three years, depreciation ordinarily occurs over 3 1/2 years. If you change the last depreciation run date during the 3 1/2 years, the last year of depreciation moves out the number of periods affected. If you move the date by three months, the last year will have nine months’ worth of depreciation, when ordinarily there would be six months’ worth of depreciation.

You can select from the following depreciation conventions.


-   Half year
-   Full month
-   Mid quarter
-   Mid month (1st of month)
-   Mid month (15th of month)
-   Half year (start of year)
-   Half year (next year)

You can select from the following depreciation methods.
-   Straight line service life
-   Reducing balance
-   Manual
-   Factor
-   Consumption
-   Straight line life remaining
-   200% reducing balance
-   175% reducing balance
-   150% reducing balance
-   125% reducing balance

 



See also
--------

[Fixed asset depreciation](fixed-asset-depreciation.md)

[Straight line service life depreciation](Straight-line-service-life-depreciation.md)

[Reducing balance depreciation](reduce-balance-depreciation.md)

[Manual depreciation](manual-depreciation.md)

[Factor depreciation](factor-depreciation.md)

[Consumption depreciation](consumption-depreciation.md)

[Straight line life remaining depreciation](straight-line-life-remaining-depreciation.md)

[125 percent reducing balance depreciation](125-percent-reducing-balance-depreciation.md)

[150 percent reducing balance depreciation](150-percent-reducing-balance-depreciation.md)

[175 percent reducing balance depreciation](175-percent-reducing-balance-depreciation.md)

[200 percent reducing balance depreciation](200-percent-reducing-balance-depreciation.md)

