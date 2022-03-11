---
# required metadata

title: VAT declaration (Finland)
description: This topic describes how to set up and generate a value-added tax (VAT) declaration for Finland in the official TXT format and preview in Microsoft Excel. 
author: liza-golub
ms.date: 03/10/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Finland
ms.author: liza-golub
# ms.search.industry: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# VAT declaration (Finland)

[!include [banner](../includes/banner.md)]

This topic describes how to set up and generate a value-added tax (VAT) declaration for Finland in the official TXT format. 
It also describes how to preview the VAT declaration in Microsoft Excel..

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each box on the VAT declaration. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate sales tax codes with the lookup result of the lookups for the boxes on the VAT declaration.

For Finland, you must configure **Report field lookup**. For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields]() section later in this topic.

In the following table, the "Lookup result" column shows the lookup result that is preconfigured for a specific VAT declaration row in the VAT declaration format. Use this information to correctly associate sales tax codes with the lookup result and then with the row of the VAT declaration.

## VAT declaration overview

The VAT declaration for Finalnd contains the following fields to report amounts about related to VAT.

| **Field ID (Tunnus)** | **Description (English)** | **Description (Finish)** | **Lookup result** |
| --- | --- | --- | --- |
| 301 | Tax on domestic sales at standard tax rate | Kotimaan verollinen myynti yleisellä verokannalla | DomesticSalesStandardRate |
| 302 | Tax on domestic sales at higher reduced tax rate | Kotimaan verollinen myynti suuremman alennetun verokannan mukaan | DomesticSalesHigherReducedRate |
| 303 | Tax on domestic sales lower reduced tax rate | Kotimaan verollinen myynti pienemmän alennetun verokannan mukaan | DomesticSalesLowerReducedRate |
| 304 | Tax on imports of goods from outside the EU | Vero tavaroiden maahantuonnista EU:n ulkopuolelta | ImportsOfGoods</br>ImportsOfGoodsUseTax – when *Use tax* option is used |
| 305 | Tax on goods purchased from other EU Member States | Vero tavaraostoista muista EU-maista | GoodsPurchasedFromEU</br>GoodsPurchasedFromEUUseTax – when *Use tax* option is used |
| 306 | Tax on services purchased from other EU Member States | Vero palveluostoista muista EU-maista | ServicesPurchasedFromEU</br>ServicesPurchasedFromEUUseTax – when *Use tax* option is used |
| 307 | Tax deductible for the tax period | Verokauden vähennettävä vero | Deductible</br>When *Use tax* is used:</br>- GoodsPurchasedFromEUUseTax</br>- ImportsOfGoodsUseTax</br>- PurchasesReverseChargeUseTax</br>- ServicesPurchasedFromEUUseTax |
| **308** | **Tax payable / Negative tax that qualifies for refund (‒)** | **Maksettava vero / Palautukseen oikeuttava vero (-)** | **Not applicable, calculated automatically** |
| 309 | Turnover taxable at zero VAT rate | 0-verokannan alainen liikevaihto | TaxableSalesZero |
| 310 | Imports of goods from outside the EU | Tavaroiden maahantuonnit EU:n ulkopuolelta | ImportsOfGoods</br>ImportsOfGoodsUseTax – when *Use tax* option is used |
| 311 | Sales of goods to other EU Member States | Tavaroiden myynnit muihin EU-maihin | EUSalesOfGoods |
| 312 | Sales of services to other EU Member States | Palveluiden myynnit muihin EU-maihin | EUSalesOfServices |
| 313 | Purchases of goods from other EU Member States | Tavaraostot muista EU-maista | GoodsPurchasedFromEU</br>GoodsPurchasedFromEUUseTax – when *Use tax* option is used |
| 314 | Purchases of services from other EU Member States | Palveluostot muista EU-maista | ServicesPurchasedFromEU</br>ServicesPurchasedFromEUUseTax – when *Use tax* option is used |
| 315 | Turnover that qualifies for VAT relief | Alarajahuojennukseen oikeuttava liikevaihto | Not applicable, filled in using **VAT relief - sales amount** user input parameter of the dialogue of the report. |
| 316 | Tax that qualifies for VAT relief | Alarajahuojennukseen oikeuttava vero | Not applicable, filled in using **VAT relief - tax amount** user input parameter of the dialogue of the report. |
| 317 | Amount of VAT relief | Alarajahuojennuksen määrä | Not applicable, calculated automatically. |
| 318 | Tax on purchases of construction services and scrap metal (reverse charge) | Vero rakentamispalvelun ja metalliromun ostoista | PurchasesReverseCharge</br>PurchasesReverseChargeUseTax – when *Use tax* option is used |
| 319 | Sales of construction services and scrap metal (reverse charge) | Rakentamispalvelun ja metalliromun myynnit | SalesReverseCharge |
| 320 | Purchases of construction services and scrap metal (reverse charge) | Rakentamispalvelun ja metalliromun ostot | PurchasesReverseCharge</br>PurchasesReverseChargeUseTax – when *Use tax* option is used |
