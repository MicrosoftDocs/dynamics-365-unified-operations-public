---
# required metadata

title: Maintain planned orders
description: This topic provides information about how to manage planned orders. It describes how you can update the status of planned orders, firm them, and filter for planned orders that have the same status as a selected planned order.
author: roxanadiaconu
manager: AnnBe
ms.date: 10/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqTransPo
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 19151
ms.assetid: 54123f4c-b4ca-4ce4-9358-b067aa04c968
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: roxanad
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Maintain planned orders

[!include [banner](../includes/banner.md)]

This topic provides information about how to manage planned orders. It describes how you can update the status of planned orders, firm them, and filter for planned orders that have the same status as a selected planned order.

You can manage planned orders from the **Master planning** workspace, the **Planned order** list, or the **Planned production orders**, **Planned purchase orders**, and **Planned transfer** lists. 

## Planned order status
You can use the **Status** field to help track your progress. The following values are used:
-   When master planning generates planned orders, the planned orders have a status of **Unprocessed**.
-   If you decide not to firm a planned order, you can give it a status of **Completed**.
-   When you want to indicate that you decide to firm a planned order, you can give it a status of **Approved**. Planned orders with Approved status are respected by master planning, so they are not modified or deleted. 

## Firming planned orders 
By firming planned orders real orders are created, also know as released or open orders. When a planned order is firmed, it's moved to the orders section of the relevant module.

There are 2 options to perform firming from the **Planned orders** form
-   **Firm** – This will firm one or multiple selected planned orders.
-   **Firm all** – This will firm all planned orders in the filter. Using **Firm all** you don’t have to select the planned order, all planned orders within the filter will be firmed. This option can be useful if you are firming a high number of planned orders.

**Note:** You can track planned orders that was firmed from the **Firming history** located under **Planned orders form > View > Firming history**

## Parallelize firming
If you are planning to firm many orders at once parallelizing the run can improve the run time or performance. The option is available when firming multiple planned order with either **Firm** or **Firm all**.
There are two parameters:
-   **Parallelize firming** – When set to **Yes** the firming process will be parallelized with the number of threads defined in **Number of threads**.
-   **Number of threads** – Controls the number of threads used to parallelize the firming process. The parameter is only shown when **Parallelize firming** is set to **Yes**.


Additional resources
--------

[Master plans](master-plans.md)



