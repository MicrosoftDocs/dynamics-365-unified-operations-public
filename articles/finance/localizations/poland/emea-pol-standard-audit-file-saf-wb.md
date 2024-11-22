---
title: SAF Bank statement file - JPK_WB
description: Users in legal entities in Poland can generate a SAF Bank statement file - JPK_WB in XML format.
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

# SAF Bank statement file - JPK_WB

[!include [banner](../../includes/banner.md)]

Users in legal entities in Poland can generate a SAF Bank statement file - JPK_WB in XML format. 

## Setup

Before you can generate a SAF Bank statement file, you must complete the following setup.

1. [Import Electronic reporting configurations](#er-import)
2. [Set up Electronic reporting format in General ledger parameters](#er-format-setup)

### <a id="er-import"></a> Import Electronic reporting configurations

In Finance, import the following versions or later of these Electronic reporting (ER) configurations from Dataverse.

For more information about how to import ER configurations, see [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

| ER configuration name       | Type          | Description |
|-----------------------------|---------------|-------------|
| Standard Audit File (SAF-T) | Model         | The common data model for different audit reports. |
| Standard Audit File model mapping | Model mapping | The model mapping that provides general source mapping for several electronic reports for Poland. |
| SAF Poland                  | Format        | The XML format that represents a parent format for several JPK formats for Poland. |
| Bank Statement (PL)         | Format        | The XML format that representsBank Statement (WB) SAF-T for Poland. |

Import the most recent versions of the configurations. 
The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!IMPORTANT]
> After all the ER configurations from the previous table are imported, set the **Default for model mapping** option to **Yes** for the **Standard Audit File model mapping** configuration.

### <a id="er-format-setup"></a> Set up Electronic reporting format in General ledger parameters

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
2. On the **Standard Audit File for Tax (SAT-T)** tab, in the **SAF Bank statements** field, select the ER format, **VAT Invoices (PL)**. 

## <a id="jpk-wb"></a>Generate a SAF Bank statement file (JPK_WB)

To generate a SAF Bank statement file, click **General ledger > Inquiries and reports > Standard Audit File for Tax (SAF-T) > SAF Bank statement**, and set the following parameters.

| Parameter                | Description                                                                        |
|--------------------------|------------------------------------------------------------------------------------|
| From date                | Specify the first date to export reporting data for.                               |
| To date                  | Specify the last date to export reporting data for.                                |
| Authority identification | In the list, select the identifier of the tax authority to use in the export file. |
| Bank account             | Specify the bank account to export transactions for.                               |

The **SAF Bank statement** file includes information about transactions posted during the specified period of time for the bank account selected on the report's dialog. The name of the counterparty reported in the **NazwaPodmiotu** element is collected from the **Customers** (**Accounts receivable** > **Customers** > **All customers**) and **Vendors** (**Accounts payable** > **Vendors** > **All vendors**) master data of the system registered in the legal entity as it relates to the posted bank transaction. The operation description reported in the **OpisOperacji** element is collected from the **Description** field of the bank transaction.

## Using batch jobs for JPK_WB

Generating JPK_WB report for a long period such as month or a quarter can include a huge data and take a long time. 
For such cases, it is recommended to use batch jobs. 
Dialog page for every SAF report has a **Run in the background** tab. 
Open this tab to set up report's generation in batch mode. Select **Batch processing** check box. 
To learn more about batch processing, see [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md). To review batch jobs or find a generated file, go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**, and find a line related to your job. Select **Show log** on the **Main menu**. If nothing is shown, no messages were produced when the file was generated. To see the file, select **Show files** on the **Main menu**, find a file that you need, and select **Open** on the **Main menu**.  

When an electronic report is generated in batch mode, you can find related batch information and the generated output file as 
an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. 
For more information about how to configure a destination for each ER format configuration and its output component, 
see [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).
