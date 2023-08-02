---
# required metadata

title: Accounting source explorer
description: This article provides information about the Accounting source explorer page, which you can use for detailed analysis of the source information behind general ledger accounting entries.
author: RyanCCarlson2
ms.date: 11/21/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AccountingSourceExplorer
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 57b95899-7298-43c0-8034-45b5d993cbf2
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Accounting source explorer

[!include [banner](../includes/banner.md)]

This article provides information about the **Accounting source explorer** page, which you can use for detailed analysis of the source information behind general ledger accounting entries.

The **Accounting source explorer** page shows source information. You can use it either as a stand-alone tool or to analyze the details behind general ledger accounting entries. For example, you can use the page to get the most detailed source information for a balance in the trail balance or for a voucher transaction. You can then use the **Export to MS Excel** feature to further slice and dice the information in Microsoft Excel (for example, in a PivotTable or on a PivotTable report).

The **Accounting source explorer** page always shows the same total amount per ledger account as General ledger shows (for example, in a trial balance). As in a trial balance, you can display segments in separate columns. Just select the appropriate financial dimension set. 

You can use parameters to define a date interval for the analysis. This functionality also resembles the functionality in a trial balance.

For all documents that use the source document framework, the **Accounting source explorer** page shows additional information, based on accounting distributions and, if applicable, project accounting distributions. This information includes the **Monetary amount type**, **Project**, **Activity**, **Category**, and **Line property** values. Here are some examples of the analysis that you can do:

- Variances between purchase orders and vendor invoices, because each variance is represented by a monetary amount type, such as charge variance
- Billable versus non-billable hours and expenses per project, business unit, and main account

For source documents that use the source document reference identities concept, the **Accounting source explorer** page shows even more details, such as the **Customer**, **Vendor**, **Worker**, **Product**, **Quantity**, **Unit text**, and **Description** values. Here are some examples of the analysis that you can do:

- Hotel expenses per business unit and hotel brand for a fiscal period, based on expense reports
- Discounts per vendor, product, department

For these documents, you can also navigate to the actual source document from the **Accounting source explorer** page.

> [!NOTE]
> As of version 10.0.31, a new **Accounting source explorer advanced filtering** feature is available in Feature management. This feature replaces the **Update** button to provide a more robust advanced query experience that resembles what is available on the **Voucher transactions** page. The advanced filter will let you filter on similar fields to what you find on the **Voucher transactions query** page, such as **Ledger account**, **Business unit**, **Cost center**, and **Department**. 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
