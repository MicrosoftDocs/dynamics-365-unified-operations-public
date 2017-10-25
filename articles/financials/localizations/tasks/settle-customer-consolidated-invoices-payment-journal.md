--- 
# required metadata 
 
title: Settle customer consolidated invoices by using a payment journal (Japan)
description: In Japan, payments are made and settled against consolidated invoices. 
author: ShylaThompson
manager: AnnBe 
ms.date: 02/16/2016
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
# Settle customer consolidated invoices by using a payment journal (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, payments are made and settled against consolidated invoices.



This procedure walks you through settling a consolidated invoice using a payment journal and payment proposal feature. 



Before you complete this procedure, be sure that you have a consolidated invoice created and confirmed. 



This procedure was created using the demo data company JPMF.

1. Go to Accounts receivable > Periodic tasks > Consolidated invoice.
2. Note the value in the Consolidation ID field to reference later
    * You can use JPMF-000002 from the demo data company JPMF.  
3. Go to Accounts receivable > Payments > Payment journal.
4. Click New.
5. In the Name field, type a value.
6. Click Lines.
7. Click Payment proposal.
8. Click Create payment proposal.
9. Expand the Advanced parameters section.
10. In the Consolidation ID field, type a value.
    * You can use the value noted previously on the Consolidated invoice page.  
11. Click OK.
12. Click Create payments.
    * Confirm the payment line is generated based on the proposal.  Provide a Date for posting.  
    * When there are multiple invoices tied on one consolidated invoice, there may be multiple lines on the payment journal been generated.  
13. Click Post.
14. Go to Accounts receivable > Periodic tasks > Consolidated invoice.
    * Confirm that the status of the consolidated invoice has been updated to be Settled.  

