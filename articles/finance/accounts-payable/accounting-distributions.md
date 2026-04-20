---
title: Accounting distributions
description: Learn about accounting distributions and describes available processing options, including an overview on distribute amounts.
author: sunfzam
ms.author: twheeloc
ms.topic: concept-article
ms.date: 04/01/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AccountingDistribution
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9030355d-8e6e-408b-9e7d-7b346eaa652c
---

# Accounting distributions

[!include [banner](../includes/banner.md)]

This article provides information about accounting distributions and describes the options for processing them. Use accounting distributions to allocate monetary amounts for a source document to specific ledger accounts.

Accounting distributions are a capability that is used and extended by each source document, such as a purchase order, vendor invoice, expense report, and free text invoice. By default, a default accounting distribution is generated for each source document line and monetary amount, and is conditionally enabled for modification.

> [!NOTE]
> Some documents also support header document monetary amounts, such as charges for orders and invoices.

The generic accounting distribution capabilities provide the following options for processing accounting distributions:

- **Distribute amounts** – View and modify the accounting distributions for an individual document header or line and any child lines, such as taxes or charges.
  - For the top monetary amount distributions (parent distributions), you might be able to edit the main account and financial dimensions directly in the segmented entry control in the grid. The extended price is a typical example of such a parent distribution.
  - The distribution amounts are based on the term currency for the document. Typically, this currency is the transaction currency. Accounting and reporting currency amounts are generated as part of subledger accounting.
  - The distributions display the accounting date and accounting event. Typically, the accounting event is set to **None** until you post or journalize the document. At that point, the accounting event becomes **Original**. After you post the distributions, you can't modify the distributions.
  - The **Split** button might be enabled for parent distributions. **Split** generates new accounting distributions, and the split can be based on percentage, amount, or quantity.
  - Use the **Distribute equally** button in combination with **Split** to automatically allocate the amount equally across all distributions.
  - The **Reset** button might be enabled for parent distributions when more than one distribution exists. **Reset** reverses any manual modification to the distribution by deleting all existing distributions and re-generating the default distributions.
  - Any child distribution, such as discount, charge, and sales tax, always follows the parent distribution. You can view the parent and child relation at **Reference** > **Parent information**.
  - You might be able to edit the main account and financial dimension for children.
  - The financial dimensions on the accounting distributions follow a defaulting pattern that a document can extend.
  - Variance distributions might be generated in matching scenarios, such as matching between a vendor invoice and a purchase order. You can view the matching relations between accounting distribution at **Reference** > **Document information**.
  - **Correct** button appears and is enabled for documents that support corrections. **Correct** creates new distributions. First, distributions are created that reverse the original distributions. These distributions can't be modified. Next, new correct accounting distributions are created. These distributions can be modified if the original distributions could be modified.
  - The **Project details** button is enabled as an extension when a line is related to a project. Project accounting distributions let you modify details such as the funding source and line property.
  - You can view the current document accounting status in **Reference**. The status is for the entire document, and indicates whether the document is in process or completed.
- **View distributions** – View the accounting distributions for all lines and monetary amounts on the document. You can't modify the accounting distributions from this view.

A feature was added that validates the accounting distribution table to ensure that new fields are properly set up. This feature is called **Enable additional validation of data for documents using the source document accounting framework**. This feature is turned on by default in version 10.0.29.

For more information, see [Accounting distributions and subledger journal entries for vendor invoices](accounting-distributions-subledger-journal-entries-vendor-invoices.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
