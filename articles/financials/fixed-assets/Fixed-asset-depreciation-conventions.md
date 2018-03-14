---
# required metadata

title: Fixed asset depreciation conventions
description: This article gives an overview of depreciation conventions.
author: saraschi2
manager: AnnBe
ms.date: 03/14/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: AssetDepreciationProfile
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 13891
ms.assetid: 36d1112d-921c-4fff-abe0-0ff2429848d3
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Fixed asset depreciation conventions

[!include[banner](../includes/banner.md)]

Depreciation conventions are used to determine when and how depreciation will be calculated for the year the fixed asset is acquired as well as the year the fixed asset will be disposed. Depreciation convention values can be assigned to the setup for a fixed asset group book, which will be used as a default when creating fixed asset books. It can also be set individually on a fixed asset book.

| **Depreciation convention** | **Definition**                                         |  
|-----------------------------|---------------------------------------------------------|
| None                        | 	Assets will begin depreciating on the **Placed in Service** Date.         |
| Half year                   | 	If this convention applies, you deduct a half-year of depreciation for the first year and the last year that you depreciate the property. You deduct a full year of depreciation for any other year during the recovery period.   |
| Full month                  |	 Assets with a **Placed in Service** Date anytime during the month will begin depreciating on the first day of the month. Assets retired anytime during the month are considered retired for depreciation purposes on the last day of the month previous to the retirement.         |
| Mid quarter                 |	Figure your depreciation deduction for the year you place the property in service by multiplying the depreciation for a full year by the percentage listed below for the quarter the property is placed in service. <br>**Quarter**   **Percentage**<br>          First        87.5%<br>             Second    62.5%<br>            Third      37.5%<br>                      Fourth        12.5%<br> One-half quarter’s depreciation is taken the quarter of disposal (or the fully depreciated quarter).|
| Mid month (1st of month)    | 	Assets that have a **Placed in Service** Date in the first half of the month (day 1-15) will begin depreciating on the first day of the month of the **Placed in Service** Date. Assets that have a **Placed in Service** Date in the second half of the month (day 16 – end of month) will being depreciating on the first day of the next month after the **Placed in Service** Date. Assets that are retired in the first half of the month (day 1-15) are considered retired for depreciation purposes on the last day of the previous month. Assets that are retired in the second half of the month (day 16 – end of month) are considered retired for depreciation purposes on the last day of the month of retirement. |   
| Mid month (15th of month)   | 	Figure your depreciation deduction for the year you place the property in service by multiplying the depreciation for a full year by a fraction. The numerator (top number) of the fraction is the number of full months in the year that the property is in service plus ½ or (0.5). The denominator (bottom number) is 12. If you dispose of the property before the end of your recovery period, figure your depreciation deduction for the year of disposition the same way.   |
| Half year (start of year)   | 	Assets that have a **Placed in Service** date in the first half of the year will begin depreciating on the first day of the year (full year). Assets that have a **Placed in Service** date in the second half of the year will begin depreciating on the midpoint of the year.    |
| Half year (next year)       | 	Assets that have a **Placed in Service** Date in the first half of the year will begin depreciating on the first day of the year (full year). Assets that have a **Placed in Service** Date in the second half of the year will begin depreciating on the first day of the next year. Assets that are retired in the first half of the year are considered retired for depreciation purposes on the last day of the previous year. Any depreciation posted in the current year must be reversed or adjusted out. Assets that are retired in the second half of the year are considered retired for depreciation purposes on the last day of the year of retirement.   |


