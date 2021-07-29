---
# required metadata

title: Intra-community VAT
description: This topic provides information about how intra-community value-added tax (VAT) is calculated and posted for the Czech Republic.
author: anasyash
ms.date: 07/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Czech Republic
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 

---

# Intra-community VAT

This topic provides information about how intra-community value-added tax (VAT) is calculated and posted for the Czech Republic.

When legal entities that have a primary address in the Czech Republic purchase from European Union (EU) member states, they should do a self-assessment of VAT to ensure that the following conditions are met:

- The output VAT is paid in the VAT period on the date the invoice was issued. (This is the document date.)
- The input VAT wasn't deducted before the document receipt date. (This is the VAT register date.)

Information about intra-community VAT can be calculated and posted automatically. When you post an EU vendor invoice, two VAT transactions for the same amount must be created: one for payable sales tax and one for receivable sales tax. Follow these steps to set up the system so that it complies with this requirement.

1. Go to **Accounts payable** \> **Setup** \> **Accounts payables parameters**.
2. On the **Ledger and sales tax** tab, on the **Sales tax** FastTab, set the **Intra-community VAT** and **Document date for intra-community VAT** options to **Yes**.
3. Create two sales tax codes: one that has a positive sales tax percentage and one that has a negative sales tax percentage.
4. Create a sales tax group that contains both the positive and negative sales tax codes.
5. Select the **Intra-community VAT** parameter for the negative sales tax code.
6. In journals, select the **Document date for intra-community VAT** parameter.

When a purchase invoice is posted, the receivable VAT and payable VAT are posted at the same time. For the positive sales tax transaction, the VAT register date is set to the VAT register date from the **Invoice posting** page, and the sales tax direction is receivable. For the negative sales tax transaction, the VAT register date is set to the document date, and the sales tax direction is payable.
