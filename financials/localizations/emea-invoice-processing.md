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

## Accounts receivable and Accounts payable dates for VAT
```Countries affected: Czech Republic, Poland```

When goods are purchased from the European Union countries, there is an obligation of self-assessment of VAT: 
-	The output VAT must be paid in a VAT period where the invoice has been issued (Document date)
-	The input VAT can’t be deducted before the document receipt (VAT register date).

The following settings should be done to support this scenario:
- On the the **Accounts payable parameters** page, enable **Intra-community VAT** and **Document date for intra-community VAT** 
- Two sales tax codes: one with positive sales tax percentage and another with negative
- Set up a sales tax group including both positive and negative sales tax codes. For the negative sales tax code set the ‘Intra-community VAT’ parameter to be **true**.

After a successfull setup, purchases will have two posted sales tax transactions:
- A positive transaction with direction ‘sales tax receivable’ and VAT register date equals to the same date from the invoice posting window
- A negative transaction with direction ‘sales tax payable’ and VAT register date equals to the document date.



Also it provides a short description for some country-specific scenarios, for example, Intra-community VAT or Deferred tax.

|Scenario   |Applicable for countries   |Description of the functionality changes   |
|---|---|---|
|Accounts receivable and Accounts payable dates for VAT   |Czech Republic, Poland | When the goods are purchased from the European Union countries, there is an obligation of self-assessment of VAT: <br>  - the output VAT must be paid in VAT period where the invoice has been issued (Document date),<br>  - the input VAT can’t be deducted before document receipt (VAT register date).<br>The following settings should be done to support this scenario:<br>  - enable ‘Intra-community VAT’ and ‘Document date for intra-community VAT’ in the Accounts payable parameters,<br>  - two sales tax codes: one with positive sales tax percentage and another with negative,<br>  - set up a sales tax group including both positive and negative sales tax codes. Negative sales tax code will have ‘Intra-community VAT’ parameter set to true.<br>In result a purchase will have two posted sales tax transactions:<br>  - a positive transaction with direction ‘sales tax receivable’ and VAT register date equals to the same date from the invoice posting window,<br>  - a negative transaction with direction ‘sales tax payable’ and VAT register date equals to the Document date. |
|Modify a sales document date   |All Eastern European countries   |You can modify the ‘Document date’ on a project invoice. This date is displayed in the printing form of invoice. A Document date field has been added to the Posting invoice and Free text invoice forms. After you post an invoice, the ‘Document date’ is displayed in its header.   |
|Document date for exchange rate   |Poland, Hungary, Czech Republic   |Legal legislation provides different rules for selecting valid exchange rate for business transactions. In the field ‘Exchange rate date’ both in Accounts receivable parameters and Accounts payable parameters you may select a date that will be used for amount in accounting currency calculation in purchase and sales documents. During data entry, the system will retrieve the exchange rate for the transaction, based on this parameter.<br>Note: When the field ‘Exchange rate date’ is set to “Document date (for EU trade only)”, the system will look to the Sales Tax group. On the sales tax group, there is a parameter on the General tab, labeled “EU trade”. If this is marked and this sales tax group exists on the header of the document, the system will retrieve the exchange rate based on the Document date. If the “EU trade” checkbox is not marked for this sales tax group, then the system will retrieve the exchange rate based on the Posting date of the document.   |
|Trade dates, VAT register dates, document and VAT date control   |Poland, Hungary, Czech Republic  |The sales date and the document receipt date are essential for conclusive evidence of VAT reporting. The sales date is the fulfilment date of the transaction in Accounts receivable. The document receipt date is a date that demonstrates the rights to claim VAT deduction in Accounts payable. Each received document has a date for audit purposes.<br>The Hungarian functionality for date deadlines, the Czech Republic functionality for fulfill dates, and the Polish functionality for the VAT register date include the requirement for the tax information reporting based on a date that is different than the posting date. The ‘Date of VAT register’ field supports this requirement and it appears on over 20 forms, including journals, sales orders, purchase orders, free-text invoices, vendor invoice journals, project invoices, etc. When the user updates or posts the documents, all taxes will be posted with the corresponding date of the VAT register, and the date is on relevant forms, such as customer and vendor invoice journals.<br>Specifically for the Czech Republic, field ‘VAT register date’ can be empty during posting just in case of Postponed VAT posting. Otherwise it must be mandatory filled in.<br>Date validation parameters can be set on the form ‘Sales tax groups’:<br>  -	Parameters ‘Date of VAT register filling’ and ‘Sales date filling’ are used as a default filling method for appropriate dates. The manual input as well as several ways of the automated filling are available.<br>  -	Field ‘Mandatory sales date’ indicates whether the sales date must be entered before posting a sales invoice.<br>On the form ‘VAT Register transactions’ you can fill in empty Dates of VAT register for posted Tax Transactions. |
|VAT register dates including deferred tax |Hungary |Due to the Hungarian tax legislation, the invoice must be created at the time of fulfilment date or not later than 15 days after the fulfilment. Fulfilment date means the date of:<br>  - providing the ordered services,<br>  - delivering the ordered items.<br>When you update or post the documents, all taxes will be posted with the corresponding date of the VAT register, and the date is on relevant forms.<br>Based on a special regulation, the VAT on continuous delivery of services, such as renting, leasing, consulting, and heating, must be:<br>  - recorded to dedicated for this purpose special general ledger accounts on the invoice date,<br>  - transferred from those special accounts to sales tax receivable \ payable accounts and included into VAT report on the due date.<br>General ledger postings on the Deferred incoming tax and the Deferred outgoing tax accounts is introduced to address that regulation.<br>To support this scenario, you need to maintain settings described below:<br>  - set accounts ‘Deferred VAT Payable’ and ‘Deferred VAT Receivable’ in Ledger posting groups,<br>  - enable parameter ‘Deferred VAT’ for Item sales tax groups.
|VAT register dates including deferred tax |Hungary |Due to the Hungarian tax legislation, the invoice must be created at the time of fulfilment date or not later than 15 days after the fulfilment. Fulfilment date means the date of:<br>  - providing the ordered services,<br>  - delivering the ordered items.<br>When you update or post the documents, all taxes will be posted with the corresponding date of the VAT register, and the date is on relevant forms.<br>Based on a special regulation, the VAT on continuous delivery of services, such as renting, leasing, consulting, and heating, must be:<br>  - recorded to dedicated for this purpose special general ledger accounts on the invoice date,<br>  - transferred from those special accounts to sales tax receivable \ payable accounts and included into VAT report on the due date.<br>General ledger postings on the Deferred incoming tax and the Deferred outgoing tax accounts is introduced to address that regulation.<br>To support this scenario, you need to maintain settings described below:<br>  - set accounts ‘Deferred VAT Payable’ and ‘Deferred VAT Receivable’ in Ledger posting groups,<br>  - enable parameter ‘Deferred VAT’ for Item sales tax groups.<br>If this option is selected, corresponding tax entries will be posted using the deferred tax logic, as indicated in the Ledger posting group. |
|Mandatory VAT date |Poland   |You can require that the date of VAT register be included in purchase and sales transaction records. Requiring this information provides the opportunity to catch the date of VAT register prior to posting a transaction. You will then avoid having to handle multiple transactions at the end of the period.<br>It’s possible to make the field ‘Date of VAT register’ mandatory when posting customer/vendor transactions. To do that you should set up a flag 'VAT date is required' for the related customer/vendor account. |
