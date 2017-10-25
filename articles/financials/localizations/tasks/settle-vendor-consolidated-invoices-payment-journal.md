--- 
# required metadata 
 
title: Settle vendor consolidated invoices by using a payment journal (Japan)
description: In Japan, payments are made and settled against consolidated invoices. 
author: ShylaThompson
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
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Settle vendor consolidated invoices by using a payment journal (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, payments are made and settled against consolidated invoices.



This procedure walks you through settling a consolidated invoice using a payment journal and payment proposal feature. 



Before you complete this procedure, be sure that you have a consolidated invoice created and confirmed. 



This procedure was created using the demo data company JPMF.

1. Go to Accounts payable > Periodic tasks > Consolidated invoice.
2. Note the value in the Consolidation ID field to reference later
    * You can use JPMF-000002 from the demo data company JPMF.  
3. Go to Accounts payable > Payments > Payment journal.
4. Click New.
5. In the Name field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
7. Click Lines.
8. Click Payment proposal.
9. Click Create payment proposal.
10. Expand or collapse the Advanced parameters section.
11. In the Consolidation ID field, type a value.
    * You can use the value noted previously on the Consolidated invoice page.  
12. Click OK.
13. Click Create payments.
    * Confirm that the payment line was generated based on the proposal and then provide a date for posting.  
    * When there are multiple invoices tied on one consolidated invoice, multiple lines might be generated on the payment journal.  
14. Click Post.
15. Go to Accounts payable > Periodic tasks > Consolidated invoice.
    * Confirm that the status of the consolidated invoice has been updated to be Settled.  

