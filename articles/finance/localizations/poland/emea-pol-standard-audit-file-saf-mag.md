---
title: SAF Inventory file - JPK_MAG
description: This article explains how users in legal entities in Poland can generate a SAF Inventory file - JPK_MAG in XML format.
author: liza-golub
ms.author: egolub
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 11/26/2024
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-11-30
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
ms.dyn365.ops.version: Version 1611
ms.assetid: b85c4019-f682-45bf-9a0d-c7549a2f1274
---

# SAF Inventory file - JPK_MAG

[!include [banner](../../includes/banner.md)]

This article provides an overview of how to set up Microsoft Dynamics 365 Finance to configure and generate the JPK_MAG file for legal entities with a primary address in Poland.

The SAF Warehouse Stock File (JPK_MAG) is a standardized electronic format that enables businesses to submit detailed records of their warehouse inventory movements to tax authorities in a structured and consistent manner. The file contains information about stock entries, withdrawals, and transfers, facilitating transparency and compliance during audits or tax inspections.

The JPK_MAG must be submitted electronically through the Polish tax authority’s portal and is required upon request by the tax authorities.

## Setup

Before you can generate a SAF Inventory file, you must complete the following setup.

1. [Import Electronic reporting configurations](#er-import).
2. [Set up Electronic reporting format in General ledger parameters](#er-format-setup).

### <a id="er-import"></a> Import Electronic reporting configurations

In Finance, import the following Electronic reporting (ER) configurations from Microsoft Dataverse.

For more information about how to import ER configurations, see [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

| ER configuration name       | Type          | Description |
|-----------------------------|---------------|-------------|
| Standard Audit File (SAF-T) | Model         | The common data model for different audit reports. |
| Standard Audit File model mapping | Model mapping | The model mapping that provides general source mapping for several electronic reports for Poland. |
| SAF Poland                  | Format        | The XML format that represents a parent format for several JPK formats for Poland. |
| Inventory (PL)           | Format        | The XML format that represents Inventory SAF-T Poland - JPK_MAG. |

Import the most recent versions of the configurations. 
The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!IMPORTANT]
> After all the ER configurations from the previous table are imported, set the **Default for model mapping** option to **Yes** for the **Standard Audit File model mapping** configuration.

### <a id="er-format-setup"></a> Set up Electronic reporting format in General ledger parameters
To set up Electronic reporting format in General ledger parameters, follow these steps.
1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
1. On the **Standard Audit File for Tax (SAT-T)** tab, in the **SAF Inventory** field, select the ER format, **Inventory (PL)**. 

## <a id="jpk-mag"></a>Generate a SAF Inventory file (JPK_MAG)

To generate a SAF Inventory file, go to **General ledger > Inquiries and reports > Standard Audit File for Tax (SAF-T) > SAF Inventory**, and set the following parameters.

| Parameter                | Description                                                                        |
|--------------------------|------------------------------------------------------------------------------------|
| From date                | Specify the first date to export reporting data for.                               |
| To date                  | Specify the last date to export reporting data for.                                |
| Authority identification | In the list, select the identifier of the tax authority to use in the export file. |
| Warehouse                | Specify the warehouse to export transactions for.                                  |

## Using batch jobs for JPK_MAG

Generating JPK_MAG report for a long period such as month or a quarter can include a large amount of data and take a long time; therefore, it is recommended to use batch jobs. 
Dialog page for every SAF report has a **Run in the background** tab. 
Open this tab to set up report's generation in batch mode. Select **Batch processing** check box. 
To learn more about batch processing, see [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md). 
To review batch jobs or find a generated file, follow these steps.
1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**, and find a line related to your job. 
1. Select **Show log** on the **Main menu**. If nothing is shown, no messages were produced when the file was generated. 
1. To see the file, select **Show files** on the **Main menu**, find a file that you need, and select **Open** on the **Main menu**.  

When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. 
For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).
