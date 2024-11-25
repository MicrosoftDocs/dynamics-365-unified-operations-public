---
title: Balance sheet financial reports
description: Learn about the default reports for balance sheets. It also describes the building blocks that are associated with these reports.
author: jinniew
ms.author: jiwo
ms.topic: article
ms.date: 06/17/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: FinanicalReports
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 52f78229-f531-4d16-b337-e2628994acb6
---

# Balance sheet financial reports

[!include [banner](../includes/banner.md)]

This article describes the default reports for balance sheets. It also describes the building blocks that are associated with these reports. 

## Default balance sheet reports

There are two default balance sheet reports. On one report, the sections are stacked. On the other report, the sections are side by side.

| Default report                       | What it does                                                                                                                           |
|--------------------------------------|--------------------------------------------------------------------------------------|
| Balance sheet – default              | Provides a view of the organization's financial position for the year.                    |
| Balance sheet and income statement side by side – default | Provides a view of the organization's financial position for the year side by side. |

## Building blocks
The balance sheet financial reports use the following building blocks.

| Default report                       | Row definition                       | Column definition             |
|--------------------------------------|--------------------------------------|-------------------------------|
| Balance sheet - default              | Balance sheet - default              | YTD and variance - default    |
| Balance sheet and income statement side by side – default | Balance sheet and income statement side by side – default | Year to date column - default |

### Row definition

The row definitions for both balance sheet reports contain sections for each part of a traditional balance sheet. The side-by-side report includes a column break, so that liability and the owner’s equity appear next to assets. The Main Account Category dimension is used to build both row definitions. Therefore, anyone can generate the reports without having to make any modifications.

### Column definition

The column definitions contain different types of columns to provide different levels of detail and financial data.

-   **YTD and Variance – Default column types:**
    -   **DESC** – The description from the row definition
    -   **FD** – Year-to-date financial data for the current year
    -   **FD** – Year-to-date financial data for the last year
    -   **CALC** – The variance from subtracting last year from this year

<!-- -->

-   **Year to Date Column – Default:**
    -   **DESC** – The description from the row definition
    -   **FD** – Year-to-date financial data for the current year



## Additional resources

[Financial reporting overview](financial-reporting-getting-started.md)

[View financial reports](view-financial-reports.md)

[Dynamics Financial Reporting Blog](https://blogs.msdn.com/b/dynamics_financial_reporting/)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
