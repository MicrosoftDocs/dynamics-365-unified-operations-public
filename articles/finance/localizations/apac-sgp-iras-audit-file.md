---
title: IRAS Audit File (IAF) for Singapore
description: This article explains how to set up and generate the IRAS Audit File (IAF) for Singapore for legal entities that have a primary address in Singapore.
author: AdamTrukawka
ms.date: 06/27/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Singapore
ms.author: atrukawk
ms.search.validFrom: 
ms.dyn365.ops.version: 
---

# IRAS Audit File (IAF) for Singapore

[!include [banner](../includes/banner.md)]

According to Inland Revenue Authority of Singapore (IRAS), companies in Singapore should maintain a listing of sales and purchases to support the figures that are reported in Goods and Services Tax (GST) returns. During an audit, the listing is provided in the form of an IRAS Audit File (IAF).

This article describes how to set up Microsoft Dynamics 365 Finance to prepare the IAF in text format for legal entities that have a primary address in Singapore.

The IAF in text format is available in Finance as of version 10.0.26.

## Prepare your environment to generate an IAF for Singapore

To work with the IAF for Singapore, you must complete the following tasks:

1. [Import Electronic reporting (ER) configurations](#import).
2. [Associate sales tax codes with Singaporean standard GST codes](#tax-codes).
3. [Enable features in Feature management](#features).
4. [Select the ER configuration in General ledger parameters](#gl-param).
5. [Set up company information for the reporting header](#header-information).

### <a name="import"></a>Import ER configurations

Before you generate an IAF for Singapore, import the latest versions of the following ER configurations.

| ER configuration name | Type | Description |
|-----------------------|------|-------------|
| Standard Audit File (SAF-T) | Model | The common data model for different audit reports. |
| SAF-T General model mapping | Model mapping | The model mapping that provides general data source mapping. |
| IRAS Audit File - IAF in TXT (SG) | Format | IRAS Audit File for Singapore in pipe-delimited text format. |

For more information about how to download ER configurations, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. Use the **Issue search** section of the [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2) portal to find and read information about specific versions of ER configurations.

> [!IMPORTANT]
> After all the ER configurations are imported, set the **Default for model mapping** option to **Yes** for the **SAF-T General model mapping** configuration.

### <a name="tax-codes"></a>Associate sales tax codes with Singaporean standard GST codes

In the IAF for Singapore, sales tax codes that are used in Finance must be associated with Singaporean standard GST codes for the purpose of IAF reporting.

If your legal entity's GST codes are set up in accordance with the Singaporean standard GST codes, follow these steps.

1. In the **Electronic reporting** workspace, in the configuration tree, select the **IRAS Audit File - IAF in TXT (SG)** ER format.
2. Make sure that the company that you're working in is the company that you will run the IAF for Singapore for.
3. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
4. On the left side of the **Application specific parameters** page, select the version of the format that you want to use.
5. Change the value of the **State** field to **Completed**, save your changes, and close the page.

If your legal entity's GST codes are **not** set up in accordance with the Singaporean standard GST codes, follow these steps to associate GST codes that are used in Finance with Singaporean standard GST codes.

1. In the **Electronic reporting** workspace, in the configuration tree, select the **IRAS Audit File - IAF in TXT (SG)** ER format.
2. Make sure that the company that you're working in is the company that you will run the IAF for Singapore for.
3. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
4. On the left side of the **Application specific parameters** page, select the version of the format that you want to use.
5. On the **Lookup** FastTab, select **StandardTaxCodes\_Lookup**.
6. On the **Conditions** FastTab, specify criteria by adding lines for each **Result** value that must be used in the selected company. If several GST codes in the selected company must result in the same standard GST code, add a separate line for each GST code, and specify the same standard GST code for each.
7. Select the **Other** value as the last condition in the list. This condition must be set to **\*Not blank\*** in the **GST code** column. Use the value in the **Line** column to verify that **Other** is the last condition in the table.
8. When you've finished setting up conditions, change the value of the **State** field to **Completed**, save your changes, and close the page.

### <a name="features"></a>Enable features in Feature management

1. Open the **Feature management** workspace.
2. On the **All** tab, find and select the following features in the feature list. Note that enabling some of these features is optional.

    | Feature name | Mandatory or optional |
    |--------------|-----------------------|
    | [Standard Audit File for Tax (SAF-T) electronic report](../general-ledger/standard-audit-file.md) | Mandatory |
    | [Optimization of query data source creation time during execution of ER reports](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) | Optional |
    | [Optimize datasets memory consumption at ER reports runtime](../../fin-ops-core/dev-itpro/analytics/er-reduce-fetched-fields-number.md) | Optional |
    | [Accelerate the ER labels storage](../../fin-ops-core/dev-itpro/analytics/er-design-multilingual-reports.md#performance) | Optional |
    | [Use application specific parameters from previous versions of ER formats](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md#reuse-legal-entitydependent-parameters) | Optional |

3. Select **Enable now**.

### <a name="gl-param"></a>Select the ER configuration in General ledger parameters

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Standard Audit File for Tax (SAF-T)** tab, in the **Standard Audit File for Tax (SAF-T)** field, select **IRAS Audit File - IAF in TXT (SG)**.

### <a name="header-information"></a>Set up company information for the reporting header

The first section of the IAF for Singapore represents the following information about the reporting legal entity:

- **[CompanyName](#company-name)** – The company name of the business user.
- **[CompanyUEN](#company-uen)** – The Unique Entity Number (UEN) of the business user.
- **[GSTNo](#company-gst)** – The GST Registration Number of the business user.

#### <a name="company-name"></a>CompanyName – Company name of the business user

The value of this field represents the name of the legal entity that is specified in the **Name** field on the **Legal entities** page (**Organization administration** \> **Organizations** \> **Legal entities**).

#### <a name="company-uen"></a>CompanyUEN – UEN of the business user

To report the UEN of the company that is reporting the IAF, the system retrieves the value from the registration ID. The registration ID is defined in the properties of the legal entity that is associated with the **Enterprise ID (COID)** registration category that is valid on the date that is specified for the **To date** parameter of the report. For more information, see [Registration type](emea-registration-ids.md#registration-type-creation) and [Registration category](emea-registration-ids.md#supported-registration-categories).

#### <a name="company-gst"></a>GSTNo - GST Registration Number of the business user

To report the GST Registration Number of the company that is reporting the IAF, the system retrieves the value from the registration ID that is defined in the properties of the legal entity that is associated with the **VAT ID** registration category that is valid on the date that is specified for the **To date** parameter of the report. If there is no such value, the value of the **Tax registration number field** field is used instead. For more information, see [Registration type](emea-registration-ids.md#registration-type-creation) and [Registration category](emea-registration-ids.md#supported-registration-categories).

## Generate an IAF for Singapore

To generate an IAF for Singapore, follow these steps.

1. Go to **General ledger** \> **Inquiries and reports** \> **Standard Audit File for Tax (SAF-T)** \> **Standard Audit File for Tax (SAF-T)**.
2. In the report dialog box, set the following fields.

    | Field name | Description |
    | ---------- | ----------- |
    | Report language | Select the language to generate the report in. |
    | Purchase and supply data in tax code currency | Select this checkbox to report the `PurchaseValueSGD` and `GSTValueSGD` amounts in the **Purchase Listing Table (PurchaseLines)** section of the report, and the `SupplyValueSGD` and `GSTValueSGD` amounts in the **Supply Listing Table (SupplyLines)** section of the report, in the tax code currency. If this checkbox is cleared, these amounts will be reported in the currency that is selected in the **Currency** field. |
    | From date, To date | Select dates to specify the date interval for the report. You can select dates within one fiscal year. |
    | Currency | Select **Accounting currency** to report amounts in the **Debit**, **Credit**, and **Balance** columns of the **GLDataLines** section of the report in the accounting currency. Select **Reporting currency** to report those amounts in the reporting currency. |
    | Main financial dimension set | Select the standard financial dimension set, including the main account that the report uses to calculate the opening balance by main account at the beginning of the reporting period. This parameter affects only the **GLDataLines** section of the report. For more information about financial dimension sets, see [Financial dimension sets](../general-ledger/financial-dimension-sets.md). |
    | Group by main account | Select this checkbox to group general ledger account entries by main account on the report. When this checkbox is selected, the amounts in **GLDataLines** section of the report that are reported for each main account are represented as aggregated amounts, where aggregation is done by the `TransactionDate` and `TransactionID` fields. |
    | Include reversed | Select this checkbox if a reversed transaction must be reported. This parameter affects only the **GLDataLines** section of the report. |
    | Posting layer(s) | Select one or more posting layer transactions to include on the report. If you leave this field blank, all the posting layers are reported. This parameter affects only the **GLDataLines** section of the report. |
    | Sales tax specification | Select this checkbox to report the standard GST codes that are [associated with the GST codes in Finance](#tax-codes) in the `TaxCode` field of the **Purchase Listing Table (PurchaseLines)** and **Supply Listing Table (SupplyLines)** sections of the report. If this checkbox is cleared, the GST codes that are set up and used in Finance are reported in the `TaxCode` field of the **Purchase Listing Table (PurchaseLines)** and **Supply Listing Table (SupplyLines)** sections of the report. |
    | Settlement period | Select a settlement period to filter sales tax transactions on the report. If you leave this field blank, sales tax transactions from all settlement periods are included on the report. |
    | Include invoices by | Data that is reported in the **Purchase Listing Table (PurchaseLines)** and **Supply Listing Table (SupplyLines)** sections of the report is filtered according to the dates that are specified in the **From date** and **To date** fields. Use the **Include invoices by** parameter to define which field of the data this filter must be applied to. The following options are available: **Invoice Date**, **Tax transaction date**, and **Date of VAT register**. The **Date of VAT register** option is available only when the [Date of VAT register](emea-tax-point-date.md) feature is enabled. |

3. You can use the **Records to include** option to filter the data on the report by one or more main accounts. This parameter affects only the **GLDataLines** section of the report.
4. On the **Run in the background** FastTab, you can specify parameters of the batch job and run the report in batch mode. When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

## Implementation details

### Special symbols in the value of text fields

A pipe or vertical bar (\|) is a special symbol in the IAF. If it's used in the value of any text field of the report, it's replaced with a space.
 
If char(10) or char(13) is included in the value of any text field of the IAF, it's excluded for the value in reporting.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
