--- 
# required metadata 
 
title: Deposit customer payments
description: Deposit customer payments. 
author: ShivamPandey-msft
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
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Deposit customer payments

[!include[task guide banner](../../includes/task-guide-banner.md)]

Deposit customer payments. This task uses the USMF demo company.

1. Go to Accounts receivable > Payments > Payment journal.
2. Click New.
3. In the Name field, click the drop-down button to open the lookup.
4. Select the payment journal. 
5. Click Lines.
6. In the Account field, select the Customer for whom you are recording the payment.
7. In the Credit field, enter the amount of the payment.
    * You can choose to leave the amount blank, and have the system calculate it by selecting the invoices which were paid.  
8. In the Payment reference field, type a value.
    * The payment reference could be the check number for the payment you are entering. The payment reference is required in order to include the payment on a deposit slip.  
9. Mark the box Use a deposit slip.
    * If the payment should be included in the deposit, change this setting to Yes.  
10. Click New.
11. In the Account field, select the Customer for the next payment.
12. In the Credit field, enter the payment amount.
13. In the Payment reference field, type a value.
14. Mark the box Use a deposit slip.
15. Click Post.
    * Payments must be posted before the deposit slip can be generated. This is to ensure that the payments don't change after the deposit slip is generated.  
16. Click Functions.
17. Click Deposit slip.
18. Click OK.
    * The first page is used to create the deposit slip.  
19. Click OK.
    * The second step is to print the deposit slip, but this step is not required.  

