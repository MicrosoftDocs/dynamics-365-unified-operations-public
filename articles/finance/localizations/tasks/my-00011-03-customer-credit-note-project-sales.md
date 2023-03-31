--- 
# required metadata 
 
title: MY-00011 03 Generate Customer Credit note for Project sales
description: This task walks you through creating and printing a project credit note for GST. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProjProjectsListPage, ProjJournalTable, ProjJournalTransEmpl, ResourceLookup, TaxGroupLookup, ProjInvoiceProposalCreateLines, ProjInvoiceProposalDetail, CustInvoiceJourLookup_MY, TaxTmpWorkTrans, ProjInvoiceEditLines,  SysOperationSandboxForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Malaysia
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# MY-00011 03 Generate Customer Credit note for Project sales

[!include [banner](../../includes/banner.md)]

This task walks you through creating and printing a project credit note for GST.



To complete this task, you must be in the 'Project accountant' role and you must select the Invoice type of 'GST invoice' in general ledger parameters.

This task was created using the demo data company MYMF.




## Create project credit note
1. Go to Project management and accounting > Projects > All projects.
2. On the Action Pane, click Project.
3. Click Hour.
4. Click New.
5. Click Lines.
6. Click New.
7. In the Resource field, enter or select a value.
8. In the Hours field, enter a number.
9. Click Save.
10. Click the General tab.
11. In the Cost price field, enter a number.
12. In the Sales price field, enter a number.
13. In the Sales tax group field, enter or select a value.
14. In the Item sales tax group field, enter or select a value.
15. Click Save.
16. Click Post.
17. Click OK.
18. Close the page.
19. Close the page.

## Create and post invoice proposal
1. On the Action Pane, click Manage.
2. Click Invoice proposal.
3. In the End date field, enter a date.
4. Click Search.
5. Click Select all.
6. Click OK.
7. In the Reason code field, enter or select a value.
8. In the Original invoice number field, enter or select a value.
9. Click Sales tax.
    * Validate calculated negative tax amount for the tax code SR  
10. Click OK.
11. Click Post.
12. Select Yes in the Print invoice field.
13. Click OK.
14. Click OK.
    * Verify that the information on credit note report is correct.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]