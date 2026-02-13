---
title: Export financial information (SIE) in Sweden
description: Learn how to export financial information for auditors in Sweden in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 10/01/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Sweden
ms.search.validFrom: 2016-05-31
---

# Export financial information \(SIE\) in Sweden

[!include[banner](../../includes/banner.md)]

This article explains how to export financial information in Microsoft Dynamics 365 Finance in the mandatory standard for exchanging accounting data electronically between different financial systems, SIE (Standard Import/Export) requirement in Sweden.

> [!NOTE]
> This topic describes the functionality available in Microsoft Dynamics 365 Finance as of version **10.0.46**, which introduces the **\[Sweden\] Standard Import and Export (SIE) modernization in Electronic Reporting** feature. This feature enables the system to use the **Standard Import and Export SIE TXT (SE)** Electronic Reporting (ER) format, along with the **Standard Import and Export SIE** model and model mapping under the **Ledger accounting reports** model.
> 
> When the **\[Sweden\] Standard Import and Export (SIE) modernization in Electronic Reporting** feature is disabled, the system continues to use the legacy  **SIE export format (SE)** ER format and the corresponding **SIE export model** model and model mapping under the **Ledger accounting reports** model are used.
>
> The scope of support and the algorithms implemented in the legacy ER configurations differ from those in the new configurations enabled by the **\[Sweden\] Standard Import and Export (SIE) modernization in Electronic Reporting** feature.
>
> The legacy ER configurations have been [announced for deprecation](../../get-started/removed-deprecated-features-finance.md#sie-export-format-se-er-format-sie-export-model-for-sweden) and will be removed in a future release:
> - **SIE export format (SE)** ER format
> - **SIE export model** model and model mapping under the **Ledger accounting reports** model

As of **version 10.0.46** of Dynamics 365 Finance, you can export financial data using the formats specified by the Standard Import Export Group (SIE), which is an organization in Sweden that develops standard formats.

- **Type 1** - Export of closing balances.
- **Type 2** - Export of period end balances.
- **Type 3** - Export of object balances.
- **Type 4E** - Export of transactions.
- **Type 4I** - Import of transactions, contains only verification entries. 

### <a name="import"></a> Import ER configurations

In Finance, import the following ER configurations from the Global repository.

| ER configuration name                        | Configuration type |
|----------------------------------------------|--------------------|
| **Ledger accounting reports**                | Model              |
| **Standard Import and Export SIE**           | Model under the **Ledger accounting reports** model, that contain mapping for **Standard Import and Export SIE TXT (SE)** format |
| **Standard Import and Export SIE TXT (SE)**  | Format (exporting) |

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

## Prerequisites

Before you export data, set up a Standardiserad Räkenskaps Utdrag (SRU) code for each general ledger account. 

1. In Dynamics 365 Finance, go to **General ledger** \> **Chart of accounts** \> **Accounts** \> **Main accounts**.
1. For each main account, specify the SRU code in the **SRU code** field.

Enable features in Feature management, following these steps.

1. In Dynamics 365 Finance, go to **Feature management** \> **All**.
1. In the feature list, find and select the following features:

    - **\[Sweden\] Standard Import and Export (SIE) modernization in Electronic Reporting** – This feature is available in Finance version **10.0.46**. This feature replaces the legacy 'SIE export format (SE)' format with the new 'Standard Import and Export SIE TXT (SE)' format under the 'Ledger accounting reports' model in Electronic Reporting. This new format enables the export of key financial data, including balances and transactions, in accordance with SIE Types 1 through 4. It supports larger datasets and introduces a redesigned export process that ensures faster generation, reduced system load, and a simplified workflow. By adopting this feature, Swedish entities can efficiently meet statutory reporting obligations while benefiting from a more scalable, performant, and maintainable export solution.
    - **Performance enhancement for general ledger dimension set balance calculation** – This feature must be enabled if you enable the **\[Sweden\] Standard Import and Export (SIE) modernization in Electronic Reporting** feature. Learn more about the **Performance enhancement for general ledger dimension set balance calculation** feature in [New financial dimension sets](../../general-ledger/financial-dimension-set-new.md).

1. Select **Enable now**.

## Set up ER format in General ledger parameters

To set up the ER format, follow these steps:

1. In Finance, go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
1. On the **General ledger parameters** page, on the **Ledger** tab, in the **Ledger transactions export format** field, select **Standard Import and Export SIE TXT (SE)**.

## Export financial data in SIE format

To export financial data using the formats specified by the SIE, follow these steps:
   
1. In Dynamics 365 Finance, go to **General ledger** \> **Periodic tasks** \> **SIE export**.
1. On the **Electronic report parameters** dialog page, specify the report parameters.

| Parameter                      | Description |
|--------------------------------|--------------------|
| SIE type                                | Select one of the SIE types from the dropdown list.             |
| Report composition (only for type 4E)   | Select one or many optional part of the Type 4E you want to include in SIE export file. |
| From date <br> To date                  | Specify the period for which you want to generate the SIE export file.|
| Currency                                | Select one of the options provided: Accounting or Reporting currency. |
| Posting layer                           | Select one or many Posting layers to include data in the SIE export file. |
| Financial dimension set                 | For Type 3 (Export of object balances), select the Financial dimension set that defines the objects you want to export financial data for.  |
| Include balances of the previous year  | Select this checkbox to include optional balances of the previous year. |
| Budget model                            | Select the Budget model from the dropdown list to include budget information in SIE export file. |
| Type of chart of accounts               | Select one of the options from the list of available options. This value is reported in `#KPTYP` field of the export file. |

1. Select **OK** to generate the report. 

An SIE report for a long time period, such as a quarter or a year, can include a large amount of data and take a long time to be generated. 
Therefore, we recommend that you use batch jobs. 
The dialog for the SIE report includes a **Run in the background** tab where you can set up report generation in batch mode. Set the **Batch processing** option to **Yes**. Learn more about batch processing in [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).

To review batch jobs or find a generated file, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
1. Find a line that relates to your job, then select **Show log**. If nothing is shown, no messages were produced when the file was generated.
1. To view a file, select **Show files**, find the file that you need, then select **Open**.

Learn more about how to configure a destination for each ER format configuration and its output component in [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
