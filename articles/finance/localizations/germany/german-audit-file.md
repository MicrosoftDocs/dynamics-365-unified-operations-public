--- 
title: Generate German audit file
description: Learn how to generate a German audit file with Germany as the region of legal entity primary address in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 12/03/2025
ms.custom:
  - bap-template
ms.reviewer: johnmichalak   
ms.search.region: Germany
ms.search.validFrom: 2016-06-30
---

# Generate German audit file

[!include [banner](../../includes/banner.md)]

This article explains how to generate a German audit file in Microsoft Dynamics 365 Finance.

To generate a GDPdU audit file, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Periodic tasks \> Data export**.
1. In the **Format mapping** field, select **German audit file output** and select **OK**.
1. On the **Electronic report parameters** dialog, fill in the following parameters as necessary.
- **Comment** - specify the comment that wil be reported in the `<Comment>` tag of the index file.
- **Media** - specify the media that will be reported in the `<Media><Name>` tag of the index file; this value will be used as the folder name in the export archive.
- **Version** - specify the version that wil be reported in the `<Version>` tag of the index file.
1. In the **Table Group** field, select one of the values from the list: [Ledger accounts](emea-deu-gdpdu-audit-data-export.md#general-ledger), [Tax codes](emea-deu-gdpdu-audit-data-export.md#tax-ledger), [Accounts payable](emea-deu-gdpdu-audit-data-export.md#accounts-payable), [Accounts receivable](emea-deu-gdpdu-audit-data-export.md#accounts-receivable), [Fixed assets](emea-deu-gdpdu-audit-data-export.md#fixed-assets).
1. In the **Period - date from** and **Period - date to** fields, specify the start and end dates of the period that you want to generate the report for.
1. Select **Include "Create by"** checkbox to include the **Created by** information for transactions in the export file.
1. Select **Show only main accounts without dimensions** checkbox to exclude dimensions information for transactions in the export file, only Main account without dimensions will be reported.
1. Select **OK** to generate GDPdU audit file.

A GDPdU audit file for a long time period, such as a quarter or a year, can include a large amount of data and take a long time to be generated. 
Therefore, we recommend that you use batch jobs. The dialog for the **Electronic report parameters** includes a **Run in the background** tab where you can set up report generation in batch mode. 
Set the **Batch processing** option to **Yes**. Learn more about batch processing in [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).

To review batch jobs or find a generated file, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
1. Find a line that is related to your job, and then select **Show log**. If nothing is shown, no messages were produced when the file was generated.
1. To view a file, select **Show files**, find the file that you need, and then select **Open**.

Learn more about how to configure a destination for each ER format configuration and its output component in [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

> [!NOTE]
> As of version 70 of the **Data export model**, the following replacements are implemented for some of the special symbols in text that's being written in column 11 (**BUCHUNGSTEXT**) of the Sachkontobuchungen output file:
> - Any sequence of symbols or individual symbols Carriage Return (ASCII code 13) and Line Feed (ASCII code 10) are replaced with space (ASCII code 32).
> - The double quotes symbol (ASCII code 34) is replaced with the single quote symbol (ASCII code 39).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
