---
# required metadata

title: Accounting source explorer
description: This article provides information about Accounting source explorer, which you can use for detailed analysis of the source information behind general ledger accounting entries.
author: twheeloc
manager: AnnBe
ms.date: 2015-12-03 20 - 15 - 14
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 15391
ms.assetid: 57b95899-7298-43c0-8034-45b5d993cbf2
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Accounting source explorer

This article provides information about Accounting source explorer, which you can use for detailed analysis of the source information behind general ledger accounting entries.

Accounting source explorer is a new page that shows source information. You can use Accounting source explorer either as a stand-alone tool or to analyze the details behind general ledger accounting entries. For example, you can use Accounting source explorer to get the most detailed source information for a balance in Trail balance or for a voucher transaction. You can then use the Export to MS Excel feature to further slice and dice the information in Microsoft Excel (for example, in a PivotTable or on a PivotTable report). Accounting source explorer always shows the same total amount per ledger account as General ledger shows (for example, in Trial balance). As in Trial balance, you can display segments in separate columns. Just select the appropriate financial dimension set. You can use parameters to define a date interval for the analysis. This functionality also resembles the functionality in Trial balance. For all documents that use the source document framework, Accounting source explorer shows additional information, based on accounting distributions and, if applicable, project accounting distributions. This information includes the monetary amount type, project, activity, category, and line property. Here are some examples of the analysis that you can do:

-   Variances between purchase orders and vendor invoices, because each variance is represented by a monetary amount type, such as charge variance
-   Billable versus non-billable hours and expenses per project, business unit, and main account

For source documents that use the source document reference identities concept, Accounting source explorer shows even more details, such as the customer, vendor, worker, product, quantity, unit text, and descriptions. Here are some examples of the analysis that you can do:

-   Hotel expenses per business unit and hotel brand for a fiscal period, based on expense reports
-   Discounts per vendor, product, department

For these documents, you can also navigate to the actual source document from Accounting source explorer.

