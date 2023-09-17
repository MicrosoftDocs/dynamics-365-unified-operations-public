---
# required metadata

title: 200 percent reducing balance depreciation
description: This article presents an overview of the 200 percent reducing balance method of depreciation.
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
ms.assetid: 69b4e010-7683-4dc2-8a06-6d572f37e903
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# 200 percent reducing balance depreciation

[!include [banner](../includes/banner.md)]

This article presents an overview of the 200 percent reducing balance method of depreciation.

When you set up a fixed asset depreciation profile and select **200% reducing balance** in the **Method** field on the **Depreciation profiles** page, fixed assets that are assigned the depreciation profile are depreciated by the same percentage in each depreciation period. The percentage is calculated based on the service life of the asset. For example, if an asset has a service life of five years, the percentage is calculated as 40 percent (200% ÷ 5). 

This method is also known as double declining balance.

To set up 200% reducing balance depreciation, you must also select options in the **Depreciation year** field and the **Period frequency** field on the **Depreciation profiles** page. The options that are available in the **Period frequency** field vary, depending on the value that you select in the **Depreciation year** field.

## Select a depreciation year
You can select either **Calendar** or **Fiscal** in the **Depreciation year** field on the **Depreciation profiles** page. The default value is **Calendar**. 

Your selection determines the options that are available in the **Period frequency** field. This field defines the depreciation accrual posting dates and amounts throughout the calendar year.

### Calendar

You can keep the default value in the **Depreciation year** field, **Calendar**. 

The **Calendar** option updates the depreciation base on January 1 of each year. Typically, the depreciation is the net book value minus the scrap value. In the examples later in this article, the depreciation base is the numerator in the first expression in the calculations column. 

If you select **Calendar** as the depreciation year, the following options are available in the **Period frequency** field:

-   **Yearly** posts an amount on December 31.
-   **Monthly** posts a monthly amount at the end of each calendar month.
-   **Quarterly** posts a quarterly amount at the end of each calendar quarter (March 31, June 30, September 30, and December 31).
-   **Half-Yearly** posts a half-yearly amount at the calendar half year (June 30 and December 31).
-   **Daily** posts the depreciation amount for the daily depreciation method by using one transaction for each day.

### Fiscal

If you select **Fiscal** in the **Depreciation** year field, 200% reducing balance depreciation is calculated based on the fiscal year for the fiscal calendar that is specified for the book, or for the fiscal calendar that is selected on the **Ledger** page. Fiscal calendars are set up on the **Fiscal calendars** page. 

For example, for the fiscal year July 1 through June 30, the depreciation calculation starts on July 1. The fiscal year can be longer or shorter than 12 months. The depreciation is adjusted for each period. The length of the next fiscal year is determined by the setup of periods on the **Fiscal calendars** page. 

When **Fiscal** is selected as the depreciation year, the following options are available in the **Period frequency** field:

-   **Yearly** posts the total amount of the depreciation that is calculated for the fiscal year as one amount, on the last day of the fiscal year.
-   **Fiscal period** posts the total amount of the depreciation that is calculated for the fiscal year. This amount is accrued into the fiscal periods that are defined on the **Fiscal calendars** page.

## Example of 200% reducing balance depreciation

| &nbsp;                         | &nbsp; |
|--------------------------------|--------|
| Acquisition cost               | 11,000 |
| Salvage value                  | 1, 000 |
| Depreciation base              | 10,000 |
| Service life years             | 5      |
| Yearly depreciation percentage | 40%    |

The 200% reducing balance method divides 200 percent by the service life years. That percentage will be multiplied by the net book value of the asset to determine the depreciation amount for the year.

| Period | Calculation of the yearly depreciation amount | Book value             | Net book value at the end of the year |
|--------|-----------------------------------------------|------------------------|---------------------------------------|
| Year 1 | (11,000 – 1,000) × 40% = 4,000                | 11,000 – 4,000 = 7,000 | 11,000 – 1,000 – 4,000 = 6,000        |
| Year 2 | 6,000 × 40% = 2,400                           | 7,000 – 2,400 = 4,600  | 6,000 – 2,400 = 3,600                 |
| Year 3 | 3,600 × 40% = 1,440                           | 4,600 – 1,440 = 3,160  | 3,600 – 1,440 = 2,160                 |

> [!NOTE] 
> Typically, when the amount that is calculated by using the 200% reducing balance depreciation method becomes less than the amount that would be calculated by using the straight line method, there is a conversion to the straight line method for the remaining life.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
