---
# required metadata

title: Sales tax reporting for the Czech Republic
description: This topic provides information about how intra-community value-added tax (VAT) is calculated and posted for the Czech Republic. 
author: LizaGolub
manager: AnnBe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxGroup, VendParameters
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 1696023
ms.search.region: Czech Republic
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
---

# Sales tax reporting for the Czech Republic

This topic provides information about how intra-community value-added tax (VAT) is calculated and posted for the Czech Republic. 

When legal entities that have their primary address in the Czech Republic purchase from European Union (EU) member states, they should do a self-assessment of value-added tax (VAT) to make sure that the following conditions are met:

-   The output VAT is paid in the VAT period when the invoice was issued (document date).
-   The input VAT wasn't deducted before the document receipt (VAT register date).

Information about intra-community VAT can be calculated and posted automatically. When you post an EU vendor invoice, two VAT transactions for the same amount are created. One VAT transaction is created for payable sales tax, and the other transaction is created for receivable sales tax. To reflect this requirement in Microsoft Dynamics 365 for Finance and Operations, you should complete the following setup:

-   Select the **Intra-community VAT** check box on the **Accounts payables parameters** page (**Accounts payable** &gt; **Setup** &gt; **Accounts payables parameters**).
-   Select the **Document date for intra-community VAT** check box on the **Accounts payables parameters** page.
-   Create two sales tax codes: one that has a positive sales tax percentage and another that has a negative sales tax percentage.
-   Create a sales tax group that contains both the positive and negative sales tax codes. Select the **Intra-community VAT** parameter for the negative sales tax code.
-   In journals, select the **Document date for intra-community VAT** parameter.

When a purchase invoice is posted, the receivable VAT and payable VAT are posted at the same time. For the positive sales tax transaction, the VAT register date is set to the VAT register date from the invoice posting page, and the sales tax direction is **Sales tax receivable**. For the negative sales tax transaction, the VAT register date is set to the document date, and the sales tax direction is **Sales tax payable**.

