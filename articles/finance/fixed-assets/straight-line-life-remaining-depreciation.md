---
# required metadata

title: Straight line life remaining depreciation
description: This article gives an overview of the Straight line life remaining method of depreciation.
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
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 0fa2f71a-596c-414c-a6e6-8f7405a0bf81
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Straight line life remaining depreciation

[!include [banner](../includes/banner.md)]

This article gives an overview of the Straight line life remaining method of depreciation.

When you set up a fixed asset depreciation profile and select **Straight line life remaining** in the **Method** field on the **Depreciation profiles** page, the depreciation of fixed assets that are assigned to the depreciation profile is based on the remaining service life of the asset. The depreciation amount is generally the same in each depreciation period. To set up straight line life remaining depreciation, you also must select options in the **Depreciation year** field and the **Period frequency** field on the **Depreciation profiles** page. The options that are available in the **Period frequency** field vary, depending on the value that is selected in the **Depreciation year** field.

## Select a depreciation year
You can select either **Calendar** or **Fiscal** in the **Depreciation year** field on the **Depreciation profiles** page. The default value is **Calendar**. Your selection determines the options that are available in the **Period frequency** field. This field defines the depreciation accrual posting dates and amounts throughout the calendar year.

### Calendar

If you select **Calendar** in the ***Depreciation year*** field, a year of January 1 through December 31 is assumed, even if you've defined the fiscal calendar differently. The **Calendar** option updates the depreciation base on January 1 of each year. Typically, the depreciation base is the net book value minus the salvage value. In the example later in this article, the depreciation base is the numerator in the first expression in the calculations column. If you select **Calendar** as the depreciation year, the following options are available in the **Period frequency** field:

- **Yearly** posts an amount on December 31.
- **Monthly** posts a monthly amount at the end of each calendar month.
- **Quarterly** posts a quarterly amount at the end of each calendar quarter (March 31, June 30, September 30, and December 31).
- **Half-Yearly** posts a half-yearly amount at the end of each calendar half year (June 30 and December 31).
- **Daily** posts the depreciation amount for the daily depreciation method by using one transaction for each day.

For example, if you select **Yearly**, the yearly depreciation is posted only one time, on December 31 of each year. If you select **Monthly**, the monthly depreciation is posted each month, as one-twelfth of the yearly depreciation amount.

### Fiscal

If you select **Fiscal** in the **Depreciation year** field, straight line life remaining depreciation is used. Depreciation is calculated based on the fiscal years remaining. For example, for the fiscal year July 1, 2015, through June 30, 2016, the depreciation calculation starts on July 1. The fiscal year can be longer or shorter than 12 months. The depreciation is adjusted for each fiscal period. The length of the next fiscal year is determined by the fiscal periods that are set up on the **Fiscal calendars** page. If you select **Fiscal** as the depreciation year, the following options are available in the **Period frequency** field:

- **Yearly** posts the total amount of the depreciation that is calculated for the fiscal year as one amount, on the last day of the fiscal year.
- **Fiscal period** calculates the total amount of the depreciation for the fiscal year. This amount is then accrued into the fiscal periods that are defined on the **Fiscal calendars** page for the fiscal calendar that is specified for the book.

## Example of straight line depreciation of an unchanged fixed asset
A fixed asset has the following characteristics.

| Field               | Value  |
|:---------------------|--------:|
| Acquisition cost    | 11,000 |
| Salvage value       | 1,000  |
| Depreciation base   | 10,000 |
| Service life years  | 5      |
| Yearly depreciation | 2,000  |

The depreciation amount is the same every year: (Acquisition cost – Salvage value) ÷ Service life years

| Period | Calculation of the yearly depreciation amount | Net book value at the end of the year |
|:--------:|:-----------------------------------------------|---------------------------------------:|
| Year 1 | (11,000 – 1,000) ÷ 5 = 2,000                  | 9,000                                 |
| Year 2 | (9,000 – 1,000) ÷ 4 = 2,000                   | 7,000                                 |
| Year 3 | (7,000 – 1,000) ÷ 3 = 2,000                   | 5,000                                 |
| Year 4 | (5,000 – 1,000) ÷ 2 = 2,000                   | 3,000                                 |
| Year 5 | (3,000 – 1,000) ÷ 1 = 2,000                   | 1,000                                 |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
