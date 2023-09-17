--- 
# required metadata 
 
title: MY-00011 02 Generate Customer Debit Note for Project sales (November 2016)
description: This task walks you through creating and printing project debit note for GST. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProjProjectsListPage, SalesCreateOrder, SalesTable, CustInvoiceJourLookup_MY, TaxGroupLookup, ProjJournalTable, ProjJournalTransEmpl, ResourceLookup, ProjInvoiceProposalCreateLines, ProjInvoiceProposalTransTypeLookup, ProjInvoiceProposalDetail, ProjInvoiceEditLines   
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
# MY-00011 02 Generate Customer Debit Note for Project sales (November 2016)

[!include [banner](../../includes/banner.md)]

This task walks you through creating and printing project debit note for GST.



To complete this task, you must be in the 'Project accountant' role and you must select the Invoice type of 'GST invoice' in general ledger parameters.

This task was recorded using the MYMF demo data company.



This procedure is for a feature that was added in Dynamics 365 for Operations, version 1611.


## Create a project sales debit note
1. Go to Project management and accounting > Projects > All projects.
2. On the Action Pane, click Manage.
3. In the New group on the Action Pane, click Item task.
4. Click Sales order.
5. Expand the General section.
6. In the Site field, enter or select a value.
7. In the Warehouse field, enter or select a value.
8. Click OK.
9. On the Action Pane, click Options.
10. Click Change view.
11. Click Header view.
12. In the Reason code field, enter or select a value.
13. Click Save.
14. Click Change view.
15. Click Line view.
16. In the Item number field, enter or select a value.
17. In the Quantity field, enter a number.
18. In the Unit price field, enter a number.
19. In the list, mark the selected row.
20. In the Original invoice number field, enter or select a value.
21. Expand the Line details section.
22. Click the Setup tab.
23. In the Sales tax group field, enter or select a value.
24. In the Item sales tax group field, enter or select a value.
25. Click Save.
26. Close the page.

## Create and post hour journal
1. On the Action Pane, click Project.
2. Click Hour.
3. Click New.
4. Click Lines.
5. Click New.
6. In the Resource field, enter or select a value.
7. In the Hours field, enter a number.
8. Click the General tab.
9. In the Cost price field, enter a number.
10. In the Sales price field, enter a number.
11. In the Sales tax group field, enter or select a value.
12. In the Item sales tax group field, enter or select a value.
13. Click Save.
14. Click Post.
15. Click OK.
16. Close the page.
17. Close the page.

## Create and post invoice proposal
1. On the Action Pane, click Manage.
2. Click Invoice proposal.
3. In the End date field, enter a date.
4. In the Transaction types field, enter or select a value.
5. Click Search.
6. Click Select all.
7. Click OK.
8. In the Reason code field, enter or select a value.
9. Expand the Invoice proposal transactions section.
10. Click the Hour tab.
11. In the list, mark the selected row.
12. In the Original invoice number field, enter or select a value.
13. Click Save.
14. Click Post.
15. Select Yes in the Print invoice field.
16. Click OK.
17. Click OK.
    * Validate debit note report  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]