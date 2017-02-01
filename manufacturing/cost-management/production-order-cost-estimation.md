---
# required metadata

title: Production order cost estimation | Microsoft Docs
description: This article provides information about production cost estimation. Production cost estimation provides the projected material and capacity consumption costs of producing an item in the planned production order quantity. 
author: YuyuScheller
manager: AnnBe
ms.date: 2016-04-12 16:06:35
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: BOMCalcTrans, InventCostTrans, ProdCalcTrans, ProdTableJour, ProdTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 2094
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 80633
ms.assetid: cd04ecc7-0c72-41ae-b191-11ed2fd5551b
ms.region: Global
ms.industry: Manufacturing
ms.author: mguada

---

# Production order cost estimation

This article provides information about production cost estimation. Production cost estimation provides the projected material and capacity consumption costs of producing an item in the planned production order quantity. 

After you create a production order, you must estimate production costs. The purpose is to estimate item and route consumption for the production process, because these estimates are used as the basis for subsequent scheduling and production processes.

## Production cost estimation
Estimates of production costs are based on the following information:

-   The quantity on the production order
-   The components on the production bills of materials (BOMs)
-   The routing operations in the production route
-   The indirect costs that apply to the components and operations
-   The active cost data as of the calculation date

If there is a phantom line item on the production BOMs, the calculations reflect the phantom’s components and route operations. You can use the estimation task to recalculate estimated costs so that they reflect updated information. For example, the updated information might be changes to the quantity on the production order, the components on the production BOMs, the routing operations in the production route, the indirect costs that apply to these components and operations, or the active cost data as of the recalculation date. The calculations of estimated cost also suggest a sales price for the production item, based on a cost-plus-markup approach. The calculations of estimated cost can optionally apply to reference orders that reflect other production orders that are linked to the production order.

## View the estimated costs
After you run estimation, you can view the results on the **Price calculation** page. The estimation calculates the following values:

-   **Production cost** – The production cost is the top line of the estimate. It shows the complete cost of running the production order and the total sales price for the production. It's the sum of all the cost lines on the estimate.
-   **Route or resource costs** – Route or resource costs are the costs for the production operations. They include the cost of elements such as setup time, run time, and overhead.
-   **Material costs** – Material costs are the costs and prices of the BOM components that are required in order to produce the item. These costs have previously been established and entered into the system.

## Other uses of cost estimation
A cost estimate also provides the following information:

-   Meaningful price quotations
-   Estimates of the profitability of the order
-   Estimates of raw material usage
-   Comparisons of cost information from previous productions
-   Budget and forecasting information
-   Estimates of the production size that is required in order to maintain a particular cost


