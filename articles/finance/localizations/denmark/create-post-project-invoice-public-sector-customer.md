--- 
# required metadata 
 
title: Create and post a project invoice for a public sector customer
description: This task walks you through creating and posting a project invoice for a customer using OIOUBL electronic invoicing. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProjProjectContractsListPage, ProjInvoiceTable, ProjFundingSourceDetail, ContactPersonLookup, ProjSalesItemReq, ProjTableLookup, InventItemIdLookupSimple, SalesEditLines,  ProjInvoiceProposalListPage, ProjInvoiceProposalCreateLines, ProjInvoiceProposalDetail, ProjInvoiceEditLines, ProjInvoiceListPage, ERFormatMappingRunJobTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Denmark
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create and post a project invoice for a public sector customer

[!include [banner](../../includes/banner.md)]

This task walks you through creating and posting a project invoice for a customer using OIOUBL electronic invoicing. 



This task was created using the demo data company USMF with the country/region of legal entity primary address updated to Denmark.



This is the sixth procedure out of six illustrating end to end process of generating e-invoices using electronic reporting configurations. It is based on OIOUBL e-invoice example which is common for Denmark, Austria and Norway. In order to find minor differences for other country/region specific e-Invoice implementations, like Spanish or Italian, please refer to available WIKI articles.



Before you can complete this procedure, you must complete the following procedures: 'Import OIOUBL electronic invoicing electronic reporting configurations', 'Set up OIOUBL electronic invoicing' and 'Set up a customer account for OIOUBL electronic invoicing'.


## Update a project contract
1. Go to Project management and accounting > Projects > Project contracts.
2. Use the Quick Filter to find records. For example, filter on the Project contract ID field with a value of '000057'.
    * Select a project contract that has a customer funding source that is enabled for electronic invoicing.  
3. Open details for a project contract.
4. Expand the Funding sources section.
5. Click Details.
6. Expand the Other section.
7. In the Customer requisition field, type a value.
8. In the Customer reference field, type a value.
9. In the Contact ID field, enter or select a value.
10. Click Save.

## Create a project transaction
1. Go to Project management and accounting > Item tasks > Item requirements.
2. Click New.
3. In the Project ID field, enter or select a value.
    * As an example, you may use '000057' project ID.  
4. In the Item number field, enter or select a value.
    * As an example, you may use 'D0001' item number.  
5. On the Action Pane, click Manage.
6. Click Posting.
7. Click Packing slip.
8. Expand the Parameters section.
9. In the Quantity field, select 'All'.
10. Click OK.
11. Click OK.

## Create a proposal and post an invoice 
1. Go to Project management and accounting > Project invoices > Project invoice proposals.
2. Click New.
3. Click Invoice proposal.
4. In the Project field, enter or select a value.
5. Click OK.
6. Click Post.
7. Click OK.
8. Click OK.

## Generate an OIOUBL project invoice
1. Go to Project management and accounting > Project invoices > Project invoices.
2. Use the Quick Filter to find records. For example, filter on the Project contract ID field with a value of '000057'.
3. On the Action Pane, click Project invoice.
4. Click Send.
5. Click Original.

## View an OIOUBL electronic invoice
1. Go to Organization administration > Electronic reporting > Electronic reporting jobs.
2. Click Show files.
3. Click Open.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]