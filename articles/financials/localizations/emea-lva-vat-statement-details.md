---
# required metadata

title: VAT statement details for Latvia
description: This topic explains how to set up the VAT statement for legal entities in Latvia.
author: ShylaThompson
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxAuthority, TaxReportCollection, TaxReportVoucher, TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 266864
ms.search.region: Latvia
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# VAT statement details for Latvia

[!include [banner](../includes/banner.md)]

This topic explains how to set up the VAT statement for legal entities in Latvia.

This topic includes country/region-specific information about the setup of the value-added tax (VAT) statement for legal entities in Latvia only. For more information about the implementation of VAT statements, see [VAT reporting](emea-vat-reporting.md).

## Set up sales tax authorities
To generate a VAT declaration in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities. On the **Sales tax authorities** page, set the **Report layout** field to **Default**. Select the same sales tax authority for the sales tax settlement period that will be used for the sales tax codes.

## Set up sales tax reporting codes
Here is an example that shows how you might set up sales tax reporting codes on the **Report setup** FastTab of the **Sales tax codes** page to generate a VAT statement.

| Sales tax reporting code | Description (English)                                                                    | Description                                                                              | XML tag name |
|--------------------------|------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|--------------|
| 41                       | Standard rate tax amount                                                                 | Ar standartlikmi apliekamie darÄ«jumi                                                     | R41          |
| 411                      | Domestic transactions for which the recipient of the goods or services pays the tax      | IekÅ¡zemÄ“ veiktie darÄ«jumi, par kuriem nodokli maksÄ preÄu vai pakalpojumu saÅ†Ä“mÄ“js       | R411         |
| 42                       | Reduced rate tax amount                                                                  | Ar samazinÄto likmi apliekamie darÄ«jumi                                                  | R42          |
| 45                       | Goods that are delivered to European Union (EU) member states                            | Uz ES dalÄ«bvalstÄ«m piegÄdÄtÄs preces                                                     | R45          |
| 46                       | Amount of custom sales in stock                                                          | Ä€rpuskopienas preÄu piegÄdes muitas noliktavÄs un brÄ«vajÄs zonÄs                         | R46          |
| 47                       | New vehicles delivered to EU countries                                                   | Uz ES dalÄ«bvalstÄ«m piegÄdÄtie jaunie transportlÄ«dzekÄ¼i                                   | R47          |
| 48                       | Provided services                                                                        | Par sniegtajiem pakalpojumiem                                                            | R48          |
| 481                      | Export goods                                                                             | EksportÄ“tÄs preces                                                                       | R48\_1       |
| 482                      | The transactions other countries                                                         | CitÄs valstÄ«s veiktie darÄ«jumi                                                           | R48\_2       |
| 49                       | Not taxable transactions                                                                 | Ar PVN neapliekamie darÄ«jumi                                                             | R49          |
| 50                       | Goods and services that are received from EU member states(standard rate)                | No ES dalÄ«bvalstÄ«m saÅ†emtÄs preces un pakalpojumi (standartlikme)                        | R50          |
| 51                       | Goods and services that are received from EU member states (reduced rate)                | No ES dalÄ«bvalstÄ«m saÅ†emtÄs preces (samazinÄtÄ likme)                                    | R51          |
| 54                       | Received services                                                                        | Par saÅ†emtajiem pakalpojumiem                                                            | R54          |
| 61                       | Imported goods for the company's economic activities                                     | Par importÄ“tajÄm precÄ“m                                                                  | R61          |
| 62                       | Domestic goods and services for the company's economic activities                        | Par precÄ“m un pakalpojumiem iekÅ¡zemÄ“                                                     | R62          |
| 63                       | Calculated tax prepayment                                                                | AprÄ“Ä·inÄtÄ PVN summa saskaÅ†Ä ar likuma 92.panta pirmÄs daÄ¼as 4.punktu (izÅ†emot 64.rindu) | R63          |
| 64                       | Calculated tax prepayment for goods and services that are received from EU member states | AprÄ“Ä·inÄtÄ PVN summa par precÄ“m un pakalpojumiem, kas saÅ†emti no ES dalÄ«bvalstÄ«m         | R64          |
| 65                       | The compensation paid to farmers                                                         | Lauksaimniekiem izmaksÄtÄ kompensÄcija                                                   | R65          |
| 66                       | Not payable tax prepayment                                                               | PVN summa, kas nav atskaitÄma kÄ priekÅ¡nodoklis                                          | R66          |
| 67                       | Tax amount reduction calculated for previous tax periods                                 | IepriekÅ¡Ä“jos taksÄcijas periodos samaksai valsts budÅ¾etÄ aprÄ“Ä·inÄtÄ nodokÄ¼a samazinÄjums | R67          |
| 57                       | Calculated prepayment tax amount reduction for previous tax periods                      | IepriekÅ¡Ä“jos taksÄcijas periodos atskaitÄ«tÄ priekÅ¡nodokÄ¼a samazinÄjums                   | R57          |

## Configure the Electronic reporting model and format for the report
To review or change the VAT statement configuration, on the **Reporting configurations** page, select **VAT declaration model** in the list of models. Then click **Designer** to review or change the model. To review or change the VAT statement format, on the **Reporting configurations** page, select **VAT declaration (LV)**, and then click **Designer**.

## Generate a VAT statement
To generate a VAT XML file, on the **Sales tax payments** page, select one or more vouchers, and then click **Export VAT XML file**.



