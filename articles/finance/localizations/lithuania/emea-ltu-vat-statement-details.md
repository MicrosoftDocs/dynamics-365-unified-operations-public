---
title: VAT statement details for Lithuania
description: Learn how to set up a VAT statement for legal entities in Lithuania in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/29/2025
ms.reviewer: johnmichalak
ms.search.region: Lithuania
ms.search.validFrom: 2016-05-31
ms.search.form: TaxAuthority, TaxReportCollection, TaxReportVoucher, TaxTable
---

# VAT statement details for Lithuania

[!include [banner](../../includes/banner.md)]

This article explains how to set up a VAT statement for legal entities in Lithuania in Microsoft Dynamics 365 Finance.

> [!NOTE]
> This feature has been replaced with the value-added tax (VAT) declaration functionality. For more information, see [VAT declaration (Lithuania)](emea-ltu-vat-declaration-lithuania.md).

This article includes country/region-specific information about the setup of the value-added tax (VAT) statement for legal entities in Lithuania only. Learn more at [VAT reporting for Europe](../europe/emea-vat-reporting.md).

## Set up sales tax authorities
To generate a VAT declaration in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities. On the **Sales tax authorities** page, in the **Report layout** field, select **Default**. Select the same sales tax authority for the sales tax settlement period that will be used for sales tax codes.

## Set up sales tax reporting codes
Here is an example that show how you can use sales tax reporting codes to generate a VAT statement. The following sales tax reporting codes can be created and used on the **Report setup** FastTab of the **Sales tax codes** page.

| Sales tax reporting code | Description                                                           | Box name on the report |
|--------------------------|-----------------------------------------------------------------------|------------------------|
| 11                       | Tax base amount of sales-taxable sales                                | E11                    |
| 12                       | Tax base amount of sales-taxable sales per paragraph 96               | E12                    |
| 13                       | Tax base amount of non-taxable sales                                  | E13                    |
| 14                       | Consumption for company requirements                                  | E14                    |
| 15                       | Fixed asset production                                                | E15                    |
| 16                       | Margin of deals that have a special taxation schema                   | E16                    |
| 17                       | Export of goods (0 percent)                                           | E17                    |
| 18                       | Sales to European Union (EU) VAT payers (0 percent)                   | E18                    |
| 19                       | Other sales that have 0-percent VAT                                   | E19                    |
| 20                       | Non-taxable sales outside Lithuanian borders                          | E20                    |
| 21                       | Amount of goods that are purchased from the EU                        | E21                    |
| 22                       | Amount of goods that are purchased from the EU (triangular trade)     | E22                    |
| 23                       | Amount of services that are purchased from foreign countries/regions  | E23                    |
| 24                       | Amount of services that are purchased from EU VAT payers.             | E24                    |
| 25                       | VAT amount of purchased goods and services                            | E25                    |
| 26                       | Paid import VAT                                                       | E26                    |
| 27                       | Import VAT that will be deducted under the control of the tax service | E27                    |
| 29                       | Tax amount of sales that have a standard tax rate                     | E29                    |
| 30                       | Tax amount of sales that have a reduced tax rate of 9 percent         | E30                    |
| 31                       | Tax amount of sales that have a reduced tax rate of 5 percent         | E31                    |
| 32                       | Tax amount of sales per paragraph 95                                  | E32                    |
| 33                       | Tax amount of sales per paragraph 96                                  | E33                    |
| 34                       | Sales VAT of goods that are purchased in the EU                       | E34                    |
| 35                       | Deductible purchase and import VAT amount                             | E35                    |

## Configure the electronic reporting model and format for the report

To configure the electronic reporting model and format for the report, follow these steps.

1. To review or change the VAT statement configuration, on the **Reporting configurations** page, select **VAT declaration model**. 
1. Select **Designer** to review or change the model.
1. To review or change the VAT statement format, on the **Reporting configurations** page, select **VAT declaration model**, and then select **Designer**.

## Generate a VAT statement

To generate a VAT XML file, on the **Sales tax payments** page, select one or more vouchers, and then select **Export VAT XML file**.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
