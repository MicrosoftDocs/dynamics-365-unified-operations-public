---
title: JPK_KR_PD reporting
description: This article explains how to report JPK_KR_PD in legal entities in Poland.
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
## JPK_KR_PD reporting

To generate a SAF Accounting Books Income Tax - JPK_KR_PD, go to **General ledger** \> **Inquiries and reports** \> **Standard Audit File for Tax (SAF-T)** \> **Standard Audit File Accounting Books Income Tax**, set the following parameters, and then select **OK**.

| Parameter | Description |
|---|---|
| From date | Specify the first date to export reporting data for. |
| To date | Specify the last date to export reporting data for. |
| Print with zero balances | By default, the **ZOiS** section of the SAF Accounting Books Income Tax - JPK_KR_PD includes main accounts that have a non-zero opening balance and/or transactions in the reporting period. Select this checkbox if you also want to include main accounts that have a zero opening balance and no turnover during the reporting period. | 
| Purpose of submission | <p>Select one of the following values to specify the purpose of the report submission:</p><ul><li>JPK for the first time</li><li>JPK correction</li></ul> |
| Report composition | <p>Select one or more of the following values to specify the sections of the report that you want to generate:</p><ul><li>ZOiS</li><li>Dziennik (includes Dziennik, KontoZapis, Ctrl, Kontrahent)</li><li>RPD</li></ul> |
| Include closing transactions | Select this parameter to include closing transactions in the data that is exported. |
| Include reversal | Select this parameter to include reversed transactions in the data that is exported. |
| Posting layer | Select one or more posting layers to consider transactions from. This parameter affects all parts of the report. |
| Update balances | Select this checkbox to update balances before report generation. |

## Using a batch job to generate a SAF Accounting Books Income Tax - JPK_KR_PD

A SAF Accounting Books Income Tax - JPK_KR_PD for a long period, such as a month or a quarter, can include a large amount of data and take a long time to be generated. Therefore, we recommend that you use batch jobs. The dialog box for every SAF report includes a **Run in the background** tab where you can set up report generation in batch mode. Set the **Batch processing** option to **Yes**. Learn more about batch processing in [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).

To review batch jobs or find a generated file, follow these steps.

1. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
1. Find a line that is related to your job, and then select **Show log**. If nothing is shown, no messages were produced when the file was generated.
1. To view a file, select **Show files**, find the file that you need, and then select **Open**.

When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.

Learn more about how to configure a destination for each ER format configuration and its output component in [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).
