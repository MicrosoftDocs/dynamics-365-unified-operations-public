---
title: Accounting distributions and journal entries for free text invoices
description: Accounting distributions are used to define how an amount will be accounted for, such as how the revenue, tax, or charges will be accounted for on a free text invoice.
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: concept-article
ms.date: 07/28/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: CustFreeInvoice
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: fecd17a2-d7b4-4a20-ac81-eb71abbfa9d1
---

# Accounting distributions and subledger entries for free text invoices

[!include [banner](../includes/banner.md)]

Accounting distributions define how to account for an amount, such as how to account for the revenue, tax, or charges on a free text invoice. Every amount that you must account for when you journalize the free text invoice has one or more accounting distributions.

## Accounting distributions

On the **Free text invoice** page, use the following buttons to view and possibly change the accounting distributions for each amount on the free text invoice.

- **Distribute amounts** – View and change the accounting distributions for an individual line and any child lines, such as taxes or charges. You can also view and change the accounting distributions for the child line directly from the **Sales tax transactions** page or the **Charges transactions** page.
  - Change free text invoice header amounts, such as charges or currency rounding amounts.
  - Change free text invoice line amounts.
- **View distributions** – View the accounting distributions for all lines on the document. You can't change the accounting distributions from this view.
  - View header and line amounts.

## Distributing amounts

When you enter a free text invoice, distribute each amount as follows.

| Type of monetary amount | Where the main account is displayed from | Order of priority that determines which default financial dimension is displayed |
|---|---|---|
| Free text invoice line | The ledger account on the free text invoice line. | 1. If the main account is an allocation account, use the default value from the allocation account definition.<br>2. If the main account isn't an allocation account, use the financial dimension default template on the free text invoice line.<br>3. Use the default financial dimension values on the free text invoice line.<br>4. Use the default financial dimension values from the ledger account on the Chart of accounts page. |
| Free text invoice line for a fixed asset number and value model combination<br>**Note:** The main account on the free text invoice line is the fixed asset disposal account. | The ledger account on the free text invoice line. | 1. Use the default financial dimension values on the free text invoice line.<br>2. Use the default financial dimension values from the ledger account on the Chart of accounts page. |
| Free text invoice discount amount | The Main account for Customer discounts field on the Cash discounts page. | 1. If the main account is an allocation account, use the default value from the allocation account definition.<br>2. If the main account isn't an allocation account, use the financial dimension default template on the free text invoice line.<br>3. Use the default financial dimension values on the free text invoice line.<br>4. Use the default financial dimension values from the ledger account on the Chart of accounts page. |
| Free text invoice sales tax amount | The Sales tax payable field on the Ledger posting groups page. | 1. Use the financial dimensions that are defined on the free text invoice line amount or the distributions for the charge line amount.<br>2. Use the default financial dimension values on the free text invoice line.<br>3. Use the default financial dimension values from the ledger account on the Chart of accounts page. |
| Free text invoice charge line amount | The Credit account field on the Charges code page. | 1. If the main account is an allocation account, use the default value from the allocation account definition.<br>2. If the main account isn't an allocation account, use the financial dimension default template on the free text invoice line.<br>3. Use the default financial dimension values on the free text invoice line.<br>4. Use the default financial dimension values from the ledger account on the Chart of accounts page. |

## Distributing taxes

You can't create accounting distributions for taxes until you calculate taxes. To calculate sales taxes, complete one of the following tasks on the **Free text invoice** page:

- View the sales tax.
- View the invoice total.
- View the cash flow.
- View accounting distributions for the whole free text invoice.
- View the subledger journal.

## Subledger journals for free text invoices

Before you post a free text invoice, you can view the full accounting entry of the invoice, which includes debits and credits, to verify that the invoice is going to the correct accounts. This view of the full accounting entry is called a subledger journal. If the subledger journal entry is incorrect when you preview it before you journalize the free text invoice, you can't change the subledger journal entry. Instead, you must change the accounting distributions or the posting profile. Use the accounting distributions to define one side of the accounting entry, the debit or the credit. The posting profiles create the offsetting subledger journal account entry, such as from the customer account or the tax.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
