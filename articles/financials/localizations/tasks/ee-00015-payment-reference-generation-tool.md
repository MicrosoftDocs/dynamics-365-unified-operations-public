--- 
# required metadata 
 
title: Payment reference generation tool (Eastern Europe)
description: This procedure walks you through generating the payment references. 
author: v-oloski
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
ms.search.region: Estonia
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Payment reference generation tool (Eastern Europe)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure walks you through generating the payment references. This task was created using the demo data company DEMF with the country/region of legal entity primary address updated to be Estonia. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Specify a number sequence for payment references
1. Go to Accounts receivable > Setup > Accounts receivable parameters.
2. Click the Number sequences tab.
3. In the Reference column. find and select 'Payment reference' record.
4. In the Number sequence code field, enter or select a value.
    * You may want to select a dedicated, newly created numeric and continuous number sequence. For demo purposes, you can use  'Acco_18'.  
5. Click Save.

## Create payment reference numbers
1. Go to Accounts receivable > Periodic tasks > Create payment reference numbers.
2. Select Yes in the Create payment reference numbers field.
    * Select 'Delete payment reference numbers' to remove reference numbers already assigned to customers. You may limit the customers for which you want to remove or create reference numbers by using 'Record to include' section and applying criteria for customers or customer groups.  
3. Click OK.

