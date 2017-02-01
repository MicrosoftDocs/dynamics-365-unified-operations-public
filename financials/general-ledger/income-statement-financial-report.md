---
# required metadata

title: Income statement financial report | Microsoft Docs
description: This article describes the default report for income statements. It also describes the building blocks that are associated with this report. 
author: twheeloc
manager: AnnBe
ms.date: 2015-11-04 19:35:20
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 12294
ms.assetid: d91a6bb8-63ec-4456-93c4-29c8789fb26d
ms.region: Global
# ms.industry: 
ms.author: jcart

---

# Income statement financial report

This article describes the default report for income statements. It also describes the building blocks that are associated with this report. 

Default income statement report
-------------------------------

| Default report             | What it does                                                                                              |
|----------------------------|-----------------------------------------------------------------------------------------------------------|
| Income Statement – Default | Provides a view of the organization’s profitability for the current period and also for the year to date. |

## Building blocks
The income statement financial report uses the following building blocks.

| Default report             | Row definition                     | Column definition          |
|----------------------------|------------------------------------|----------------------------|
| Income Statement - Default | Summary Income Statement - Default | Periodic and YTD - Default |

### Row definition

The row definition, Summary Income Statement – Default, contains a section for each part of a traditional income statement. The Main Account Category dimension is used to build this row definition. Therefore, anyone can generate the report without having to make any modifications.

### Column Definition

The column definitions contain different types of columns to provide different levels of detail and financial data.

-   **Periodic and YTD – Default column types:**
    -   **DESC** – The description from the row definition
    -   **FD** – Financial data for the current period
    -   **FD** – Financial data for the year to date

 

See also
--------

[Financial reporting](https://docs.microsoft.com/en-us/dynamics365/operations/financials/general-ledger/financial-reporting)

[View financial reports](https://docs.microsoft.com/en-us/dynamics365/operations/financials/general-ledger/view-financial-reports)

[Dynamics Financial Reportign Blog](http://blogs.msdn.com/b/dynamics_financial_reporting/)

