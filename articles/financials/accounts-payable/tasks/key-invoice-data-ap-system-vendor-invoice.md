--- 
# required metadata 
 
title: Key invoice data into accounts payable using a vendor invoice
description: This task guide will help you create a vendor invoice from a purchase order and view the results of matching the purchase order, receipt, and invoice (3 way matching). 
author: abruer
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
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Key invoice data into accounts payable using a vendor invoice

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide will help you create a vendor invoice from a purchase order and view the results of matching the purchase order, receipt, and invoice (3 way matching).


## Create a purchase order
1. Go to Accounts payable > Purchase orders > All purchase orders.
2. Click New.
3. In the Vendor account field, click the drop-down button to open the lookup.
4. Find a vendor to select. For example, scroll down to US-104.
5. Select vendor US-104.
6. Click OK.
7. In the Item number field, click the drop-down button to open the lookup.
8. Select an inventory item. For example, select item number 1000.
9. Expand or collapse the Line details section.
10. Click the Setup tab.
    * You can override the matching policy to use no matching, 2-way matching, or 3-way matching.  
11. Expand or collapse the Line details section.
12. On the Action Pane, click Purchase.
13. Click Confirm.

## Receive the products
1. On the Action Pane, click Receive.
2. Click Product receipt.
3. In the Product receipt field, enter the product receipt number. For example, enter PR123.
4. Click OK to post the product receipt.
5. Close the page.

## Create a vendor invoice
1. Go to Accounts payable > Purchase orders > Purchase orders received but not invoiced.
2. Select the purchase order that you created.
3. On the Action Pane, click Invoice.
4. Click Invoice.
5. In the Number field, enter the invoice number.
6. In the Invoice description field, type a value.
7. In the Invoice date field, enter a date.
8. In the Unit price field, enter 1200.
9. Click Add line.
10. In the Item number field, click the drop-down button to open the lookup.
11. In the list, find the installation charge item number. For example, S0001
12. Select the installation charge item number.
    * Note that matching has not been performed since you made the changes.  
13. Click Update match status.
14. On the Action Pane, click Review.
15. Click Matching details.
    * The new line with services does not need to be matched so the status stays "Not performed".  
16. Select the product receipt for the inventory item that you received.
    * The line with the product receipt was matched but there is a mismatch of quantity or price so it fails.  
17. In the Unit price field, enter a number.
    * Now that the unit price matches, the status is updated to Passed. If your policy allows discrepancies or if matching is only a warning, you can still post the invoice.  
18. Close the page.
19. Click Post.
20. Close the form.
    * Note that the purchase order is no longer listed as received but not invoiced.  

