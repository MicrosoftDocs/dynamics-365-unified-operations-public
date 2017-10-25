--- 
# required metadata 
 
title: Control access to purchase agreements in the public sector
description: You can make sure that only approved departments can access a purchase agreement. 
author: twheeloc
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
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Control access to purchase agreements in the public sector

[!include[task guide banner](../../includes/task-guide-banner.md)]

You can make sure that only approved departments can access a purchase agreement. You can also limit the amount that each department can spend against the purchase agreement. In order to do this, the account structure and financial dimensions for department access must be set on the Accounts payable parameters form. This procedure was created for French public sector organizations using the PSUS demo company data in the public sector partition.

1. Go to Accounts payable > Purchase orders > Purchase agreements.
2. In the list, select the purchase agreement that you want to control access to.
3. On the Action Pane, click Purchase agreement.
4. Click Department access.
5. Click New.
6. In the Department field, click the drop-down button to open the lookup.
7. In the list, select the financial dimension for a department that has access to this purchase agreement.
8. In the Authorized amount field, enter the total amount that this department is authorized to release from this purchase agreement.
    * Add additional departments until all authorized departments have been added to the purchase agreement.  
9. Click Save.

