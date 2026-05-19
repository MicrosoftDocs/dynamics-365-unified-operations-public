---
title: SAF VAT sales and purchase register - JPK_VAT
description: This article explains how users in legal entities in Poland can generate a SAF VAT sales and purchase register - JPK_VAT.
author: liza-golub
ms.author: egolub
ms.topic: reference
ms.custom: 
  - bap-template
ms.date: 05/05/2026
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

To set up the ER format in General ledger parameters, follow these steps:

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

| Sales tax code | Sales tax reporting code | Description | Tag name in SAF-T VAT | Sign in SAF-T VAT |
|---|---|---|---|---|
| ExportCust | 10101 | Taxable sales | K_11 | - |
| ExportCust | 10102 | Tax-free sale | K_11 | - |
| ExportCust | 10104 | Taxable sales credit note | K_11 | - |
| ExportCust | 10105 | Tax exempt sales credit note | K_11 | - |
| Art100 | 10201 | Taxable sales | K_12 | - |
| Art100 | 10204 | Taxable sales credit note | K_12 | - |
| VAT22_23 | 10301 | Taxable sales | K_19 | - |
| VAT22_23 | 10302 | Tax-free sale | K_10 | - |
| VAT22_23 | 10303 | Sales tax payable | K_20 | - |
| VAT22_23 | 10304 | Taxable sales credit note | K_19 | - |
| VAT22_23 | 10306 | Sales tax on sales credit note | K_20 | - |
| VAT7_8 | 10401 | Taxable sales | K_17 | - |
| VAT7_8 | 10402 | Tax-free sale | K_10 | - |
| VAT7_8 | 10403 | Sales tax payable | K_18 | - |
| VAT7_8 | 10404 | Taxable sales credit note | K_17 | - |
| VAT7_8 | 10406 | Sales tax on sales credit note | K_18 | - |
| VAT5 | 10501 | Taxable sales | K_15 | - |
| VAT5 | 10502 | Tax-free sale | K_10 | - |
| VAT5 | 10503 | Sales tax payable | K_16 | - |
| VAT5 | 10504 | Taxable sales credit note | K_15 | - |
| VAT5 | 10506 | Sales tax on sales credit note | K_16 | - |
| VAT0 | 10601 | Taxable sales | K_13 | - |
| VAT0 | 10602 | Tax-free sale | K_10 | - |
| VAT0 | 10604 | Taxable sales credit note | K_13 | - |
| ART129 | 10701 | Taxable sales | K_14 | - |
| ART129 | 10702 | Tax-free sale | K_14 | - |
| ART129 | 10704 | Taxable sales credit note | K_14 | - |
| ART129 | 10705 | Tax exempt sales credit note | K_14 | - |
| IntraEUGoods | 10801 | Tax-free sale | K_21 | - |
| IntraEUGoods | 10810 | Taxable import | K_23 | + |
| IntraEUGoods | 10811 | Taxable sales (Reverse charge) | K_23 | - |
| IntraEUGoods | 10812 | Use tax | K_24 | + |
| ExportOfGoods | 10901 | Tax-free sale | K_22 | - |
| ExportOfGoods | 10905 | Tax exempt sales credit note | K_22 | - |
| SpecialProc-XII | 11303 | Sales tax payable | Not applicable, JPK_FA only | - |
| SpecialProc-XII | 11306 | Sales tax on sales credit note | Not applicable, JPK_FA only | - |
| ImportOfGoodsART33 | 20207 | Taxable import | K_45 | + |
| ImportOfGoodsART33 | 11010 | Offset Taxable import | K_25 | - |
| ImportOfGoodsART33 | 20209 | Use tax | K_46 | + |
| ImportOfGoodsART33 | 11012 | Offset use tax | K_26 | - |
| ImportOfServices | 20207 | Taxable import | K_45 | + |
| ImportOfServices | 11110 | Offset Taxable import | K_27 | - |
| ImportOfServices | 11117 | Taxable sales (Reverse charge) | K_27 | + |
| ImportOfServices | 20209 | Use tax | K_46 | + |
| ImportOfServices | 11112 | Offset use tax | K_28 | - |
| ImportART28 | 20207 | Taxable import | K_45 | + |
| ImportART28 | 11210 | Offset Taxable import | K_29 | - |
| ImportART28 | 11119 | Taxable sales (Reverse charge) | K_29 | + |
| ImportART28 | 20209 | Use tax | K_46 | + |
| ImportART28 | 11212 | Offset use tax | K_30 | - |
| ReverseCharge | 11301 | Taxable sales | K_34 | - |
| ReverseCharge | 11302 | Sales tax payable | K_35 | - |
| ReverseCharge | 11304 | Taxable sales credit note | K_34 | - |
| ReverseCharge | 11306 | Sales tax on sales credit note | K_35 | - |
| FixedAssetPurch | 20107 | Taxable purchases | K_43 | + |
| FixedAssetPurch | 20109 | Sales tax receivable | K_44 | + |
| FixedAssetPurch | 20115 | Taxable purchase credit note | K_43 | + |
| FixedAssetPurch | 20116 | Sales tax on purchase credit note | K_47 | + |
| GoodServPurch | 20207 | Taxable purchases | K_45 | + |
| GoodServPurch | 20209 | Sales tax receivable | K_46 | + |
| GoodServPurch | 20215 | Taxable purchase credit note | K_45 | + |
| GoodServPurch | 20216 | Sales tax on purchase credit note | K_48 | + |
| CorrATR89b1 | 30101 | Sales tax payable | K_49 | + |
| CorrATR89b1 | 30109 | Sales tax receivable | K_49 | + |
| CorrATR89b4 | 30201 | Sales tax payable | K_50 | + |
| CorrATR89b4 | 30209 | Sales tax receivable | K_50 | + |

For invoices that aren't paid within 150 days, an **Overdue debt VAT** periodic task can be applied. In this case, the same reporting codes that are used for **K_44** and/or **K_46** can be used. The system automatically interprets transactions for reporting in **K_49** (Overdue invoice) and **K_50** (Paid overdue invoice).

### <a id="configure-er"></a>Configure the ER model and format for the report (optional)

Initially, the configuration is an example of a SAF VAT invoices file - JPK_FA that is based on the reporting codes from the table earlier in this article. If you must adapt the configuration to another set of reporting codes, use the configuration to derive the format.

To configure the ER model and format for the report, follow these steps:

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

To review batch jobs or find a generated file, follow these steps:

1. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
1. Find a line that is related to your job, and then select **Show log**. If nothing is shown, no messages were produced when the file was generated.
1. To view a file, select **Show files**, find the file that you need, and then select **Open**.

