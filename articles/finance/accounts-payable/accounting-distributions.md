---
# required metadata

title: Accounting distributions
description: This article provides information about accounting distributions and describes available processing options.
author: sunfzam
ms.date: 09/17/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AccountingDistribution
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 9030355d-8e6e-408b-9e7d-7b346eaa652c
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Accounting distributions

[!include [banner](../includes/banner.md)]

This article provides information about accounting distributions and describes the options that are available for processing them. Accounting distributions are used to allocate monetary amounts for a source document to specific ledger accounts. 

Accounting distributions are a program-wide capability that is used and extended by each source document, such as a purchase order, vendor invoice, expense report, and free text invoice. By default, a default accounting distribution is generated for each source document line and monetary amount, and is conditionally enabled for modification. 

> [!NOTE] 
> Some documents also support header document monetary amounts, such as charges for orders and invoices. 

The generic accounting distribution capabilities provide the following options for processing accounting distributions:

-   **Distribute amounts** – View and modify the accounting distributions for an individual document header or line and any child lines, such as taxes or charges.
    -   For the top monetary amount distributions (parent distributions), the main account and financial dimensions might be editable directly in the segmented entry control in the grid. The extended price is a typical example of such a parent distribution.
    -   The distributions amounts are based on the term currency for the document. Typically, this currency is the transaction currency. Accounting and reporting currency amounts are generated as part of subledger accounting.
    -   The distributions display the accounting date and accounting event. Typically, the accounting event is set to **None** until the document is posted/journalized. At that point, the accounting event becomes **Original**. After the distributions have been posted, you can't modify the distributions.
    -   **Split** button might be enabled for parent distributions. **Split** generates new accounting distributions, and the split can be based on percentage, amount, or quantity.
    -   The **Distribute equally** button can be used in combination with **Split** to automatically allocate the amount equally across all distributions.
    -   **Reset** button might be enabled for parent distributions when more than one distribution exists. **Reset** reverses any manual modification to the distribution by deleting all existing distributions and re-generating the default distributions.
    -   Any child distribution, such as discount, charge, and sales tax, always follows the parent distribution. You can view the parent/child relation at **Reference** &gt; **Parent information**.
    -   The main account and financial dimension might also be editable for children.
    -   The financial dimensions on the accounting distributions follow a defaulting pattern that a document can extended.
    -   Variance distributions might be generated in matching scenarios, such as matching between a vendor invoice and a purchase order. You can view the matching relations between accounting distribution at **Reference** &gt; **Document information**.
    -   **Correct** button appears and is enabled for documents that support corrections. **Correct** creates new distributions. First, distributions are created that reverse the original distributions. These distributions can't be modified. Next, new correct accounting distributions are created. These distributions can be modified if the original distributions could be modified.
    -   The **Project details** button is enabled as an extension when a line is related to a project. Project accounting distributions let you modify details such as the funding source and line property.
    -   You can view the current document accounting status in **Reference**. The status is for the entire document, and indicates whether the document is in process or completed.
-   **View distributions** – View the accounting distributions for all lines and monetary amounts on the document. You can't modify the accounting distributions from this view.

A feature has been added that validates the accounting distribution table to ensure that new fields are properly set up. This feature is called **Enable additional validation of data for documents using the source document accounting framework**. This feature was turned on by default in version 10.0.29. 

For more information, see [Accounting distributions and subledger journal entries for vendor invoices](accounting-distributions-subledger-journal-entries-vendor-invoices.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
