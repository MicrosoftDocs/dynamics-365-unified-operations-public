---
# required metadata

title: Accounting distributions and subledger journal entries for vendor invoices
description: Accounting distributions are used to define how an amount will be accounted for, such as how the expense, tax, or charges will be accounted for on a vendor invoice. Every amount that must be accounted for when the vendor invoice is journalized will have one or more accounting distributions. 
author: twheeloc
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: VendEditInvoice
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 26891
ms.assetid: 93dc608a-b5b4-4ec3-83c2-618e3d80a583
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Accounting distributions and subledger journal entries for vendor invoices

Accounting distributions are used to define how an amount will be accounted for, such as how the expense, tax, or charges will be accounted for on a vendor invoice. Every amount that must be accounted for when the vendor invoice is journalized will have one or more accounting distributions. 

Accounting distributions 
-------------------------

You can use the following buttons in the Vendor invoice page to view, and possibly modify, the accounting distributions for each amount on the vendor invoice.
-   **Distribute amounts** – View and modify the accounting distributions for an individual line and any child lines, such as taxes or charges. You can also view and modify the accounting distributions for the child line directly from the Sales tax transactions page or the Charges transactions page.
    -   Modify vendor invoice header amounts, such as charges or currency rounding amounts.
    -   Modify vendor invoice line amounts.
-   **View distributions** – View the accounting distributions for all lines on the document. You cannot modify the accounting distributions from this view.
    -   View header and line amounts.

If the vendor invoice references a purchase order, you can split and modify the accounting distributions for lines that contain an item that is not stocked. If the vendor invoice line does not reference a purchase order line, you can also delete an accounting distribution. You cannot split or delete lines for charges, taxes, and line discounts. You can modify the ledger account, but you cannot change the amounts or percentages.
> [!NOTE]                                                                                                                                 
> If the parent line contains an item that is not stocked and the accounting distributions are split, the child line will be split automatically to match the financial dimensions of the parent line. The accounting distributions for the child line cannot be additionally split or deleted, but depending on the setup of the child line, you might be able to modify the ledger account for the accounting distributions of the child line.

## Distributing amounts
When you enter a vendor invoice, each amount will be distributed as follows.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Type of vendor invoice line</th>
<th>Order of priority that determines where the main account is displayed from</th>
<th>Order of priority that determines which default financial dimension is displayed</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Stocked product</td>
<td><ol>
<li>The accounting distribution for the purchase order line.</li>
<li>The Main account field when Purchase expenditure for product is selected in the Posting page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the default financial dimension values on the vendor invoice.</li>
</ol></td>
</tr>
<tr class="even">
<td>A procurement category or a product that is not stocked</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the vendor invoice line references a purchase order line.</li>
<li>The Main account field when Purchase expenditure for expense is selected in the Posting page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>If the main account is an allocation account, use the default value from the allocation account definition.</li>
<li>Use the default financial dimension values on the vendor invoice.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account in the Chart of Accounts page.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Fixed asset</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the vendor invoice line references a purchase order line.</li>
<li>If Acquisition is selected in the Transaction type field in the Vendor invoice form, the Main account field when Acquisition is selected in the Fixed asset posting profiles page.</li>
<li>If Acquisition adjustment is selected in the Transaction type field, the Main account field when Acquisition adjustment is selected in the Fixed asset posting profiles page.</li>
</ol></td>
<td><ol>
<li>Use the account distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account in the Chart of Accounts page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Project defined on the vendor invoice line</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>If Balance is selected in the Post costs - item field in the Project groups page, the Main account field when Cost is selected in the Ledger posting setup page.</li>
<li>If Profit and loss is selected in the Post costs - item field in the Project groups page, the Main account field when Cost - item is selected in the Ledger posting setup page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Line discount</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>The Main account field when Discount is selected in the Posting page.</li>
<li>If a main account for a discount is not defined on the posting profile, the accounting distribution of the extended price on the purchase order line.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the accounting distribution for the purchase order line.</li>
<li>Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.</li>
<li>Use the financial dimension values for the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account in the Chart of Accounts page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Purchase charge, which is entered on the Price and discount tab of the purchase order line</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>The accounting distribution of the extended price on the purchase order line.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Line charge</td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>If Ledger account is selected in the debit Type field in the Charges code form, the debit Account field in the Charges code page.</li>
<li>If Item is selected in the debit Type field in the Charges code form, the accounting distribution for the extended price on the purchase order line.</li>
<li>If Customer/Vendor is selected in the debit Type field in the Charges code form, the credit Account field in the Charges code page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account in the Chart of Accounts page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Tax, with the following condition:
<ul>
<li>The Apply U.S. taxation rules option is selected in the General ledger parameters page.</li>
</ul></td>
<td><ol>
<li>The accounting distribution for the purchase order line, if the invoice line references a purchase order line.</li>
<li>The accounting distribution of the extended price or charge.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Tax, with the following conditions:
<ul>
<li>The Apply U.S. taxation rules option is cleared in the General ledger parameters page.</li>
<li>The Use tax field for the sales tax group is cleared in the Sales tax groups page.</li>
</ul></td>
<td><ol>
<li>If the tax amount is recoverable, the Sales tax receivable field in the Ledger posting groups page.</li>
<li>If the tax amount is not recoverable, the extended price or the accounting distribution for the charge.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the extended price or the accounting distributions for the charge on the vendor invoice line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account in the Chart of Accounts page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Tax, with the following conditions:
<ul>
<li>The Apply U.S. taxation rules option is cleared in the General ledger parameters page.</li>
<li>The Use tax field for the sales tax group is selected in the Sales tax groups page.</li>
</ul></td>
<td><ol>
<li>If the tax amount is recoverable, the Sales tax receivable field in the Ledger posting groups page.</li>
<li>If the tax amount is not recoverable, the Use tax expense field in the Ledger posting groups page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the extended price or the accounting distributions for the charge on the vendor invoice line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account in the Chart of Accounts page.</li>
</ol></td>
</tr>
<tr class="odd">
<td>Header charge</td>
<td><ol>
<li>If Ledger account is selected in the debit Type field in the Charges code form, the debit Account field in the Charges code page.</li>
<li>If Customer/Vendor is selected in the debit Type field in the Charges code form, the credit Account field in the Charges code page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>If the main account is an allocation account, use the default value from the allocation account definition.</li>
<li>Use the financial dimension default template values from the vendor invoice header.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account in the Chart of Accounts page.</li>
</ol></td>
</tr>
<tr class="even">
<td>Header discount</td>
<td><ol>
<li>The Main account field for the Vendor invoice discount posting type in the Accounts for automatic transactions page.</li>
</ol></td>
<td><ol>
<li>If the invoice line references a purchase order line, use the account distribution for the purchase order line.</li>
<li>Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.</li>
<li>Use the financial dimension values from the vendor invoice line.</li>
<li>Use the default financial dimension values from the main account in the Chart of Accounts page.</li>
</ol></td>
</tr>
</tbody>
</table>

 
Distributing taxes
------------------

Accounting distributions for taxes cannot be created until taxes are calculated. To calculate sales taxes, you must complete one of the following tasks in the Vendor invoice page:
-   View the invoice total.
-   View the sales tax.
-   View the subledger journal.
-   View accounting distributions for the complete vendor invoice.
-   Place the vendor invoice on hold.
-   Post the vendor invoice.

## Subledger journals for vendor invoices
Before you post a vendor invoice, you can view the full accounting entry of the invoice, which includes debits and credits, to verify that the invoice is being posted to the correct accounts. This view of the full accounting entry is called a subledger journal. 

If the subledger journal entry is incorrect when you preview it before you journalize the vendor invoice, you cannot modify the subledger journal entry. Instead, you must modify the accounting distributions or the posting profile. The accounting distributions are used to define one side of the accounting entry, the debit or the credit. The offsetting subledger journal account entry is created by using the posting profiles, such as from the vendor account or tax.



