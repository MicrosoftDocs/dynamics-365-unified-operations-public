--- 
# required metadata 
 
title: Set up withholding tax
description: Withholding tax is a tax on vendors that does not create sales tax transactions. 
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
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up withholding tax

[!include[task guide banner](../../includes/task-guide-banner.md)]

Withholding tax is a tax on vendors that does not create sales tax transactions. Withholding tax that is calculated on vendor payments is a liability. Therefore, only balance sheet accounts or liability accounts are valid accounts for posting withholding tax. This task guide demonstrates how to set up withholding tax.

1. Go to Tax > Indirect taxes > Withholding tax > Withholding tax codes.
2. Click New.
3. In the Withholding tax code field, type a value.
4. In the Withholding tax name field, enter the name of the withholding tax code.
5. In the Main account field, select the main account for posting the withholding tax liability.
6. Click Save.
7. Click Values.
8. In the list, mark the selected row.
9. In the Value field, enter a percentage used for the calculation of the withholding tax.
10. Click Save.
11. Close the page.
12. Click Save.
13. Close the page.
14. Go to Tax > Indirect taxes > Withholding tax > Withholding tax groups.
15. Click New.
16. In the Withholding tax group field, enter the identifier of the withholding tax group.
17. In the Description field, enter the name of the withholding tax group.
18. In the list, mark the selected row.
19. In the Withholding tax code field, select the withholding tax code.
20. In the list, click the link in the selected row.
21. Click Save.

