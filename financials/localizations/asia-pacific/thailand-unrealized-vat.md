---
# required metadata

title: Thailand unrealized VAT | Microsoft Docs
description: This topic provides information about unrealized VAT and how to set it up. It also explains how to calculate and post purchase orders that have unrealized purchase VAT and sales orders that have unrealized sales VAT, and generate reports.
author: ShylaThompson
manager: AnnBe
ms.date: 2017-01-05 15:50:54
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 265924
ms.assetid: ebcbad3f-e21e-4226-8dd0-d44d964d11dc
ms.region: Thailand
# ms.industry: 
ms.author: leguo

---

# Thailand unrealized VAT

This topic provides information about unrealized VAT and how to set it up. It also explains how to calculate and post purchase orders that have unrealized purchase VAT and sales orders that have unrealized sales VAT, and generate reports.

Unrealized purchase value-added tax (VAT), or deferred input VAT, is the calculated VAT amount that isn't due until the invoice is paid. This amount is posted to an unrealized purchase VAT account and can be claimed only after the tax invoice is received. Unrealized sales VAT, or deferred output VAT, is the calculated VAT amount that isn't due until the invoice is paid. This amount is posted to an unrealized sales VAT account and can be claimed only after a tax invoice or receipt/tax invoice is printed.

## Set up unrealized VAT
Before you create and post transactions that have unrealized VAT, complete the following setup:

1.  Set up sales tax codes for unrealized VAT on the **Sales tax codes** and **Values** pages.
2.  Set up sales tax groups, item sales tax groups, and ledger posting groups for unrealized VAT on the **Sales tax groups**, **Item sales tax groups**, and **Ledger posting groups** pages.
3.  Set up the sales tax document set on the **Sales tax document set** page to specify the layout of documents that are generated, printed, and given to the customer as proof of the sales transaction.
4.  Set up number sequences for unrealized sales VAT on the **Accounts receivable parameters** page, so that number sequences are assigned for Accounts receivable documents for unrealized VAT.
5.  Set up number sequences for unrealized purchase VAT on the **Accounts payable parameters** page, so that number sequences are assigned for Accounts payable documents for unrealized VAT.

## Unrealized purchase VAT
Follow these steps to calculate and post purchase orders that have unrealized purchase VAT, and to generate the **Purchase Unrealized VAT Remaining** and **Input sales tax** reports.

1.  **Reverse the unrealized purchase VAT that was posted.** You can reverse the unrealized VAT when you receive the tax invoice from the vendor. Follow one of these steps, depending on when you receive the tax invoice from the vendor:
    -   Reverse unrealized VAT directly when you post the payment journal. On the **Journal voucher** page, enter the tax invoice number, tax invoice date, and tax invoice receipt date that are applicable to the payment.
    -   Reverse unrealized VAT only for the transactions only before you receive the tax invoice from the vendor. When you receive the tax invoice from the vendor for the settled transactions, you can reverse the unrealized purchase VAT for the transactions and post the input VAT by using the **Reversal journal** page.

2.  **Generate the Purchase Unrealized VAT Remaining report.** This report includes the transactions that the taxes haven't been realized for.
3.  **Create and post a purchase order that has unrealized purchase VAT.** On the **Create purchase order**, **Purchase order**, and **Vendor invoice** pages, create and post a purchase order that has unrealized purchase VAT. The purchase order can be for an item or a service. When you post the purchase order before you receive the tax invoice from the vendor, the unrealized purchase VAT is posted to the unrealized purchase VAT account.
4.  **Generate the Input sales tax report.** This report includes transactions that the purchase VAT is realized for, and includes the details of the VAT that the legal entity pays for the purchase of goods and services.

## Unrealized sales VAT
Follow these steps to calculate and post sales orders that have unrealized sales VAT, and to generate the **Output sales tax** report.

1.  **Create and post a sales order that has unrealized sales VAT.** The sales order can be for an item of the **Item** type or the **Service** type. When you post the sales order before you receive the payment from the customer, the unrealized sales VAT is posted to the unrealized sales VAT account.
2.  **Reverse the unrealized sales VAT that was posted.** After you receive and make the payment, the unrealized sales VAT is reversed, and the output VAT is posted. You can use the **Payments** page to generate the tax invoice or receipt/tax invoice for the transaction. You can then send the tax invoice or receipt/tax invoice to the customer.
3.  **Generate the Output sales tax report.** This report includes the transactions that the sales VAT is realized for, and includes the details of the VAT that the legal entity receives for the sales of goods and services.


