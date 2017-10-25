--- 
# required metadata 
 
title: Import a customer payment with JBA file format (Japan)
description: In Japan, the Japanese Bankers Association (JBA) file format is commonly used for Electronic Fund Transfer (EFT) among banks. 
author: ShylaThompson
manager: AnnBe 
ms.date: 09/16/2016
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
# Import a customer payment with JBA file format (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, the Japanese Bankers Association (JBA) file format is commonly used for Electronic Fund Transfer (EFT) among banks. 



This task walks you through importing an EFT file with a JBA format.



This procedure was created using the demo company data JPMF.

1. Go to Accounts receivable > Payments > Payment journal.
2. Click New.
3. In the Name field, type 'CustPay'.
4. Click Lines.
5. Click Functions.
6. Click Import payments.
7. In the Method of payment field, type a value.
    * For example, enter the method of payment that uses JBA(JP) - Format A.  
8. Click OK.
    * Select the file to upload.  
9. Click OK.
10. Close the report
    * A control report is generated.  
    * Note that the payment amount and description are imported.  
11. In the Account field, specify the values 'JPMF-000001'.
12. Click Post.

