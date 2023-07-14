--- 
# required metadata 
 
title: Create and post a free text invoice for a public sector customer
description: This procedure walks you through creating and posting a free text invoice for a customer using OIOUBL electronic invoicing. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustFreeInvoice, CustTableLookup, ContactPersonLookup, CustPostInvoiceJob   
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
# Create and post a free text invoice for a public sector customer

[!include [banner](../../includes/banner.md)]

This procedure walks you through creating and posting a free text invoice for a customer using OIOUBL electronic invoicing. 



It was created using the demo data company USMF with a legal entity primary address in Denmark.



This is the fourth procedure out of six illustrating end to end process of generating e-invoices using electronic reporting configurations. It is based on OIOUBL e-invoice example which is common for Denmark, Austria and Norway. In order to find minor differences for other country/region specific e-Invoice implementations, like Spanish or Italian, please refer to available WIKI articles.



Before you can complete this procedure, you must complete the following procedures: 'Import OIOUBL electronic invoicing electronic reporting configurations', 'Set up OIOUBL electronic invoicing' and 'Set up a customer account for OIOUBL electronic invoicing'.

1. Go to Accounts receivable > Invoices > All free text invoices.
2. Click New.
3. In the Customer account field, enter or select a value.
    * A customer selected for the free text invoice must be enabled for electronic invoicing.  
4. Select a free text invoice header view.
5. Expand the Customer section.
6. In the Customer requisition field, type a value.
7. In the Customer reference field, type a value.
8. In the Contact field, enter or select a value.
9. Select a free text invoice lines view.
10. In the list, mark the selected row.
11. In the Description field, type a value.
12. In the Main account field, specify the desired values.
13. In the Unit price field, enter a number.
14. Click Post.
15. Click OK.

## Generate an OIOUBL electronic invoice
1. Click Send.
2. Click Original.
    * You can verify the status of the job and download the actual file on the Electronic reporting jobs page.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]