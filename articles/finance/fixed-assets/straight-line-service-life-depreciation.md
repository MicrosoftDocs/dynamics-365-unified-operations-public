---
# required metadata

title: Straight line service life depreciation
description: This topic gives an overview of the Straight line service life method of depreciation.
author: moaamer
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetDepreciationProfile
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 3341
ms.assetid: ae5ceaeb-aeb7-45cd-b835-23cf9c5cf95a
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Straight line service life depreciation

[!include [banner](../includes/banner.md)]

This topic gives an overview of the Straight line service life method of depreciation.

When you set up a fixed asset depreciation profile and select Straight line service life in the Method field in the Depreciation profiles page, the assets that have this depreciation profile assigned to them are depreciated based on the total service life of the asset. This generally is the same depreciation amount in each depreciation period. 

The difference in the depreciation amount that is calculated between straight line service life remaining and straight line service life is when there is an adjustment posted to the asset. 

To set up straight line service life depreciation, you must also select options in the Depreciation year and Period frequency fields in the Depreciation profiles page.

## Select a depreciation year
You can select either Calendar or Fiscal in the Depreciation year field in the Depreciation profiles page. The selection defines the options that are available in the Period frequency field. The default option is Calendar.

### Calendar

If you select Calendar, a year of January 1 to December 31 is assumed, even if you have defined the fiscal calendar differently. 

The Calendar option updates the depreciation base, which is typically the net book value minus the salvage value, on January 1 of each year. In the examples later in this topic, the depreciation base is the numerator in the first expression in the calculations column. 

If you select Calendar, the following options are available in the Period frequency field, which defines the depreciation accrual posting dates and amounts throughout the calendar year:
- Yearly posts an amount on December 31.
- Monthly posts a monthly amount at the end of each calendar month.
- Quarterly posts a quarterly amount at the end of each calendar quarter (March 31, June 30, September 30, and December 31).
- Half-Yearly posts a half-yearly amount at the end of each calendar half year (June 30 and December 31).
- Daily posts the depreciation amount for the daily depreciation method using one transaction for each day.

For example, if you select Yearly, the yearly depreciation is posted only one time, on December 31 of each year. If you select Monthly, the monthly depreciation is posted each month as 1/12 of the yearly depreciation amount.

### Fiscal

If you select Fiscal in the Depreciation year field, the straight line service life depreciation is used. It is calculated based on the fiscal year, which is defined by the fiscal calendar that is specified for the book, or by the fiscal calendar that is selected in the Ledger page. Fiscal calendars are set up in the Fiscal calendars page.

For example, for fiscal year July 1 through June 30, the depreciation calculation starts on July 1. The fiscal year can be longer or shorter than 12 months. The depreciation automatically is adjusted for each fiscal period. The length of the next fiscal year is based on the fiscal periods that you set up when you create a new fiscal year in the Fiscal calendars form. 

If you select Fiscal, the following options are available in the Period frequency field:
- Yearly posts the total amount of the depreciation that is calculated for the fiscal year as one amount on the last day of the fiscal year.
- Fiscal period calculates the total amount of the depreciation for the fiscal year, which is accrued into the periods that are defined in the Fiscal calendars form for the fiscal calendar.

## Example: Straight line depreciation of an unchanged fixed asset
Suppose that a fixed asset has the following characteristics.

| Characteristic      | Value  |
|:---------------------|--------:|
| Acquisition cost    | 11,000 |
| Salvage value       | 1,000  |
| Depreciation base   | 10,000 |
| Service life years  | 5      |
| Yearly depreciation | 2,000  |

You get the same depreciation amount each year. (Acquisition cost - Salvage value) / Service life years

| Period | Calculation of yearly depreciation amount | Net book value at the end of the year |
|:--------:|:-------------------------------------------|---------------------------------------:|
| Year 1 | (11,000 - 1,000) / 5 = 2,000              | 9,000                                 |
| Year 2 | (11,000 - 1,000) / 5 = 2,000              | 7,000                                 |
| Year 3 | (11,000 - 1,000) / 5 = 2,000              | 5,000                                 |
| Year 4 | (11,000 - 1,000) / 5 = 2,000              | 3,000                                 |
| Year 5 | (11,000 - 1,000) / 5 = 2,000              | 1,000                                 |

## Example: Straight line depreciation of a modified fixed asset

Suppose that you add an acquisition adjustment of 4,000 in year 2 to the same fixed asset. 

The service life of the acquisition adjustment is the same as that of the fixed asset and starts at the time of its acquisition. A net book value remains at the end of year 5, corresponding to the net book value of the acquisition adjustment. The depreciation by period is calculated as shown in the following table.

| Period | Calculation of yearly depreciation amount | Net book value at the end of the year |
|:--------:|:-------------------------------------------|---------------------------------------:|
| Year 1 | 10,000 / 5 = 2,000                        | 11,000 - 2,000 = 9,000                |
| Year 2 | 4,000 (acquisition adjustment)            | 9,000 + 4,000 =13,000                 |
| Year 2 | 14,000 / 5 = 2,800                        | 13,000 - 2,800 = 10,200               |
| Year 3 | 14,000 / 5 = 2,800                        | 10,200 - 2,800 = 7,400                |
| Year 4 | 14,000 / 5 = 2,800                        | 7,400 - 2,800 = 4,600                 |
| Year 5 | 14,000 / 5 = 2,800                        | 4,600 - 2,800 = 1,800                 |
| Year 6 | Remaining 800\*                           | 1,800 – 800 = 1,000                   |

\*Because the remaining amount is less than the depreciation amount, only the remaining amount minus the salvage value is taken.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
