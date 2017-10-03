--- 
# required metadata 
 
title: Key invoice data into the AP system using invoice pool
description: This task guide will show you how to use the invoice register to create invoices. 
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
# Key invoice data into the AP system using invoice pool

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide will show you how to use the invoice register to create invoices.  Then use the invoice pool to match the invoice to a purchase order and finalize the expense in the vendor invoice page.


## Create a purchase order
1. Go to Accounts payable > Purchase orders > Purchase orders.
2. Click New to create a purchase order.
3. In the Vendor account field, click the drop down button to open the lookup.
4. Select the vendor from the list. For example, vendor 1001.
5. Click OK.
6. In the Item number field, click the drop down button to open the lookup.
7. Find the services item number in the list. For example, select S0001.
8. Click on the item number and select it.
    * The net amount is 75.00.  That is the amount that we will expect on the invoice.  
9. On the action pane, click Purchase.
10. Click Confirm.

## Create and post and invoice
1. Go to Accounts payable > Invoices > Invoice register.
2. Click New.
3. Open the lookup to select the name of the invoice register that you want to use.
4. Select the name of the invoice register that you want to use.
5. Click on Lines to open the register and enter expense lines.
6. In the lookup, select a vendor. For example, click on vendor 1001.
7. In the Invoice field, enter the invoice number.
8. In the Description field, type a value.
9. In the Credit field, enter a number.
10. In the Purchase order field, click the drop down button to open the lookup.
11. Select the purchase order that you created earlier.
12. In the Approved by field, click the drop down button to open the lookup.
13. Highlight an approver and click Select to select that approver.
14. Click Post.
15. Close the form.
16. Close the form.

## Open an invoice from the pool and match it to a purchase order to complete the invoice process
1. Go to Accounts payable > Invoices > Invoice pool.
2. Click Purchase order to create a vendor invoice from the invoice in the pool.
3. Select the invoice that you want to review.
4. Click Update match status to complete the matching.
5. On the action pane, click Options.
6. Click Change view.
7. Click Grid view.
8. Click Post.
9. Close the form.
10. Go to Accounts payable > Vendors > Vendors.
11. Select the vendor that was on the purchase order. For example, select vendor 1001.
12. In the list, click the link in the selected row.
13. On the action pane, click Vendor.
14. Click Transactions.
15. Select the invoice that you created.
    * The invoice register accrual was reversed and posted to the appropriate expense account.  

