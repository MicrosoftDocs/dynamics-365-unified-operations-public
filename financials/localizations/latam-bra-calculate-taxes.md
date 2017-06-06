---
# required metadata

title: Brazilian taxes
description: Microsoft Dynamics 365 for Operations calculates Brazilian taxes based on the tax type that you specify for the sales tax code. You can set up and calculate sales taxes on sales, purchases, transfers between fiscal establishments, delivery of items to a third party, or receipt of items from a third party.
author: sndray
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 268704
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Brazilian taxes

[!include[banner](../includes/banner.md)]


Microsoft Dynamics 365 for Operations calculates Brazilian taxes based on the tax type that you specify for the sales tax code. You can set up and calculate sales taxes on sales, purchases, transfers between fiscal establishments, delivery of items to a third party, or receipt of items from a third party.

You can set up taxation codes for Imposto sobre Circulação de Mercadorias e Serviços (ICMS), Imposto sobre Produtos Industrializados (IPI), Program de Integracao Social (PIS), and Contribuição para Financiamento da Seguridade Social (COFINS) taxes. The taxation codes are used for fiscal reporting and generating federal electronic fiscal documents (NF-e). You can also set up taxation codes for other tax types. When you set up a taxation code for a tax type, you assign a fiscal value to indicate the type of treatment that applies to taxes, such as taxable, not taxable or exempt, or taxable without credit. When a taxation code is not set up for a tax type, you can set up the fiscal value by selecting the **Without tax credit** and **Exempt** options on the **Sales tax groups** and **Item sales tax groups** pages. Sales taxes are calculated and saved on the **Posted sales tax** page. You can specify a default taxation code for the sales tax code in the **Taxation code** field on the **Sales tax codes** page. You can also specify the taxation code for a sales tax code when you attach the sales tax code to the following:
-   A sales tax group and the sales tax code is exempt.
-   An item sales tax group.

When you create and post tax transactions from sales orders, purchase orders, free text invoices, or project invoice proposals, the taxes are calculated based on either the fiscal value of taxation codes that are selected in the **Fiscal value** field on the **Taxation code** page, or the fiscal value that is determined based on the **Without tax credit** and **Exempt** options on the **Sales tax groups** and **Item sales tax groups** pages. The tax base and tax amount are displayed on the **Posted sales tax** and **Temporary sales tax transactions** pages, as follows:
-   For transactions with taxation codes that have a **1. with credit/debit fiscal** value, or item sales tax groups for which the **Without tax** **credit** option is not selected, the amount that the sales tax is calculated for is equal to the taxable base amount. Sales tax is calculated according to the tax rate and is updated in the **Actual sales tax amount** field.
-   For transactions with taxation codes that have a **2. without credit/debit** **(exempt or not taxable)** fiscal value, or sales tax groups or item sales tax groups for which the **Exempt** option is selected, the exempt base amount is equal to the transaction value, and no tax amount is calculated.
-   For transactions with taxation codes that have a **3. without credit/debit (other) fiscal** value, or item sales tax groups for which the **Without tax credit** option is selected, the other base amount is equal to the transaction value. The sales tax amount is calculated according to the tax rate and is updated in the **Other tax amount** field.

## Brazilian tax types
The following  of tax types are available in the sales tax code configuration.
-   IPI – Imposto sobre Produtos Industrializados (IPI)
-   PIS – Program de Integracao Social (PIS)
-   ICMS – Imposto sobre Circulação de Mercadorias e Serviços (ICMS)
-   COFINS – Contribuição para Financiamento da Seguridade Social (COFINS)
-   ISS – Imposto sobre Serviços (ISS)
-   IRRF – Imposto de Renda Retido na Fonte (IRRF)
-   INSS – Imposto Nacional de Seguridade Social (INSS).
-   Import tax
-   Other taxes
-   Retained INSS
-   CSLL – Contribuição Social sobre Lucro Líquido (CSLL)
-   ICMS-ST – ICMS tributary substitution (ICMS-ST). In addition to this, the user can specify the one of the following calculation methods:
    -   Own operation, IPI, and markup
    -   Own operation only
-   ICMS-DIF – ICMS differential (ICMS-DIF) . This tax type is used to calculate the ICMS differential tax amount under the following scenarios:
    -   Fiscal document is issued to the final consumer located in another state.
    -   Fiscal document is receipted from a different state. Applicable for fixed assets and use and consumption items.

## Examples
For a base transaction amount of BRL 1,000.00 and a tax rate of 18 percent, Microsoft Dynamics 365 for Operations calculates the taxes as follows for the different fiscal values.
| Fiscal value                                    | Amount origin | Actual sales tax amount | Exempt base amount | Other base amount | Other tax amount |
|-------------------------------------------------|---------------|-------------------------|--------------------|-------------------|------------------|
| 1. with credit/debit                            | BRL 1,000.00  | BRL 180.00              |                    |                   |                  |
| 2. without credit/debit (exempt or not taxable) |               |                         | BRL 1,000.00       |                   |                  |
| 3. without credit/debit (other)                 |               |                         |                    | BRL 1,000.00      | BRL 180.00       |

For a base transaction amount of BRL 1,000.00, tax rate of 18 percent, and tax reduction percentage of 40 percent, taxes are calculated as follows for the different fiscal values.
| Fiscal value                                    | Amount origin | Actual sales tax amount | Exempt base amount | Other base amount | Other tax amount |
|-------------------------------------------------|---------------|-------------------------|--------------------|-------------------|------------------|
| 1. with credit/debit                            | BRL 600.00    | BRL 108.00              | BRL 400.00         |                   |                  |
| 2. without credit/debit (exempt or not taxable) |               |                         | BRL 1,000.00       |                   |                  |
| 3. without credit/debit (other)                 |               |                         | BRL 400.00         | BRL 600.00        | BRL 108.00       |

For sales transactions with taxation codes that have a **1. with credit/debit** fiscal value, or item sales tax groups for which the **Without tax credit** option is not selected, the actual sales tax amount is posted to the main accounts for which **Sales tax** and **Sales tax expense** are selected in the **Posting type** field on the **Accounts for automatic transactions** page. For purchase transactions with taxation codes that have a **1. with credit/debit** fiscal value, or item sales tax groups for which the **Without tax credit** option is not selected, the actual sales tax amount is posted to the main accounts for which **Sales tax** is selected in the **Posting type** field on the **Accounts for automatic transactions** page.

## Additional resources
-   [Brazilian tax attributes](latam-bra-tax-attributes.md)
-   [Brazilian tax payments](latam-bra-tax-payments.md)



