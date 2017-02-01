---
# required metadata

title: Balance sheet financial reports | Microsoft Docs
description: This article describes the default reports for balance sheets. It also describes the building blocks that are associated with these reports. 
author: twheeloc
manager: AnnBe
ms.date: 2015-11-04 19:29:22
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
ms.custom: 12274
ms.assetid: 0902397b-0e45-4284-8cf9-147d20c3de64
ms.region: Global
# ms.industry: 
ms.author: jcart

---

# Balance sheet financial reports

This article describes the default reports for balance sheets. It also describes the building blocks that are associated with these reports. 

Default balance sheet reports
-----------------------------

There are two default balance sheet reports. On one report, the sections are stacked. On the other report, the sections are side by side.

| Default report                       | What it does                                                                                                                           |
|--------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| Balance Sheet – Default              | Provides a view of the organization's financial position for the year.                                                                 |
| Side by Side Balance Sheet – Default | Provides a view of the organization's financial position for the year. Assets and liability and shareholder’s equity are side by side. |

## Building blocks
The balance sheet financial reports use the following building blocks.

| Default report                       | Row definition                       | Column definition             |
|--------------------------------------|--------------------------------------|-------------------------------|
| Balance Sheet - Default              | Balance Sheet - Default              | YTD and Variance - Default    |
| Side by Side Balance Sheet – Default | Side by Side Balance Sheet – Default | Year to Date Column - Default |

### Row definition

The row definitions for both balance sheet reports contain sections for each part of a traditional balance sheet. The side-by-side report includes a column break, so that liability and the owner’s equity appear next to assets. The Main Account Category dimension is used to build both row definitions. Therefore, anyone can generate the reports without having to make any modifications.

### Column definition

The column definitions contain different types of columns to provide different levels of detail and financial data.

-   **YTD and Variance – Default column types:**
    -   **DESC** – The description from the row definition
    -   **FD** – Year-to-date financial data for the current year
    -   **FD** – Year-to-date financial data for the last year
    -   **CALC** – The variance from subtracting last year from this year

<!-- -->

-   **Year to Date Column – Default:**
    -   **DESC** – The description from the row definition
    -   **FD** – Year-to-date financial data for the current year

 

See also
--------

[Financial reporting](https://docs.microsoft.com/en-us/dynamics365/operations/financials/general-ledger/financial-reporting)

[View financial reports](https://docs.microsoft.com/en-us/dynamics365/operations/financials/general-ledger/view-financial-reports)

[Dynamics Financial Reporting Blog](http://blogs.msdn.com/b/dynamics_financial_reporting/)

