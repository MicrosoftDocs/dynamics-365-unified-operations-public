---
title: Sales tax settlement and numbering of pages in Sales tax books
description: This article explains sales tax settlement and numbering of pages in Sales tax books for legal entities in Italy.
author: liza-golub
ms.date: 07/12/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: 
ms.search.region: Italy
ms.author: egolub
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 
ms.assetid: af07d122-5694-4de6-96bf-7bf5478b0175
ms.search.form: TaxAuthority, TaxPeriod
---

# Sales tax settlement and numbering of pages in Sales tax books

The topic describes specifics of Sales tax settlement process for legal entities with primary address in Italy and how to manage the numbering of pages in Sales tax books.

As of 10.0.39 version of Dynamics 365 Finance, the **Italian sales tax books** functionality supports reporting of Italian sales tax book in [Electronic reporting (ER) tool](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting) and accomodates reporting for [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md). 

**Sales tax settlement** process can be executed independently from **Italian sales tax books** functionality. To separate sales tax settlement process from generation of Italian sales tax book in electronic reporting tool, enable **Separate sales tax payment report generation from sales tax settlement** feature in **Feature management**. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). When **Separate sales tax payment report generation from sales tax settlement** feature is disabled, the Italian sales tax book in ER is generated automatically after the settlement is completed. For more information about **Sales tax settlement** process, see [Create a sales tax payment](https://learn.microsoft.com/en-us/dynamics365/finance/general-ledger/tasks/create-sales-tax-payment).

**Sales tax settlement** process can be run in batch mode. Select **Use batch processing for sales tax settlement** check box parameter for the **Sales tax settlement period** in **Tax > Indirect taxes > Sales tax > Sales tax settlement periods** to enable executing of tha sales tax settlement process for the settlement period as batch job in the background. This is recommended for a large number of tax transactions within a period interval.

Per Italian legislation, rules apply to settlement periods. For example, after the settlement period is closed, no change is allowed. You are required to report if the settlement refers to the last period on the fiscal year. View the settlement period status and report if it refers to a year closing. To support these rules, in legal entities with address in Italy, on **Sales tax settlement periods** page there are following columns added for **Period intervals**.

|    <strong>Field</strong>    |                                   <strong>Description</strong>                                    |
|------------------------------|---------------------------------------------------------------------------------------------------|
|   <strong>Closed</strong>    | Indicates if the interval of the sales tax settlement period has been settled and closed. |
| <strong>Last period</strong> |             Select this option if the period is the last period in a sales tax year.              |

When the **Sales tax settlement** process is executed, the **Closed** parameter is selected for related **Period interval** automatically. **Closed** parameter is updated together with **Close Italian sales tax book section** parameter of each of the [Sales tax book section](emea-ita-sales-tax-books.md#sales-tax-book-sections) with the closing date of the tax period. You can't post or reverse an invoice in sales tax book sections that has a date that is earlier than the closing date of the tax period.

For **Sales tax settlement periods** associated with **Sales tax authority** connected to a **Vendor account** with address in Italy, only **Original** **Sales tax payment version** can be selected for **Sales tax settlement** process.

When you run **Sales tax settlement** process for Italian **Sales tax settlement period**, the main accounts that are set up in **Account gain** and **Account loss** fields for related **Sales tax authority** are used for posting of rounding result.

As of 10.0.39 version of Dynamics 365 Finance, when [Italian sales tax book in Electronic reporting (ER) tool is enabled](emea-ita-sales-tax-books.md), number of page of Italian sales tax books is updated only when [Italian sales tax books electronic report is generated](emea-ita-sales-tax-books.md#generate-italian-sales-tax-books-electronic-report) with selected **Update number of pages** checkbox parameter.

> [!IMPORTANT]
> It is important to generate **Italian sales tax books electronic report** with selected **Update number of pages** checkbox at least onece per each interval of sales tax settlement period to support correct numbering of pages. When **Update number of pages** checkbox is selected and **Attach report to Sales tax book status** checkbox is selected in parameters of the **Sales tax settlement period**, you can find the generated **Italian sales tax books electronic report** attached to the **Sales tax book status** records.


