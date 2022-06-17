---
# required metadata

title: IRAS Audit File (IAF) for Singapore
description: This article explains how to set up and generate the IRAS Audit File (IAF) for Singapore for legal entities that have their primary address in Singapore. 
author: liza-golub
ms.author: elgolu
ms.date: 06/17/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Singapore
# ms.search.industry: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# IRAS Audit File (IAF) for Singapore

[!include [banner](../includes/banner.md)]

According to Inland Revenue Authority of Singapore (IRAS), companies in Singapore should maintain sales and purchases listings to support the figures reported in GST returns. During an audit, the listings are to be provided in the form of an IRAS Audit File (IAF).

This topic describes how to set up the IAF in TXT format for legal entities that have their primary address in Singapore.

The IAF in TXT format is available in Dynamics 365 Finance as of version 10.0.26.

## Prepare your environment to generate a IRAS Audit File (IAF) for Singapore

To start to work with the **IRAS Audit File (IAF) for Singapore**, complete the following tasks:

1. [Import Electronic reporting (ER) configurations](#import).
2. [Associate sales tax codes with singaporean standard GST codes](#tax-codes)
3. [Enable features in Feature management](#features).
4. [Select the ER configuration in General ledger parameters](#gl-param).

### <a name="import"></a>Import ER configurations

Before you can generate a **IRAS Audit File (IAF) for Singapore**, you must import the latest versions of the following ER configurations.

| ER configuration name | Type | Description |
|-----------------------|------|--------------------|
| Standard Audit File (SAF-T) | Model | The common data model for different audit reports. |
| SAF-T General model mapping | Model mapping | The model mapping that provides general data source mapping. |
| IRAS Audit File - IAF in TXT (SG) | Format | IRAS Audit File for Singapore in pipe delimited text format. |

For more information about how to download ER configurations, see [Download ER configurations from the Global repository](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. Use the **Issue search** section of the [LCS](https://lcs.dynamics.com/v2) portal to find and read information about specific version of ER configuration.

> [!IMPORTANT]
> After all the ER configurations are imported, set the **Default for model mapping** option to **Yes** for the **SAF-T General model mapping** configuration.

### <a name="tax-codes"></a>Associate sales tax codes with Singaporean standard GST codes

As the documentation explains, in **IRAS Audit File (IAF) for Singapore**, sales tax codes that are used in Finance must be associated with Singaporean standard GST codes for the purpose of IAF reporting. 

In case your legal entity's GST codes set up is *in accordance* with the Singaporean standard GST codes, complete the following tasks:

1. Open the **Electronic reporting** workspace, in the configuration tree, select the **IRAS Audit File - IAF in TXT (SG)** electronic reporting format. 
2. Make sure that company you are working is the company for which you will be running **IRAS Audit File (IAF) for Singapore**.
3. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
4. Select the version of the format that you want to use on the left side of the **Application specific parameters** page.
7. Change the value of the **State** field to **Completed**, save your changes, and close the page.

In case your legal entity's GST codes set up *is **not** in accordance* with the Singaporean standard GST codes, to associate GST codes that are used in Finance with Singaporean standard GST codes, follow these steps.

1. Open the **Electronic reporting** workspace, in the configuration tree, select the **IRAS Audit File - IAF in TXT (SG)** electronic reporting format. 
2. Make sure that company you are working is the company for which you will be running **IRAS Audit File (IAF) for Singapore**.
3. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
4. Select the version of the format that you want to use on the left side of the **Application specific parameters** page.
5. On the **Lookup** FastTab, select **StandardTaxCodes_Lookup**, and then specify criteria on the **Conditions** FastTab by adding lines for each **Result** value which must be used in the selected company. If several **GST codes** in the selected company must result the same **Standard GST codes**, add a separate line for each **GST code** and specify the same **Standard GST code** for each one.
6. Select the value, **Other** as the last condition in the list. It must be set to **\*Not blank\*** in **GST code** column. Verify the value in the **Line** column that **Other** is the last condition in the table.
7. When you've finished setting up conditions, change the value of the **State** field to **Completed**, save your changes, and close the page.

### <a name="features"></a>Enable features in Feature management

1. Open the **Feature management** workspace.
2. On the **All** tab, in the feature list, find and select the following features:
 
    - [Standard Audit File for Tax (SAF-T) electronic report](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/standard-audit-file.md) - mandatory to be enabled
    - [Optimization of query data source creation time during execution of ER reports](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting) - optionally to be enabled
    - Optimize datasets memory consumption at ER reports runtime - optionally to be enabled
    - [Accelerate the ER labels storage](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-design-multilingual-reports#performance) - optionally to be enabled
    - [Use application specific parameters from previous versions of ER formats](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up#reuse-legal-entitydependent-parameters) - optionally to be enabled

3. Select **Enable now**.

### <a name="gl-param"></a>Select the ER configuration in General ledger parameters

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **General ledger parameters** page, on the **Standard Audit File for Tax (SAF-T)** tab, in the **Standard Audit File for Tax (SAF-T)** field, select **IRAS Audit File - IAF in TXT (SG)**.

## Generate an IRAS Audit File (IAF) for Singapore

To generate a **IRAS Audit File (IAF) for Singapore**, follow these steps.

1. Go to **General ledger** \> **Inquiries and reports** \> **Ledger reports** \> **General ledger statement by main account**.
2. In the report dialog box, set the following fields.

    | Field name | Description |
    | ---------- | ----------- |
    | From date, To date | Select dates to specify the date interval for the report. You can select dates within one fiscal year. |
    | Currency | Select **Accounting currency** to report amounts in the **Debit**, **Credit**, and **Accumulated balance** columns of the report in the accounting currency. Select **Reporting currency** to report those amounts in the reporting currency. |
    | Main financial dimension set | Select the standard financial dimension set, including the main account that the report uses to calculate the opening balance by main account at the beginning of the reporting period. For more information about financial dimension sets, see [Financial dimension sets](financial-dimension-sets.md). |
    | Group by main account | Select this checkbox to group general ledger account entries by main account on the report. When this checkbox is selected, the **Ledger account** column is hidden, and the amounts of the general ledger account entries that are reported for each main account are represented as aggregated amounts in the **Transaction posting date** and **Transaction number** columns. |
    | Include reversed | Select this checkbox if reversed transaction must be reported. |
    | Posting layer(s) | Select one or more posting layer transactions to include on the report. If you leave this field blank, all the posting layers are reported. |
    | Sales tax specification | Select this checkbox to include information about the sales tax codes and amounts for each general ledger account entry. This option is available only if the **Group by main account** checkbox is cleared. |
    | Settlement period | Select a settlement period to filter sales tax transactions on the report. If you leave this field blank, sales tax transactions from all settlement periods are included on the report. |
    | Split file by main accounts | Select this checkbox to split the report data into multiple files by main account. |

3. You can use the **Records to include** option to filter the data on the report by one or more main accounts.
4. On the **Run in the background** FastTab, you can specify parameters of the batch job and run the report in batch mode. When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).
