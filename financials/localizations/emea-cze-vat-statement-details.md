---
# required metadata

title: VAT statement for the Czech Republic
description: Set up and generate the VAT statement for users in legal entities located in the Czech Republic.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxAuthority, TaxReportCollection, TaxReportVoucher, TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 263614
ms.assetid: eef73389-e480-451d-a43d-562429b41742
ms.search.region: Czech Republic
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# VAT statement for the Czech Republic

[!include[banner](../includes/banner.md)]


Set up and generate the VAT statement for users in legal entities located in the Czech Republic.

This topic includes country-specific information about VAT statement setup for users in legal entities in the Czech Republic. For more information about general VAT reporting, see [VAT reporting](emea-vat-reporting.md).

## Set up sales tax authorities
To generate a VAT declaration in the required format for the specific tax authority, you must set up the report layout for the sales tax authorities.

-   On the **Sales tax authorities** page, in the **General** section, set the **Report layout **to **Default**.
-   Select the same **Sales tax authority** for the **Sales tax settlement period** that you will use for the sales tax codes.

## Set up sales tax reporting codes
The following is an example of how sales tax reporting codes could be set up for VAT statement generation.

### Example

For users in legal entities in the Czech Republic, according VAT declaration in 2016, the following sales tax reporting codes could be created.

|                              |                                                         |
|------------------------------|---------------------------------------------------------|
| **Sales tax reporting code** | **Description**                                         |
| 2101                         | ř.210 - se zákl. sazbou daně  - Základ                  |
| 2102                         | ř.210 - se zákl. sazbou daně  - Daň                     |
| 2151                         | ř.215 - se sníž. sazbou daně  - Základ                  |
| 2152                         | ř.215 - se sníž. sazbou daně  - Daň                     |
| 2201                         | ř.220 - se zákl. sazbou daně  - Základ                  |
| 2202                         | ř.220 - se zákl. sazbou daně  - Daň                     |
| 2251                         | ř.225 - se sníž. sazbou daně  - Základ                  |
| 2252                         | ř.225 - se sníž. sazbou daně  - Daň                     |
| 2301                         | ř.230 - se zákl. sazbou daně  - Základ                  |
| 2302                         | ř.230 - se zákl. sazbou daně  - Daň                     |
| 2351                         | ř.235 - se sníž. sazbou daně – Základ                   |
| 2352                         | ř.235 - se sníž. sazbou daně – Daň                      |
| 2401                         | ř.240 - se zákl. sazbou daně  - Základ                  |
| 2402                         | ř.240 - se zákl. sazbou daně  - Daň                     |
| 2451                         | ř.245 - se sníž. sazbou daně  - Základ                  |
| 2452                         | ř.245 - se sníž. sazbou daně  - Daň                     |
| 2501                         | ř.250 - od osob reg. v jiném čl.státě - Základ          |
| 2502                         | ř.250 - od osob reg. v jiném čl.státě - Daň             |
| 2551                         | ř.255 - od osob nereg. v jiném čl.státě - Základ        |
| 2552                         | ř.255 - od osob nereg. v jiném čl.státě - Daň           |
| 2601                         | ř.260 - se zákl. sazbou daně – Základ                   |
| 2602                         | ř.260 - se zákl. sazbou daně – Daň                      |
| 2651                         | ř.265 - se sníž. sazbou daně – Základ                   |
| 2652                         | ř.265 - se sníž. sazbou daně - Daň                      |
| 2701                         | ř.270 - se zákl. sazbou daně  - Základ                  |
| 2702                         | ř.270 - se zákl. sazbou daně  - Daň                     |
| 2751                         | ř.275 - se sníž. sazbou daně  - Základ                  |
| 2752                         | ř.275 - se sníž. sazbou daně  - Daň                     |
| 3101                         | ř.310 - se zákl. sazbou daně - Základ                   |
| 3102                         | ř.310 - se zákl. sazbou daně - Daň, plný nárok          |
| 3103                         | ř.310 - se zákl. sazbou daně - Daň, krác. nárok         |
| 3151                         | ř.315 - se sníž. sazbou daně - Základ                   |
| 3152                         | ř.315 - se sníž. sazbou daně - Daň, plný nárok          |
| 3153                         | ř.315 - se sníž. sazbou daně - Daň, krác. nárok         |
| 3201                         | ř.320 - se zákl. sazbou daně  - Základ                  |
| 3202                         | ř.320 - se zákl. sazbou daně  - Daň, plný nárok         |
| 3203                         | ř.320 - se zákl. sazbou daně  - Daň, krác. nárok        |
| 3251                         | ř.325 - se sníž. sazbou daně  - Základ                  |
| 3252                         | ř.325 - se sníž. sazbou daně  - Daň, plný nárok         |
| 3253                         | ř.325 - se sníž. sazbou daně  - Daň, krác. nárok        |
| 3301                         | ř.330 - se zákl. sazbou daně - Základ                   |
| 3302                         | ř.330 - se zákl. sazbou daně - Daň, plný nárok          |
| 3303                         | ř.330 - se zákl. sazbou daně - Daň, krác. nárok         |
| 3351                         | ř.335 - se sníž. sazbou daně  - Základ                  |
| 3352                         | ř.335 - se sníž. sazbou daně  - Daň, plný nárok         |
| 3353                         | ř.335 - se sníž. sazbou daně  - Daň, krác. nárok        |
| 3401                         | ř.340 - se zákl. sazbou daně - Základ                   |
| 3402                         | ř.340 - se zákl. sazbou daně - Daň, plný nárok          |
| 3403                         | ř.340 - se zákl. sazbou daně - Daň, krác. nárok         |
| 3451                         | ř.345 - se sníž. sazbou daně  - Základ                  |
| 3452                         | ř.345 - se sníž. sazbou daně  - Daň, plný nárok         |
| 3453                         | ř.345 - se sníž. sazbou daně  - Daň, krác. nárok        |
| 3501                         | ř.350 - se zákl. sazbou daně  - Základ                  |
| 3502                         | ř.350 - se zákl. sazbou daně  - Daň, plný nárok         |
| 3503                         | ř.350 - se zákl. sazbou daně  - Daň, krác. nárok        |
| 3551                         | ř.355 - se sníž. sazbou daně  - Základ                  |
| 3552                         | ř.355 - se sníž. sazbou daně  - Daň, plný nárok         |
| 3553                         | ř.355 - se sníž. sazbou daně  - Daň, krác. nárok        |
| 3601                         | ř.360 - od osob reg. v jiném čl.státě - Základ          |
| 3602                         | ř.360 - od osob reg. v jiném čl.státě - Daň             |
| 3603                         | ř.360 - od osob reg. v jiném čl.státě - Daň, krác.      |
| 3651                         | ř.365 - od osob nereg. v jiném čl.státě - Základ        |
| 3652                         | ř.365 - od osob nereg. v jiném čl.státě - Daň           |
| 3653                         | ř.365 - od osob nereg. v jiném čl.státě - Daň, kr.      |
| 3702                         | ř.370 - při změně režimu  - Daň, plný nárok             |
| 3703                         | ř.370 - při změně režimu  - Daň, krác. nárok            |
| 3803                         | ř.380 - celková suma pro krácení nároku na odpočet daně |
| 3902                         | ř.390 - celková suma plného nároku na odpočet daně      |
| 4102                         | ř.410 - dodání zboží do jiného čl.státu                 |
| 4202                         | ř.420 - dodání nového dopr.prostř. osobě reg.           |
| 4252                         | ř.425 - dodání nového dopr. prostř. osobě nereg.        |
| 4302                         | ř.430 - vývoz zboží (§66)                               |
| 4402                         | ř.440 - Ost.plnění osv.od daně s nárok. na odpočet      |
| 5102                         | ř.510 - Celk. usk.plnění s nárokem na odpočet daně      |
| 5202                         | ř.520 - Uskut. plnění, která se nezapoč. do koef.       |
| 5302                         | ř.530 - Celk. osv.usk.plnění bez nároku na odpočet      |
| 5402                         | ř.540 - Usk.plnění nezapoč. do výpočtu koeficientu      |
| 5503                         | ř.550 - Vypočt. poměr.část odp.daně (§76) - Koef.       |
| 5502                         | ř.550 - Vypočt. poměr.část odp.daně (§76)               |
| 5603                         | ř.560 - Vypoř. odp. daně (§76 odst.7-10) - Koef.        |
| 5602                         | ř.560 - Vypoř. odp. daně (§76 odst.7-10)                |
| 5702                         | ř.570 - Úprava odpočtu daně (§78)                       |
| 5802                         | ř.580 - Vyrovnání odpočtu daně (§79)                    |
| 6002                         | ř.600 - Vrácení daně                                    |
| 7102                         | ř.710 - Vypořádání daně na výstupu (§91)                |
| 7302                         | ř.730 - Daň na výstupu                                  |
| 7502                         | ř.750 - Odpočet daně                                    |
| 7532                         | ř.753 - Vlastní daňová povinnost                        |
| 7542                         | ř.754 - Nadměrný odpočet                                |
| 7802                         | ř.780 - Změna daň.povinnosti při podání dod. přiz.      |
| 8101                         | ř.810 - Pořízení zboží prostřední osobou                |
| 8151                         | ř.815 - Dodání zboží prostřední osobou                  |

## Configure the ER model and format for the report
You can use the **Electronic reporting** workspace to review or change the VAT statement configuration. Go to the **Configurations** page and select **VAT declaration model** from the list of models. This model is common for Austria, Czech Republic, Estonia, Finland, Latvia, and Lithuania and it aggregates tax data needed for VAT declaration. To review or change the VAT statement format for users in legal entities in the Czech Republic, select **VAT declaration (CZ)**, which is a child of **VAT declaration model** in the model tree. Select it and click **Designer** on the Action Pane to review or change the format. For more information, see [Electronic reporting.](/dynamics365/operations/dev-itpro/analytics/general-electronic-reporting)

## Generate the VAT statement
To generate a VAT XML file, open the **Sales tax payments** page, select vouchers, and then click **Export VAT XML file**.



