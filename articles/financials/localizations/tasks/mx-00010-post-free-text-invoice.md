--- 
# required metadata 
 
title: Post a free text invoice (Mexico)
description: Use the Free text invoice form to create and post a customer invoice as an electronic invoice by using CFDI method. 
author: sndray
manager: AnnBe 
ms.date: 05/09/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Post a free text invoice (Mexico)

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use the Free text invoice form to create and post a customer invoice as an electronic invoice by using CFDI method. You must to be logged in a Mexican legal entity. This task guide was created using the MXMF demo data company.


## Post and issue a CFDI electronic invoice
1. Go to Accounts receivable > Invoices > All free text invoices.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. In the Description field, type a value.
7. In the Main account field, specify the desired values.
8. In the Sales tax group field, type a value.
9. In the Item sales tax group field, type a value.
10. In the Unit price field, enter a number.
11. Expand or collapse the Line details section.
12. Click the Electronic invoices tab.
13. In the Property number field, type a value.
    * You must specify the property registration number provided by the Mexican government when you create the free text invoice for a leasing service.  
14. Click Post.
15. Click OK.
    * After you press OK, the customer invoice is posted and scheduled in a specific batch processing for issuing electronic invoices (CFDI).  
16. Close the page.
17. Go to Accounts receivable > Invoices > E-Invoices > Export/import electronic invoice process.
18. Click OK.
    * This batch job executes the connection with the PAC web services to get the approval or cancellation of a CFDI electronic invoice. The task in the batch can run manually or scheduled by specific period of time.   	After you press OK, a web connection with the  is established in order to get the validation and digital signature. If the electronic invoice is approved,  the PAC sends the response XML message and the status of the electronic invoice is set to Approved. An email is automatically sent out to the customer with the XML and PDF file attached. Send mail and Send report file - PDF checkboxes must be enable in the electronic invoice parameters. Otherwise, you can email or print a PDF report based on customer's request by using Inquire and Reports > CFDI (electronic invoices) menu.    
19. Go to Accounts receivable > Inquiries and reports > CFDI (electronic invoices).
20. In the list, mark the selected row.
21. In the list, click the link in the selected row.

