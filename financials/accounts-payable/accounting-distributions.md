---
# required metadata

title: Accounting distributions
description: This article provides information about accounting distributions and describes the options that are available for processing them. Accounting distributions are used to allocate monetary amounts for a source document to specific ledger accounts. 
author: twheeloc
manager: AnnBe
ms.date: 2015-12-04 16 - 01 - 41
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AccountingDistribution
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 17231
ms.assetid: 4581d5c2-e4b9-426f-bc5b-b7b6f253ebed
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Accounting distributions

This article provides information about accounting distributions and describes the options that are available for processing them. Accounting distributions are used to allocate monetary amounts for a source document to specific ledger accounts. 

Accounting distributions are a program-wide capability that is used and extended by each source document, such as a purchase order, vendor invoice, expense report, and free text invoice. By default, a default accounting distribution is generated for each source document line and monetary amount, and is conditionally enabled for modification. **Note: ** Some documents also support header document monetary amounts, such as charges for orders and invoices. The generic accounting distribution capabilities provide the following options for processing accounting distributions:

-   **Distribute amounts** – View and modify the accounting distributions for an individual document header or line and any child lines, such as taxes or charges.
    -   For the top monetary amount distributions (parent distributions), the main account and financial dimensions might be editable directly in the segmented entry control in the grid. The extended price is a typical example of such a parent distribution.
    -   The distributions amounts are based on the term currency for the document. Typically, this currency is the transaction currency. Accounting and reporting currency amounts are generated as part of subledger accounting.
    -   The distributions display the accounting date and accounting event. Typically, the accounting event is set to **None** until the document is posted/journalized. At that point, the accounting event becomes **Original**. After the distributions have been posted, you can't modify the distributions.
    -   **Split** button might be enabled for parent distributions. **Split** generates new accounting distributions, and the split can be based on percentage, amount, or quantity.
    -   The **Distribute equally** button can be used in combination with **Split** to automatically allocate the amount equally across all distributions.
    -   **Reset** button might be enabled for parent distributions when more than one distributions exists. **Reset** reverses any manual modification to the distribution by deleting all existing distributions and re-generating the default distributions.
    -   Any child distribution, such as discount, charge, and sales tax, always follows the parent distribution. You can view the parent/child relation at **Reference** &gt; **Parent information**.
    -   The main account and financial dimension might be editable for children too.
    -   The financial dimensions on the accounting distributions follow a defaulting pattern that a document can extended. For more details, see the related articles.
    -   Variance distributions might be generated in matching scenarios, such as matching between a vendor invoice and a purchase order. You can view the matching relations between accounting distribution at **Reference** &gt; **Document information**.
    -   **Correct** button appears and is enabled for documents that support corrections. **Correct** creates new distributions. First, distributions are created that reverse the original distributions. These distributions can't be modified. Next, new correct accounting distributions are created. These distributions can be modified if the original distributions could be modified.
    -   The **Project details** button is enabled as an extension when a line is related to a project. Project accounting distributions let you modify details such as the funding source and line property.
    -   You can view the current document accounting status in **Reference**. The status is for the entire document, and indicates whether the document is in process or completed.
-   ** View distributions** – View the accounting distributions for the all lines and monetary amounts on the document. You can't modify the accounting distributions from this view.


See also
--------

[Accounting distributions and subledger journal entries for free text invoices](accounting-distributions-subledger-journal-entries-free-text-invoices.md)

[Dimension defaulting in accounting distributions (blog)](http://blogs.msdn.com/b/ax_gfm_framework_team_blog/archive/2013/12/16/dimension-defaulting-in-accounting-distributions-blog-1-introduction.aspx)

