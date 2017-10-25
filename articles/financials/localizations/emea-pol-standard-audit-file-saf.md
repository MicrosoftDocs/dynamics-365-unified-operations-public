---
# required metadata

title: Standard audit file (SAF) for Poland
description: Users in legal entities in Poland can generate a Standard Audit File for Tax (SAF-T) in XML format. This topic provides information about the formats for Poland. 
author: LizaGolub
manager: AnnBe
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations, UnifiedOperations
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

Users in legal entities in Poland can generate a Standard Audit File for Tax (SAF-T) in XML format. This topic provides information about the formats for Poland. 

Users in legal entities in Poland can generate a Standard Audit File for Tax (SAF-T) in XML format. This document provides information about the formats for Poland. This document refers to functionality that has not yet been released.

## Set up the Standard Audit File for Tax for Poland
To specify an Electronic reporting (ER) format for each SAF-T scheme, click **General ledger** &gt; **Ledger setup** &gt; **General ledger parameters**, and then, on the **Standard Audit File for Taxes (SAF-T)** tab, set up a specific format for each of the following schemes:

-   SAF Accounting books
-   SAF Bank statements
-   SAF Inventory
-   SAF VAT sale and purchase registers
-   SAF VAT invoices

Each ER format should be predefined and can be updated in ER.

## Generate a SAF Accounting books file
To generate a SAF Accounting books file, click **General ledger** &gt; **Inquiries and reports** &gt; **Standard Audit File for Tax (SAF-T)** &gt; **SAF Accounting books**, and set the following parameters.

|                                                 |                                                                                                                                                            |
|-------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Parameter**                                   | **Description**                                                                                                                                            |
| **From date**                                   | Specify the first date to export reporting data for.                                                                                                       |
| **To date**                                     | Specify the last date to export reporting data for.                                                                                                        |
| **Authority identification**                    | Specify the identifier of the tax authority to use in the export file.                                                                                     |
| **Posting layer**                               | Select the posting layer to consider transactions from. This parameter affects only the ZOiS? part of the export file.                                     |
| **Should opening balance be shown by turnover** | If this parameter is selected, opening transactions affect accumulated turnover. This parameter affects only the ZOiS export file part.                    |
| **Separate balance**                            | This parameter can be considered for main accounts where the corresponding parameter is marked. This parameter affects only the ZOiS export file part.     |
| **Closing transactions**                        | If this parameter is selected, closing transactions will be included in the data that is exported. This parameter affects only the ZOiS? export file part. |

You can specify additional selection parameters by using **Filter** functionality on the **Records to include** tab.

## Generate a SAF Bank statement file
To generate a SAF Bank statement file, click **General ledger** &gt; **Inquiries and reports** &gt; **Standard Audit File for Tax (SAF-T)** &gt; **SAF Bank statement**, and set the following parameters.

|                              |                                                                                    |
|------------------------------|------------------------------------------------------------------------------------|
| **Parameter**                | **Description**                                                                    |
| **From date**                | Specify the first date to export reporting data for.                               |
| **To date**                  | Specify the last date to export reporting data for.                                |
| **Authority identification** | In the list, select the identifier of the tax authority to use in the export file. |
| **Bank account**             | Specify the bank account to export transactions for.                               |

 

## Generate a SAF Inventory file
To generate a SAF Inventory file, click **General ledger** &gt; **Inquiries and reports** &gt; **Standard Audit File for Tax (SAF-T)** &gt; **SAF Inventory**, and set the following parameters.

|                              |                                                                                    |
|------------------------------|------------------------------------------------------------------------------------|
| **Parameter**                | **Description**                                                                    |
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

For more information about the setup of VAT statements, see [(EU) VAT reporting](emea-vat-reporting.md).

### Set up sales tax authorities

For general information about how to set up a sales tax authority, see [Set up sales tax authorities (Task guide)](../general-ledger/tasks/set-up-sales-tax-authorities.md). To generate a SAF VAT sales and purchase register in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities. On the **Sales tax authorities** page (**Tax** &gt; **Indirect taxes** &gt; **Sales tax** &gt; **Sales tax authorities**), set the **Report layout** field to **Default**. Select the same sales tax authority for the sales tax settlement period that will be used for the sales tax codes.

### Set up sales tax codes and sales tax reporting codes

A reporting code is an integer value. Reporting codes should be numbered according to the company's rules. However, we recommend that you vary the codes by tax direction. For example, use a five-digit code, and set the codes for all outgoing transactions, which should be reflected in the first part of the VAT scheme, so that they are less than or equal to 19999. Set the codes for all incoming transactions, which should be reflected in the second part of the VAT scheme, so that they are more than or equal to 20000. In this way, you simplify the setup for reports and for data export that is based on tax transactions that are aggregated by reporting codes. Here is an example that shows how you can use sales tax reporting codes to generate a SAF VAT sales and purchase register. For this example, reporting codes are in the format *ABBCC*. This format consists of the following parts:

-   **A** - The transaction direction. The value is **1** for outgoing, **2** for incoming, **3** for corrections.
-   **BB** - The tax code. The numbering is sequential among all tax codes.
-   **CC**-   The transaction type number within a tax code. See the following table.

|                                       |                             |
|---------------------------------------|-----------------------------|
| **Transaction type**                  | **Transaction type number** |
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
<td rowspan="3"><strong>IntraEUGoods</strong></td>
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
<td rowspan="4"><strong>ImportOfServices</strong></td>
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
<td rowspan="4"><strong>ImportART28</strong></td>
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
<td>K_31</td>
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
<td>K_31</td>
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

### Configure the ER model, and format for the report

To review or change the configuration for the SAF VAT sales and purchase register, on the **Reporting configurations** page, in the list of models, select the **Standard Audit File (SAF-T)** model. Then click **Designer** to review or change the model. To review or change the format for the SAF VAT sales and purchase register, on the **Reporting configurations** page, under **Standard Audit File (SAF-T)**, select **VAT Register (PL)**, and then click **Designer**. For more information about ER, see the following topics:

-   [Electronic reporting overview](../../dev-itpro/analytics/general-electronic-reporting.md)
-   [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)
-   [Localization requirements - Create a ER configuration](../../dev-itpro/analytics/electronic-reporting-configuration.md)

Initially, the configuration is an example of VAT Register based on Reporting codes described in table above. If you need to adopt the configuration to another set of reporting codes, you should derive the format of the configuration. To do so, select the format in the configuration's tree and click **Create configuration** in **Main menu**. **Mark Derive from name:...,** fill in **Name** and **Description** fields of a new format and click **Create configuration** button. Created format is a copy of the parent format. Select the created format and click **Designer** on the **Main menu** to open format designer and update format with your reporting codes. Format designer window is divided into two parts: the left side â€“ is a format structure (in VAT register case it is a XML scheme); the right side â€“ is a Data Model (data). Press **Mapping** button in the right side to see the **Data model**. The Data Model includes all the field for all the SAF-T reports. VAT register format is mapped mostly to the **TaxTransaction** node. Scroll down the tree to find and select it. All tax transactions are grouped into two groups: for tag **SprzedazWiersz** and for tag **ZakupWiersz**. And called **$SalesList** and **$PurchaseList** respectively. These are record lists calculated (filtered) by formulas. You can review and modify formula in formula redactor. To do so, select calculated field or record list (in this particular case) and click **Edit** in tree menu. Edit formulas for **$SalesList** and **$PurchaseList** according to your company's Reporting codes and save them. Formula designer window in the left side shows the Data model where you can select fields or record lists and in the right side all the functions which you may implement. (More information about Format designer - [Formula designer in Electronic reporting](../../dev-itpro/analytics/general-electronic-reporting-formula-designer.md)). After Tax transactions were divided into two groups, inside each of both groups Tax transactions should be grouped for each tag according to your company's Reporting codes. Find calculated fields "list\_K" under **$SalesList** and **$PurchaseList** and update their formulas with your Reporting codes using Formula Designer. After all "list\_K"? nodes formulas were updated find and modify **SalasCtrl** and **PurchCtrl** under **$SalesList** and **$PurchaseList** respectively. These nodes are used for **SprzedazCtrl** and **ZakupCtrl**  tags respectively. Basically, no other modifications in the format are needed. Save the format. Close it and complete the format using **Change status** &gt; **Complete** button on the versions menu on **Versions** FastTab on **Configurations**.

### Generate a SAF VAT sales and purchase register

To generate a SAF VAT sales and purchase register, click **General ledger** &gt; **Inquiries and reports** &gt; **Standard Audit File for Tax (SAF-T)** &gt; **SAF VAT sales and purchase register**, and set the following parameters.

|                              |                                                                                    |
|------------------------------|------------------------------------------------------------------------------------|
| **Parameter**                | **Description**                                                                    |
| **From date**                | Specify the first date to export reporting data for.                               |
| **To date**                  | Specify that last date to export reporting data for.                               |
| **Authority identification** | In the list, select the identifier of the tax authority to use in the export file. |

You can specify additional selection parameters by using the **Filter** functionality on the **Records to include** tab.

### Generate a SAF VAT invoices file

Before you can generate a SAF VAT invoices file, you must complete the following additional setup.

-   Set up sales tax authorities.
-   Sales tax codes for VAT reporting.
-   Set up sales tax codes.
-   Configure the ER model, and format for the report.

This setup resembles the additional setup that you completed for the SAF VAT sales and purchase register excepting **Configure the ER model, and format for the report.**

### Configure the ER model, and format for the report

To review or change the configuration for the SAF VAT sales and purchase register, on the **Reporting configurations** page, in the list of models, select the **Standard Audit File (SAF-T)** model. Then click **Designer** to review or change the model. To review or change the format for the SAF VAT invoices, on the **Reporting configurations** page, under **Standard Audit File (SAF-T)**, select **VAT invoices (PL)**, and then click **Designer**. For more information about ER, see the following topics:

-   [Electronic reporting overview](../../dev-itpro/analytics/general-electronic-reporting.md)
-   [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md)
-   [Localization requirements - Create a ER configuration](../../dev-itpro/analytics/electronic-reporting-configuration.md)

Initially, the configuration is an example of VAT Register based on Reporting codes described in table above. If you need to adopt the configuration to another set of reporting codes, you should derive the format of the configuration. To do so, select the format in the configuration's tree and click **Create configuration** in **Main menu**. **Mark Derive from name:...,** fill in **Name** and **Description** fields of a new format and click **Create configuration** button. Created format is a copy of the parent format. Select the created format and click **Designer** on the **Main menu** to open format designer and update format with your reporting codes. Format designer window is divided into two parts: the left side is a format structure (in VAT register case it is a XML scheme); the right side is a Data Model (data). Press **Mapping** button in the right side to see the **Data model**. The Data Model includes all the field for all the SAF-T reports. **VAT invoices** format includes several parts with different data sources. Data under tag **Faktura** is mapped mostly to the **Model &gt; SourceDocuments &gt; $Invoices** node. Scroll down the tree to find and select it. Find calculated fields **list\_P\_** under **$Invoices** node and update their formulas with your Reporting codes using Formula Designer. The Formula designer window shows the data model where you can select fields or record lists and in the right side all the functions which you may implement. For more information about Format designer, see [Formula designer in Electronic reporting](../../dev-itpro/analytics/general-electronic-reporting-formula-designer.md). Values for tags under **StawkiPodatku** tag is constants. Select value node (String) for each of tag under **StawkiPodatku** tag and set up its value in **Value** field on **Format** tab on the right side of the **Designer**. Basically, no other modifications in the format are needed. Save the format. Close it and complete the format using **Change status** &gt; **Complete** button on the versions menu on **Versions** FastTab on **Configurations**.

### Generate a SAF VAT invoices

To generate a SAF VAT invoices file, click **General ledger** &gt; **Inquiries and reports** &gt; **Standard Audit File for Tax (SAF-T)** &gt; **SAF VAT invoices**, and set the following parameters.

|                              |                                                                                        |
|------------------------------|----------------------------------------------------------------------------------------|
| Parameter                    | Description                                                                            |
| **From date**                | Specify the first date to export reporting data for.                                   |
| **To date**                  | Specify the last date to export reporting data for.                                    |
| **Authority identification** | In the list, select the identifier of the tax authority to use in the export file.     |
| **Invoice ID From / To**     | Specify a range of invoice IDs to limit the invoice that are selected for data export. |

You can specify additional selection parameters by using the **Filter** functionality on the **Records to include** tab.

## Using batch jobs for SAFT
Generating SAF-T reports for a long period such as month or a quarter can include a huge data and take a long time. For such cases, it is recommended to use batch jobs. Dialog page for every SAF-T report has a **Run in the background** tab. Open this tab to set up report's generation in batch mode. Select **Batch processing** check box. To learn more about batch processing see the [Batch processing overview](../../dev-itpro/sysadmin/batch-processing-overview.md) topic. To review batch jobs or find generated file open **Organization administration** &gt; **Electronic reporting** &gt; **Electronic reporting jobs** and find a line related to your job. Click **Show log** button on the **Main menu**. If nothing is shown it means that no messages were produced during the file generation. To see the file click **Show files** button on **Main menu**, find a file that you need and click **Open** on the **Main menu** to review or save the file.  

