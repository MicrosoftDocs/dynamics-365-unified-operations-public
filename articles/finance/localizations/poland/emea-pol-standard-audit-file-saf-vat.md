---
title: SAF VAT sales and purchase register - JPK_VAT
description: This article explains how users in legal entities in Poland can generate a SAF VAT sales and purchase register - JPK_VAT.
author: liza-golub
ms.author: egolub
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 11/27/2024
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-11-30
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
ms.dyn365.ops.version: Version 1611
ms.assetid: b85c4019-f682-45bf-9a0d-c7549a2f1274
---

# SAF VAT sales and purchase register - JPK_VAT

[!include [banner](../../includes/banner.md)]

This article explains how to set up Microsoft Dynamics 365 Finance to configure and generate a SAF VAT sales and purchase register - JPK_VAT for legal entities that have a primary address in Poland.

SAF VAT File (JPK_VAT) is a standardized electronic format that enables businesses to submit detailed records of their VAT sales and purchase transactions directly to Polish tax authorities. The file that is generated in this format, SAF VAT sales and purchase register - JPK_VAT, provides a structured overview of value-added tax (VAT) settlements. Therefore, it enables efficient tax audits and enhances compliance with Polish VAT regulations.

A SAF VAT sales and purchase register - JPK_VAT is required monthly, even if no transactions occurred during the reporting period. It must be submitted electronically through the Polish tax authority's portal.

> [!NOTE]
> The Act of July 4, 2019, issued by the Polish Parliament and signed by the President of Poland, replaced the previous JPK_VAT records and VAT-7/VAT-7K declarations with a single electronic document, JPK_V7, submitted as JPK_V7M or JPK_V7K. For more details, see [VAT declaration with registers (JPK-V7, VDEK)](emea-pol-vdek.md). Due to this regulatory change, the JPK_VAT format was deprecated. For more details, see [Removed or deprecated features in Dynamics 365 Finance in the Finance 10.0.43 release](/dynamics365/finance/get-started/removed-deprecated-features-finance#features-removed-or-deprecated-in-the-finance-10043-release).

## Setup

Before you can generate a SAF VAT sales and purchase register - JPK_VAT, you must complete the following setup.

1. [Import Electronic reporting (ER) configurations](#er-import).
1. [Set up the ER format in General ledger parameters](#er-format-setup).
1. [Set up sales tax authorities](#tax-authorities).
1. [Set up sales tax reporting codes](#tax-codes).
1. Optional: [Configure the ER model and format for the report](#configure-er).

### <a id="er-import"></a>Import ER configurations

In Finance, import the following ER configurations from Dataverse. Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

| ER configuration name | Type | Description |
|---|---|---|
| Standard Audit File (SAF-T) | Model | The common data model for different audit reports. |
| Standard Audit File model mapping | Model mapping | The model mapping that provides general source mapping for several electronic reports for Poland. |
| SAF Poland | Format | The XML format that represents a parent format for several JPK formats for Poland. |
| VAT Register (PL) | Format | VAT sale and purchase registers (VAT) for Poland, JPK_VAT. |

Import the most recent versions of the configurations. The version description usually includes the number of the Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!IMPORTANT]
> After all the ER configurations from the previous table are imported, set the **Default for model mapping** option to **Yes** for the **Standard Audit File model mapping** configuration.

### <a id="er-format-setup"></a>Set up the ER format in General ledger parameters

To set up the ER format in General ledger parameters, follow these steps.

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
1. On the **Standard Audit File for Tax (SAT-T)** tab, in the **SAF VAT sale and purchase registers** field, select the **VAT Register (PL)** ER format.

### <a id="tax-authorities"></a>Set up sales tax authorities

You can find general information about how to set up a sales tax authority in [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md).

To generate a SAF VAT sales and purchase register - JPK_VAT in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**.
1. Set the **Report layout** field to **Default**.
1. Select the same sales tax authority for the sales tax settlement period that will be used for the sales tax codes.

### <a id="tax-codes"></a>Set up sales tax reporting codes

A reporting code is an integer value. Reporting codes should be numbered according to the company's rules. You can find general information about how to set up sales tax reporting codes in [Set up sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md). You can find general information about how to report tax by reporting codes in [Tax reporting by reporting codes](../../localizations/europe/emea-vat-reporting.md).

We recommend that you vary the codes by tax direction. For example, use a five-digit code. For all outgoing transactions, which should be reflected in the first part of the VAT scheme, set the codes so that they are less than or equal to 19999. Then, for all incoming transactions, which should be reflected in the second part of the VAT scheme, set the codes so that they are greater than or equal to 20000. In this way, you simplify the setup for reports and for data export that is based on tax transactions that are aggregated by reporting codes.

Here is an example that shows how you can use sales tax reporting codes to generate a SAF VAT sales and purchase register - JPK_VAT. For this example, reporting codes are in the format *ABBCC*. This format consists of the following parts:

- **A** – The transaction direction. The value is **1** for outgoing transactions, **2** for incoming transactions, or **3** for corrections.
- **BB** – The tax code. The numbering is sequential among all tax codes.
- **CC** – The transaction type number within a tax code, as explained in the following table.

    | Transaction type | Transaction type number |
    |---|---|
    | Taxable Sales | 01 |
    | Tax-free sales | 02 |
    | Sales tax payable | 03 |
    | Taxable sales credit note | 04 |
    | Tax exempt sales credit note | 05 |
    | Sales tax on sales credit note | 06 |
    | Taxable purchases | 07 |
    | Tax-free purchase | 08 |
    | Sales tax receivable | 09 |
    | Taxable import | 10 |
    | Offset taxable import | 11 |
    | Use tax | 12 |
    | Offset use tax | 13 |
    | Taxable purchase credit note | 14 |
    | Tax exempt purchase credit note | 15 |
    | Sales tax on purchase credit note | 16 |
    | Taxable import credit note | 17 |
    | Offset taxable import credit note | 18 |

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

For invoices that aren't paid within 150 days, an **Overdue debt VAT** periodic task can be applied. In this case, the same reporting codes that are used for **K_44** and/or **K_46** can be used. The system automatically interprets transactions for reporting in **K_49** (Overdue invoice) and **K_50** (Paid overdue invoice).

### <a id="configure-er"></a>Configure the ER model and format for the report (optional)

Initially, the configuration is an example of a SAF VAT invoices file - JPK_FA that is based on the reporting codes from the table earlier in this article. If you must adapt the configuration to another set of reporting codes, use the configuration to derive the format.

To configure the ER model and format for the report, follow these steps.

1. In the configuration tree, select the format. Then select **Create configuration**.
1. Select the **Derive from name** option, enter the name and description of the new format, and then select **Create configuration**. The format that is created is a copy of the parent format. 
1. Select the new format, and then select **Designer** to open the format designer.
1. Update the format with your reporting codes.

    The **Format designer** page is divided into two parts. The left side shows a format structure. (In the case of the VAT register, this structure is an XML scheme.) The right side shows a data model (data).

1. On the right side of the page, select **Mapping** to view the data model. The data model includes all the fields for all the SAF-T reports. The **VAT invoices** format includes several parts that have different data sources.
1. Data under the **Faktura** tag is mostly mapped to the **Model** \> **SourceDocuments** \> **\$Invoices** node. Scroll down the tree to find and select the node.
1. Under the **Invoices** node, find the **list_P_** calculated fields, and use the formula designer to update their formulas with your reporting codes.

    The **Formula designer** page shows the data model, where you can select fields or record lists. The right side of the page shows all the functions that you can implement. Learn more about the formula designer in [Formula designer in Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting-formula-designer.md).

1. The values for tags under the **StawkiPodatku** tag are constants. For each tag under the **StawkiPodatku** tag, select the value node (string). Then, on the **Format** tab on the right side of the page, set up the value in the **Value** field. No other modifications to the format are needed.
1. Save and close the format.
1. On the **Configurations** page, on the **Versions** FastTab, complete the format by selecting **Change status** \> **Complete**.

## Generate a SAF VAT sales and purchase register - JPK_VAT

To generate a SAF VAT sales and purchase register - JPK_VAT, go to **General ledger** \> **Inquiries and reports** \> **Standard Audit File for Tax (SAF-T)** \> **SAF VAT sales and purchase register**, set the following parameters, and then select **OK**.

| Parameter | Description |
|---|---|
| From date | Specify the first date to export reporting data for. |
| To date | Specify the last date to export reporting data for. |
| Authority identification | In the list, select the identifier of the tax authority to use in the export file. |

You can specify additional selection parameters by selecting **Filter** on the **Records to include** tab.

## Using a batch job to generate a SAF VAT sales and purchase register - JPK_VAT

A SAF VAT sales and purchase register - JPK_VAT for a long period, such as a month or a quarter, can include a large amount of data and take a long time to be generated. Therefore, we recommend that you use batch jobs. The dialog box for every SAF report includes a **Run in the background** tab where you can set up report generation in batch mode. Set the **Batch processing** option to **Yes**. Learn more about batch processing in [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).

To review batch jobs or find a generated file, follow these steps.

1. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
2. Find a line that is related to your job, and then select **Show log**. If nothing is shown, no messages were produced when the file was generated.
3. To view a file, select **Show files**, find the file that you need, and then select **Open**.

