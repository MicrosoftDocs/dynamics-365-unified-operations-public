---
# required metadata

title: Intra-community VAT for Spain
description: This topic provides information about the functionality for intra-community value-added tax (VAT). It explains how to turn on the functionality, calculate and print intra-community VAT amounts, and review intra-community VAT amounts that have been posted.
author: Anasyash
manager: AnnBe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 271523
ms.search.region: Spain
# ms.search.industry: 
ms.author: anasyash
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Intra-community VAT for Spain
[!include[banner](../includes/banner.md)]


This topic provides information about the functionality for intra-community value-added tax (VAT). It explains how to turn on the functionality, calculate and print intra-community VAT amounts, and review intra-community VAT amounts that have been posted.

Information about intra-community value-added tax (VAT) can be calculated and posted automatically. When you post a European Union (EU) vendor invoice, two VAT transactions are created. One VAT transaction is created for payable sales tax, and the other VAT transaction is created for receivable sales tax. Before you can use the intra-community VAT functionality, you must enable the **Intra-community VAT** option on the **Ledger and sales tax** tab of the **Accounts payable parameters** page.

## Calculating intracommunity VAT for purchase transactions
To calculate intra-community VAT for purchase transactions, you must have two sales tax codes that have the same tax percentage. However, one code must have a positive tax percentage, and the other code must have a negative tax percentage. You must also have a sales tax group that contains both a positive sales tax code and a negative sales tax code. Select the **Intra-community VAT** check box for the line that has a negative sales tax code. 

## Printing intracommunity VAT on a purchase invoice
To print intra-community VAT on a purchase invoice, enable the **Print EU sales tax on Spanish invoices** option on the **Invoice** tab of the **Form setup** page (**Accounts payable** &gt; **Setup** &gt; **Forms** &gt; **Form setup**).

## Printing invoices that have intracommunity VAT amounts
To print purchase invoices and intra-community invoices that have intra-community VAT amounts, on the vendor invoice page, on the **Process** tab, click **Print setup** &gt; **Print options**. In the **Print options** dialog box, enable the **Print invoice** and **Print intra-community invoice** options.

## Reviewing posted intracommunity VAT amounts
To review the intra-community VAT amounts that have been posted, run the Posted sales tax query (**Tax** &gt; **Inquiries and reports** &gt; **Sales tax inquiries** &gt; **Posted sales tax**). On the **Posted sales tax** page, on the **General** tab, if the **Intra-community VAT** check box is selected, the tax transaction is an intra-community VAT transaction. Spanish VAT books must be set up so that posted payable and receivable VAT transactions are reflected in the appropriate sections. To set up Spanish VAT books, click **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Spanish VAT books**. For more information, see VAT 340 Modelo declaration for Spain.


