---
title: Fixed asset depreciation conventions
description: Learn about depreciation conventions for fixed assets, including a table that defines various depreciation conventions.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 05/27/2026
ms.update-cycle: 1095-days
ms.custom: evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AssetDepreciationProfile
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 36d1112d-921c-4fff-abe0-0ff2429848d3
---

# Fixed asset depreciation conventions

[!include [banner](../includes/banner.md)]

This article describes depreciation conventions for fixed assets. Use depreciation conventions to determine when and how to calculate depreciation for both the year when you acquire the fixed asset and the year when you dispose of the fixed asset.

Assign depreciation conventions to the setup for a fixed asset group book. To view or assign the depreciation convention, in the setup area of fixed assets, select **Fixed asset** groups. Select the **Books** button. The assigned depreciation conventions are the default values when you create fixed asset books. You can also set depreciation conventions on an individual fixed asset book. To do this, select **Books** in the setup area of fixed assets, and then select the **Fixed assets groups** button.

| Depreciation convention   | Description |
|---------------------------|-------------|
| None                      | Assets start to depreciate on the <strong>Placed in service</strong> date. |
| Half year                 | Deduct a half-year of depreciation for both the first year and the last year that you depreciate the property. Deduct a full year of depreciation for every other year during the recovery period. |
| Full month                | Assets that have a <strong>Placed in service</strong> date that occurs at any time during the month start to depreciate on the first day of that month. For depreciation purposes, assets are considered retired on the last day of the previous month. The specific day of the month when they were retired isn't considered. |
| Mid quarter               | To calculate your depreciation deduction for the year when you put the property into service, multiply the depreciation for a full year by the percentage for the quarter when the property is put into service, as shown in the following table.<br><br>**Quarter** \| **Percentage**<br>First \| 87.5<br>Second \| 62.5<br>Third \| 37.5<br>Fourth \| 12.5<br><br>A half-quarter of depreciation is taken in the quarter when the asset was disposed of (or the quarter when it was fully depreciated). |
| Mid month (first of month)  | Assets that have a <strong>Placed in service</strong> date in the first half of the month (days 1 through 15) start to depreciate on the first day of the month of the <strong>Placed in service</strong> date. Assets that have a <strong>Placed in service</strong> date in the second half of the month (day 16 through the end of the month) start to depreciate on the first day of the month after the <strong>Placed in service</strong> date. Assets that are retired in the first half of the month (days 1 through 15) are considered retired on the last day of the previous month for depreciation purposes. Assets that are retired in the second half of the month (day 16 through the end of the month) are considered retired on the last day of the month of retirement for depreciation purposes. |
| Mid month (15th of month) | To calculate your depreciation deduction for the year when you put the property in service, multiply the depreciation for a full year by a fraction. The numerator (top number) of this fraction is the number of full months in the year that the property is in service, plus 1/2 or (0.5). The denominator (bottom number) is 12. If you dispose of the property before the end of your recovery period, use the same method to calculate your depreciation deduction for the year of disposition. |
| Half year (start of year) | Assets that have a <strong>Placed in service</strong> date in the first half of the year start to depreciate on the first day of the year (full year). Assets that have a <strong>Placed in service</strong> date in the second half of the year start to depreciate at the midpoint of the year. |
| Half year (next year)     | Assets that have a <strong>Placed in service</strong> date in the first half of the year start to depreciate on the first day of the year (full year). Assets that have a <strong>Placed in service</strong> date in the second half of the year start to depreciate on the first day of the next year. Assets that are retired in the first half of the year are considered retired on the last day of the previous year for depreciation purposes. Any depreciation that is posted in the current year must be reversed or adjusted out. Assets that are retired in the second half of the year are considered retired on the last day of the year of retirement for depreciation purposes. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
