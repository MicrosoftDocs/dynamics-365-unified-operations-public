--- 
# required metadata 
 
title: Create a collection letter sequence
description: Use this task guide to create a collection letter sequence. 
author: mikefalkner
manager: AnnBe 
ms.date: 11/10/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a collection letter sequence

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use this task guide to create a collection letter sequence. This task uses the USMF demo company.

1. Go to Credit and collections > Setup > Set up collection letter sequence.
2. Click New.
3. In the Collection letter sequence field, enter a sequence ID that will represent the sequence. It will be used when you set up a posting profile.
4. In the Description field, type a value.
    * The terms of payment is optional. If you enter a value here, the collection letter fee invoice will use these terms of payment instead of the terms of payment stored with the customer.  
5. In the collection letter code field, select the code for the first collection letter that you want to send.
    * The first collection letter is created according to the due date on the invoice, the value that you enter for the grace period in the Days field on this line, and other information that you enter on this line.  
6. In the Description field, type a value.
    * The currency for the fee defaults to the customer currency. This currency code can be different than the invoice currency.  
7. Click Add to add the next collection letter that will be sent in the sequence
    * In many cases, the first collection letter is just a warning. You can add fees if needed.  
8. In the collection letter code field, select the next collection letter that will be sent in the sequence.
9. In the Description field, type a value.
10. In the main account field, select the revenue account that will be used for fees.
11. Enter the fee that will be charged when this collection letter is posted.
12. In the Item sales tax group field, click the drop down button to open the lookup.
    * Select an item sales tax group if sales taxes must be calculated on the fee.  
13. In the list, click the link in the selected row.
14. Enter the minimum overdue balance required before a collection letter is sent.
15. Enter the number of grace days that you will allow.
    * This is the number of days after the due date that a collection letter can be generated. The due date that is used for the calculation depends on the position of the collection letter in the collection letter sequence:   ⦁	The grace period for collection letter 1 is relative to the due date on the invoice.  ⦁	The grace period for collection letters 2 and higher is relative to the date that the previous collection letter is posted or printed, depending on the selection in the Update collection letter code field in the Accounts receivable parameters page.  
16. Click Add to add the last collection letter in the sequence.
    * You can add up to five collection letter codes for a collection letter sequence.  
17. In the collection letter code field, select the next collection letter that will be sent in the sequence.
18. In the Description field, type a value.
19. In the Main account field, specify the desired values.
20. In the Fee in currency field, enter a number.
21. In the Item sales tax group field, click the drop-down button to open the lookup.
22. In the list, click the link in the selected row.
23. In the Minimum overdue balance field, enter a number.
24. In the Days field, enter a number.
25. Select this check box to stop the customer from additional deliveries and invoicing.
    * To unblock the account, select No in the Invoicing and delivery on hold field in the Customers page.  
26. Expand the Note fasttab.
27. Enter the text to appear on the collection letter for the selected collection letter code.
    * You can translate this text in to multiple languages using the Translations menu above the note box.  

