--- 
# required metadata 
 
title: Configure standard costs for labor and expenses
description: This procedure shows you how to set up standard costs for labor and expenses for a project. 
author: KimANelson
manager: AnnBe 
ms.date: 02/13/2017
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
ms.search.industry: Service industries
ms.author: knelson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure standard costs for labor and expenses

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to set up standard costs for labor and expenses for a project. This task uses the USSI data set.

1. Go to Project management and accounting > Setup > Prices > Cost price (hour).
2. Click New.
3. In the Effective date field, enter a date.
4. In the Cost price field, enter a number.
    * You can set up a standard cost price for the project category, or you can set up a cost price by worker number, project number, category, date, or any combination of these. The cost price that is applied is the cost price with the highest level of detail.  
5. Click Save.
6. Close the page.
7. Go to Project management and accounting > Setup > Prices > Sales price (hour).
8. Click New.
9. In the Effective date field, enter a date.
10. In the Valid for field, select an option.
11. In the Pricing field, enter a number.
    * You can set up a standard sales price for hour transactions or for a project category. You can also set up sales prices by worker number, project number, category, transaction date, or any combination of these. The actual sales price, which is applied when a worker enters a transaction in the Hour journal, is the sales price with the highest level of detail. For example, if both a general sales price and a worker-specific sales price are set up, the worker-specific sales price is used.  
12. Click Save.
13. Close the page.
14. Go to Project management and accounting > Setup > Prices > Cost price (expense).
15. Click New.
16. In the Effective date field, enter a date.
17. In the Cost price field, enter a number.
    * Multiple fields can be filled in, but this is the minimum needed to save the record.  
18. Click Save.
19. Close the page.
20. Go to Project management and accounting > Setup > Prices > Sales price (expense).
21. Click New.
22. In the Effective date field, enter a date.
23. In the Valid for field, select an option.
24. In the Pricing field, enter a number.
    * The actual sales price, which is applied when a worker enters transactions in an expense journal, is the sales price with the highest level of detail. For example, if both a general and a worker-specific sales price are set up, the worker-specific sales price is used.  
25. Click Save.

