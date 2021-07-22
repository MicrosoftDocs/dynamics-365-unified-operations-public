---
# required metadata

title: Intra-community VAT
description: This topic provides information about how intra-community value-added tax (VAT) is calculated and posted for the Czech Republic. 
author: ShylaThompson
ms.date: 07/22/2021
ms.topic: article
ms.prod: 
ms.technology: 
---

# Intra-community VAT

This topic provides information about how intra-community value-added tax (VAT) is calculated and posted for the Czech Republic. 

When legal entities that have a primary address in the Czech Republic purchase from European Union (EU) member states, they should do a self-assessment of VAT to ensure that the following conditions are met:

-   The output VAT is paid in the VAT period when the invoice was issued (document date).
-   The input VAT wasn't deducted before the document receipt (VAT register date).

Information about intra-community VAT can be calculated and posted automatically. When you post an EU vendor invoice, two VAT transactions for the same amount are created. One VAT transaction is created for payable sales tax, and the other transaction is created for receivable sales tax. To reflect this requirement, you should complete the following setup:

-   Select the **Intra-community VAT** check box on the **Accounts payables parameters** page (**Accounts payable** > **Setup** > **Accounts payables parameters**).
-   Select the **Document date for intra-community VAT** check box on the **Accounts payables parameters** page.
-   Create two sales tax codes: one that has a positive sales tax percentage and another that has a negative sales tax percentage.
-   Create a sales tax group that contains both the positive and negative sales tax codes. Select the **Intra-community VAT** parameter for the negative sales tax code.
-   In journals, select the **Document date for intra-community VAT** parameter.

When a purchase invoice is posted, the receivable VAT and payable VAT are posted at the same time. For the positive sales tax transaction, the VAT register date is set to the VAT register date from the invoice posting page, and the sales tax direction is **Sales tax receivable**. For the negative sales tax transaction, the VAT register date is set to the document date, and the sales tax direction is **Sales tax payable**.
