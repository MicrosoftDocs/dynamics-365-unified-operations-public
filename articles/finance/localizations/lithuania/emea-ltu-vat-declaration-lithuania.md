---
title: VAT declaration for Lithuania
description: This article explains how to set up a VAT declaration for legal entities in Lithuania.
author: liza-golub
ms.date: 04/18/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Lithuania
ms.author: egolub
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
ms.search.form: TaxAuthority, TaxReportCollection, TaxReportVoucher, TaxTable
---

# VAT declaration for Lithuania (FR0600)

[!include [banner](../../includes/banner.md)]

This article describes how to set up and generate a value-added tax (VAT) declaration for Lithuania in the XML format (FR0600) and how to preview it in Microsoft Excel.

The VAT declaration feature for Lithuania supports filing a VAT return for companies with [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md) and for companies that report as a VAT group in the same system database.

## VAT declaration overview

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each type of operation that's subject to reporting in the VAT declaration for Lithuania. 
Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate available sales tax transaction attributes 
(sales tax code, tax classifier) with the lookup result of the **Report field lookup** lookup field. 
In the following table, the "Lookup result" column shows the lookup result that's preconfigured for a specific VAT declaration field in the VAT declaration format. 
Use this information to correctly associate tax transaction attributes with the lookup result and then with the field of the VAT declaration.

| **Operation description**      | **FR0600: Tax Base**<br><br>**(sum without VAT)** | **FR0600: VAT amount** | **Lookup result <br>(ReportFieldLookup)** | **Lookup result description label EN** | **Lookup result description label LT** |
| ------------------------------- | --- | --- | --- | --- | --- |
| Sales in Lithuania, VAT 21%     | 11  | 29  | DomesticSalesStandardRate | 11/29 Sales in Lithuania, VAT 21% | 11/29 Pardavimai Lietuvoje, kai taikomas 21 proc. PVM tarifas |
| Sales in Lithuania, VAT 9%      | 11  | 30  | DomesticSalesReducedRate | 11/30 Sales in Lithuania, VAT 9% | 11/30 Pardavimai Lietuvoje, kai taikomas 9 proc. PVM tarifas |
| Sales in Lithuania, VAT 5%      | 11  | 31  | DomesticSalesSecondReducedRate | 11/31 Sales in Lithuania, VAT 5% | 11/31 Pardavimai Lietuvoje, kai taikomas 5 proc. PVM tarifas |
| Sales in Lithuania, when reverse charge VAT is applied Art. 96. | 12  | not reported | DomesticSalesReverseCharge | 12 Sales in Lithuania, when reverse charge VAT is applied Art. 96. | 12 Pardavimai Lietuvoje, kai taikomas PVMĮ 96 str. (atvirkštinis apmokestinamas) |
| Supply of goods to a EU VAT payer (0% VAT rate is applied, according to VAT Article 49 d. 1) | 18  | not reported | EUSalesZeroRate | 18 Supply of goods to a EU VAT payer (0% VAT rate is applied, according to VAT Article 49 d. 1) | 18 Prekių tiekimas Europos Sąjungos PVM mokėtojui (taikomas 0 proc. PVM tarifas, pagal PVMĮ 49 str. 1 d.) |
| Triangular trade: phase I       | 18  | not reported | SalesTriangularTradePhaseI | 18 Triangular trade (sales): phase I | 18 Trikampė prekyba: I grandis |
| Triangular trade: phase II      | 20  | not reported | SalesTriangularTradePhaseII | 20 Triangular trade (sales): phase II | 20 Trikampė prekyba: II grandis |
| Export of goods (sales to third countries with 0% VAT rate according to Article 41 of VAT) | 17<br><br>&nbsp; | not reported | Export | 17 Export of goods (sales to third countries with 0% VAT rate according to Article 41 of VAT) | 17 Prekių eksportas (pardavimai į trečiąsias<br><br>šalis su 0 proc. PVM tarifu pagal PVMĮ 41 str.) |
| Sales that are not subject to VAT according to Articles 20-33 of VAT. | 13  | not reported | NonTaxableSales | 13 Sales that are not subject to VAT according to Articles 20-33 of VAT. | 13 Pardavimai, kurie neapmokestinami PVM pagal PVMĮ 20-33 str. |
| Sales under the margin charge scheme when the margin is positive, 21% | 16  | 29  | MarginSchemaPositiveStandardRate | 16/29 Sales under the margin charge scheme when the margin is positive, 21% | 16/29 Pardavimai pagal maržos apmokestinimo schemą (kai marža teigiama), 21% |
| Sales under the margin charge scheme when the margin is positive, 9% | 16  | 30  | MarginSchemaPositiveReducedRate | 16/30 Sales under the margin charge scheme when the margin is positive, 9% | 16/30 Pardavimai pagal maržos apmokestinimo schemą (kai marža teigiama), 9% |
| Sales under the margin charge scheme when the margin is positive, 5% | 16  | 31  | MarginSchemaPositiveSecondReducedRate | 16/31 Sales under the margin charge scheme when the margin is positive, 5% | 16/31 Pardavimai pagal maržos apmokestinimo schemą (kai marža teigiama), 5% |
| Sales under the margin charge scheme when the negative margin, 21% | not reported | not reported | n/a | n/a | n/a |
| Sales under the margin charge scheme when the negative margin, 9% | not reported | not reported | n/a | n/a | n/a |
| Sales under the margin charge scheme when the negative margin, 5% | not reported | not reported | n/a | n/a | n/a |
| Sales under the margin charge scheme with 0% | not reported | not reported | n/a | n/a | n/a |
| Sales under the margin tax scheme, where the margin is positive and can be applied at 0% VAT rate according to Article 108¹ of VAT. | 16  | not reported | MarginSchemaPositiveZeroRate | 16 Sales under the margin tax scheme, where the margin is positive and can be applied at 0% VAT rate according to Article 108¹ of VAT. | 16 Pardavimas pagal maržos apmokestinimo schemą (kai marža lygi 0 arba neigiama) |
| Other cases when sales in Lithuania are taxed at 0% VAT rate (Articles 42, 43, 44, 45, 46, 47, 48, 49, Articles 2 and 3 of VAT, Articles 51, 52, 53) | 19  | not reported | OtherSalesZeroRate | 19 Other cases when sales in Lithuania are taxed at 0% VAT rate (Articles 42, 43, 44, 45, 46, 47, 48, 49, Articles 2 and 3 of VAT, Articles 51, 52, 53) | 19 Kiti atvejai, kai pardavimas Lietuvoje apmokestinamas 0 proc. PVM tarifu (PVMĮ 42, 43, 44, 45, 46, 47, 48, 49 str. 2 ir 3 d., 51, 52, 53 str.) |
| Sales that are not considered a VAT object in Lithuania, if VAT deduction is possible according to Article 58 of VAT. | 20  | not reported | NonTaxableSalesOutsideLithuania15 | 20 (PVM15) Sales that are not considered a VAT object in Lithuania, if VAT deduction is possible according to Article 58 of VAT. | 20 (PVM15) Pardavimai, kurie laikomi ne PVM objektu Lietuvoje |
| Sales that are not considered a VAT object in Lithuania, if VAT deduction is not possible according to Article 58 of VAT. | 20  | not reported | NonTaxableSalesOutsideLithuania34 | 20 (PVM34) Sales that are not considered a VAT object in Lithuania, if VAT deduction is not possible according to Article 58 of VAT. | 20 (PVM34) Pardavimai, kurie laikomi ne PVM objektu Lietuvoje |
| Production of tangible fixed assets, 21% VAT rate | 15  | 29, 25, 35<br><br> | FixedAssetProduction | 15/29/25/35 Production of tangible fixed assets, 21% VAT rate | 15/29/25/35 Ilgalaikio turto pasigaminimas, kai apskaičiuojamas 21 proc. PVM tarifas |
| Consumption for private needs, 21% | 14  | 29  | PrivateConsumptionStandardRate | 14/29 Consumption for private needs, 21% | 14/29 Suvartojimas privatiems poreikiams, 21% |
| Consumption for private needs, 9% | 14  | 30  | PrivateConsumptionReducedRate | 14/30 Consumption for private needs, 9% | 14/30 Suvartojimas privatiems poreikiams, 9% |
| Consumption for private needs, 5% | 14  | 31  | PrivateConsumptionSecondReducedRate | 14/31 Consumption for private needs, 5% | 14/31 Suvartojimas privatiems poreikiams, 5% |
| Purchase in Lithuania with VAT 21%, 9%, 5%. | not reported | 25, 35 | DomesticPurchase | 25/35 Purchase in Lithuania with VAT 21%, 9%, 5% | 25/35 Standartiniai pirkimai Lietuvoje su PVM (21 proc., 9 proc., 5 proc.) |
| Purchase in Lithuania, when reverse charge VAT is applied Art. 96 | not reported | 25, 33, 35 | DomesticPurchaseReverseCharge | 25/33/35 Purchase in Lithuania, when reverse charge VAT is applied Art. 96 | 25/33/35 Pirkimai Lietuvoje, kai taikomas PVMĮ\* 96 str. (atvirkštinis apmokestinimas) |
| Purchase in Lithuania, 0% VAT (VAT 41, 42, 43, 44, 45,46, 47, 48, 51, 52, 53 str.) | not reported | not reported | n/a | n/a | n/a |
| Purchase in Lithuania, when the margin tax scheme is applied | not reported | not reported | n/a | n/a | n/a |
| Purchase of goods from EU VAT payers, when there is an obligation to calculate VAT in Lithuania (VAT Article 4¹ and Article 12²) | 21  | 25, 34, 35<br><br> | EUPurchaseGoods | 21/34/25/35 Purchase of goods from EU VAT payers, when there is an obligation to calculate VAT in Lithuania (VAT Article 4¹ and Article 12²) | 21/34/25/35 Prekių įsigijimas iš Europos Sąjungos PVM mokėtojų, kai atsiranda prievolė priskaičiuoti PVM Lietuvoje (PVMĮ 4¹ str. ir 12² str.) |
| Import of goods (purchases of goods from third countries) when import VAT is paid to customs | not reported | 26, 35  | ImportPaid | 26/35 Import of goods (purchases of goods from third countries) when import VAT is paid to customs | 26/35 Prekių importas (prekių įsigijimai iš trečiųjų šalių) - kai importo PVM mokamas muitinei |
| Import of goods (purchases of goods from third countries) when control of import VAT payment is taken over by VMI. | not reported | 27, 35<br><br> | ImportControlledVMI | 27/35 Import of goods (purchases of goods from third countries) when control of import VAT payment is taken over by VMI. | 27/35 Prekių importas (prekių įsigijimai iš trečiųjų šalių) - kai importo PVM mokėjimo kontrolę perima VMI |
| Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from an EU VAT payer. | 23, 24 | 25, 32, 35<br><br> | ForeignPurchaseServicesEU | 23/24/32/25/35 Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from an EU VAT payer. | 23/24/32/25/35 Paslaugų įsigijimai iš užsienio valstybių, kai 21 proc. pardavimo PVM apskaičiuoja pirkėjas (PVMĮ 95 str. 2 dalis) - Paslaugos įsigytos iš ES PVM mokėtojo |
| Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from third parties or non-EU VAT payer. | 23  | 25, 32, 35<br><br> | ForeignPurchaseServicesNonEU | 23/32/25/35 Purchases of services from foreign countries, when 21% VAT is calculated by the buyer (VAT Article 95, Part 2), when the services are purchased from third parties or non-EU VAT payer. | 23/32/25/35 Paslaugų įsigijimai iš užsienio valstybių, kai 21 proc. pardavimo PVM apskaičiuoja pirkėjas (PVMĮ 95 str. 2 dalis) - Paslaugos įsigytos iš trečiųjų šalių arba ES ne PVM mokėtojo |
| Triangular trade: Phase II | 22  | not reported | PurchaseTriangularTradePhaseII | 22 Triangular trade (purchase): Phase II | 22 Trikampė prekyba: II grandis |
| Triangular trade: Phase III | not reported | 25, 32, 35<br><br> | PurchaseTriangularTradePhaseIII | 32/25/35 Triangular trade (purchase): Phase III | 32/25/35 Trikampė prekyba: III grandis |
| Cases where the "reserve" rule applies for the purchase of goods from another EU Member State | 21  | 25, 34 | EUPurchaseGoodsReserve | 21/25/34 Cases where the "reserve" rule applies for the purchase of goods from another Member State | 21/25/34 Atvejai, kai dėl prekių įsigijimo iš kitos valstybės narės taikoma „rezervo“ taisyklė |




## Set up sales tax authorities

To generate a VAT declaration in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities. 
On the **Sales tax authorities** page, in the **Report layout** field, select **Default**. Select the same sales tax authority for the sales tax settlement period that will be used for sales tax codes.
