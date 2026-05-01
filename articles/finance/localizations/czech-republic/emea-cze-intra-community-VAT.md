---
title: Intra-community VAT
description: Learn how intra-community value-added tax (VAT) is calculated and posted for the Czech Republic, including a process on setting up system to compile VAT.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Czech Republic
ms.search.validFrom: 2019-06-01
---

# Intra-community VAT

This article provides information about how to calculate and post intra-community value-added tax (VAT) for the Czech Republic.

When legal entities with a primary address in the Czech Republic purchase from European Union (EU) member states, they need to self-assess VAT to ensure that the following conditions are met:

- The output VAT is paid in the VAT period on the date the invoice was issued. (This is the document date.)
- The input VAT wasn't deducted before the document receipt date. (This is the VAT register date.)

Information about intra-community VAT can be calculated and posted automatically. When you post an EU vendor invoice, two VAT transactions for the same amount must be created: one for payable sales tax and one for receivable sales tax. Follow these steps to set up the system so that it complies with this requirement.

1. Go to **Accounts payable** > **Setup** > **Accounts payables parameters**.
1. On the **Ledger and sales tax** tab, on the **Sales tax** FastTab, set the **Intra-community VAT** and **Document date for intra-community VAT** options to **Yes**.
1. Create two sales tax codes: one that has a positive sales tax percentage and one that has a negative sales tax percentage.
1. Create a sales tax group that contains both the positive and negative sales tax codes.
1. Select the **Intra-community VAT** parameter for the negative sales tax code.
1. In journals, select the **Document date for intra-community VAT** parameter.

When you post a purchase invoice, the system posts the receivable VAT and payable VAT at the same time. For the positive sales tax transaction, the system sets the VAT register date to the VAT register date from the **Invoice posting** page, and the sales tax direction is receivable. For the negative sales tax transaction, the system sets the VAT register date to the document date, and the sales tax direction is payable.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]