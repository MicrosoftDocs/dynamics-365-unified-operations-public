---
title: Tax reconciliation report for Iceland and Norway
description: This article explains how to set up and generate the Tax reconciliation report for legal entities with a primary address in Iceland or Norway.
author: liza-golub
ms.date: 07/11/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Iceland, Norway
ms.author: egolub
ms.search.validFrom: 
ms.dyn365.ops.version: 
---

# Tax reconciliation report for Iceland and Norway

[!include [banner](../includes/banner.md)]

This article describes how to generate the tax reconciliation report that is available for Icelandic and Norwegian legal entities.

In Finance, to generate the tax reconciliation report from legal entity with primary address in Iceland or Norway, go to **Tax** > **Inquiries and reports** > **Sales tax reports** > **Tax reconciliation report** and specify parameters of the report.

| **Parameter name** | **Description** |
|--------------------|-----------------|
| LEDGER ACCOUNTS: <br>-From account<br>-To Account | Use the **From account** and **To account** fields to define a range of main accounts. |
| Settlement period | Select the sales tax settlement periods to reconcile tax data for. |
| -From date<br>-To date | Specify the period for which you want to reconcile data that's posted in general ledger and tax. |
| Show details | Select this checkbox to include voucher details on the report. |
| Print sales tax codes | Select this checkbox to include sales tax code details on the report. |
| Sort order sales tax codes | Select this checkbox to sort data by sales tax code. When the checkbox isn't selected, the data in the report is ordered by main account. Select the **Print sales tax codes** checkbox together with the **Sort order sales tax codes** checkbox. |

Use the **Records to include** FastTab to define additional criteria for filtering data in the report. For example, **Sales tax code**.

Use the **Run in the background** FastTab to define batch-specific parameters and run the report execution in batch mode.

> [!NOTE]
> We recommend that you enable the **Performance improvement of the Tax reconciliation report** feature in the **Feature management** workspace.
> The **Performance improvement of the Tax reconciliation report** feature is available in the **Feature management** workspace as of Finance version 10.0.33. You can check for specific build information using Issue Search in the [LCS portal](https://lcs.dynamics.com/).

