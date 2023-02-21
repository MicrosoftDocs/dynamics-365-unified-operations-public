---
# required metadata

title: Retained earnings calculation in Financial reporting
description: This article describes how the **Retained earnings calculation** enhancement for Financial reporting is used. This enhancement has implications for organizations that use currency translation.
author: jinniew
ms.date: 09/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: FinancialReports
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 261824
ms.search.region: Global
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2020-01-09
ms.dyn365.ops.version: Version 10.0.8

---

# Retained earnings calculation in Financial reporting

[!include [banner](../includes/banner.md)]

This article describes how the **Retained earnings calculation** enhancement for Financial reporting is used. This enhancement has implications for organizations that use currency translation.

> [!NOTE]
> To turn the enhancement on or off, log a support ticket.
>
> When you turn on the enhancement, any retained earnings account where the currency translation type is set to **Transaction date** will calculate the accounting currency balance by using the change in the current year and the exchange rate at the end of the year. The total retained earning balance at the end of any year will be a sum of each calculated year.

### What happens when you turn on this enhancement?

For this example, you're closing the year on December 31. If the **Retained earnings calculation** enhancement is turned on, the change in the current year will be calculated by using the currency rate as of that date. If the enhancement is turned off, the retained earnings as of December 31 will be USD250.00. The amount in the reporting currency will be EUR312.50. This amount equals the USD250.00 multiplied by 1.25, which was the exchange rate as of December 31, 2021.

If the enhancement is turned on, the retained earnings in the reporting currency as of December 31, 2021, will be EUR288.75. This number is made up of the calculated balances, as shown by (d).

| Retained earnings                                                                                | Currency | 2018   | 2019   | 2020   | 2021   |
|--------------------------------------------------------------------------------------------------|:----------:|--------:|--------:|--------:|--------:|
| Balance on 12/31/XXXX when the enhancement is turned off (a).                                    | USD      | 100.00 | 150.00 | 225.00 | 250.00 |
| Balance on 12/31/XXXX when the enhancement is turned on and currency translation is used (b).    | USD      | 100.00 | 50.00  | 75.00  | 25.00  |
| Exchange rate on 12/31/XXXX (c).                                                                 |          | 1.10   | 1.15   | 1.20   | 1.25   |
| Translated exchange rate on 12/31/XXXX (d). The calculation is b × c.                           | EUR      | 110.00 | 57.50  | 90.00  | 31.25  |
| Retained earnings as of 12/31/2021 when the enhancement is turned on (a).                            | USD      | 100.00 | 150.00 | 225.00 | 250.00 |
| Exchange rate in the reporting currency on 12/31/XXXX when the enhancement is turned off (a × c).    | EUR      | 110.00 | 172.50 | 270.00 | 312.50 |
| Summed exchange rate in the reporting currency on 12/31/XXXX when the enhancement is turned on (d). | EUR      | 110.00 | 167.50 | 257.50 | 288.75 |


For more information, see [Set up for Retained earnings](/general-ledger/financial-reporting-currency-capability.md#setup-for-retained-earnings).
