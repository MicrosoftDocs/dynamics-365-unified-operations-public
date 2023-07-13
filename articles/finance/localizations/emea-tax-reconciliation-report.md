---
title: Tax reconciliation report for Iceland and Norway
description: This article explains how to set up and generate the Tax reconciliation report for legal entities that have a primary address in Iceland or Norway.
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

In Microsoft Dynamics 365 Finance, to generate the tax reconciliation report from a legal entity that has a primary address in Iceland or Norway, go to **Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Tax reconciliation report**. Then specify the parameters of the report.

| Parameter name | Description |
|----------------|-------------|
| **From account**, **To account** (in the **Ledger accounts** section) | Define a range of main accounts. |
| **Settlement period** | Select the sales tax settlement periods to reconcile tax data for. |
| **From date**, **To date** | Define the period for which to reconcile data that's posted in General ledger and Tax. |
| **Show details** | Select this checkbox to include voucher details on the report. |
| **Print sales tax codes** | Select this checkbox to include sales tax code details on the report. |
| **Sort order sales tax codes** | Select this checkbox to sort data by sales tax code. If the checkbox is cleared, the data on the report is sorted by main account. Select the **Print sales tax codes** checkbox together with the **Sort order sales tax codes** checkbox. |

Use the **Records to include** FastTab to define additional criteria for filtering data on the report. For example, you can filter by **Sales tax code** value.

Use the **Run in the background** FastTab to define batch-specific parameters and run the report in batch mode.

> [!NOTE]
> We recommend that you enable the **Performance improvement of the Tax reconciliation report** feature in the **Feature management** workspace. This feature is available in the **Feature management** workspace as of Finance version 10.0.33. You can check for specific build information by using Issue search in [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/).
