--- 
# required metadata 
 
title: Create and post a customer invoice for a public sector customer
description: This procedure walks you through creating and posting a sales order invoice for a customer using OIOUBL electronic invoicing. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, ContactPersonLookup, SalesEditLines,  CustInvoiceJournal, ERFormatMappingRunJobTable   
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
# Create and post a customer invoice for a public sector customer

[!include [banner](../../includes/banner.md)]

This procedure walks you through creating and posting a sales order invoice for a customer using OIOUBL electronic invoicing. 



It was created using the demo data company USMF with a legal entity primary address in Denmark.



This is the fifth procedure out of six illustrating end to end process of generating e-invoices using electronic reporting configurations. It is based on OIOUBL e-invoice example which is common for Denmark, Austria and Norway. In order to find minor differences for other country/region specific e-Invoice implementations, like Spanish or Italian, please refer to available WIKI articles.



Before you can complete this procedure, you must complete the following procedures: 'Import OIOUBL electronic invoicing electronic reporting configurations', 'Set up OIOUBL electronic invoicing' and 'Set up a customer account for OIOUBL electronic invoicing'.


## Create a sales order
1. Go to Accounts receivable > Orders > All sales orders.
2. Click New.
3. In the Customer account field, enter or select a value.
    * Select a customer that is enabled for electronic invoicing.  
4. Click OK.
5. Select a sales order header view.
6. In the Contact field, enter or select a value.
7. In the Customer requisition field, type a value.
8. In the Customer reference field, type a value.
9. Expand the Setup section.
10. Select a sales order line view.
11. In the Item number field, enter or select a value.
    * You may use an item number 'D0001'.  
12. Click Save.

## Post an invoice for a sales order
1. On the Action Pane, click Invoice.
2. Click Invoice.
3. Expand the Parameters section.
4. In the Quantity field, select 'All'.
5. Click OK.
6. Click OK.

## Generate OIOUBL electronic invoice
1. Click Invoice.
2. On the Action Pane, click Invoice.
3. Click Send.
4. Click Original.

## View an OIOUBL electronic invoice
1. Go to Organization administration > Electronic reporting > Electronic reporting jobs.
2. Click Show files.
3. Click Open.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]