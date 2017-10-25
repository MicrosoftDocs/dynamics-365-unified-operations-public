--- 
# required metadata 
 
title: Create a billing classification in the public sector
description: Public-sector organizations can use billing classifications to help manage free text invoices. 
author: twheeloc
manager: AnnBe 
ms.date: 11/10/2016
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
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a billing classification in the public sector

[!include[task guide banner](../../includes/task-guide-banner.md)]

Public-sector organizations can use billing classifications to help manage free text invoices. Billing classifications are used to group similar free text invoices for processing and viewing. Before using this procedure, verify that a billing code exists that can be assigned to a billing classification. This procedure was created using the PSUS demo company data in the public sector partition.

1. Go to Accounts receivable > Setup > Billing classifications.
2. Click New.
3. In the Billing classification field, type a value.
4. In the Description field, type a value.
5. In the Terms of payment field, click the drop-down button to open the lookup.
6. In the list, click the terms of payment for this billing classification.
    * When you accept the default settings for interest and collection letters, interest won't be calculated for invoices that use this billing classification, and collection letters won't be sent. To change these settings, unlock the task guide by clicking the Unlock icon at the top of the screen.  
7. Expand or collapse the Billing codes section.
8. Click Add.
9. In the Billing code field, click the drop-down button to open the lookup.
10. In the list, click a billing code to add to this billing classification.
11. Click Save.

