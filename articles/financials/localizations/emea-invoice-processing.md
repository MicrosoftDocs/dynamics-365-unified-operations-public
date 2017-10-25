---
# required metadata
title: Invoice processing
description: This topic provides information about invoice processing for Eastern Europe.
author: v-kikozl
manager: AnnBe
ms.date: 07/21/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
# ms.search.industry: 
ms.author: v-kikozl
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Enterprise edition, July 2017 update
---

# Invoice processing

This topic briefly describes some country-specific scenarios, such as intra-community value-added tax (VAT) and deferred tax. Legal requirements for some European countries affect the invoicing process. This topic provides also an information about how customer and vendor invoices are processed for these countries. 
<table>
<thead>
<tr>
<th>Scenario</th>
<th>Countries</th>
<th>Description of the functionality changes</th>
</tr>
</thead>
<tbody>
<tr>
<td>Accounts receivable and Accounts payable dates for VAT</td>
<td>Czech Republic, Poland</td>
<td>
<p>When goods are purchased from European Union (EU) countries, there is an obligation of self-assessment of VAT:</p>
<ul>
<li>The output VAT must be paid in a VAT period where the invoice was issued (document date).</li>
<li>The input VAT can’t be deducted before the document receipt (VAT register date).</li>
</ul>
<p>The following settings should be configured to support this scenario:</p>
<ul>
<li>On the <strong>Accounts payable parameters</strong> page, enable the <strong>Intra-community VAT</strong> and <strong>Document date for intra-community VAT</strong> parameters.</li>
<li>Set up two sales tax codes, one that has a positive sales tax percentage and one that has a negative sales tax percentage.</li>
<li>Set up a sales tax group that includes both the positive and negative sales tax codes. For the negative sales tax code, set the <strong>Intracommunity VAT</strong> parameter to <strong>Yes</strong>.</li>
</ul>
<p>After successful setup, purchases will have two posted sales tax transactions:</p>
<ul>
<li>A positive transaction that has a direction of <strong>sales tax receivable</strong> and a VAT register date that equals the date from the invoice posting page.</li>
<li>A negative transaction that has a direction of <strong>sales tax payable</strong> and a VAT register date that equals the document date.</li>
</ul>
</td>
</tr>
<tr>
<td>Modify a sales document date.</td>
<td>All Eastern European countries</td>
<td><p>You can modify the <strong>Document date</strong> field on a project invoice. This date appears on the printed invoice.</p>
<p>There is also a <strong>Document date</strong> field on the <strong>Posting invoice</strong> and <strong>Free text invoice</strong> pages. After you post an invoice, the document date appears on the invoice header.</p>
</td>
</tr>
<tr>
<td>Document date for exchange rates</td>
<td>Poland, Hungary, Czech Republic</td>
<td>
<p>Legislation provides different rules for selecting valid exchange rates for business transactions. In the <strong>Exchange rate date</strong> field on the <strong>Accounts receivable parameters</strong> and <strong>Accounts payable parameters</strong> pages, you can select the date that should be used for amounts in the accounting currency calculation on purchase and sales documents. During data entry, the system retrieves the exchange rate for the transaction, based on this parameter.</p>
<blockquote>[!NOTE]<br>When you set the <strong>Exchange rate date</strong> field to <strong>Document date (for EU trade only)</strong>, the system uses the sales tax group. For the sales tax group, there is a <strong>EU trade</strong> parameter on the <strong>General</strong> tab. If the <strong>EU trade</strong> option is set to <strong>Yes</strong> for the sales tax group, and if this sales tax group exists on the header of the document, the system retrieves the exchange rate based on the document date. If the <strong>EU trade</strong> option is set to <strong>No</strong> for this sales tax group, the system retrieves the exchange rate based on the posting date of the document.</blockquote>
</td>
</tr>
<tr>
<td>Trade dates, VAT register dates, and document and VAT date control</td>
<td>Poland, Hungary, Czech Republic</td>
<td>
<p>The sales date and the document receipt date are required for VAT reporting:</p>
<ul>
<li>The sales date is the fulfilment date of the transaction in Accounts receivable.</li>
<li>The document receipt date is a date that demonstrates the rights to claim a VAT deduction in Accounts payable. Each document that is received has a date for audit purposes.</li>
</ul>
<p>The Hungarian functionality for date deadlines, the Czech Republic functionality for fulfill dates, and the Polish functionality for the VAT register date include the requirement for tax information reporting that is based on a date that differs from the posting date.</p>
<p>The <strong>Date of VAT register</strong> field supports this requirement and appears on more than 20 pages. These pages include journals, sales orders, purchase orders, free-text invoices, vendor invoice journals, and project invoices. When you update or post the documents, all taxes are posted by using the corresponding date of the VAT register, and the date is included on pages such as the customer and vendor invoice journals pages.</p>
<p>Specifically, for the Czech Republic, the <strong>VAT register date</strong> field can be blank during posting, in the event of postponed VAT posting. Otherwise, the field is mandatory and must be filled in.</p>
<p>Date validation parameters can be set on the <strong>Sales tax groups</strong> page:</p>
<ul>
<li>The <strong>Date of VAT register filling</strong> and <strong>Sales date filling</strong> parameters are used as a default filling method for appropriate dates. Manual input and several automated input methods are also available.</li>
<li>The <strong>Mandatory sales date</strong> field indicates whether the sales date must be entered before a sales invoice is posted.</li>
</ul>
<p>On the <strong>VAT Register transactions</strong> page, you can fill in blank dates for the VAT register for posted tax transactions.</p>
</td>
</tr>
<tr>
<td>VAT register dates that include deferred tax</td>
<td>Hungary</td>
<td>
<p>Hungary tax regulations require that invoices be created at either the time of fulfilment or no later than 15 days after fulfilment.</p>
<p>The fulfilment date is either the date when the ordered services were provided or the date when ordered items were delivered. When you update or post the documents, all taxes are posted by using the corresponding date of the VAT register, and the date appears on relevant pages. Additionally, regulations require that VAT on continuous delivery of services, such as renting, leasing, consulting, and heating, meet the following criteria:</p>
<ul>
<li>VAT must be posted to a dedicated general ledger account on the invoice date.</li>
<li>VAT must be transferred from the special accounts to a sales tax receivable account or a payable account, and must be included in the VAT report on the due date.</li>
</ul>
<p>To support these requirements, you can transfer General ledger postings to the Deferred incoming tax account and the Deferred outgoing tax account. However, you must first complete the following prerequisites:</p>
<ul>
<li>Set up the Deferred VAT Payable and Deferred VAT Receivable ledger accounts in ledger posting groups.</li>
<li>Enable the <strong>Deferred VAT</strong> parameter for item sales tax groups.</li>
</ul>
</td>
</tr>
<tr>
<td>Mandatory VAT date</td>
<td>Poland</td>
<td>
<p>You can require that the date of the VAT register be included in purchase and sales transaction records. Therefore, the date of the VAT register can be captured before a transaction is posted. This functionality helps you avoid having to handle multiple transactions at the end of the period.</p>
<p>You can make the <strong>Date of VAT register</strong> field mandatory when customer or vendor transactions are posted. To make this field mandatory, enable the <strong>VAT date is required</strong> option for the related customer or vendor account.</p>
</td>
</tr>
</tbody>
</table>
