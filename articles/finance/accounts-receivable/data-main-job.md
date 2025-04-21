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

Starting in Dynamics 365 Finance version 10.0.44, data maintenance jobs are automatically scheduled. These jobs clean up:
 - free text invoice temporary data used in **Free text invoice** reports
 - sales invoice temporary data used in **Sales invoice** reports
To schedule the data maintenance job, go to **System administration** > **Periodic tasks** > **Data maintenance**.

## New maintenance jobs
Previously, temporary data from **Free text invoice** and **Sales invoice** reports accumulated without an automated cleanup mechanism. 
Two new data maintenance jobs are available: 
 - Clean up free text invoice temporary data used in **Free text invoice** reports
 - Clean up sales invoice temporary data used in **Sales invoice** reports
  
These data maintenance jobs are scheduled to run daily. By default, they retain data for 30 days and remove older records in small, controlled batches. 
To modify the retention period, follow these steps:
1. Go to **Accounts receivable parameters** > **Updates** > **Data maintenance**.
2. Update **Number of days to retain customer invoice reporting data** field. This allows organizations to set their own data retention policies based on their requirements.

The **Free text invoice** job - cleans up data in FreeTextInvoiceTmp and FreeTextInvoiceHeaderFooterTmp tables. Users must define the retention period for each company individually.
The **Sales invoice job** - cleans up data in SalesInvoiceTmp, SalesInvoiceTmp_IN, and SalesInvoiceHeaderFooterTmp tables. The SalesInvoiceTmp table doesn't store data per company, the retention period is configured in the default DAT legal entity. 

