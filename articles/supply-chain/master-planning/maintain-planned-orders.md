---
# required metadata

title: Maintain planned orders
description: This article provides information about how to manage planned orders. It describes how you can update the status of planned orders, firm them, and filter for planned orders that have the same status as a selected planned order.
author: t-benebo
ms.date: 12/10/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqTransPo, ReqTransFirmLog
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 54123f4c-b4ca-4ce4-9358-b067aa04c968
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Maintain planned orders

[!include [banner](../includes/banner.md)]

This article provides information about how to manage planned orders. It describes how you can update the status of planned orders, firm them, and filter for planned orders that have the same status as a selected planned order.

You can manage planned orders from the **Master planning** workspace, the **Planned order** list, or the **Planned production orders**, **Planned purchase orders**, and **Planned transfer** lists. 

## Planned order status
You can use the **Status** field to help track your progress. The following values are used:

-   When master planning generates planned orders, the planned orders have a status of **Unprocessed**.
-   If you decide not to firm a planned order, you can give it a status of **Completed**.
-   If you want to firm a planned order, you can change the status to **Approved**. Planned orders with **Approved** status are respected by master planning, so they are not modified or deleted during a later master planning run. To achieve this, the planning logic copies the **Approved** planned orders from the old plan version to the new plan version during master planning.

## Firming planned orders 
By firming planned orders, real orders are created. These are also known as *released* or *open orders*. When a planned order is firmed, it's moved to the orders section of the relevant module.

You can select two firming options from the **Planned orders** page:

-   **Firm** – This will firm one or multiple selected planned orders.
-   **Firm all** – This will firm all planned orders in the filter. Using **Firm all** you don’t have to select the planned order, all planned orders within the filter will be firmed. This option can be useful if you are firming a high number of planned orders.

> [!NOTE]
> You can track a planned order that was firmed from **Firming history** under **Planned orders form > View > Firming history**.

## Parallelize firming
If you are planning to firm many orders at the same time, parallelizing the run can improve the run time or performance. This option is available when firming multiple planned orders with either **Firm** or **Firm all**. The following parameters are available:

-   **Parallelize firming** – If **Yes**, the firming process will be parallelized with the number of threads defined in **Number of threads**.
-   **Number of threads** – Controls the number of threads used to parallelize the firming process. The parameter is only shown when **Parallelize firming** is set to **Yes**.

> [!NOTE]
> The option for **Parallelize firming** is only shown when you have more than one planned order selected for firming.

## Additional resources

- [Master plans overview](master-plans.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]