---
title: RB/SL depreciation
description: RB/SL is a depreciation method that is used in France. Depreciation amounts are calculated by using both the reducing balance depreciation method and the straight-line remaining depreciation method. The larger of the two calculated depreciation amounts is then used as the RB/SL reducing balance depreciation amount.
author: AdamTrukawka
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: France
ms.author: atrukawk
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.form: AssetRBSLFactorTable
---

# RB/SL depreciation

[!include [banner](../includes/banner.md)]

RB/SL is a depreciation method that is used in France. Depreciation amounts are calculated by using both the reducing balance depreciation method and the straight-line remaining depreciation method. The larger of the two calculated depreciation amounts is then used as the RB/SL reducing balance depreciation amount.

The RB/SL (France) depreciation method always uses the monthly depreciation period in the depreciation profile. When you create a fixed asset and assign a value model by using the RB/SL (France) depreciation method, the start date of the depreciation is always the first day of the month, and the end date is always the end of the fiscal year. The reducing balance depreciation amount is calculated by using the reducing balance percentage, which is calculated based on RB/SL factors. You set up the RB/SL factors according to the service life of the fixed asset on the **RB/SL factors** page. For example, you can set up the following factors.

| From date       | Years | Months | RB/SL factor | Comment                                                                                                                     |
|-----------------|-------|--------|--------------|-----------------------------------------------------------------------------------------------------------------------------|
| January 1, 2016 | 1     | 0      | 1.00         | For a fixed asset that has a service life that is equal to or more than one year, the RB/SL factor is 1.00.                 |
| January 1, 2016 | 3     | 0      | 1.25         | For a fixed asset that has a service life that is equal to or more than three years, the RB/SL factor is 1.25.              |
| January 1, 2016 | 5     | 0      | 1.75         | For a fixed asset that has service life that is equal to or more than five years, the RB/SL factor is 1.75.                 |
| January 1, 2016 | 6     | 8      | 2.25         | For a fixed asset that has service life that is equal to or more than six years and eight months, the RB/SL factor is 2.25. |

When you create a **Fixed asset group/value model** setup, you specify the number of years and the number of months in the service life of the fixed asset. By default, these values will be used for some fixed asset value models, and will be used to calculating the RB/SL factor for the fixed asset. For each fixed asset, the reducing balance percentage is calculated based on the service life of the asset and the appropriate RB/SL factor: Reducing balance % = RB/SL factor ÷ Service life × 100% Additionally, the reducing balance and straight line remaining depreciation amounts are calculated and compared, and the larger amount is used as the RB/SL depreciation amount. For example, a fixed asset that has an acquisition price of EUR 1,000.00 is put into service on February 10, 2016, and is depreciated over five years by using the RB/SL method. Here is the calculation for the reducing balance percentage: Reducing balance % = 1.75 ÷ 5 × 100% = 35% The following table shows the depreciation amounts and the book value for the asset for each year.

| Year      | Straight line remaining           | Reducing balance                    | RB/SL (the larger of the two amounts) | Book value         |
|-----------|-----------------------------------|-------------------------------------|---------------------------------------|--------------------|
| 2016      | 183.33 (= 1,000.00 ÷ 5 × 11 ÷ 12) | 320.83 (= 1,000.00 × 35% × 11 ÷ 12) | 320.83                                | 679.17             |
| 2017      | 169.79 (= 679.17 ÷ 4)             | 237.71 (= 679.17 × 35%)             | 237.71                                | 441.46             |
| 2018      | 147.15                            | 154.51                              | 154.51                                | 286.95             |
| 2019      | 143.48                            | 100.43                              | 143.48                                | 143.47             |
| 2020      | 143.47                            | 50.21                               | 143.47                                | 0.00               |
| **Total** | **Not applicable**                | **Not applicable**                  | **1,000.00**                          | **Not applicable** |

**Note:** If you depreciated an asset by using fixed asset software other than Dynamics 365 Finance, you must post the acquisition and the accumulated depreciation in Finance for the period before you started using the software. For example, if you started using the software on January 1, 2016, you must post the acquisition and accumulated depreciation in Finance for the period that ended December 31, 2015. After you post the acquisition, you must change the acquisition date to the correct date from your previous software and enter the remaining life of the asset. You can then depreciate the asset as usual, starting on January 1, 2016.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
