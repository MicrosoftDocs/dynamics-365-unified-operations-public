---
# required metadata

title: VAT statement details for Austria
description: This topic explains how to set up the VAT statement for legal entities in Austria.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: TaxAuthority, TaxReportCollection, TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 264334
ms.assetid: 2542c9e1-ed47-416f-9773-7b87eef66e78
ms.search.region: Austria
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# VAT statement details for Austria

This topic explains how to set up the VAT statement for legal entities in Austria.

This topic includes country/region-specific information about the setup of the value-added tax (VAT) statement for legal entities in Austria only. For more information about the setup of the VAT statement, see [VAT reporting](emea-vat-reporting.md). The rest of this topic shows how to set up sales tax codes and sales tax reporting codes for the Austrian VAT declaration, so that VAT statements can be generated.

## Set up sales tax authorities
To generate a VAT declaration in the correct format for the appropriate tax authority, you must set up the report layout for the sales tax authorities. On the **Sales tax authorities** page, in the **Report layout** field, select **Austrian report layout**. Select the same sales tax authority for the sales tax settlement period that will be used in the sales tax codes.

## Set up sales tax codes and sales tax reporting codes for VAT reporting
Here is an example that shows how you might set up sales tax codes and sales tax reporting codes to generate a VAT statement.

| Sales tax code | Percentage | Description                                                                                                                  |
|----------------|------------|------------------------------------------------------------------------------------------------------------------------------|
| AT20           | 20         | Included in groups for Austrian customers and vendors, and European Union (EU) vendors. For EU vendors, **Use tax**=**Yes**. |
| AT13           | 13         | Included in groups for Austrian customers and vendors, and EU vendors. For EU vendors, **Use tax**=**Yes**.                  |
| AT10           | 10         | Included in groups for Austrian customers and vendors, and EU vendors. For EU vendors, **Use tax**=**Yes**.                  |
| ATImp20        | 20         | Included in a group for non-EU vendors.                                                                                      |
| ATImp13        | 13         | Included in a group for non-EU vendors.                                                                                      |
| ATImp10        | 10         | Included in a group for non-EU vendors.                                                                                      |
| ATRC20         | 20         | Included in a group for vendors with reverse charge. **Use tax**=**Yes**.                                                    |
| ATRC13         | 13         | Included in a group for vendors with reverse charge. **Use tax**=**Yes**.                                                    |
| ATRC10         | 10         | Included in a group for vendors with reverse charge. **Use tax**=**Yes**.                                                    |

Here is an example of sales tax reporting codes.

| Sales tax reporting code | Description                                                                   | Corresponding box in the declaration |
|--------------------------|-------------------------------------------------------------------------------|--------------------------------------|
| 1022                     | Tax base amount by domestic sales that have a standard tax rate of 20 percent | 022                                  |
| 1122                     | Tax amount by domestic sales that have a standard tax rate of 20 percent      | 022                                  |
| 1029                     | Tax base amount by domestic sales that have a reduced tax rate of 10 percent  | 029                                  |
| 1129                     | Tax amount by domestic sales that have a reduced tax rate of 10 percent       | 029                                  |
| 1006                     | Tax base amount by domestic sales that have a reduced tax rate of 13 percent  | 006                                  |
| 1106                     | Tax amount by domestic sales that have a reduced tax rate of 13 percent       | 006                                  |
| 1072                     | Tax base amount by EU purchases that have a standard tax rate of 20 percent   | 072                                  |
| 1172                     | Tax amount by EU purchases that have a standard tax rate of 20 percent        | 072                                  |
| 1073                     | Tax base amount by EU purchases that have a reduced tax rate of 10 percent    | 073                                  |
| 1173                     | Tax amount by EU purchases that have a reduced tax rate of 10 percent         | 073                                  |
| 1008                     | Tax base amount by EU purchases that have a reduced tax rate of 13 percent    | 008                                  |
| 1108                     | Tax amount by EU purchases that have a reduced tax rate of 13 percent         | 008                                  |
| 1161                     | Tax amount by import purchases                                                | 061                                  |
| 1160                     | Tax amount by purchases                                                       | 060                                  |
| 1165                     | Tax receivable by EU purchases                                                | 065                                  |
| 1132                     | Tax liability pursuant to §19 1d payable                                      | 032                                  |
| 1189                     | Tax liability pursuant to §19 1d receivable                                   | 089                                  |

To set up an assignment of sales tax reporting codes to sales tax codes, go to **Sales tax codes** &gt; ****Report setup****. Here is an example of an assignment of sales tax reporting codes to sales tax codes.

| Sales tax code | Taxable sales | Sales tax payable | Taxable purchases | Sales tax receivable | Taxable import | Use tax | Offset use tax |
|----------------|---------------|-------------------|-------------------|----------------------|----------------|---------|----------------|
| AT20           | 1022          | 1122              |                   | 1160                 | 1072           | 1172    | 1165           |
| AT13           | 1006          | 1106              |                   | 1160                 | 1008           | 1108    | 1165           |
| AT10           | 1029          | 1129              |                   | 1160                 | 1073           | 1173    | 1165           |
| ATImp20        |               |                   |                   |                      | 1061           |         | 1161           |
| ATImp13        |               |                   |                   |                      | 1061           |         | 1161           |
| ATImp10        |               |                   |                   |                      | 1061           |         | 1161           |
| ATRC20         |               |                   |                   |                      |                | 1132    | 1189           |
| ATRC13         |               |                   |                   |                      |                | 1132    | 1189           |
| ATRC10         |               |                   |                   |                      |                | 1132    | 1189           |

**Note:** The preceding configuration is an example and depends on the structure of the sales tax codes that are used, as defined by the user. To have values calculated and transferred to the declaration, for each tax code that is used in the sales tax payment process, you must set a relevant sales tax reporting code in one or multiple fields on the **Report setup** tab.

## Configure the Electronic reporting model and format for the report
To review or change the VAT statement configuration for legal entities in Austria, on the **Reporting configurations** page, select **VAT declaration model** in the list of models. This model is used for Austria, Czech Republic, Estonia, Finland, Latvia, and Lithuania, and for aggregate tax data that is required for the VAT declaration. On the Action Pane, click **Designer** to review or change the model. To review or change the VAT statement format for legal entities in Austria, on the **Reporting configurations** page, select **VAT declaration model** in the list of models, and then select **U30** below **VAT declaration model**. On the Action Pane, click **Designer** to review or change the format.

## Generate a VAT statement
At the end of the VAT reporting period, run **Settle and post** **sales tax** to calculate statement line amounts for the definition of sales tax reporting codes that you created. The following table describes the fields that you must set.

|Field|Description|
|-----|-----------|
|Settlement period|Select the applicable reporting period.|
|From date|Enter the first day of the sales tax settlement period to calculate sales tax for. This value corresponds to the date in the From field on the Sales tax settlement periods page.|
|Transaction date|Enter the date when the sales tax report is calculated. The default value is the current date. The end date of the settlement period that is shown in the From field corresponds to the To field on the Sales tax settlement periods page. The sales tax payment is calculated for all transactions that were posted during the settlement period.|
|Sales tax payment version|Select the type of transactions to include in the sales tax payment calculation: 
**Original** – Include sales tax transactions of the first posted settlement calculation for the period.
**Latest corrections** – Include sales tax transactions that are included in the most recent settlement calculation for the period.|
|Format mapping|Specify U30.|

To generate a VAT XML file, use the **Report sales tax for settlement period** page.

