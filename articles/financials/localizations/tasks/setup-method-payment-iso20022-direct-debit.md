--- 
# required metadata 
 
title: Set up method of payment for ISO20022 direct debit
description: This procedure shows how to set up the customer method of payment for ISO20022 direct debit or any other payment type using electronic reporting. 
author: mrolecki
manager: AnnBe 
ms.date: 10/13/2016
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
ms.search.region: Global
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up method of payment for ISO20022 direct debit

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to set up the customer method of payment for ISO20022 direct debit or any other payment type using electronic reporting. 



Before you complete this task, you must set up export format configurations and payment accounts.



This procedure was created using the demo data company DEMF.



This is the third of five procedures that demonstrate the customer payment process using electronic reporting configurations.

1. Go to Accounts receivable > Payments setup > Methods of payment.
2. Use the Quick Filter to find records. For example, filter on the Method of payment field with a value of 'ELECTRONIC'.
3. Click Edit.
4. In the Payment account field, specify the values 'DEMF OPER'.
5. Expand the File formats section.
6. Select Yes in the Generic electronic reporting field.
7. In the Export format configuration field, enter or select a value.
    * In the list, select ISO20022 Direct debit (DE).  If the list is empty, the customer payment export format configuration has not been imported and active.  
8. Select Yes in the Require mandate field.
    * Select the Require mandate parameter for customer payment formats, which require including mandate information in the payment message, like SEPA direct debit.  
9. Click Save.

