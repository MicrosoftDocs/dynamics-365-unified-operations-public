---
title: Tax attributes for Brazil
description: This article explains how to set up fiscal information for addresses, legal entities, customers, and vendors, and for products that are released to a Brazilian legal entity. This information is required for tax calculation, and for fiscal documents and other required statements that you submit from Fiscal books.
author: AdamTrukawka
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 269544
ms.assetid: 92b0cf1b-51ec-4611-bf8e-db4cd10ffed0
ms.search.form: CustTable, EcoResProductDetails, LogisticsAddressSetup
---

# Tax attributes for Brazil

[!include [banner](../includes/banner.md)]

This article explains how to set up fiscal information for addresses, legal entities, customers, and vendors, and for products that are released to a Brazilian legal entity. This information is required for tax calculation, and for fiscal documents and other required statements that you submit from Fiscal books.

## Tax address attributes

For any legal entity that has an address in Brazil, the Instituto Brasileiro de Geografia e Estatística (IBGE) code must be set up on the state and/or city. The IBGE code is used to identify the region where the address is located, so that correct taxes are considered. The IBGE code information comes from the IBGE, which is an official organization that maps the Brazilian geography.

1.  On the **Address setup** page, in the **State/province** field group, in the **Country/region** field, select **BRA**. Then, in the **IBGE code** field, enter the IBGE code for the state.
2.  In the **City** field group, in the **Country/region** field, select **BRA**. Then, in the **IBGE code** field, enter the IBGE code for the city.

## Customer tax attributes
The following fields on the **Customer** page are required for a Brazilian legal entity.

| Field                                                                   | Description                                                                                                                                                                                                       |
|-------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CNPJ/CPF                                                                | The tax payer registration number, or Cadastro Nacional da Pessoa Jurídica (CNPJ)/Cadastro de Pessoas Físicas (CPF), of the legal entity.                                                                         |
| IE                                                                      | The state registration number, or Inscrição Estadual (IE), of the legal entity.                                                                                                                                   |
| CCM                                                                     | The municipal registration number, or Cadastro de contribuinte mobiliário (CCM), of the legal entity.                                                                                                             |
| NIT                                                                     | The worker identification number.                                                                                                                                                                                 |
| INSS\_CEI                                                               | The Brazilian security number.                                                                                                                                                                                    |
| CNAE                                                                    | The national/regional classification code, or Classificação Nacional de Atividades Econômicas (CNAE), for the economic activity of the legal entity.                                                                       |
| Foreigner ID                                                            | The natural country/region ID number for foreign customers.                                                                                                                                                       |
| Service on delivery address                                             | When this option is set to **Yes**, the service codes and IBGE city code from the delivery address are applied.                                                                                                   |
| SUFRAMA (In the **SUFRAMA region** field group)                         | Set this option to **Yes** if the customer is located in the Superintendência da Zona Franca de Manaus (SUFRAMA) region in Brazil.                                                                                |
| SUFRAMA number (In the **SUFRAMA region** field group)                  | If the customer is located in the SUFRAMA region, you must enter the customer's SUFRAMA registration number.                                                                                                      |
| Discount PIS and COFINS                                                 | If the customer is located in the SUFRAMA region, set this option to **Yes** to apply discounts to Programa de Integração Social (PIS) and Contribuição para o Financiamento da Seguridade Social (COFINS) taxes. |
| Generate incoming fiscal document (In the **Sales return** field group) | Set this option to **Yes** to issue the incoming fiscal document for sales returns when the customer isn't a company and didn't issue fiscal documents.                                                           |
| Final user                                                              | If this option is set to **Yes**, the customer is the final user.                                                                                                                                                 |
| ICMS contributor                                                        | If this option is set to **Yes**, the customer has registration and should collect Imposto sobre Circulação de Mercadorias e Serviços (ICMS) taxes.                                                               |
| Presence type                                                           | The type of presence when a fiscal document is issued to the customer.                                                                                                                                            |

## Vendor tax attributes
The following fields on the **Vendor** page are required for a Brazilian legal entity.

| Field                             | Description                                                                                                                         |
|-----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| CNPJ/CPF                          | Enter the tax payer registration number (CNPJ/CPF) of the legal entity.                                                             |
| IE                                | Enter the state registration number (IE) of the legal entity.                                                                       |
| CCM                               | Enter the municipal registration number (CCM) of the legal entity.                                                                  |
| NIT                               | The worker identification number.                                                                                                   |
| INSS\_CEI                         | The Brazilian security number.                                                                                                      |
| CNAE                              | Enter the national/regional classification code (CNAE) for the economic activity of the legal entity.                                        |
| Foreigner ID                      | The vendor's natural country/region ID number, if the vendor is a person from another country/region.                               |
| Generate incoming fiscal document | Set this option to **Yes** to issue the incoming fiscal document when the vendor isn't a company and didn't issue fiscal documents. |
| Use and consumption               | Set this option to **Yes** if products from this vendor are intended to be used and consumed in any process.                        |
| Income code                       | The code that is used in Fiscal books to identify the income code of the vendor.                                                    |
| ICMS contributor                  | If this option is set to **Yes**, the vendor has registration and should collect ICMS taxes.                                        |
| Presence type                     | The type of presence when a fiscal document is received from vendor.                                                                |
| Service on delivery address       | Set this option to **Yes** to apply the service codes and IBGE city code.                                                           |

## Product tax attributes
The following fields on the **Product information** page are required for a Brazilian legal entity.

| Field                                   | Description                                                                        |
|-----------------------------------------|------------------------------------------------------------------------------------|
| Taxation origin                         | The origin of the product for taxation purposes.                                   |
| Product type                            | The type of product. This field is used to classify the type of product.           |
| Fiscal classification code              | The fiscal classification code.                                                    |
| Exception code                          | The exception code for Imposto sobre Produtos Industrializados (IPI) tax.          |
| Service code                            | The fiscal classification for an item of the service type.                         |
| ICMS on service                         | The ICMS tax that is applied on an item of the service type.                       |
| Approximate tax percentage (Tax burden) | The tax rate that is used to calculate the approximate tax amount for the product. |
| CEST (Tax substitution code)            | The code number that is used if tax substitution is allowed for the item.          |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
