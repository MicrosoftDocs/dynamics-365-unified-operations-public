---
title: Depreciation methods and conventions
description: Learn about the depreciation conventions and depreciation methods that are supported by Microsoft Dynamics 365 Finance, including additional resources.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/05/2024
ms.custom: evergreen 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AssetDepreciationProfile, AssetGroupBookSetup, AssetGroupDepBookSetup
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 1d8267b1-86a8-44bf-8814-f56b5d45a0ae
---

# Depreciation methods and conventions

[!include [banner](../includes/banner.md)]

This article provides an overview of the supported depreciation conventions and depreciation methods.

You can select various depreciation methods and conventions. The purpose of the methods is to allocate the depreciable value of the fixed asset into fiscal periods. The depreciable value of the fixed asset is the acquisition price, reduced by a scrap value, if any. 

If you are using depreciation conventions and you modify the last depreciation run date for an asset, which then causes some depreciations to be skipped, the depreciation for the last year might be more than or less than is expected. The depreciation is adjusted by the number of depreciation periods affected by the modification of the last depreciation run date.

For example, if you are using the Half year depreciation convention over three years, depreciation ordinarily occurs over three-and-a-half years. If you change the last depreciation run date during the three-and-a-half years, the last year of depreciation moves out the number of periods affected. If you move the date by three months, the last year will have nine months’ worth of depreciation, when ordinarily there would be six months’ worth of depreciation.

You can select from the following depreciation conventions.


-   Half year
-   Full month
-   Mid quarter
-   Mid month (1st of month)
-   Mid month (15th of month)
-   Half year (start of year)
-   Half year (next year)

You can select from the following depreciation methods.
-   Straight-line service life
-   Reducing balance
-   Manual
-   Factor
-   Consumption
-   Straight-line life remaining
-   200% reducing balance
-   175% reducing balance
-   150% reducing balance
-   125% reducing balance





## Additional resources

[Fixed asset depreciation](fixed-asset-depreciation.md)

[Straight-line service life depreciation](Straight-line-service-life-depreciation.md)

[Reduce balance depreciation](reduce-balance-depreciation.md)

[Manual depreciation](manual-depreciation.md)

[Factor depreciation](factor-depreciation.md)

[Consumption depreciation](consumption-depreciation.md)

[Straight-line life remaining depreciation](straight-line-life-remaining-depreciation.md)

[125 percent reducing balance depreciation](125-percent-reducing-balance-depreciation.md)

[150 percent reducing balance depreciation](150-percent-reducing-balance-depreciation.md)

[175 percent reducing balance depreciation](175-percent-reducing-balance-depreciation.md)

[200 percent reducing balance depreciation](200-percent-reducing-balance-depreciation.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
