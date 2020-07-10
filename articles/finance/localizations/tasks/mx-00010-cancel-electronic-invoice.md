--- 
# required metadata 
 
title: MX-00010 Cancel an electronic invoice
description: You can cancel a CFDI electronic invoice that was previously validated and certified by the PAC. 
author: sndray
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: EInvoiceCFDIJournal_AR   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# MX-00010 Cancel an electronic invoice

[!include [banner](../../includes/banner.md)]

You can cancel a CFDI electronic invoice that was previously validated and certified by the PAC. You can also cancel a CFDI electronic invoice by using the manual process.


## Cancel a CFDI electronic invoice
1. Go to Accounts receivable > Inquiries and reports > CFDI (electronic invoices).
2. Select an electronic invoice with a status of Approved.
3. Click the invoice number link to see the details.
4. On the Action Pane, click Functions.
5. Click Cancel CFDI.
6. Close the page.
7. Go to Accounts receivable > Invoices > E-Invoices > Export/import electronic invoice process.
8. Click OK.
    * When the cancelation is confirmed, the status of the electronic invoice is changed to be Canceled.  
9. Go to Accounts receivable > Inquiries and reports > CFDI (electronic invoices).
10. Select the canceled invoice to verify the status.

## Manually cancel a CFDI electronic invoice
1. Select an invoice with status Approved.
2. On the Action Pane, click Functions.
3. Click Manual cancel.
4. Enter the date of cancelation.
5. In the Cancel key name field, enter the reason for the cancelation..
6. Click OK to confirm the cancelation of the electronic invoice.
    * The status of electronic invoice is Manual cancel.  

