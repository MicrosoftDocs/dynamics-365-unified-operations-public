---
title: Sales tax settlement and numbering of pages in sales tax books
description: Learn about sales tax settlement and the numbering of pages in sales tax books for legal entities in Italy, including a description of various fields.
author: liza-golub
ms.author: egolub
ms.topic: conceptual
ms.date: 03/04/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2016-11-30
ms.search.form: TaxAuthority, TaxPeriod
ms.dyn365.ops.version: Version 1611
ms.assetid: af07d122-5694-4de6-96bf-7bf5478b0175
---

# Sales tax settlement and numbering of pages in sales tax books

The topic describes the sales tax settlement process for legal entities that have a primary address in Italy. It also explains how to manage the numbering of pages in sales tax books.

As of Microsoft Dynamics 365 Finance version 10.0.39, the Italian sales tax books functionality supports reporting of Italian sales tax books in the [Electronic reporting (ER) tool](/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting). It also accommodates reporting for [multiple value-added tax (VAT) registrations](../global/emea-multiple-vat-registration-numbers.md).

The sales tax settlement process can be run independently of the Italian sales tax books functionality. To separate the sales tax settlement process from the generation of the Italian sales tax book in ER, enable the **Separate sales tax payment report generation from sales tax settlement** feature in Feature management. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). When the **Separate sales tax payment report generation from sales tax settlement** feature is disabled, the Italian sales tax book in ER is automatically generated after the settlement is completed. For more information about the sales tax settlement process, see [Create a sales tax payment](/dynamics365/finance/general-ledger/tasks/create-sales-tax-payment).

The sales tax settlement process can be run in batch mode. To enable the sales tax settlement process for the settlement period to be run as a batch job in the background, select the **Use batch processing for sales tax settlement** checkbox for the sales tax settlement period on the **Sales tax settlement periods** page (**Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax settlement periods**). This approach is recommended if there are many tax transactions within a period interval.

According to Italian legislation, rules apply to settlement periods. For example, after the settlement period is closed, no change is allowed. You're required to report whether the settlement refers to the last period of the fiscal year. To determine whether the settlement period refers to a year closing, view the settlement period status. To support these rules, the following columns are added for period intervals on the **Sales tax settlement periods** page in legal entities that have an address in Italy.

| Field | Description |
|-------|-------------|
| Closed | A value that indicates whether the interval of the sales tax settlement period has been settled and closed. |
| Last period | Select this option if the period is the last period in a sales tax year. |

When the sales tax settlement process is run, the **Closed** parameter is automatically selected for the related period interval. Additionally, the **Close Italian sales tax book section** parameter of each [sales tax book section](emea-ita-sales-tax-books.md#sales-tax-book-sections) is updated with the closing date of the tax period. You can't post or reverse an invoice in sales tax book sections that has a date that's earlier than the closing date of the tax period.

For sales tax settlement periods that are associated with a sales tax authority that's connected to a vendor account that has an address in Italy, **Original** is the only value that can be selected in the **Sales tax payment version** field for the **Sales tax settlement** process.

When you run the sales tax settlement process for an Italian sales tax settlement period, the main accounts that are set up in the **Account gain** and **Account loss** fields for the related sales tax authority are used to posting rounding results.

As of Dynamics 365 Finance version 10.0.39, when [reporting of Italian sales tax books in the ER tool is enabled](emea-ita-sales-tax-books.md), the number of pages of Italian sales tax books is updated only when the [Italian sales tax books electronic report is generated](emea-ita-sales-tax-books.md#generate-the-italian-sales-tax-books-electronic-report) with the **Update number of pages** checkbox selected.

> [!IMPORTANT]
> To ensure correct numbering of pages, be sure to generate the Italian sales tax books electronic report with the **Update number of pages** checkbox selected at least once for each interval of the sales tax settlement period. If the **Update number of pages** checkbox is selected, and the **Attach report to Sales tax book status** checkbox is selected in the parameters of the sales tax settlement period, you can find the generated Italian sales tax books electronic report attached to the **Sales tax book status** records.
