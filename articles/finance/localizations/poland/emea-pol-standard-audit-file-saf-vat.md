---
title: SAF VAT sales and purchase register - JPK_VAT
description: Users in legal entities in Poland can generate a SAF VAT sales and purchase register - JPK_VAT.
author: liza-golub
ms.author: egolub
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-11-30
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
ms.dyn365.ops.version: Version 1611
ms.assetid: b85c4019-f682-45bf-9a0d-c7549a2f1274
---

# SAF VAT sales and purchase register - JPK_VAT

[!include [banner](../../includes/banner.md)]

The SAF VAT File (JPK_VAT) is a standardized electronic format that allows businesses to submit detailed records of their VAT sales and purchase transactions directly to the Polish tax authorities. This file provides a structured overview of VAT settlements, enabling efficient tax audits and enhancing compliance with Polish VAT regulations.

The JPK_VAT must be submitted electronically through the Polish tax authority’s portal and is required on a monthly basis, even if no transactions occurred during the reporting period.

This topic provides an overview of how to set up Dynamics 365 Finance to configure and generate the JPK_VAT file for legal entities with a primary address in Poland.

## Setup

Before you can generate a SAF VAT sales and purchase register file, you must complete the following setup.

1. [Import Electronic reporting configurations](#er-import)
2. [Set up Electronic reporting format in General ledger parameters](#er-format-setup)
3. [Set up sales tax authorities](#tax-authorities)
4. [Set up sales tax reporting codes](#tax-codes)
5. [Configure the ER model and format for the report (optional)](#configure-er)

### <a id="er-import"></a> Import Electronic reporting configurations

In Finance, import the following Electronic reporting (ER) configurations from Dataverse.

For more information about how to import ER configurations, see [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

| ER configuration name       | Type          | Description |
|-----------------------------|---------------|-------------|
| Standard Audit File (SAF-T) | Model         | The common data model for different audit reports. |
| Standard Audit File model mapping | Model mapping | The model mapping that provides general source mapping for several electronic reports for Poland. |
| SAF Poland                  | Format        | The XML format that represents a parent format for several JPK formats for Poland. |
| VAT Register (PL)           | Format        | VAT sale and purchase registers (VAT) for Poland, JPK_VAT. |

Import the most recent versions of the configurations. 
The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!IMPORTANT]
> After all the ER configurations from the previous table are imported, set the **Default for model mapping** option to **Yes** for the **Standard Audit File model mapping** configuration.

### <a id="er-format-setup"></a> Set up Electronic reporting format in General ledger parameters

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
2. On the **Standard Audit File for Tax (SAT-T)** tab, in the **SAF VAT sale and purchase registers** field, select the ER format, **VAT Register (PL)**. 

### <a id="tax-authorities"></a> Set up sales tax authorities

For general information about how to set up a sales tax authority, see [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md). 
To generate a JPK_FA in XML file in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities. 

On the **Sales tax authorities** page (**Tax > Indirect taxes > Sales tax > Sales tax authorities**), 
set the **Report layout** field to **Default**. Select the same sales tax authority for the sales tax settlement period that will be used for the sales tax codes.

### <a id="tax-codes"></a> Set up sales tax reporting codes

A reporting code is an integer value. Reporting codes should be numbered according to the company's rules. 

For general information about how to set up sales tax reporting codes, see [Set up sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md).

For general information about how to report tax by reporting codes, see [Tax reporting by reporting codes](../../localizations/europe/emea-vat-reporting.md).

We recommend that you vary the codes by tax direction. 
For example, use a five-digit code, and set the codes for all outgoing transactions, which should be reflected in the first part of the VAT scheme, so that they are less than or equal to 19999. 
Set the codes for all incoming transactions, which should be reflected in the second part of the VAT scheme, so that they are more than or equal to 20000. 
In this way, you simplify the setup for reports and for data export that is based on tax transactions that are aggregated by reporting codes. 
Here is an example that shows how you can use sales tax reporting codes to generate a SAF VAT sales and purchase register. 
For this example, reporting codes are in the format *ABBCC*. This format consists of the following parts:

- **A** – The transaction direction. The value is **1** for outgoing, **2** for incoming, **3** for corrections.
- **BB** – The tax code. The numbering is sequential among all tax codes.
- **CC** – The transaction type number within a tax code. See the following table.

| Transaction type                  | Transaction type number     |
|-----------------------------------|-----------------------------|
| Taxable Sales                     | 01                          |
| Tax-free sales                    | 02                          |
| Sales tax payable                 | 03                          |
| Taxable sales credit note         | 04                          |
| Tax exempt sales credit note      | 05                          |
| Sales tax on sales credit note    | 06                          |
| Taxable purchases                 | 07                          |
| Tax-free purchase                 | 08                          |
| Sales tax receivable              | 09                          |
| Taxable import                    | 10                          |
| Offset taxable import             | 11                          |
| Use tax                           | 12                          |
| Offset use tax                    | 13                          |
| Taxable purchase credit note      | 14                          |
| Tax exempt purchase credit note   | 15                          |
| Sales tax on purchase credit note | 16                          |
| Taxable import credit note        | 17                          |
| Offset taxable import credit note | 18                          |

The following table shows the sales tax codes and sales tax reporting codes for this example.

<table>
<thead>
<tr>
<th>Sales tax code</th>
<th>Sales tax reporting code</th>
<th>Description</th>
<th>Tag name in SAF-T VAT</th>
<th>Sign in SAF-T VAT</th>
</tr>
</thead>
<tbody>
<tr>
<td rowspan="4">ExportCust</td>
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
<td rowspan="2">Art100</td>
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
<td rowspan="5">VAT22_23</td>
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
<td rowspan="5">VAT7_8</td>
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
<td rowspan="5">VAT5</td>
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
<td rowspan="3">VAT0</td>
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
<td rowspan="4">ART129</td>
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
<td rowspan="4">IntraEUGoods</td>
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
<td rowspan="2">ExportOfGoods</td>
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
<td rowspan="2">SpecialProc-XII</td>
<td>11303</td>
<td>Sales tax payable</td>
<td>Not applicable, JPK_FA only</td>
<td>-</td>
</tr>
<tr>
<td>11306</td>
<td>Sales tax on sales credit note</td>
<td>Not applicable, JPK_FA only</td>
<td>-</td>
</tr><tr>
<td rowspan="4">ImportOfGoodsART33</td>
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
<td rowspan="5">ImportOfServices</td>
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
<td rowspan="5">ImportART28</td>
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
<td>11119</td>
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
<td rowspan="4">ReverseCharge</td>
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
<td rowspan="4">FixedAssetPurch</td>
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
<td rowspan="4">GoodServPurch</td>
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
<td rowspan="2">CorrATR89b1</td>
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
<td rowspan="2">CorrATR89b4</td>
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

For invoices that aren't paid within 150 days, an **Overdue debt VAT** periodic task can be applied. 
In this case, the same reporting codes that are used for **K_44** and/or **K_46** can be used. 
The system will automatically interpret transactions for reporting in **K_49** (Overdue invoice) and **K_50** (Paid overdue invoice). 

### <a id="configure-er"></a> Configure the ER model and format for the report (optional)

Initially, the configuration is an example of the VAT Invoices report (JPK_FA) based on the reporting codes that are described in table earlier in this article. If you have to adapt the configuration to another set of reporting codes, use the configuration to derive the format. 

1. Select the format in the configuration's tree and then, in the **Main menu**, select **Create configuration**. 
2. Mark **Derive from name:...**, enter the name and description of the new format and then select **Create configuration**. The created format is a copy of the parent format. 
3. Select the created format, and on the **Main menu**, select **Designer** to open format designer.
4. Update format with your reporting codes. The **Format designer** window is divided into two parts. The left side is a format structure (in the case of the VAT register case, it is an XML scheme). The right side is a Data model (data). 
5. On the right side, select **Mapping** to see the Data model. The Data model includes all the fields for all of the SAF-T reports. The **VAT invoices** format includes several parts with different data sources. 
6. Data under the **Faktura** tag is mapped mostly to the **Model &gt; SourceDocuments &gt; $Invoices** node. Scroll down the tree to find and select the node. 
7. Under the **Invoices** node, find the calculated fields **list\_P\_** and update their formulas with your reporting codes using Formula Designer. The Formula designer window shows the data model where you can select fields or record lists and in the right side all the functions that you may implement. For more information about Format designer, see [Formula designer in Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting-formula-designer.md). The values for tags under the **StawkiPodatku** tag are constants. 
8. Select the value node (string) for each tag under the **StawkiPodatku** tag and set up its value in the **Value** field on the **Format** tab on the right side of the **Designer** page. No other modifications in the format are needed. 
9. Save the format, close, and complete the format by selecting **Change status** > **Complete** on the versions menu on **Versions** FastTab on **Configurations**.

## Generate a SAF VAT sales and purchase register
To generate a SAF VAT sales and purchase register, click **General ledger > Inquiries and reports > Standard Audit File for Tax (SAF-T) > SAF VAT sales and purchase register**, and set the following parameters.

| Parameter                |   Description                                                                      |
|--------------------------|------------------------------------------------------------------------------------|
| From date                | Specify the first date to export reporting data for.                               |
| To date                  | Specify that last date to export reporting data for.                               |
| Authority identification | In the list, select the identifier of the tax authority to use in the export file. |

You can specify additional selection parameters by using the **Filter** functionality on the **Records to include** tab.

## Using batch jobs for JPK_VAT

Generating JPK_VAT report for a long period such as month or a quarter can include a huge data and take a long time. 
For such cases, it is recommended to use batch jobs. 
Dialog page for every SAF report has a **Run in the background** tab. 
Open this tab to set up report's generation in batch mode. Select **Batch processing** check box. 
To learn more about batch processing, see [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md). To review batch jobs or find a generated file, go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**, and find a line related to your job. Select **Show log** on the **Main menu**. If nothing is shown, no messages were produced when the file was generated. To see the file, select **Show files** on the **Main menu**, find a file that you need, and select **Open** on the **Main menu**.  
