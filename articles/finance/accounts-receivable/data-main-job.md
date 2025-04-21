---
title: Data maintenance jobs for cleaning temporary data
description: Learn about the data maintenance jobs for cleaning temporary data.
author: JodiChristiansen
ms.author: reetuchopra
ms.topic: article
ms.date: 04/21/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-02-09
ms.search.form: CustPosting, CustVendExternalItem
ms.dyn365.ops.version: 10.0.25
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
---

# Data maintenance jobs for cleaning temporary data

[!include [banner](../includes/banner.md)]

When you update to version 10.0.44, the data update automatically schedules a data maintenance jobs for cleaning up free text invoice temporary data used in Free Text Invoice reports and for cleaning up sales 
invoice temporary data used in Sales Invoice reports, users’ needs to manually schedule the data maintenance job. These jobs can be accessed through System administration > Periodic tasks > Data maintenance.
Previously, temporary data from Free Text Invoice and Sales Invoice reports accumulated in the system without an automated cleanup mechanism. While users could manually delete these records, it was inefficient and 
could impact performance over time. To address this, Microsoft has introduced two new data maintenance jobs: one for cleaning up free text invoice temporary data used in Free Text Invoice reports and another for 
cleaning up sales invoice temporary data used in Sales Invoice reports. 
These data maintenance jobs are scheduled to run daily. By default, they retain data for 30 days and remove older records in small, controlled batches. However, users can modify the retention period by updating
the "Number of days to retain customer invoice reporting data" parameter in AR parameters > Updates > Data Maintenance. This flexibility ensures that organizations can set their own data retention policies based
on their requirements.
The Free Text Invoice job cleans up data in FreeTextInvoiceTmp and FreeTextInvoiceHeaderFooterTmp tables, where users must define the retention period for each company individually. The Sales Invoice job, on the 
other hand, cleans up data in SalesInvoiceTmp, SalesInvoiceTmp_IN, and SalesInvoiceHeaderFooterTmp tables. Since SalesInvoiceTmp does not store data per company, the retention period is configured in the default
DAT legal entity. 

