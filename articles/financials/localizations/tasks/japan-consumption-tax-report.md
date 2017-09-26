--- 
# required metadata 
 
title: Generate consumption tax report (Japan)
description: This procedure walks you through generating the Japan consumption tax report. 
author: ShylaThompson
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
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Generate consumption tax report (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure walks you through generating the Japan consumption tax report.



This procedure was created using the demo data company JPMF.





1. Go to Tax > Declarations > Sales tax > Japanese sales tax report.
2. In the From date field, enter a date.
    * For example: 2012/1/1  
3. In the To date field, enter a date.
    * For example: 2012/12/31  
4. In the Settlement period field, type a value.
5. In the Declaration type field, select an option.
6. In the Calculation method field, select an option.
7. Select Yes in the Amendment field.
    * If you have already generated the report previously and you are generating it again, you must choose to update the existing record on the amendment.  
8. Click OK.
9. Click Edit.
10. In the Item 6 field, enter a number.
    * The data is retrieved and summarized from the transactions. You can update the editable fields for adjustment purposes.  
11. Click Save.
12. Click Update amount.
    * This recalculates the amounts.  
13. Click Finalize.
14. Click Yes.
15. Click Consumption tax report.
16. Click the Tax calculation tab.
17. Click Edit.
18. In the Item 10 field, enter a number.
19. Click Save.
20. Click Update amount.
21. Click the Additional information tab.
    * In the Additional information tab, the information is printed as configured.  
    * For example: you can change the Installment basis slider to be 'Yes' to print a yes on the final report.  
22. Click Finalize.
23. Click Yes.
24. On the Action Pane, click Consumption tax report.
    * Click Print reports to generate the final report.  

