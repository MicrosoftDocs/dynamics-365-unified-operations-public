--- 
# required metadata 
 
title: Record a vendor invoice in the invoice journal
description: This task guide will show how to record vendor invoices that are not associated with purchase orders. 
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
# Record a vendor invoice in the invoice journal

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide will show how to record vendor invoices that are not associated with purchase orders. Examples of this type of invoice include expenses for supplies or services.  This recording uses the USMF demo company.

1. Go to Accounts payable > Workspaces > Vendor invoice entry.
2. Click New invoice journal.
3. Click New.
4. In the Name field, enter the journal name or click the drop down button to open the lookup.
5. In the Description field, type a value.
6. Click Lines.
    * In the Date field, enter the posting date that will update General Ledger.  
7. In the Account field, specify the Vendor account.
8. In the Invoice field, enter the invoice number.
9. In the Description field, type a value.
10. In the Credit field, enter a number.
11. In the Offset account field, enter the account number or click the drop down button to open the lookup
    * The Sales tax group will default from the vendor account.  
    * The Item sales tax group will default from the main account specified in the Offset account field.  
    * The Due date will be calculated based on the Terms of payment.  
    * The Cash discount will default from the Vendor account.  
12. Click Post.
13. Close the page.

