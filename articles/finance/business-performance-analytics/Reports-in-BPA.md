---
title: Reports in Business performance analytics
description: Learn about reports that are related to the record-to-report value chain in business performance analytics, including a table outlining various aspects of reports.
author: jinniew
ms.author: jiwo
ms.topic: conceptual
ms.date: 05/20/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Reports in Business performance analytics

[This article is prerelease documentation and is subject to change.]

This article describes the financial reports that are available out of the box in Business performance analytics. These reports were designed to provide a detailed overview of an organization's financial health, so that stakeholders can make informed decisions and drive business success. To better understand these reports, stakeholders can use the slicer, filter pane, and drill-in functions. The availability of these functions depends on the report. Slicers are filters that are available directly on the report page, whereas the filter pane must be opened before users can access the filters in it. When users hover over a table, the drill-in functionality is available in the upper right. Users must first select the direction that they want to drill in. They can then select a data point to reference where they want to drill from.

All reports use a data model in Microsoft Power BI. They can also easily be customized to suit the needs of your organization. For more information, see [Create business performance analytics reports](how-to-create-and-edit-reports.md).

> [!Important]
> Out-of-the-box reports are Microsoft-type reports. These types of reports are limited in their capacity to be updated as users can't rename, delete, or edit this type of report. If a user wishes to rename or edit a Microsoft type report, they should duplicate the report to make a Custom type report and then make the changes with the duplicate.

## Record to report

The following table describes the reports that are related to the record-to-report value chain in Business performance analytics.

| Report                             | Finance and operations report | Purpose |
| ---------------------------------- | ----------------------------- | ------- |
| Balance sheet                      | Balance sheet                 | This report provides a view of the organization's financial position for the year. The account category setup in finance and operations apps is used to create the structure of the balance sheet. |
| Budget vs actual                   | Budget vs actual              | This report compares the planned budget to actual financial amounts to help organizations identify areas where spending is in line with expectations and areas that require more attention. |
| Financial performance              | Not applicable                | This report provides an in-depth analysis of a company's financial performance. It highlights key metrics, such as revenue, expenses, net income, and cash flow. |
| General ledger dimension details   | Dimension statement           | This report breaks the general ledger down into its constituent dimensions to offer detailed insights into each aspect of the organization's financial transactions. |
| General ledger transaction details | Ledger transaction list       | This report presents a comprehensive view of all financial transactions that have been recorded in the general ledger, so that stakeholders can track and analyze the flow of funds throughout the organization. |
| Profit and loss                    | Profit and loss               | This report summarizes an organization's revenues, costs, and expenses over a specific period, and provides a view of the company's overall profitability. |

## Procure to pay

The following table describes the reports that are related to the procure-to-pay value chain in Business performance analytics.

| Report                    | Finance and operations report | Purpose                                                                                                                         |
| ------------------------- | ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Purchase orders           | Not applicable        | This report provides detailed information about purchase orders, including order dates, supplier details, items ordered, and quantities.   |
| Vendor aging              | Vendor aging report           | This report helps organizations track outstanding vendor invoices by age, allowing them to manage cash flow and vendor relationships effectively. |
| Vendor invoices           | Vendor invoice transaction report         | This report summarizes all vendor invoices received, including invoice dates, amounts, and payment status.                       |
| Vendor payments           | Vendor posted payment journal report         | This report outlines payments made to vendors, detailing payment dates, amounts, and associated purchase orders or invoices.       |
| Vendor transaction details| Not applicable       | This report presents a comprehensive view of all transactions with vendors, including orders, invoices, payments, and credits.              |

## Order to cash

The following table describes the reports that are related to the procure-to-pay value chain in Business performance analytics. Additional reports will be added as we incrementally release the Order to Cash value chain.

| Report                   | Finance and operations report | Purpose                                                                                                                     |
| ------------------------ | ----------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Sales aging              | Sales aging report            | This report helps organizations track outstanding customer invoices by age, enabling effective management of receivables and cash flow. |
| Sales transaction details| Transactions report        | This report provides a detailed view of all sales transactions, including order dates, customer details, items sold, and amounts.        |


