--- 
# required metadata 
 
title: E-invoicing CFDI (Mexico)
description: This task walks you through creating and posting a customer invoice as an electronic invoice by using the CFDI method. 
author: sndray
manager: AnnBe 
ms.date: 11/14/2016
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
# E-invoicing CFDI (Mexico)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task walks you through creating and posting a customer invoice as an electronic invoice by using the CFDI method. You can create and post multiple sales orders as electronic invoices and send the .pdf and .xml files as email attachments to customers. This task can only be completed if you are logged into a legal entity with a primary address in Mexico. This task uses the MXMF demo company data.

1. Go to Accounts receivable > Orders > All sales orders.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Click OK.
7. In the list, mark the selected row.
8. In the Item number field, click the drop-down button to open the lookup.
9. In the list, click the link in the selected row.
10. In the Unit price field, enter a number.
11. Expand or collapse the Line details section.
12. Click the Setup tab.
13. In the Sales tax group field, click the drop-down button to open the lookup.
14. In the list, click the link in the selected row.
15. In the Item sales tax group field, click the drop-down button to open the lookup.
16. In the list, find and select the desired record.
17. In the list, click the link in the selected row.
18. Click the Product tab.
19. In the Warehouse field, click the drop-down button to open the lookup.
20. In the list, find and select the desired record.
21. In the list, click the link in the selected row.
22. Click OK.
23. In the Custom number field, type a value.
    * Enter the number of the customs document that was generated when the item was imported.  
24. In the Custom date field, enter a date.
    * Select the date when the item was imported.  
25. In the Custom name field, type a value.
    * Enter the name of the customs authority in the country/region that the item was imported from.  If you enter values in the Custom number, Custom date, and Custom name fields, you cannot enter a value in the Property number field.  
26. In the Unit price field, enter a number.
27. Expand or collapse the Sales order header section.
28. On the Action Pane, click Sell.
29. Click Confirm sales order.
30. Click OK.
31. Click OK.
32. On the Action Pane, click Invoice.
33. Click Invoice.
34. Expand the Parameters section to review the parameters before posting.
35. Click OK.
    * After you press OK, the customer invoice is posted and scheduled in a specific batch processing for issuing electronic invoices (CFDI).  
36. Click OK.
37. Go to Accounts receivable > Invoices > E-Invoices > Export/import electronic invoice process.
38. Click OK.
    * This batch job initiates the connection with the PAC web services to get the approval or cancellation of an electronic invoice (CFDI). The task in the batch can run manually or it can be scheduled by specific period of time.   	After you press OK, the validation and the digital signature will be retrieved from the PAC. If the electronic invoice is approved,  the PAC send the response XML message and the status of the electronic invoice will update to be Approved. An email is automatically sent out to the customer with the XML and PDF file attached. The Send mail and Send report file - PDF sliders must be set to "Yes" on the electronic invoice parameters page. Otherwise, you can email or print PDF report based on the customer's request by using the Inquire and Reports > CFDI (electronic invoices) menu.  
39. Go to Accounts receivable > Inquiries and reports > CFDI (electronic invoices).
40. In the list, click the electronic invoice to review.

