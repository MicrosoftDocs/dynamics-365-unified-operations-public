--- 
# required metadata 
 
title: Configure standard costs for labor and expenses
description: This topic explains how to set up standard costs for labor and expenses for a project. 
author: KimANelson
manager: AnnBe 
ms.date: 08/02/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProjCostPriceHour, ProjSalesPriceHour, ProjCostPriceExpense, ProjSalesPriceCost   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Service industries
ms.author: knelson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Configure standard costs for labor and expenses

[!include [banner](../../includes/banner.md)]

This topic explains how to set up standard costs for labor and expenses for a project. This task uses the USSI data set.

1. In the navigation pane, go to **Modules > Project management and accounting > Setup > Prices > Cost price (hour)**.
2. Select **New**.
3. In the **Effective date** field, enter a date.
4. In the **Cost price** field, enter a number. You can set up a standard cost price for the project category, or you can set up a cost price by worker number, project number, category, date, or any combination of these. The cost price that is applied is the cost price with the highest level of detail.  
5. Select **Save**.
6. In the navigation pane, go to **Modules > Project management and accounting > Setup > Prices > Sales price (hour)**.
7. Select **New**.
8. In the **Effective date** field, enter a date.
9. In the **Valid for** field, select an option.
10. In the **Pricing** field, enter a number. You can set up a standard sales price for hour transactions or for a project category. You can also set up sales prices by worker number, project number, category, transaction date, or any combination of these. The actual sales price, which is applied when a worker enters a transaction in the Hour journal, is the sales price with the highest level of detail. For example, if both a general sales price and a worker-specific sales price are set up, the worker-specific sales price is used.  
11. Select **Save**.
12. Close the page.
13. In the navigation pane, go to **Modules > Project management and accounting > Setup > Prices > Cost price (expense)**.
14. Select **New**.
15. In the **Effective date** field, enter a date.
16. In the **Cost price** field, enter a number. Multiple fields can be filled in, but this is the minimum needed to save the record.  
17. Select **Save**.
18. In the navigation pane, go to **Modules > Project management and accounting > Setup > Prices > Sales price (expense)**.
19. Select **New**.
20. In the **Effective date** field, enter a date.
21. In the **Valid for** field, select an option.
22. In the **Pricing** field, enter a number. The actual sales price, which is applied when a worker enters transactions in an expense journal, is the sales price with the highest level of detail. For example, if both a general and a worker-specific sales price are set up, the worker-specific sales price is used.  
23. Select **Save**.

