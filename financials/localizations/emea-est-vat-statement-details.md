---
# required metadata

title: VAT statement details for Estonia
description: This topic explains how to set up a VAT statement for legal entities in Estonia.
author: ShylaThompson
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: TaxPeriod, TaxReportCollection, TaxReportVoucher
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 266904
ms.assetid: 7a804f8e-3595-463c-8371-21425c992c91
ms.search.region: Estonia
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# VAT statement details for Estonia

This topic explains how to set up a VAT statement for legal entities in Estonia.

This topic includes country/region-specific information about the setup of the value-added tax (VAT) statement for legal entities in Estonia only. For more information about the setup of VAT statements, see [VAT reporting](emea-vat-reporting.md).

## Set up sales tax authorities
To generate a VAT declaration in the correct format for the appropriate tax authority, you must set up the report layout for sales tax authorities. On the **Sales tax authorities** page, in the **Report layout** field, select **Estonian report layout**. Select the same sales tax authority for the sales tax settlement period that will be used for the sales tax codes.

## Set up sales tax reporting codes
Here is an example that shows how you can use sales tax reporting codes to generate VAT statements.

| Sales tax reporting code | Description                                                                                                                                                                                                                                   | Line on the VAT return (KMD) |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------|
| 1                        | Acts and transactions that are subject to tax at a rate of 20 percent                                                                                                                                                                         | 1                            |
| 11                       | Self-supply of goods or services that are taxable at 20 percent                                                                                                                                                                               | 1.1                          |
| 2                        | Acts and transactions that are subject to tax at a rate of 9 percent                                                                                                                                                                          | 2                            |
| 21                       | Self-supply of goods or services that are taxable at 9 percent                                                                                                                                                                                | 2.1                          |
| 3                        | Acts and transactions that are subject to tax at a rate of 0 percent, inclusive                                                                                                                                                               | 3                            |
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
| 71                       | Acquisition of immovables and metal waste that are taxable by special arrangements for the imposition of VAT on immovables, metal waste, and precious metals (VAT Act §41)                                                                    | 7.1                          |
| 8                        | Supply that is exempt from tax                                                                                                                                                                                                                | 8                            |
| 9                        | Supply of goods that are taxable by special arrangements for the imposition of VAT on immovable, metal waste, and precious metals (VAT Act §1 41), and the taxable value of goods that will be installed or assembled in another member state | 9                            |
| 1010                     | Adjustments (+)                                                                                                                                                                                                                               | 10                           |
| 1011                     | Adjustments (–)                                                                                                                                                                                                                               | 11                           |

## Set up VAT declaration tax codes
The VAT declaration tax codes are used to map sales tax codes to values that are required in the declaration (20, 9, 20erikord, or 9erikord). In addition, for every tax code, you can specify optional sales and purchase comment codes (01, 02, or 03 for sales, and 11 or 12 for purchases). To set up VAT declaration tax codes, on the **VAT declaration tax code** page, set the following fields.

| Field                    | Description                                                                                   |
|--------------------------|-----------------------------------------------------------------------------------------------|
| Sales tax code           | Select the sales tax code that is used for sales or purchase invoices.                        |
| VAT declaration tax code | Enter the code that will appear on the declaration.                                           |
| Special code             | Enter the comment code that will appear in the sales and purchase annexes of the declaration. |

## Configure the Electronic reporting model and format for the report
To review or change the VAT statement configuration, on the **Reporting configurations** page, select **VAT declaration model**. This same model is used for Austria, Czech Republic, Estonia, Finland, Latvia, and Lithuania, and for aggregate tax data that is required for the VAT declaration. Click **Designer** to review or change the model. To review or change the VAT statement format, on the **Reporting configurations** page, select **VAT declaration model**, and then click **Designer**.

## Generate a VAT statement
At the end of the VAT reporting period, the Settle and post sales tax process calculates statement line amounts for the definition of sales tax reporting codes that you created.

-   If the company must use the date of the VAT register instead of the tax transaction date, the **Date of Vat register** field on the **General ledger parameters** page must be selected.
-   **Estonian report layout** must be selected as the report layout of the sales tax authority that is configured for the settlement period.
-   If the **Conditional sales tax** field is selected on the **General ledger parameters** page, the Estonian VAT declaration will support the Cash accounting scheme, and the Sales and Purchase annexes must be completed.

To generate a VAT XML file, on the **Sales tax payments** page, select one or more vouchers, and then click **Export VAT XML file**. **Notes:**

-   You can select more than one sales tax payment line for each requested period.
-   If the selected lines occurred in more than one settlement period, you receive an error message.

Then set the following fields.

| Field                                          | Description                                                                                                                         |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Format mapping                                 | Specify the name and path of the exported XML file.                                                                                 |
| Name                                           | Specify the employee who creates the declaration.                                                                                   |
| Declaration period type                        | Select one of the following declaration types: **Normal** or **Bankruptcy**.                                                        |
| Invoice threshold                              | Specify the minimum total net amount of invoices per customer or vendor in a reporting period that must be included in the annexes. |
| Declaration (In the **Export** field group)    | Set this option to **Yes** to export the declaration body.                                                                          |
| Sales annex (In the **Export** field group)    | Set this option to **Yes** to export invoices and credit notes in the Sales annex.                                                  |
| Purchase annex (In the **Export** field group) | Set this option to **Yes** to export invoices and credit notes in the Purchase annex.                                               |

**Note:** The field values in the **Period** field group are entered automatically, based on options on the **Sales tax settlement periods** page. To set up sales tax settlement periods, go to the **Sales tax settlement periods** page.

