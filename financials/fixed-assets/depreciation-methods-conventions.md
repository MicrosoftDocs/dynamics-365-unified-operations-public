---
# required metadata

title: Depreciation methods and conventions | Microsoft Docs
description: This article provides an overview of the depreciation conventions and depreciation methods that are supported by Microsoft Dynamics AX.
author: twheeloc
manager: AnnBe
ms.date: 2015-09-10 21:04:03
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: AssetDepreciationProfile, AssetGroupBookSetup, AssetGroupDepBookSetup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 3441
ms.assetid: 4aefa217-479c-47fa-816f-081f5eab40d8
ms.region: Global
# ms.industry: 
ms.author: saraschi

---

# Depreciation methods and conventions

This article provides an overview of the depreciation conventions and depreciation methods that are supported by Microsoft Dynamics AX.

You can select various depreciation methods and conventions. The purpose of the methods is to allocate the depreciable value of the fixed asset into fiscal periods. The depreciable value of the fixed asset is the acquisition price, reduced by a scrap value, if any. If you are using depreciation conventions and you modify the last depreciation run date for an asset, which then causes some depreciations to be skipped, the depreciation for the last year might be more than or less than is expected. The depreciation is adjusted by the number of depreciation periods affected by the modification of the last depreciation run date. For example, if you are using the Half year depreciation convention over three years, depreciation ordinarily occurs over 3 1/2 years. If you change the last depreciation run date during the 3 1/2 years, the last year of depreciation moves out the number of periods affected. If you move the date by three months, the last year will have nine months’ worth of depreciation, when ordinarily there would be six months’ worth of depreciation. You can select from the following depreciation conventions.
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

[Fixed asset depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/fixed-asset-depreciation)

[Straight line service life depreciation](https://ax.help.dynamics.com/en/wiki/Straight-line-service-life-depreciation/)

[Reducing balance depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/reducing-balance-depreciation)

[Manual depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/manual-depreciation)

[Factor depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/factor-depreciation)

[Consumption depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/consumption-depreciation)

[Straight line life remaining depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/straight-line-life-remaining-depreciation)

[125 percent reducing balance depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/125-percent-reducing-balance-depreciation)

[150 percent reducing balance depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/150-percent-reducing-balance-depreciation)

[175 percent reducing balance depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/175-percent-reducing-balance-depreciation)

[200 percent reducing balance depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/200-percent-reducing-balance-depreciation)

