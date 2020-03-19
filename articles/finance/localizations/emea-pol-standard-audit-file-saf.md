---
# required metadata

title: Standard audit file (SAF) for Poland
description: Users in legal entities in Poland can generate a Standard Audit File for Tax (SAF-T) in XML format. This topic provides information about the formats for Poland. 
author: LizaGolub
manager: AnnBe
ms.date: 02/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 274193
ms.assetid: b85c4019-f682-45bf-9a0d-c7549a2f1274
ms.search.region: Poland
# ms.search.industry: 
ms.author: v-elgolu
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Standard audit file (SAF) for Poland

[!include [banner](../includes/banner.md)]

Users in legal entities in Poland can generate a Standard Audit File for Tax (SAF-T) in XML format. This topic provides information about the formats for Poland. 

Users in legal entities in Poland can generate a Standard Audit File for Tax (SAF-T) in XML format. This document provides information about the formats for Poland. This document refers to functionality that has not yet been released.

## Set up the Standard Audit File for Tax for Poland
To specify an Electronic reporting (ER) format for each SAF-T scheme, click **General ledger > Ledger setup > General ledger parameters**, and then, on the **Standard Audit File for Taxes (SAF-T)** tab, set up a specific format for each of the following schemes:

-   SAF Accounting books
-   SAF Bank statements
-   SAF Inventory
-   SAF VAT sale and purchase registers
-   SAF VAT invoices

Each ER format should be predefined and can be updated in ER.

## Generate a SAF Accounting books file
To generate a SAF Accounting books file, click **General ledger > Inquiries and reports > Standard Audit File for Tax (SAF-T) > SAF Accounting books**, and set the following parameters.

|Parameter                                        |  Description            |
|-------------------------------------------------|-------------------------|
| **From date**                                   | Specify the first date to export reporting data for. |
| **To date**                                     | Specify the last date to export reporting data for.  |
| **Authority identification**                    | Specify the identifier of the tax authority to use in the export file.|
| **Posting layer**                               | Select one or several posting layers to consider transactions from. This parameter affets all parts of the report. |
| **Should opening balance be shown by turnover** | If this parameter is selected, opening balance is affected by accumulated turnover. This parameter affects only the ZOiS export file part. |
| **Separate balance**                            | This parameter can be considered for main accounts where the corresponding parameter is marked. This parameter affects only the ZOiS export file part.     |
| **Closing transactions**                        | If this parameter is selected, closing transactions will be included in the data that is exported. This parameter affects only the ZOiS export file part. |

This regulatory report must be provided by request and includes accounting data for the reporting period. It includes accounting data in selected posting layer(s) by all the main accounts which have non-zero aggregated turnover or transactions in the reporting period.

## Generate a SAF Bank statement file
To generate a SAF Bank statement file, click **General ledger > Inquiries and reports > Standard Audit File for Tax (SAF-T) > SAF Bank statement**, and set the following parameters.

| Parameter                    | Description                                                                        |
|------------------------------|------------------------------------------------------------------------------------|
| **From date**                | Specify the first date to export reporting data for.                               |
| **To date**                  | Specify the last date to export reporting data for.                                |
| **Authority identification** | In the list, select the identifier of the tax authority to use in the export file. |
| **Bank account**             | Specify the bank account to export transactions for.                               |

 

## Generate a SAF Inventory file
To generate a SAF Inventory file, click **General ledger > Inquiries and reports > Standard Audit File for Tax (SAF-T) > SAF Inventory**, and set the following parameters.

| Parameter                    | Description                                                                        |
|------------------------------|------------------------------------------------------------------------------------|
| **From date**                | Specify the first date to export reporting data for.                               |
| **To date**                  | Specify the last date to export reporting data for.                                |
| **Authority identification** | In the list, select the identifier of the tax authority to use in the export file. |
| **Warehouse**                | Specify the warehouse to export transactions for.                                  |

### 

## Generate a SAF VAT sales and purchase register
Before you can generate a SAF value-added tax (VAT) sales and purchase register, you must complete the following additional setup:

-   Set up sales tax authorities.
-   Set up sales tax codes for VAT reporting.
-   Set up sales tax codes.
-   Configure the ER model, and format for the report.

For more information about the setup of VAT statements, see [VAT reporting for Europe](emea-vat-reporting.md).

### Set up sales tax authorities

For general information about how to set up a sales tax authority, see [Set up sales tax authorities](../general-ledger/tasks/set-up-sales-tax-authorities.md). To generate a SAF VAT sales and purchase register in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities. On the **Sales tax authorities** page (**Tax > Indirect taxes > Sales tax > Sales tax authorities**), set the **Report layout** field to **Default**. Select the same sales tax authority for the sales tax settlement period that will be used for the sales tax codes.

### Set up sales tax codes and sales tax reporting codes

A reporting code is an integer value. Reporting codes should be numbered according to the company's rules. However, we recommend that you vary the codes by tax direction. For example, use a five-digit code, and set the codes for all outgoing transactions, which should be reflected in the first part of the VAT scheme, so that they are less than or equal to 19999. Set the codes for all incoming transactions, which should be reflected in the second part of the VAT scheme, so that they are more than or equal to 20000. In this way, you simplify the setup for reports and for data export that is based on tax transactions that are aggregated by reporting codes. Here is an example that shows how you can use sales tax reporting codes to generate a SAF VAT sales and purchase register. For this example, reporting codes are in the format *ABBCC*. This format consists of the following parts:

-   **A** - The transaction direction. The value is **1** for outgoing, **2** for incoming, **3** for corrections.
-   **BB** - The tax code. The numbering is sequential among all tax codes.
-   **CC**-   The transaction type number within a tax code. See the following table.

| Transaction type                      | Transaction type number     |
|---------------------------------------|-----------------------------|
| **Taxable Sales**                     | 01                          |
| **Tax-free sales**                    | 02                          |
| **Sales tax payable**                 | 03                          |
| **Taxable sales credit note**         | 04                          |
| **Tax exempt sales credit note**      | 05                          |
| **Sales tax on sales credit note**    | 06                          |
| **Taxable purchases**                 | 07                          |
| **Tax-free purchase**                 | 08                          |
| **Sales tax receivable**              | 09                          |
| **Taxable import**                    | 10                          |
| **Offset taxable import**             | 11                          |
| **Use tax**                           | 12                          |
| **Offset use tax**                    | 13                          |
| **Taxable purchase credit note**      | 14                          |
| **Tax exempt purchase credit note**   | 15                          |
| **Sales tax on purchase credit note** | 16                          |
| **Taxable import credit note**        | 17                          |
| **Offset taxable import credit note** | 18                          |

The following table shows the sales tax codes and sales tax reporting codes for this example.

<table width="100%">
<tbody>
<tr>
<td><strong>Sales tax code</strong></td>
<td><strong>Sales tax reporting code</strong></td>
<td><strong>Description</strong></td>
<td><strong>Tag name in SAF-T VAT</strong></td>
<td><strong>Sign in SAF-T VAT</strong></td>
</tr>
<tr>
<td rowspan="4"><strong>ExportCust</strong></td>
<td>10101</td>
<td>Taxable sales</td>
<td>K_11</td>
<td>-</td>
</tr>
<tr>
<td>10102</td>
<td>Tax-free sale</td>
<td>K_11</td>
<td>-</td>
</tr>
<tr>
<td>10104</td>
<td>Taxable sales credit note</td>
<td>K_11</td>
<td>-</td>
</tr>
<tr>
<td>10105</td>
<td>Tax exempt sales credit note</td>
<td>K_11</td>
<td>-</td>
</tr>
<tr>
<td rowspan="2"><strong>Art100</strong></td>
<td>10201</td>
<td>Taxable sales</td>
<td>K_12</td>
<td>-</td>
</tr>
<tr>
<td>10204</td>
<td>Taxable sales credit note</td>
<td>K_12</td>
<td>-</td>
</tr>
<tr>
<td rowspan="5"><strong>VAT22_23</strong></td>
<td>10301</td>
<td>Taxable sales</td>
<td>K_19</td>
<td>-</td>
</tr>
<tr>
<td>10302</td>
<td>Tax-free sale</td>
<td>K_10</td>
<td>-</td>
</tr>
<tr>
<td>10303</td>
<td>Sales tax payable</td>
<td>K_20</td>
<td>-</td>
</tr>
<tr>
<td>10304</td>
<td>Taxable sales credit note</td>
<td>K_19</td>
<td>-</td>
</tr>
<tr>
<td>10306</td>
<td>Sales tax on sales credit note</td>
<td>K_20</td>
<td>-</td>
</tr>
<tr>
<td rowspan="5"><strong>VAT7_8</strong></td>
<td>10401</td>
<td>Taxable sales</td>
<td>K_17</td>
<td>-</td>
</tr>
<tr>
<td>10402</td>
<td>Tax-free sale</td>
<td>K_10</td>
<td>-</td>
</tr>
<tr>
<td>10403</td>
<td>Sales tax payable</td>
<td>K_18</td>
<td>-</td>
</tr>
<tr>
<td>10404</td>
<td>Taxable sales credit note</td>
<td>K_17</td>
<td>-</td>
</tr>
<tr>
<td>10406</td>
<td>Sales tax on sales credit note</td>
<td>K_18</td>
<td>-</td>
</tr>
<tr>
<td rowspan="5"><strong>VAT5</strong></td>
<td>10501</td>
<td>Taxable sales</td>
<td>K_15</td>
<td>-</td>
</tr>
<tr>
<td>10502</td>
<td>Tax-free sale</td>
<td>K_10</td>
<td>-</td>
</tr>
<tr>
<td>10503</td>
<td>Sales tax payable</td>
<td>K_16</td>
<td>-</td>
</tr>
<tr>
<td>10504</td>
<td>Taxable sales credit note</td>
<td>K_15</td>
<td>-</td>
</tr>
<tr>
<td>10506</td>
<td>Sales tax on sales credit note</td>
<td>K_16</td>
<td>-</td>
</tr>
<tr>
<td rowspan="3"><strong>VAT0</strong></td>
<td>10601</td>
<td>Taxable sales</td>
<td>K_13</td>
<td>-</td>
</tr>
<tr>
<td>10602</td>
<td>Tax-free sale</td>
<td>K_10</td>
<td>-</td>
</tr>
<tr>
<td>10604</td>
<td>Taxable sales credit note</td>
<td>K_13</td>
<td>-</td>
</tr>
<tr>
<td rowspan="4"><strong>ART129</strong></td>
<td>10701</td>
<td>Taxable sales</td>
<td>K_14</td>
<td>-</td>
</tr>
<tr>
<td>10702</td>
<td>Tax-free sale</td>
<td>K_14</td>
<td>-</td>
</tr>
<tr>
<td>10704</td>
<td>Taxable sales credit note</td>
<td>K_14</td>
<td>-</td>
</tr>
<tr>
<td>10705</td>
<td>Tax exempt sales credit note</td>
<td>K_14</td>
<td>-</td>
</tr>
<tr>
<td rowspan="4"><strong>IntraEUGoods</strong></td>
<td>10801</td>
<td>Tax-free sale</td>
<td>K_21</td>
<td>-</td>
</tr>
<tr>
<td>10810</td>
<td>Taxable import</td>
<td>K_23</td>
<td>+</td>
</tr>
<tr>
<td>10811</td>
<td>Taxable sales (Reverse charge)</td>
<td>K_23</td>
<td>-</td>
</tr>
<tr>
<td>10812</td>
<td>Use tax</td>
<td>K_24</td>
<td>+</td>
</tr>
<tr>
<td rowspan="2"><strong>ExportOfGoods</strong></td>
<td>10901</td>
<td>Tax-free sale</td>
<td>K_22</td>
<td>-</td>
</tr>
<tr>
<td>10905</td>
<td>Tax exempt sales credit note</td>
<td>K_22</td>
<td>-</td>
</tr>
<tr>
<td rowspan="4"><strong>ImportOfGoodsART33</strong></td>
<td>20207</td>
<td>Taxable import</td>
<td>K_45</td>
<td>+</td>
</tr>
<tr>
<td>11010</td>
<td>Offset Taxable import</td>
<td>K_25</td>
<td>-</td>
</tr>
<tr>
<td>20209</td>
<td>Use tax</td>
<td>K_46</td>
<td>+</td>
</tr>
<tr>
<td>11012</td>
<td>Offset use tax</td>
<td>K_26</td>
<td>-</td>
</tr>
<tr>
<td rowspan="5"><strong>ImportOfServices</strong></td>
<td>20207</td>
<td>Taxable import</td>
<td>K_45</td>
<td>+</td>
</tr>
<tr>
<td>11110</td>
<td>Offset Taxable import</td>
<td>K_27</td>
<td>-</td>
</tr>
<tr>
<td>11117</td>
<td>Taxable sales (Reverse charge)</td>
<td>K_27</td>
<td>+</td>
</tr>
<tr>
<td>20209</td>
<td>Use tax</td>
<td>K_46</td>
<td>+</td>
</tr>
<tr>
<td>11112</td>
<td>Offset use tax</td>
<td>K_28</td>
<td>-</td>
</tr>
<tr>
<td rowspan="5"><strong>ImportART28</strong></td>
<td>20207</td>
<td>Taxable import</td>
<td>K_45</td>
<td>+</td>
</tr>
<tr>
<td>11210</td>
<td>Offset Taxable import</td>
<td>K_29</td>
<td>-</td>
</tr>
<tr>
<td>111119</td>
<td>Taxable sales (Reverse charge)</td>
<td>K_29</td>
<td>+</td>
</tr>
<tr>
<td>20209</td>
<td>Use tax</td>
<td>K_46</td>
<td>+</td>
</tr>
<tr>
<td>11212</td>
<td>Offset use tax</td>
<td>K_30</td>
<td>-</td>
</tr>
<tr>
<td rowspan="4"><strong>ReverseCharge</strong></td>
<td>11301</td>
<td>Taxable sales</td>
<td>K_34</td>
<td>-</td>
</tr>
<tr>
<td>11302</td>
<td>Sales tax payable</td>
<td>K_35</td>
<td>-</td>
</tr>
<tr>
<td>11304</td>
<td>Taxable sales credit note</td>
<td>K_34</td>
<td>-</td>
</tr>
<tr>
<td>11306</td>
<td>Sales tax on sales credit note</td>
<td>K_35</td>
<td>-</td>
</tr>
<tr>
<td rowspan="4"><strong>FixedAssetPurch</strong></td>
<td>20107</td>
<td>Taxable purchases</td>
<td>K_43</td>
<td>+</td>
</tr>
<tr>
<td>20109</td>
<td>Sales tax receivable</td>
<td>K_44</td>
<td>+</td>
</tr>
<tr>
<td>20115</td>
<td>Taxable purchase credit note</td>
<td>K_43</td>
<td>+</td>
</tr>
<tr>
<td>20116</td>
<td>Sales tax on purchase credit note</td>
<td>K_47</td>
<td>+</td>
</tr>
<tr>
<td rowspan="4"><strong>GoodServPurch</strong></td>
<td>20207</td>
<td>Taxable purchases</td>
<td>K_45</td>
<td>+</td>
</tr>
<tr>
<td>20209</td>
<td>Sales tax receivable</td>
<td>K_46</td>
<td>+</td>
</tr>
<tr>
<td>20215</td>
<td>Taxable purchase credit note</td>
<td>K_45</td>
<td>+</td>
</tr>
<tr>
<td>20216</td>
<td>Sales tax on purchase credit note</td>
<td>K_48</td>
<td>+</td>
</tr>
<tr>
<td rowspan="2"><strong>CorrATR89b1</strong></td>
<td>30101</td>
<td>Sales tax payable</td>
<td>K_49</td>
<td>+</td>
</tr>
<tr>
<td>30109</td>
<td>Sales tax receivable</td>
<td>K_49</td>
<td>+</td>
</tr>
<tr>
<td rowspan="2"><strong>CorrATR89b4</strong></td>
<td>30201</td>
<td>Sales tax payable</td>
<td>K_50</td>
<td>+</td>
</tr>
<tr>
<td>30209</td>
<td>Sales tax receivable</td>
<td>K_50</td>
<td>+</td>
</tr>
</tbody>
</table>

For invoices which are not paid within 150 days an “Overdue debt VAT” periodic task can be applied. In this case same Reporting codes as for K_44 and(or) K_46 can be used. Transactions will be automaticaly interpreted by the system for reporting in K_49 (Overdue invoice) and K_50 (Paid overdue invoice) respectively. 

### Configure the ER model, and format for the report

To review or change the configuration for the SAF VAT sales and purchase register, on the **Reporting configurations** page, in the list of models, select the **Standard Audit File (SAF-T)** model. Then click **Designer** to review or change the model. To review or change the format for the SAF VAT sales and purchase register, on the **Reporting configurations** page, under **Standard Audit File (SAF-T)**, select **VAT Register (PL)**, and then click **Designer**. For more information about ER, see the following topics:

-   [Electronic reporting overview](../../dev-itpro/analytics/general-electronic-reporting.md)
-   [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)
-   [Localization requirements - Create a ER configuration](../../dev-itpro/analytics/electronic-reporting-configuration.md)

Initially, the configuration is an example of VAT Register based on Reporting codes described in table above. If you need to adopt the configuration to another set of reporting codes, you should derive the format of the configuration. To do so, select the format in the configuration's tree and click **Create configuration** in **Main menu**. **Mark Derive from name:...,** fill in **Name** and **Description** fields of a new format and click **Create configuration** button. Created format is a copy of the parent format. Select the created format and click **Designer** on the **Main menu** to open format designer and update format with your reporting codes. Format designer window is divided into two parts: the left side â€“ is a format structure (in VAT register case it is a XML scheme); the right side â€“ is a Data Model (data). Press **Mapping** button in the right side to see the **Data model**. The Data Model includes all the field for all the SAF-T reports. VAT register format is mapped mostly to the **TaxTransaction** node. Scroll down the tree to find and select it. All tax transactions are grouped into two groups: for tag **SprzedazWiersz** and for tag **ZakupWiersz**. And called **$SalesList** and **$PurchaseList** respectively. These are record lists calculated (filtered) by formulas. You can review and modify formula in formula redactor. To do so, select calculated field or record list (in this particular case) and click **Edit** in tree menu. Edit formulas for **$SalesList** and **$PurchaseList** according to your company's Reporting codes and save them. Formula designer window in the left side shows the Data model where you can select fields or record lists and in the right side all the functions which you may implement. (More information about Format designer - [Formula designer in Electronic reporting](../../dev-itpro/analytics/general-electronic-reporting-formula-designer.md)). After Tax transactions were divided into two groups, inside each of both groups Tax transactions should be grouped for each tag according to your company's Reporting codes. Find calculated fields "list\_K" under **$SalesList** and **$PurchaseList** and update their formulas with your Reporting codes using Formula Designer. After all "list\_K"? nodes formulas were updated find and modify **SalasCtrl** and **PurchCtrl** under **$SalesList** and **$PurchaseList** respectively. These nodes are used for **SprzedazCtrl** and **ZakupCtrl**  tags respectively. Basically, no other modifications in the format are needed. Save the format. Close it and complete the format using **Change status** &gt; **Complete** button on the versions menu on **Versions** FastTab on **Configurations**.

### Generate a SAF VAT sales and purchase register

To generate a SAF VAT sales and purchase register, click **General ledger > Inquiries and reports > Standard Audit File for Tax (SAF-T) > SAF VAT sales and purchase register**, and set the following parameters.

|   Parameter                  |   Description                                                                      |
|------------------------------|------------------------------------------------------------------------------------|
| **From date**                | Specify the first date to export reporting data for.                               |
| **To date**                  | Specify that last date to export reporting data for.                               |
| **Authority identification** | In the list, select the identifier of the tax authority to use in the export file. |

You can specify additional selection parameters by using the **Filter** functionality on the **Records to include** tab.

## Generate a SAF VAT invoices file

Before you can generate a SAF VAT invoices file, you must complete the following additional setup.

-   Set up sales tax authorities.
-   Sales tax codes for VAT reporting.
-   Set up sales tax codes.
-   Configure the ER model, and format for the report.

This setup resembles the additional setup that you completed for the SAF VAT sales and purchase register excepting **Configure the ER model, and format for the report.**

To report correctly some important tags in the report, define **Application specific parameters** (for versions of the “VAT Invoices (PL)” format starting from 48.36.58). Open **Configurations > Application specific parameters > Setup** on Action pane, select version of the format which you are going to use (for example, “48.36.58”) and set up for this version values for each of the Lookups in the list on the right:

|   Name            |   Short description En. | Short description Pl. | Description En. |  Description Pl. |
|-------------------|-------------------------|-----------------------|-----------------|------------------|
| **TaxFree_LOOKUP**    | Tax free  | Tax free | Non-taxable transactions for the supply of goods and services outside the country; exempt from taxation. | Niepodlegające opodatkowaniu-transakcje dostawy towarów oraz świadczenia usług poza terytorium kraju; zwolnione z opodatkowania. |
| **TaxExemptReason_LOOKUP** | Tax exempt reason | Przyczyna lub podstawa zwolnienia z podatku lub jego zmniejszenia | In the case of delivery of goods or provision of services exempt from tax pursuant to art. 43 paragraph 1, art. 113 section 1 and 9 or provisions issued on the basis of art. 82 paragraph 3 | W przypadku dostawy towarów lub świadczenia usług zwolnionych od podatku na podstawie art. 43 ust. 1, art. 113 ust. 1 i 9 albo przepisów wydanych na podstawie art. 82 ust. 3 |
| **ItemType_LOOKUP** | Type of item | Rodzaj przedmiotu | Delivery of second-hand goods, works of art, collectors' items and antiques, for which the tax base is constituted in accordance with art. 120 paragraph 4th and 5th margin; New means of transport is the subject of Intra-Community supply. | Dostawy towarów używanych, dzieł sztuki, przedmiotów kolekcjonerskich i antyków, dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża; W przypadku gdy przedmiotem wewnątrzwspólnotowej dostawy są nowe środki transportu. |

### TaxFree_LOOKUP

P_12 field’s value (starting from JPK_FA v.2) may report, besides the tax rate and “zw” (reverse charge), the following values: 

-   “oo” (reverse charge as part of domestic transactions), 
-   "np" (for transactions of delivery of goods and provision of services outside the country). 

User must setup and use specific Exempt codes (Tax > Setup > Sales tax > Sales tax exempt codes) for sales tax codes setup with exempt on Sales tax groups (Tax > Indirect tax > Sales tax > Sales tax groups) to distinguish tax transactions by this Exempt code in the report. For the purposes of the report it is needed to define which Exempt codes must be reported with the given values of P_12 tag. To do so, select the “VAT Invoices (PL)” format and open Configurations > Application specific parameters > Setup on the Action pane. For the latest version of the configuration select the “TaxFree_LOOKUP” on the “Lookups” fast tab, go to the “Conditions” fast tab and define conditions for the Lookup results:

|  Lookup result               | Exempt codes                                                                            |
|------------------------------|----------------------------------------------------------------------------------------|
| **np**                       | Select those Exempt codes which are used for sales tax transactions of delivery of goods and provision of services outside the country. If there are more than one such code, you need to add as much lines as more Exempt codes are used for transactions of delivery of goods and provision of services outside the country.                                   |
| **zw**                       | Select *Not blank*. All other transactions with exempt not considering the reason will be reported as reverse charge as part of domestic transactions. This must be the last line in the list, check by the value in the “Line” column. |

Note! Tax transactions marked as “Reverse charge” will be reported as “oo”, no additional setup is needed.

(!) Click "Save" button when you complete the setup for “TaxFree_LOOKUP” Lookup field and going to setup next lookup field.

### TaxExemptReason_LOOKUP

Conditions for the “TaxExemptReason_LOOKUP” are Sales tax exempt codes defined in Finance (Modules > Tax > Setup > Sales tax > Sales tax exempt codes) and used in Sales tax group during posting of tax transactions. When invoice contains no lines with Sales tax exemptions P_19 field will be reported with “false” value and P_19A, P_19B, P_19C tags will be omitted.

-   P_19 indicates the provision of the act or act issued on the basis of the act on the basis of which the taxpayer applies tax exemption
-   P_19 indicates the provision of Directive 2006/112 / EC, which exempts from such tax the supply of goods or such services
-   P_19 indicates another legal basis indicating that the supply of goods or services benefits from the exemption

(!) Click "Save" button when you complete the setup for “TaxExemptReason_LOOKUP” Lookup field and going to setup next lookup field.

### ItemType_LOOKUP

This lookup field is introduced in version 48.36.58 of “VAT Invoices (PL)” format (current KB).

In “ItemType_LOOKUP” lookup the following values are available for setup:

|   Name |   Description (En) | Description (Pl) | Setup |
|--------|--------------------|------------------|-------|
| **SecondHandGoods** | Deliveries of second-hand goods for which the tax base is constituted in accordance with art. 120 paragraph 4th and 5th margin | Dostawy towarów używanych dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | Specify “Sales tax codes” which are used for transaction related to second-hand goods. With this setup for an invoice with tax transaction by the specified tax code “procedura marży - towary używane” will be reported in <P_106E_3A> tag. |
| **ArtWorks**  | Deliveries of works of art for which the tax base is constituted in accordance with art. 120 paragraph 4th and 5th margin | Dostawy dzieł sztuk dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | Specify “Sales tax codes” which are used for transaction related to works of art. With this setup for an invoice with tax transaction by the specified tax code “procedura marży - dzieła sztuki” will be reported in <P_106E_3A> tag. |
| **CollectorAntiques** | Deliveries of collectors' items and antiques, for which the tax base is constituted in accordance with art. 120 paragraph 4th and 5th margin | Dostawy przedmiotów kolekcjonerskich i antyków, dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | Specify “Sales tax codes” which are used for transaction related to collectors' items and antiques. With this setup for an invoice with tax transaction by the specified tax code “procedura marży - przedmioty kolekcjonerskie i antyki” will be reported in <P_106E_3A> tag. |
| **Transport** | Intra-Community delivery of new means of transport | Wewnątrzwspólnotowa dostawa nowych środków transportu | Specify “Sales tax codes” which are used for transaction related to Intra-Community delivery of new means of transport. With this setup for an invoice with tax transaction by the specified tax code <P_22> tag will be reported with “true” value. |
| **Other** | Other | Inne | Specify *Not blank* in “Tax Exempt code” field. This value must be the last in the list of values. At least this value must be mandatory specified for this Lookup. |

When configuration of lookup fields values is completed, mark **State** as “Completed”, save and close the page. If any of the lookup fields doesn’t contain at least one value with *Not blank*, an error will be thrown in the report run-time informing that Application specific parameters are missing.

### Configure the ER model, and format for the report

To review or change the configuration for the SAF VAT sales and purchase register, on the **Reporting configurations** page, in the list of models, select the **Standard Audit File (SAF-T)** model. Then click **Designer** to review or change the model. To review or change the format for the SAF VAT invoices, on the **Reporting configurations** page, under **Standard Audit File (SAF-T)**, select **VAT invoices (PL)**, and then click **Designer**. For more information about ER, see the following topics:

-   [Electronic reporting overview](../../dev-itpro/analytics/general-electronic-reporting.md)
-   [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)
-   [Localization requirements - Create a ER configuration](../../dev-itpro/analytics/electronic-reporting-configuration.md)

Initially, the configuration is an example of VAT Register based on Reporting codes described in table above. If you need to adopt the configuration to another set of reporting codes, you should derive the format of the configuration. To do so, select the format in the configuration's tree and click **Create configuration** in **Main menu**. **Mark Derive from name:...,** fill in **Name** and **Description** fields of a new format and click **Create configuration** button. Created format is a copy of the parent format. Select the created format and click **Designer** on the **Main menu** to open format designer and update format with your reporting codes. Format designer window is divided into two parts: the left side is a format structure (in VAT register case it is a XML scheme); the right side is a Data Model (data). Press **Mapping** button in the right side to see the **Data model**. The Data Model includes all the field for all the SAF-T reports. **VAT invoices** format includes several parts with different data sources. Data under tag **Faktura** is mapped mostly to the **Model &gt; SourceDocuments &gt; $Invoices** node. Scroll down the tree to find and select it. Find calculated fields **list\_P\_** under **$Invoices** node and update their formulas with your Reporting codes using Formula Designer. The Formula designer window shows the data model where you can select fields or record lists and in the right side all the functions which you may implement. For more information about Format designer, see [Formula designer in Electronic reporting](../../dev-itpro/analytics/general-electronic-reporting-formula-designer.md). Values for tags under **StawkiPodatku** tag is constants. Select value node (String) for each of tag under **StawkiPodatku** tag and set up its value in **Value** field on **Format** tab on the right side of the **Designer**. Basically, no other modifications in the format are needed. Save the format. Close it and complete the format using **Change status** &gt; **Complete** button on the versions menu on **Versions** FastTab on **Configurations**.

### Generate a SAF VAT invoices

To generate a SAF VAT invoices file, click **General ledger > Inquiries and reports > Standard Audit File for Tax (SAF-T) > SAF VAT invoices**, and set the following parameters.

|  Parameter                   | Description                                                                            |
|------------------------------|----------------------------------------------------------------------------------------|
| **From date**                | Specify the first date to export reporting data for.                                   |
| **To date**                  | Specify the last date to export reporting data for.                                    |
| **Authority identification** | In the list, select the identifier of the tax authority to use in the export file.     |
| **Invoice ID From / To**     | Specify a range of invoice IDs to limit the invoice that are selected for data export. |

You can specify additional selection parameters by using the **Filter** functionality on the **Records to include** tab.

### Implementation details

Version 3 of JPK_FA report introduces possibility of reporting invoices with different document currency in the same file. For this purpose, “Currency” parameter on the dialog form of “SAF VAT invoices (Poland)” report is made optional. When user specifies in this parameter a currency, the report will include only invoices with this currency, when user doesn’t specify any currency in this field, report will be generated for all the invoices not considering document currency of the invoices.

#### <P_14x> tags

According to the requirements of the version 3 of JPK_FA report, when invoices is posted in a currency which differs from “PLN”, <P_13x>, <P_14x> and <P_15> tags must represent amounts in the invoice currency and new <P_14xW> tags must represent related amounts in “PLN”. It is assumed that “PLN” is defined as currency for the Sales tax codes used for transactions to be included in to JPK_FA report. Basing on this assumption, for invoices which document currency differs from the currency setup in Sales tax codes used in the tax transaction(s) of this document, system reports additionally <P_14xW> tags with amount in sales tax code currency (as it is assumed to be “PLN”).

#### <P_18A> tag

KB #4339927 (“A country specific update for Poland for Split payments in Dynamics 365 for Finance and Operations”) introduces possibility to setup Methods of payments in Account receivable module as “Split payment”.

According to the requirements of the version 3 of JPK_FA report, <P_18A> tag for an invoice must be reported as “true” when split payment mechanism was applied for this invoice. To define if split payment mechanism was applied to invoice, system checks “Split payment” parameter of the Method of payment which was used during the invoice posting and reflected in the corresponding customer transaction (in CustTrans table). It is important to keep setup of “Split payment” parameter of Methods of payments stable to guaranty correct reporting.

#### <P_22> tag

<P_22> tag will be reported with “true” value according to setup of Sales tax codes in “ItemType_LOOKUP” for Result = “Transport” in Application specific parameters of “VAT Invoices (PL)” format.

#### <P_106E_3> and <P_106E_3A> tags

According to the requirements of JPK_FA report <P_106E_3> tag must report “true” in the case of delivery of second-hand goods, works of art, collectors' items and antiques, taxable base of which is in accordance with art. 120 paragraph 4th and 5th.  When <P_106E_3> tag is reported with “true” value, <P_106E_3A> tag must represent related value(s):

|   Value of <P_106E_3A> tag |   Description (Pl) | Description (En) | How Finance will distinguish |
|--------|--------------------|------------------|-------|
| **procedura marży - towary używane** | Dostawy towarów używanych dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | Deliveries of second-hand goods for which the tax base is constituted in accordance with art. 120 paragraph 4th and 5th margin | According to setup of Sales tax codes in “ItemType_LOOKU” for Result = “SecondHandGoods” in Application specific parameters of “VAT Invoices (PL)” format. | 
| **procedura marży - dzieła sztuki** | Dostawy dzieł sztuki, przedmiotów kolekcjonerskich i antyków, dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | Deliveries of works of art for which the tax base is constituted in accordance with art. 120 paragraph 4th and 5th margin | According to setup of Sales tax codes in “ItemType_LOOKU” for Result = “ArtWorks” in Application specific parameters of “VAT Invoices (PL)” format. |
| **procedura marży - przedmioty kolekcjonerskie i antyki** | Dostawy przedmiotów kolekcjonerskich i antyków, dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | Deliveries of collectors' items and antiques, for which the tax base is constituted in accordance with art. 120 paragraph 4th and 5th margin | According to setup of Sales tax codes in “ItemType_LOOKU” for Result = “CollectorAntiques” in Application specific parameters of “VAT Invoices (PL)” format. |

#### <Zamowienie> and <ZamowienieCtrl> nodes
  
According to the requirements of version 3 of JPK_FA report <Zamowienie> node must represent orders or contracts referred to in art. 106f paragraph 1 item 4 of the Act (for advance invoices) in the currency in which the advance invoice was issued (Zamówienia lub umowy, o których mowa w art. 106f ust. 1 pkt 4 ustawy (dla faktur zaliczkowych) w walucie, w której wystawiono fakturę zaliczkową).

To complete this requirement system collects information through the data base by the lines of Sales orders (SO) and Free text invoices (FTI) which are linked to the advance invoices included to the report are provide the following information from them:

|   Tag name |   Description (Pl) | Description (En) | How Finance collects information |
|--------|--------------------|------------------|-------|
| **P_7Z** | Nazwa (rodzaj) towaru lub usługi | Name (type) of the good or service | Value stored in line of SO or FTI in Finance data base |
| **P_8AZ** | Miara zamówionego towaru lub zakres usługi | Unit of measure of the ordered goods or scope of the service | UOM value stored in line of SO or FTI in Finance data base. ("usługa" when empty) |
| **P_8BZ** | Ilość zamówionego towaru lub zakres usługi | Quantity of ordered goods or scope of service | Value of quantity stored in line of SO or FTI in Finance data base. |
| **P_9AZ** | Cena jednostkowa netto | Net unit price | Value of price stored in line of SO or FTI in F&O data base. |
| **P_11NettoZ** | Wartość zamówionego towaru lub usługi bez kwoty podatku | Value of the ordered goods or services without the amount of tax | Calculated value of tax base amount by the line of SO or FTI basing on quantity stored in the line (P_8BZ). |
| **P_11VatZ** | Kwota podatku od zamówionego towaru lub usługi | Tax amount on ordered goods or services | Calculated value of tax amount by the line of SO or FTI basing on quantity stored in the line (P_8BZ). |
| **P_12Z** | Stawka podatku | Tax rate | Calculated value tax rate based on tax setup in the line of SO or FTI (Sales tax group and Item sales tax group). |

In respect to the values reported for the lines of SO or FTI, <WartoscZamowienia> tag value of <Zamowienie> node is calculated as sum by all the document lines of calculated values of tax base amount and calculated values of tax amount (P_11NettoZ + P_11VatZ).
  
<WartoscZamowien> tag value of <ZamowienieCtrl> node is calculated as sum of <WartoscZamowienia> tag values by all the documents reported in <Zamowienie> node.

## Using batch jobs for SAFT
Generating SAF-T reports for a long period such as month or a quarter can include a huge data and take a long time. For such cases, it is recommended to use batch jobs. Dialog page for every SAF-T report has a **Run in the background** tab. Open this tab to set up report's generation in batch mode. Select **Batch processing** check box. To learn more about batch processing see the [Batch processing overview](../../dev-itpro/sysadmin/batch-processing-overview.md) topic. To review batch jobs or find generated file open **Organization administration** &gt; **Electronic reporting** &gt; **Electronic reporting jobs** and find a line related to your job. Click **Show log** button on the **Main menu**. If nothing is shown it means that no messages were produced during the file generation. To see the file click **Show files** button on **Main menu**, find a file that you need and click **Open** on the **Main menu** to review or save the file.  

