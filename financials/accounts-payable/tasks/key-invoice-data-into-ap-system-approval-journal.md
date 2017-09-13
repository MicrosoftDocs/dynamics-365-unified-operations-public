--- 
# required metadata 
 
title: Key invoice data into accounts payable using an approval journal
description: This task guide will show you how to use the invoice register to create invoices and then use the approval journal to update the expense accounts. 
author: abruer
manager: AnnBe 
ms.date: 11/15/2016
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
# Key invoice data into accounts payable using an approval journal

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide will show you how to use the invoice register to create invoices and then use the approval journal to update the expense accounts.


## Create and post and invoice
1. Go to Accounts payable > Invoices > Invoice register.
2. Click New.
3. Select the name of the invoice register that you want to use.
4. In the list, click the link in the selected row.
5. Click on Lines to open the register and enter expense lines.
6. Select a vendor. For example, enter or select US-104
7. In the Invoice field, type a value.
8. In the Description field, type a value.
9. In the Credit field, enter a number.
10. In the Approved by field, click the drop-down button to open the lookup.
11. Highlight an approver and click Select to select that approver.
12. Click Post.
13. Close the page.
14. Close the page.

## Approve an invoice
1. Go to Accounts payable > Invoices > Invoice approval.
2. Click New.
3. Select the name of the invoice approval journal that you want to use.
4. In the list, click the link in the selected row.
5. Click lines to display a page where you will be able to select the invoices that you want to approve.
6. Select Find Vouchers to display all of the invoices that are ready for approval.
7. Mark the invoice that you created.
8. Click Select.
    * The vouchers that you selected above are moved to this list after you select them.  
9. Click OK.
10. Click on the account number field to add an expense account to the invoice.
11. Enter an account number and tab off of the field. For example, enter 600120.
12. Click Post.
13. Click Voucher to view the entries that were posted.
    * The Invoice Pending Approval account is reversed and replaced with the actual expense account.  

