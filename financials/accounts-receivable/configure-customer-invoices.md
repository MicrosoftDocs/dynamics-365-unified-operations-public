---
# required metadata

title: Create a customer invoice
description: 
author: twheeloc
manager: AnnBe
ms.date: 2016-04-04 23 - 11 - 36
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 101
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 77772
ms.assetid: 00b4b40c-1576-4098-9aed-ac376fdeb8c5
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Create a customer invoice



A **customer invoice for a sales order** is a bill that is related to a sale, and that an organization gives to a customer. This type of customer invoice is created based on a sales order, which includes order lines and item numbers. Item numbers are specified and posted in the ledger. Subledger journal entries aren't available for a customer invoice for a sales order. A **free text invoice** isn't related to a sales order. It contains order lines that include ledger accounts, free-text descriptions, and a sales amount that you enter. You can't enter an item number on this kind of invoice. You must enter the appropriate sales tax information. A main account for the sale is indicated on each invoice line, which you can distribute to multiple ledger accounts by clicking **Distribute amounts** on the **Free text invoice** page. Additionally, the customer balance is posted to the summary account from the posting profile that is used for the free text invoice. A **pro forma invoice** is an invoice that is prepared as an estimate of the actual invoice amounts before the invoice is posted. You can print a pro forma invoice either for a customer invoice for a sales order or for a free text invoice.

## Post and print individual customer invoices that are based on sales orders
Use this process to create an invoice that is based on a sales order. You might do this if you decide to invoice the customer before you deliver the goods or services. When you post an invoice, the **Invoice remainder** quantity for each item is updated with the total of the invoiced quantities from the selected sales order. If both the **Invoice remainder** quantity and the **Deliver remainder** quantity for all items on the sales order are 0 (zero), the status of the sales order is changed to **Invoiced**. If the **Invoice remainder** quantity isn't 0 (zero), the status of the sales order remains unchanged, and additional invoices can be entered for it. You can view the status of the sales orders on the **All sales orders** list page. Use the **Open customer invoices** list page to view the invoices that you posted.

## Post and print individual customer invoices that are based on packing slips and the date
Use this process when one or more packing slips have been posted for the sales order. The customer invoice is based on these packing slips and reflects the quantities from them. The financial information for the invoice is based on the information that is entered when you post the invoice. You can create a customer invoice that is based on the packing slip line items that have been shipped to date, even if all the items for a particular sales order haven't yet been shipped. You might do this if, for example, your legal entity issues one invoice per customer per month that covers all the deliveries that you ship during that month. Each packing slip represents a partial or complete delivery of the items on the sales order. When you post the invoice, the **Invoice remainder** quantity for each item is updated with the total of the delivered quantities from the selected packing slips. If both the **Invoice remainder** quantity and the **Deliver remainder** quantity for all items on the sales order are 0 (zero), the status of the sales order is changed to **Invoiced**. If the **Invoice remainder** quantity isn't 0 (zero), the status of the sales order remains unchanged, and additional invoices can be entered for it. Inventory transactions are updated with the invoice number, and the status in the **Line status** field on the sales order is changed to **Invoiced**. View the status of the sales orders in the **All sales orders** list page.

## Consolidate sales orders or packing slips for posting
Use this process when one or more sales orders are ready to be invoiced, and you want to consolidate them into a single invoice. You can select multiple invoices on the **Sales order** list page and then use **Generate invoices** to consolidate them. On the **Posting invoice** page, you can change the **Summary order** setting to summarize by order number (where there are multiple packing slips for a single sales order) or by invoice account (where there are multiple sales orders for a single invoice account). Use the **Arrange** button to consolidate sales orders into single invoices, based on the **Summary order** settings.

## Additional settings that change the posting behavior
The following fields change the behavior of the posting process.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Quantity</td>
<td>Select the quantities to base the posting of the document on. The options that are available vary, depending on the type of document that you are posting, such as a packing slip or an invoice.
<ul>
<li><strong>Deliver now</strong> – Select all quantities that are entered in the <strong>Deliver now</strong> field. Use this option to confirm or deliver a partial order.</li>
<li><strong>Picked</strong> – Select all quantities that have been picked.</li>
<li><strong>All</strong> – Select all quantities on the sales order that haven't yet been updated by the current document type.</li>
<li><strong>Packing slip</strong> – Select all quantities that have been updated by a packing slip.</li>
<li><strong>Picked quantity and not stocked products</strong> – Select all quantities that have been picked and all product quantities that aren't stocked.</li>
</ul></td>
</tr>
<tr class="even">
<td>Posting</td>
<td><ul>
<li>Select this option to journalize the sales order.</li>
<li>Clear this option to print a pro forma sales order. <strong>Note:</strong> If you made an agreement for a payment schedule, the payment schedule isn't shown on the pro forma sales order. Payment schedules are shown only on actual sales orders.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Late selection</td>
<td>Select this option to apply the selected query later. This option is used for batch jobs. The query is run when the batch job is run.</td>
</tr>
<tr class="even">
<td>Reduce quantity</td>
<td>Select this option to automatically reduce the delivered quantity when the document is posted, so that the delivered quantity equals the available inventory.</td>
</tr>
<tr class="odd">
<td>Print</td>
<td>Select when to print documents:
<ul>
<li><strong>Current</strong> – Print documents after each invoice has been updated.</li>
<li><strong>After</strong> – Print documents after all the invoices have been updated.</li>
</ul>
<strong>Note:</strong> The <strong>Print</strong> field is available only if you select the <strong>Print invoice</strong>, <strong>Print confirmation</strong>, <strong>Print picking list</strong>, or <strong>Print packing slip</strong> option. For example, on the <strong>Form sorting</strong> page, you have set up the system to sort the information by invoice account. You can then select <strong>After</strong> to print the documents in a batch that is sorted by invoice account. Otherwise, the documents are printed before processing is completed, and the documents aren't sorted in the order that is specified on the <strong>Form sorting</strong> page.</td>
</tr>
<tr class="even">
<td>Print invoice</td>
<td>Select this option to print the invoice. If this option is turned off, you can post an invoice without printing it.</td>
</tr>
<tr class="odd">
<td>Send e-mail</td>
<td>Select this option to send the invoice for a sales order to the customer as an email attachment after the invoice is posted. Attachments are sent as PDF and XML files. This option is available only if you select the <strong>Enable CFD (electronic invoices)</strong> option on the <strong>Electronic invoice parameters</strong> page. <strong>Note:</strong> (MEX) This control is available only to legal entities whose primary address is in Mexico.</td>
</tr>
<tr class="even">
<td>Use print management destination</td>
<td>Select this option to use the print settings that are specified for the transaction, document, or module on the <strong>Print management setup</strong> page.</td>
</tr>
<tr class="odd">
<td>Check credit limit</td>
<td>Select the information that should be analyzed when a credit limit check is performed. For more information, see <a href="https://technet.microsoft.com/en-us/library/aa576022.aspx">About credit limit types in Accounts receivable parameters</a>.
<ul>
<li><strong>None</strong> – There is no requirement for the credit limit check.</li>
<li><strong>Balance</strong> – The credit limit is checked against the customer balance.</li>
<li><strong>Balance + packing slip or product receipt</strong> – The credit limit is checked against the customer balance and deliveries.</li>
<li><strong>Balance+All</strong> – The credit limit is checked against the customer balance, deliveries, and open orders.</li>
</ul></td>
</tr>
<tr class="even">
<td>Credit correction</td>
<td>Select this option to display the credit note as a debit in the voucher transactions.</td>
</tr>
<tr class="odd">
<td>Credit remaining quantity</td>
<td>If you're posting a credit note, select this option to keep the remaining quantity on order. If this option is cleared, the remaining quantity is set to 0 (zero).</td>
</tr>
<tr class="even">
<td>Summary update for</td>
<td>Select how multiple sales orders should be summarized:
<ul>
<li><strong>None</strong> – Don't summarize sales orders. For example, a separate invoice will be created for each sales order.</li>
<li><strong>Invoice account</strong> – Summarize all selected orders, based on the criteria that are set up on the <strong>Summary update parameters</strong> page.</li>
<li><strong>Order</strong> – Summarize a selected range of orders into one order that you specify. The orders are summarized based on the criteria that are set up on the <strong>Summary update parameters</strong> page. If you select this option, you must select a value in the <strong>Sales order</strong> field.</li>
<li><strong>Automatic summary</strong> – If summary updates have been specified on the <strong>Summary update</strong> page, summarize all selected orders, based on the criteria that are set up on the <strong>Summary update parameters</strong> page. If summary updates haven't been specified, the order is posted separately.</li>
<li><strong>Packing slip</strong> – Summarize a selected range of orders into one invoice for each packing slip. This option is available only if <strong>Packing slip</strong> is selected in the <strong>Quantity</strong> field.</li>
</ul></td>
</tr>
</tbody>
</table>



