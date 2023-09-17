---
title: VAT statement for Norway
description: This article explains how to set up and generate the VAT statement for legal entities that have a primary address in Norway.
author: EricWangChen
ms.date: 03/21/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Norway
ms.author: wangchen
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update
---

# VAT statement for Norway

[!include [banner](../includes/banner.md)]

This article includes country/region-specific information about how to set up the value-added tax (VAT) statement for legal entities that have a primary address in Norway. For more information about general VAT reporting, see [VAT reporting for Europe](emea-vat-reporting.md).

> [!NOTE]
> As part of the modernization of VAT systems, the Norwegian Tax Administration introduced a new format for VAT return reporting for periods that start on or after January 1, 2022. VAT returns for periods before that date, and corrections to those VAT returns, must be reported in the format that is described in this article. For more information about the new VAT return format, see [VAT return with direct submission to Altinn](emea-nor-vat-return.md).

## Set up sales tax authorities
To generate a VAT declaration in the required format for a specific tax authority, you must set up the report layout for the sales tax authorities.

1. On the **Sales tax authorities** page, in the **Report layout** field, select **Norwegian report format**.
2. Select the same sales tax authority for the sales tax settlement period that you will use for the sales tax codes.

## Set up sales tax reporting codes
The following example shows how you can set up sales tax reporting codes to generate the VAT statement.

For users in legal entities in Norway, the following sales tax reporting codes can be created and assigned to sales tax codes.

| Reporting code | Description                                                                        | Select the reporting code in this field on the Report setup tab or Report setup - credit note tab on the Sales tax codes page |
|--------------|--------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| 11             | Total turnover not covered by the VAT Act                                          | **Taxable sales** or **Tax-free sales**, depending on the type of sales |
| 31             | Domestic turnover and withdrawal, and calculated VAT 25 %, basis                   | **Taxable sales** |
| 32             | Domestic turnover and withdrawal, and calculated VAT 25 %, calc. tax               | **Sales tax payable** |
| 41             | Domestic turnover and withdrawal, and calculated VAT 15%, basis                    | **Taxable sales** |
| 42             | Domestic turnover and withdrawal, and calculated VAT 15%, calc. tax                | **Sales tax payable** |
| 51             | Domestic turnover and withdrawal, and calculated VAT 10 %, basis                   | **Taxable sales** |
| 52             | Domestic turnover and withdrawal, and calculated VAT 10 %, calc. tax               | **Sales tax payable** |
| 61             | Zero rated domestic turnover and withdrawal, basis                                 | **Taxable sales** |
| 71             | Domestic turnover subject to reverse charge (emission trading and gold), basis     | **Taxable import** |
| 72             | Domestic turnover subject to reverse charge (emission trading and gold), calc. tax | **Use tax** |
| 81             | Total zero rated turnover due to export of goods and services, basis               | **Tax-free sales** |
| 91             | Import of goods, and calculated VAT 25 %, basis                                    | **Taxable import** |
| 92             | Import of goods, and calculated VAT 25 %, calc. tax                                | **Use tax**         |
| 93             | Offset for the 92                                                                  | **Offset use tax**         |
| 101            | Import of goods, and calculated VAT 15 %, basis                                    | **Taxable import** |
| 102            | Import of goods, and calculated VAT 15 %, calc. tax                                | **Use tax** |
| 103            | Offset for the 102                                                                 | **Offset use tax** |
| 111            | Import of goods not subject to VAT, basis                                          | **Tax-free purchase** |
| 121            | Purchase of intangible services from abroad, and calculated VAT 25 %, basis        | **Taxable import** |
| 122            | Purchase of intangible services from abroad, and calculated VAT 25 %, calc. tax    | **Use tax** |
| 123            | Offset for the 122                                                                 | **Offset use tax** |
| 131            | Domestic purchases subject to reverse charge, and calculated VAT 25 %, basis       | **Taxable import** |
| 132            | Domestic purchases subject to reverse charge, and calculated VAT 25 %, calc. tax   | **Use tax** |
| 133            | Offset for the 132                                                                 | **Offset use tax** |
| 142            | Deductible domestic input VAT, 25 %, calc. tax                                     | **Sales tax receivable** |
| 152            | Deductible domestic input VAT, 15 %, calc. tax                                     | **Sales tax receivable** |
| 162            | Deductible domestic input VAT, 10 %, calc. tax                                     | **Sales tax receivable** |
| 172            | Deductible import VAT, 25 %, calc. tax                                             | **Offset use tax** if you aren't using reporting codes 93, 123, or 133. |
| 182            | Deductible import VAT, 15 %, calc. tax                                             | **Offset use tax** if you aren't using reporting code 103. |

## Set up the sales tax period code
On the **Sales tax settlement periods** page, create a list of periods. In the **Sales tax period code** field, set the period codes according to the submission periods. These period codes should be aligned with the values that the tax authorities provided. The values in this field will be used when an XML file is generated.

Here is an example for bi-monthly reporting.

|             Period               | Sales tax period code |
|----------------------------------|-----------------------|
| First period – January/February  | 014                   |
| Second period – March/April      | 024                   |
| Third period – May/June          | 034                   |
| Fourth period – July/August      | 044                   |
| Fifth period – September/October | 054                   |
| Sixth period – November/December | 064                   |

## Configure the ER model and format for the report
To review or change the reporting formats, you must use Electronic reporting (ER) functionality. You can find the VAT statement format for legal entities that have a primary address in Norway on the **Configurations** page (**Organization administration** > **Electronic reporting** > **Configurations**). In the tree of ER models, expand the **Vat declaration model** node, and then select **VAT declaration (NO)**.

You can use the designer to review or change the configuration that you selected in the model tree. For more information, see [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

> [!NOTE]
> The same VAT declaration model is used for Austria, Czech Republic, Estonia, Finland, Latvia, Lithuania, and Norway. This model aggregates tax data that is required for VAT declaration.

## Generate the VAT statement
1. On the **Report sales tax for settlement period** page, enter values in the **Settlement period**, **From date**, and **Sales tax payment version** fields.
2. Click **OK**.
3. In the **Format mapping** field, select one of the following options:

    - **VAT declaration (NO)** – Generate an XML file.
    - **Sales tax report (NO)** – Print the report in Microsoft Excel.

4. Before the XML file can be created, you must enter values in the following fields:

    - **Message type** – Select **Main**, **Additional**, or **Correction**.
    - **KID number**
    - **Industry type**
    - **Explanation**
  
### Create a report after a sales tax payment update
1. On the **Sales tax payments** page, select the applicable vouchers, and then click **Export VAT file**.
2. In the **Format mapping** field, select one of the following options to specify the type of output file:

    - **VAT declaration (NO)** – Generate an XML file.
    - **Sales tax report (NO)** – Print the report in Microsoft Excel.

> [!NOTE]
> You can combine several sales tax payments and print one combined report/XML file that includes summarized data for all selected records. You can combine only records that are related to one settlement period, and that have the same **From date** and **To date** values. For example, you can combine an **Original version** record and its **Corrections/Latest corrections** record.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
