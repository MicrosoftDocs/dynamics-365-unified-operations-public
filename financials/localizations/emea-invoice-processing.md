---
# required metadata
title: Invoice processing for
description: This topic provides information about invoice processing for Eastern Europe.
author: v-kikozl
manager: AnnBe
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 
# optional metadata
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: shylaw
# ms.search.scope: All topics: Operations Platform
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 53658174-3830-49de-8d01-23d1623d97d5
ms.search.region: Czech Republic, Hungary, Estonia, Poland,
# ms.search.industry: 
ms.author: v-kikozl
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2
---

# Invoice processing

This topic provides information about processing customer and vendor invoices for some European countries. Legal requirements for these countries affect the invoicing process. 

<table>
 <thead>
  <tr >
   <td>
   <p><strong>Scenario</strong></p>
   </td>
   <td>
   <p><strong>Countries</strong></p>
   </td>
   <td>
   <p><strong>Description of the functionality changes</strong></p>
   </td>
  </tr>
 </thead>
 <tr>
  <td>Accounts receivable and Accounts payable
  dates for VAT </td>
  <td> The Czech Republic, Poland </td>
  <td>When goods are purchased from the European Union countries, there is an obligation of self-assessment of VAT:
  <ul>
   <li>The output VAT must be paid in a VAT period where the invoice has been issued (Document date)</li>
   <li>The input VAT can’t be deducted before the document receipt (VAT register date).</li>
  </ul>
  <p>The following settings should be done to support this scenario:</p>
  <ul>
   <li>On the the <strong>Accounts payable parameters</strong> page, enable <strong>Intra-community VAT</strong> and <strong>Document date for intra-community VAT</strong></li>
   <li>Two sales tax codes: one with positive sales tax percentage and another with negative</li>
   <li>Set up a sales tax group including both positive and negative sales tax codes. For the negative sales tax code set the ‘Intra-community VAT’ parameter to be <strong>true</strong>.</li>
  </ul>
  <p>After a successful setup, purchases will have two posted sales tax transactions:</p>
  <ul >
   <li>A positive transaction with direction ‘sales tax receivable’ and VAT register date equals to the same date from the invoice posting window</li>
   <li>A negative transaction with direction ‘sales tax payable’ and VAT register date equals to the document date.</li>
  </ul>
  <p>Also, it provides a short description for some country-specific scenarios, for example, Intra-community VAT or Deferred tax.</p>
  </td>
 </tr>
 <tr>
  <td>
  <p>Modify a sales document date</p>
  </td>
  <td>
  <p>All Eastern European countries</p>
  </td>
  <td>
  <p>You can modify the <strong>Document date</strong> field on a project invoice. This date is displayed on the printed invoice. </p>
  <p>There is also a <strong>Document date</strong> field on the <strong>Posting invoice</strong> and <strong>Free text invoice</strong> pages. After you post an invoice, the document date is displayed on the invoice header.</p>
  </td>
 </tr>
 <tr>
  <td>
  <p><strong>Document date for exchange rate</strong></p>
  </td>
  <td>
  <p>Poland, Hungary, Czech Republic</p>
  </td>
  <td>
  <p>Legal legislation provides different rules for selecting valid exchange rates for business transactions. In the <strong>Exchange rate date</strong> field on the <strong>Accounts receivable parameters</strong> and <strong>Accounts payable parameters</strong> pages you may select a date that will be used for amount in accounting currency calculation in purchase and sales documents. During data entry, the system will retrieve the exchange rate for the transaction, based on this parameter.</p>
  <p><br>
  <strong>Note</strong>: When you set the <strong>Exchange rate date</strong> field to be <strong>Document date (for EU trade only)</strong>, the system will use the sales tax group. On the sales tax group, there is a parameter on the <strong>General</strong> tab, labeled <strong>EU trade</strong>. If the EU trade check box is selected for the sales tax group and if this sales tax group exists on the header of the document, the system will retrieve the exchange rate based on the document date. If the <strong>EU trade</strong> check box is not selected for this sales tax group, then the system will retrieve the exchange rate based on the posting date of the document.</p>
  </td>
 </tr>
 <tr>
  <td>
  <p><strong>Trade dates, VAT register dates, document and VAT date control</strong></p>
  </td>
  <td> <p>Poland, Hungary, Czech Republic</p>
  </td>
  <td>
  <p>The sales date and the document receipt date are required for VAT reporting.</p>
  <ul><li><p>The sales date is the fulfilment date of the transaction in Accounts receivable. </p><li>
  <li><p>The document receipt date is a date that demonstrates the rights to claim VAT deduction in Accounts payable. Each received document has a date for audit purposes.</p></li></ul>
  <p>The Hungarian functionality for date deadlines, the Czech Republic functionality for fulfill dates, and the Polish functionality for the VAT register date include the requirement for the tax information reporting based on a date that is different than the posting date. </p>
  <p>The <strong>Date of VAT register</strong> field supports this requirement and it appears on over 20 pages, including journals, sales orders, purchase orders, free-text invoices, vendor invoice journals, project invoices, etc. When you update or post the documents, all taxes are posted with the corresponding date of the VAT register, and the date is included on pages such as the customer and vendor invoice journals pages.</p>
  <p>Specifically, for the Czech Republic, the <strong>VAT register date</strong> field can be empty during posting just in case of Postponed VAT posting. Otherwise it must be mandatory filled in. Date validation parameters can be set on the <strong>Sales tax groups</strong> page:</p>
  <ul><li><p>The <strong>Date of VAT register filling</strong> and <strong>Sales date filling</strong> parameters are used as a default filling method for appropriate dates. The manual input as well as several ways of the automated filling are available.</p></li>
  <li><p>The <strong>Mandatory sales</strong> <strong>date</strong> field indicates whether the sales date must be entered before posting a sales invoice.</p></li></ul>
  <p>On the <strong>VAT Register transactions</strong> page, you can fill in empty dates of VAT register for posted tax transactions.</p>
  </td>
 </tr>
 <tr>
  <td>
  <p><strong>VAT register dates including deferred tax</strong></p>
  </td>
  <td>
  <p>Hungary</p>
  </td>
  <td>
  <p>Hungary tax regulations require that invoices must be created at either the time of fulfilment or no later than 15 days after fulfilment.</p>
  <p>The fulfilment date is either the date that the ordered services were provided or the date that ordered items were delivered. When you update or post the documents, all taxes are posted with the corresponding date of the VAT register, and the date is on relevant forms.Additionally, regulations require that VAT on continuous delivery of services, such as renting, leasing, consulting, and heating, must meet the following criteria:</p>
 <ul>
 <li><p>VAT must be posted to a dedicated general ledger account on the invoice date.</p></li>
 <li> <p>Vat must be transferred from those special accounts to a sales tax receivable account or a payable account and included into VAT report on the due date.</p></li></ul>
  <p>To support this requirement, you can transfer General ledger postings to the Deferred incoming tax account and the Deferred outgoing tax account. Before you can do this, you must complete the following prerequisites:</p>
  <ul>
 <li><p>Set up the ledger accounts <strong>Deferred VAT Payable</strong> and <strong>Deferred VAT Receivable</strong> in Ledger posting groups</p></li>
 <li><p>Enable the <strong>Deferred VAT</strong> parameter for item sales tax groups</p></li></ul>
  </td>
 </tr>
 <tr>
  <td>
  <p>Mandatory VAT date</p>
  </td>
  <td>
  <p>Poland</p>
  </td>
  <td>
  <p>You can require that the date of VAT register be included in purchase and sales transaction records. Requiring this information provides the opportunity to catch the date of VAT register prior to posting a transaction. As a result, this will help you to avoid handling multiple transactions at the end of the period.</p>
  <p><br>
  It’s possible to make the <strong>Date of VAT register</strong> field mandatory when posting customer or vendor transactions. To do this, enable the <strong>VAT date is required </strong>option for the related customer or vendor account.</p>
  </td>
 </tr>
</table>
