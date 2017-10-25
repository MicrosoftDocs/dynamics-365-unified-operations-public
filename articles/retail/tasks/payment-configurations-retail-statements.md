--- 
# required metadata 
 
title: Payment configurations for Retail statements
description: This procedure demonstrates configurations for Retail store payment methods, which affect how Retail statements get created and posted. 
author: jashanno
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
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Payment configurations for Retail statements

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure demonstrates configurations for Retail store payment methods, which affect how Retail statements get created and posted.

This recording uses the USRT demo company.

1. Go to Retail and commerce > Channels > Retail stores > All retail stores.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. On the Action Pane, click Set up.
5. Click Payment methods.
6. Expand or collapse the Posting section.
7. Click Edit.
    * Select whether the amounts received for this payment method should be posted to a ledger account or bank account.  
    * Select the account that amounts received for this payment method should be posted to.  
    * Select an account to post possible differences between the total transaction amount received and the amount counted for this payment method.  
    * In this field you can enter an amount to control when the difference amount should be posted to another difference account. You can use this to track big differences.  
    * Select an account to post possible differences between the total transaction amount received and the amount counted, when it exceeds the value that is defined in the "Maximum difference amount" field.  
    * Select "Yes" to post bank drop amounts to a seperate account.  
    * In this field you can select whether bank drop amounts should be posted to a ledger account or a bank account.  
    * Select the account to post bank drop amounts into.  
    * Select the bank transaction type to use when posting bank drop amounts to the bank account.  
    * Select "Yes" to post safe drop amounts to a seperate account.  
    * Select whether safe drop amounts should be posted to the ledger account or the bank account.  
    * Select the account to post safe drop amounts into.  
8. Click Save.

