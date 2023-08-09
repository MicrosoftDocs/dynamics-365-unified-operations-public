---
title: VAT declaration (Denmark)
description: This article describes how to set up and generate an advance value-added tax (VAT) declaration for Denmark.
author: liza-golub
ms.date: 03/10/2022
ms.topic: article
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: egolub
ms.search.validFrom: 
---

# Overview of VAT declaration of Denmark

[!include [banner](../includes/banner.md)]

This article describes how to set up the value-added tax (VAT) declaration for Denmark, preview it in Microsoft Excel and submit to the Danish Tax Agency (Skattestyrelsen).

As of version 10.0.37 of Finance direct submission of VAT return in XML format to the Danish Tax Agency (Skattestyrelsen) is supported.

The **VAT return with direct submission to Danish Tax Agency** feature in Finance supports filing a VAT return for [multiple VAT registrations](emea-multiple-vat-registration-numbers.md) and [collect tax data from several legal entities to one VAT declaration](emea-dnk-vat-declaration-submission.md#run-vat-declaration) in the same system database.

For more information about how to prepare a VAT return with direct submission to Danish Tax Agency, see [Submit VAT return in XML to the Danish Tax Agency](emea-dnk-vat-declaration-submission.md)

## Privacy notice

When you enable Finance to interoperate with the Danish Tax Agency VAT application programming interface (API), both customer content and personal data will be shared with the Danish Tax Agency as part of the submission of your VAT declaration. To learn more about the kinds of information that are included in your submission, you can view the Danish Tax Agency [requirements](https://go.microsoft.com/fwlink/?linkid=2244145). A system administrator can disable the interoperation with the Danish Tax Agency web service in Finance by going to **Tax** \> **Setup** \> **Electronic Messages**.

Your privacy is important to us. To learn more, read our [Privacy notice](https://go.microsoft.com/fwlink/?LinkId=521839).

## VAT declaration overview

The structure of data reported in VAT declaration in Excel and XML format is the same. Excel format serves to preview the amounts that are calculated to be reported to the Danish Tax Agency in XML format. 
To automatically generate the VAT declaration in Excel or XML format, first create enough sales tax codes to keep a separate VAT accounting for each box of VAT declaration. 
Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate sales tax codes with the lookup result for the boxes on the VAT declaration.

For Denmark, you must configure **Report field lookup**. For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up-application-specific-parameters) section later in this article.

In the following table, the "Lookup result" column shows the lookup result that is preconfigured for a specific box of the VAT declaration format. Use this information to correctly associate sales tax codes with the lookup result and then with the box of the VAT declaration.

The VAT declaration in Denmark contains the following information.

### VAT payable

| Description                                                  | Tax base/Tax amount | Lookup result/Total                                                                                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Output VAT                                                   | Tax amount          | **OutputVAT**</br> **DomesticVATUseTax** (also reported in the "Input VAT" box)                                                                                                                                                                                                                                                                       |
| VAT on goods etc. purchased abroad                           | Tax amount          | **PurchaseGoodsAbroad**</br>**PurchaseGoodsAbroadUseTax** (also reported in the "Input VAT" box)</br>**PurchaseGoodsEU** (The tax base is reported in "Box A - acquisition of goods.")</br>**PurchaseGoodsEUUseTax** (The tax amount is also reported in the "Input VAT" box. The tax base is reported in "Box A - acquisition of goods.")                   |
| VAT on services purchased abroad subject to a reverse charge | Tax amount          | **PurchaseServicesAbroad**</br> **PurchaseServicesAbroadUseTax** (also reported in the "Input VAT" box)</br>**PurchaseServicesEU** (The tax base is reported in "Box A - acquisition of services.")</br>**PurchaseServicesEUUseTax** (The tax amount is also reported in the "Input VAT" box. The tax base is reported in "Box A - acquisition of services.") |
| Total payable                                                | Tax amount          | Total of the previous three boxes                                                                                                                                                                                                                                                                                                            |

### Deductions

| Description                                                                               | Tax base/Tax amount | Lookup result/Total                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------------------------------------------------------------------------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Input VAT                                                                                 | Tax amount          | **InputVAT**</br> **DomesticVATUseTax** (also reported in the "Output VAT" box)</br>**PurchaseGoodsAbroadUseTax** (also reported in the "VAT on goods etc. purchased abroad" box)</br>**PurchaseServicesAbroadUseTax** (also reported in the "VAT on services purchased abroad subject to a reverse charge" box)</br>**PurchaseGoodsEUUseTax** (also reported in the "VAT on goods etc. purchased abroad" box)</br> **PurchaseServicesEUUseTax** (also reported in the "VAT on services purchased abroad subject to a reverse charge" box) |
| Oil and bottled gas duty                                                                  | Tax amount          | **OilGasDuty**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Power/electricity duty                                                                    | Tax amount          | **PowerElectricityDuty**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Natural gas and town gas duty                                                             | Tax amount          | **NaturalTownGasDuty**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Carbon duty                                                                               | Tax amount          | **CarbonDuty**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| CO2Duty                                                                                   | Tax amount          | **CO2Duty**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Water charge                                                                              | Tax amount          | **WaterCharge**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Total deductions                                                                          | Tax amount          | Total of the previous six boxes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Total amount of duties (positive amount = make payment, negative amount = receive refund) | Tax amount          | "Total payable" – "Total deductions"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

### Supplementary information

| Description                                                                                                                                                                                                                                | Tax base/Tax amount | Lookup result/Total                             |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|-------------------------------------------------|
| Box A - acquisition of goods. The value without VAT of intra-Union acquisition of goods.                                                                                                                                                   | Tax base            | **PurchaseGoodsEU PurchaseGoodsEUUseTax**       |
| Box A - acquisition of services. The value without VAT of intra-Union acquisition of services.                                                                                                                                             | Tax base            | **PurchaseServicesEU PurchaseServicesEUUseTax** |
| Box B - supply of goods - to be reported to "EU-sales without VAT"/DK VIES. The value without VAT of intra-Union supply of goods                                                                                                           | Tax base            | **SalesGoodsEU**                                |
| Box B - supplies - not to be reported to "EU-sales without VAT"/DK VIES. The value without VAT of certain intra-Union supplies, for instance of installation, assembly, distance sales, and new means of transport to non-taxable persons. | Tax base            | **SalesInstallationAssemblyEtcEU**              |
| Box B - supply of services. The value without VAT of intra-Union supply of services for which the purchaser is liable to pay the VAT as reverse charge - must also be reported to "EU-sales without VAT"/DK VIES.                          | Tax base            | **SalesServicesEU**                             |
| Box C - other supplies. Value of supply of other goods and services that are supplied without VAT in the territory of Denmark, to other EU Member States, and to other countries/regions or territories.                                     | Tax base            | **OtherSuppliesWithoutVAT**                     |

## Note about purchase reverse charge VAT

If you configure sales tax codes to post incoming reverse charge VAT by using use tax, associate your sales tax codes with the lookup result of **Report field lookup** that contains "UseTax" in the name.

Alternatively, you can configure two separate sales tax codes: one for VAT due and one for VAT deduction. Then associate each code with the corresponding lookup results of **Report field lookup**.

For example, for taxable intra-community acquisitions, you configure sales tax code **UT_S_EU** with use tax and associate it with the **PurchaseGoodsEUUseTax** lookup result of **Report field lookup**. In this case, tax amounts that use the **UT_S_EU** sales tax code are reflected in the "VAT on goods etc. purchased abroad" and "Input VAT" boxes. Tax bases are reflected in "Box A - acquisition of goods."

Alternatively, you configure two sales tax codes:

- **VAT_S_EU**, which has a tax rate value of -25 percent
- **InVAT_S_EU**, which has a tax rate value of 25 percent

You then associate the codes with lookup results of **Report field lookup** in the following way:

- Associate **VAT_S_EU** with the **PurchaseGoodsEU** lookup result.
- Associate **InVAT_S_EU** with the **InputVAT** lookup result.

In this case, amounts that use the **VAT_S_EU** sales tax code are reflected in the "VAT on goods etc. purchased abroad" box and "Box A - acquisition of goods." Amounts that use the **InVAT_S_EU** sales tax code are reflected in the "Input VAT" box.

For more information about how to configure reverse charge VAT, see [Reverse charges](emea-reverse-charge.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
