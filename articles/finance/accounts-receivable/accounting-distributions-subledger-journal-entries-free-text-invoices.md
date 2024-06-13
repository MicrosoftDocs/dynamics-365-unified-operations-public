---
title: Accounting distributions and journal entries for free text invoices
description: Accounting distributions are used to define how an amount will be accounted for, such as how the revenue, tax, or charges will be accounted for on a free text invoice.
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: article
ms.date: 08/22/2017
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

Accounting distributions are used to define how an amount will be accounted for, such as how the revenue, tax, or charges will be accounted for on a free text invoice. Every amount that must be accounted for when the free text invoice is journalized will have one or more accounting distributions.

## Accounting distributions

You can use the following buttons on the **Free text invoice** page to view, and possibly change, the accounting distributions for each amount on the free text invoice.

-   **Distribute amounts**—View and change the accounting distributions for an individual line and any child lines, such as taxes or charges. You can also view and change the accounting distributions for the child line directly from the **Sales tax transactions** page or the **Charges transactions** page.
    -   Change free text invoice header amounts, such as charges or currency rounding amounts.
    -   Change free text invoice line amounts.
-   **View distributions**—View the accounting distributions for all lines on the document. You can't change the accounting distributions from this view.
    -   View header and line amounts.

## Distributing amounts
When you enter a free text invoice, each amount will be distributed as follows.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Type of monetary amount</th>
<th>Where the main account is displayed from</th>
<th>Order of priority that determines which default financial dimension is displayed</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Free text invoice line</td>
<td>The ledger account on the free text invoice line.</td>
<td><ol>
<li>If the main account is an allocation account, use the default value from the allocation account definition.</li>
<li>If the main account is not an allocation account, use the financial dimension default template on the free text invoice line.</li>
<li>Use the default financial dimension values on the free text invoice line.</li>
<li>Use the default financial dimension values from the ledger account on the Chart of accounts page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Free text invoice line for a fixed asset number and value model combination
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The main account on the free text invoice line will be the fixed asset disposal account.</td>
</tr>
</tbody>
</table>
</div></td>
<td>The ledger account on the free text invoice line.</td>
<td><ol>
<li>Use the default financial dimension values on the free text invoice line.</li>
<li>Use the default financial dimension values from the ledger account on the Chart of accounts page.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Free text invoice discount amount</td>
<td>The Main account for Customer discounts field on the Cash discounts page.</td>
<td><ol>
<li>If the main account is an allocation account, use the default value from the allocation account definition.</li>
<li>If the main account is not an allocation account, use the financial dimension default template on the free text invoice line.</li>
<li>Use the default financial dimension values on the free text invoice line.</li>
<li>Use the default financial dimension values from the ledger account on the Chart of accounts page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Free text invoice sales tax amount</td>
<td>The Sales tax payable field on the Ledger posting groups page.</td>
<td><ol>
<li>Use the financial dimensions that are defined on the free text invoice line amount or the distributions for the charge line amount.</li>
<li>Use the default financial dimension values on the free text invoice line.</li>
<li>Use the default financial dimension values from the ledger account on the Chart of accounts page.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Free text invoice charge line amount</td>
<td>The Credit account field on the Charges code page.</td>
<td><ol>
<li>If the main account is an allocation account, use the default value from the allocation account definition.</li>
<li>If the main account is not an allocation account, use the financial dimension default template on the free text invoice line.</li>
<li>Use the default financial dimension values on the free text invoice line.</li>
<li>Use the default financial dimension values from the ledger account on the Chart of accounts page.</li>
</ol></td>
</tr>
</tbody>
</table>

## Distributing taxes
Accounting distributions for taxes cannot be created until taxes are calculated. To calculate sales taxes, you must complete one of the following tasks on the **Free text invoice** page:
-   View the sales tax.
-   View the invoice total.
-   View the cash flow.
-   View accounting distributions for the whole free text invoice.
-   View the subledger journal.

## Subledger journals for free text invoices
Before you post a free text invoice, you can view the full accounting entry of the invoice, which includes debits and credits, to verify that the invoice is being posted to the correct accounts. This view of the full accounting entry is called a subledger journal. If the subledger journal entry is incorrect when you preview it before you journalize the free text invoice, you can't change the subledger journal entry. Instead, you must change the accounting distributions or the posting profile. The accounting distributions are used to define one side of the accounting entry, the debit or the credit. The offsetting subledger journal account entry is created from the posting profiles, such as from the customer account or the tax.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
