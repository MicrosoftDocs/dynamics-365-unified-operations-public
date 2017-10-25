--- 
# required metadata 
 
title: Set up sales tax groups for reverse charge VAT (UK)
description: This task walks you through setting up reverse charge sales tax groups for purchasing and sales purposes. 
author: epodkolz
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
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: United Kingdom
# ms.search.industry: 
ms.author: epodkolz
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up sales tax groups for reverse charge VAT (UK)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task walks you through setting up reverse charge sales tax groups for purchasing and sales purposes. This walkthrough was created using the demo company GBSI.

This task requires that the following sales tax codes are created for Reverse charge purposes.  

REV17.5 – positive value

REV-17.5 – negative value

The sales tax group 'RC-VAT' should already contain both +ve and -ve sales tax codes.

In this task you'll create a new sales tax group that will contain a +ve sales tax code.

1. Go to Tax > Indirect taxes > Sales tax > Sales tax groups.
2. In the list, find and select the desired record.
    * For this example, select 'RC-VAT'.  
3. Expand or collapse the Setup section.
    * Verify that the following sales tax codes exist for Reverse charge purposes:  REV17.5 – positive value  REV-17.5 – negative value    
4. In the list, find and select the desired record.
    * Select the 'REV-17.5' sales tax code. This must be a sales tax code with a negative value.  
5. Click Edit.
6. Select the Reverse charge check box.
7. Click Save.
8. Click New.
9. In the Sales tax group field, type a value.
    * For this example, enter 'RC-VAT-AR'.  
10. In the Description field, type a value.
    * For this example, enter "Reverse charge VAT sales".  
11. Click Add.
12. In the Sales tax code field, click the drop-down button to open the lookup.
13. In the list, find and select the sales tax code REV17.5 with positive value
14. In the list, click the link in the selected row.
15. Select the Exempt check box.
16. Select the Reverse charge check box.
17. Click Save.

