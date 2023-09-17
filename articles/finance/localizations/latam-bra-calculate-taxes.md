---
title: Brazil taxes overview
description: Microsoft Dynamics 365 Finance calculates Brazilian taxes based on the tax type that you specify for the sales tax code.
author: AdamTrukawka
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 268704
ms.collection: get-started
---

# Brazil taxes overview

[!include [banner](../includes/banner.md)]

Dynamics 365 Finance calculates Brazilian taxes based on the tax type that you specify for the sales tax code. You can set up and calculate sales taxes for: 

   - Sales
   - Purchases
   - Transfers between fiscal establishments 
   - Delivery of items to a third party
   - Receipt of items from a third party

You can set up taxation codes for the following taxes:

   - Imposto sobre Circulação de Mercadorias e Serviços (ICMS)
   - Imposto sobre Produtos Industrializados (IPI)
   - Program de Integracao Social (PIS)
   - Contribuição para Financiamento da Seguridade Social (COFINS) 

The taxation codes are used for fiscal reporting and generating federal electronic fiscal documents (NF-e). You can set up taxation codes for other tax types. When you set up a taxation code for a tax type, you assign a fiscal value to indicate the type of treatment that applies to taxes. Types of treatment include taxable, not taxable or exempt, or taxable without credit. When a tax type doesn't have a taxation code, select **Without tax credit** and **Exempt**  on the **Sales tax groups** and **Item sales tax groups** pages to set up the fiscal value. Sales taxes are calculated and saved on the **Posted sales tax** page. Specify the default taxation code for a sales tax code in the **Taxation code** field on the **Sales tax codes** page. You can also specify the taxation code for a sales tax code when you attach the sales tax code to:
-   A sales tax group with an exempt sales tax code
-   An item sales tax group

When you create and post tax transactions from sales orders, purchase orders, free text invoices, or project invoice proposals, the taxes are calculated based on one of the following fiscal values:

   - The fiscal value of taxation codes that are selected in the **Fiscal value** field on the **Taxation code** page
   - The fiscal value that is determined based on the **Without tax credit** and **Exempt** options on the **Sales tax groups** and **Item sales tax groups** pages. 

The tax base and tax amount are displayed on the **Posted sales tax** and **Temporary sales tax transactions** pages, as follows:

   - For transactions with taxation codes that have a **1. with credit/debit fiscal** value, or item sales tax groups for which the **Without tax** **credit** option isn't selected, the amount that the sales tax is calculated for is equal to the taxable base amount. Sales tax is calculated according to the tax rate and is updated in the **Actual sales tax amount** field.
   - For transactions with taxation codes that have a **2. without credit/debit** **(exempt or not taxable)** fiscal value, or sales tax groups or item sales tax groups for which the **Exempt** option is selected, the exempt base amount is equal to the transaction value, and no tax amount is calculated.
   - For transactions with taxation codes that have a **3. without credit/debit (other) fiscal** value, or item sales tax groups for which the **Without tax credit** option is selected, the other base amount is equal to the transaction value. The sales tax amount is calculated according to the tax rate and is updated in the **Other tax amount** field.

## Brazilian tax types
The following tax types are available in the sales tax code configuration.
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
-   ICMS-ST – ICMS tributary substitution (ICMS-ST). In addition, the user can specify the one of the following calculation methods:
    -   Own operation, IPI, and markup
    -   Own operation only
-   ICMS-DIF – ICMS differential (ICMS-DIF). This tax type is used to calculate the ICMS differential tax amount under the following scenarios:
    -   Fiscal document is issued to the final consumer located in another state.
    -   Fiscal document is receipted from a different state. Applicable for fixed assets and use and consumption items.

## Examples
For a base transaction amount of BRL 1,000.00 and a tax rate of 18 percent, Finance calculates the taxes as follows for the different fiscal values.

| Fiscal value                                    | Amount origin | Actual sales tax amount | Exempt base amount | Other base amount | Other tax amount |
|-------------------------------------------------|---------------|-------------------------|--------------------|-------------------|------------------|
| 1. with credit/debit                            | BRL 1,000.00  | BRL 180.00              |                    |                   |                  |
| 2. without credit/debit (exempt or not taxable) |               |                         | BRL 1,000.00       |                   |                  |
| 3. without credit/debit (other)                 |               |                         |                    | BRL 1,000.00      | BRL 180.00       |

For a base transaction amount of BRL 1,000.00, tax rate of 18 percent, and tax reduction percentage of 40 percent, taxes are calculated as follows for the different fiscal values.

| Fiscal value                                    | Amount origin | Actual sales tax amount | Exempt base amount | Other base amount | Other tax amount |
|-------------------------------------------------|---------------|-------------------------|--------------------|-------------------|------------------|
| 1. with credit/debit                            | BRL 600.00    | BRL 108.00              | BRL 400.00         |                   |                  |
| 2. without credit/debit (exempt or not taxable) |               |                         | BRL 1,000.00       |                   |                  |
| 3. without credit/debit (other)                 |               |                         | BRL 400.00         | BRL 600.00        | BRL 108.00       |

For sales transactions with taxation codes that have a fiscal value of **1. with credit/debit**, or item sales tax groups where **Without tax credit** isn't selected, the actual sales tax amount is posted to the main accounts where **Sales tax** and **Sales tax expense** are selected on the **Accounts for automatic transactions** page. For purchase transactions with taxation codes that have a fiscal value of **1. with credit/debit**, or item sales tax groups where **Without tax credit** isn't selected, the actual sales tax amount is posted to the main accounts where **Sales tax** is selected in the **Posting type** field on the **Accounts for automatic transactions** page.

## Additional resources
-   [Tax attributes for Brazil](latam-bra-tax-attributes.md)
-   [Tax payments for Brazil](latam-bra-tax-payments.md)
-   [Brazilian withholding taxes](tasks/br-00009-brazilian-withholding-taxes.md)




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
