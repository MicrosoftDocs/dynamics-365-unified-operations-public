---
title: VAT statement details for Estonia
description: Learn how to set up a VAT statement for legal entities in Estonia, including outlines on setting up sales tax authorites and sales tax reporting codes.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Estonia
ms.search.validFrom: 2016-05-31
ms.search.form: TaxPeriod, TaxReportCollection, TaxReportVoucher
---

# VAT statement details for Estonia

[!include [banner](../../includes/banner.md)]

> [!NOTE]
> This feature is replaced by the value-added tax (VAT) declaration functionality. For more information, see [VAT declaration (Estonia)](emea-est-vat-declaration.md).

This article explains how to set up a VAT statement for legal entities in Estonia.

This article includes country/region-specific information about the setup of the VAT statement for legal entities in Estonia only. For more information about the setup of VAT statements, see [VAT reporting for Europe](../europe/emea-vat-reporting.md).

## Set up sales tax authorities
To generate a VAT declaration in the correct format for the appropriate tax authority, set up the report layout for sales tax authorities. On the **Sales tax authorities** page, in the **Report layout** field, select **Estonian report layout**. Select the same sales tax authority for the sales tax settlement period that you use for the sales tax codes.

## Set up sales tax reporting codes
The following example shows how you can use sales tax reporting codes to generate VAT statements.

| Sales tax reporting code | Description                                                                                                                                                                                                                                   | Line on the VAT return (KMD) |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------|
| 1                        | Acts and transactions that are subject to tax at a rate of 20 percent                                                                                                                                                                         | 1                            |
| 11                       | Self-supply of goods or services that are taxable at 20 percent                                                                                                                                                                               | 1.1                          |
| 2                        | Acts and transactions that are subject to tax at a rate of 9 percent                                                                                                                                                                          | 2                            |
| 21                       | Self-supply of goods or services that are taxable at 9 percent                                                                                                                                                                                | 2.1                          |
| 3                        | Acts and transactions that are subject to tax at a rate of 0 percent, inclusive                                                                                                                                                               | 3                            |
| 31                       | Total intra-community supply of goods and services that are provided to a taxable person of another member state/taxable person that has limited liability, inclusive                                                                         | 3.1                          |
| 311                      | Intra-community supply of goods                                                                                                                                                                                                               | 3.1.1                        |
| 32                       | Export of goods, inclusive                                                                                                                                                                                                                    | 3.2                          |
| 321                      | Sale to passengers that involves the return of VAT                                                                                                                                                                                            | 3.2.1                        |
| 5                        | Total amount of input VAT that is subject to deduction according to law, inclusive                                                                                                                                                            | 5                            |
| 51                       | VAT that is paid or payable on import                                                                                                                                                                                                         | 5.1                          |
| 52                       | VAT that is paid or payable on the acquisition of fixed assets                                                                                                                                                                                | 5.2                          |
| 6                        | Total intra-community acquisitions of goods and services that are received from a taxable person of another member state, inclusive                                                                                                           | 6                            |
| 61                       | Intra-community acquisitions of goods                                                                                                                                                                                                         | 6.1                          |
| 7                        | Acquisition of other goods and services that are subject to VAT, inclusive                                                                                                                                                                    | 7                            |
| 71                       | Acquisition of immovables and metal waste that are taxable by special arrangements for the imposition of VAT on immovables, metal waste, and precious metals (VAT Act §41)                                                                    | 7.1                          |
| 8                        | Supply that is exempt from tax                                                                                                                                                                                                                | 8                            |
| 9                        | Supply of goods that are taxable by special arrangements for the imposition of VAT on immovable, metal waste, and precious metals (VAT Act §1 41), and the taxable value of goods that will be installed or assembled in another member state | 9                            |
| 1010                     | Adjustments (+)                                                                                                                                                                                                                               | 10                           |
| 1011                     | Adjustments (–)                                                                                                                                                                                                                               | 11                           |

## Set up VAT declaration tax codes
Use the VAT declaration tax codes to map sales tax codes to values that the declaration requires, such as 20, 9, 20erikord, or 9erikord. For each tax code, you can also specify optional sales and purchase comment codes, like 01, 02, or 03 for sales, and 11 or 12 for purchases. To set up VAT declaration tax codes, set the following fields on the **VAT declaration tax code** page.

| Field                    | Description                                                                                   |
|--------------------------|-----------------------------------------------------------------------------------------------|
| Sales tax code           | Select the sales tax code for sales or purchase invoices.                        |
| VAT declaration tax code | Enter the code that appears on the declaration.                                           |
| Special code             | Enter the comment code that appears in the sales and purchase annexes of the declaration. |

## Configure the Electronic reporting model and format for the report
To review or change the VAT statement configuration, select **VAT declaration model** on the **Reporting configurations** page. This model is used for Austria, Czech Republic, Estonia, Finland, Latvia, and Lithuania. It provides aggregate tax data that's required for the VAT declaration. Select **Designer** to review or change the model. To review or change the VAT statement format, select **VAT declaration model** on the **Reporting configurations** page, and then select **Designer**.

## Generate a VAT statement
At the end of the VAT reporting period, the Settle and post sales tax process calculates statement line amounts for the definition of sales tax reporting codes that you created.

-   Select the **Date of Vat register** field on the **General ledger parameters** page if the company must use the date of the VAT register instead of the tax transaction date.
-   Select **Estonian report layout** as the report layout of the sales tax authority that you configure for the settlement period.
-   If you select the **Conditional sales tax** field on the **General ledger parameters** page, the Estonian VAT declaration supports the Cash accounting scheme, and you must complete the Sales and Purchase annexes.

To generate a VAT XML file, select one or more vouchers on the **Sales tax payments** page, and then select **Export VAT XML file**. **Notes:**

-   You can select more than one sales tax payment line for each requested period.
-   If the selected lines occurred in more than one settlement period, you receive an error message.

Then set the following fields.

| Field                                          | Description                                                                                                                         |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Format mapping                                 | Specify the name and path of the exported XML file.                                                                                 |
| Name                                           | Specify the employee who creates the declaration.                                                                                   |
| Declaration period type                        | Select one of the following declaration types: **Normal** or **Bankruptcy**.                                                        |
| Invoice threshold                              | Specify the minimum total net amount of invoices per customer or vendor in a reporting period that must be included in the annexes. |
| Declaration (In the **Export** field group)    | Set this option to **Yes** to export the declaration body.                                                                          |
| Sales annex (In the **Export** field group)    | Set this option to **Yes** to export invoices and credit notes in the Sales annex.                                                  |
| Purchase annex (In the **Export** field group) | Set this option to **Yes** to export invoices and credit notes in the Purchase annex.                                               |

> [!NOTE]
> The system automatically enters the field values in the **Period** field group, based on options on the **Sales tax settlement periods** page. To set up sales tax settlement periods, go to the **Sales tax settlement periods** page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
