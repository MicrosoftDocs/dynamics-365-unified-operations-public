---
# required metadata

title: Scheduled work order maintenance jobs
description: This topic explains scheduled work order maintenance jobs in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 08/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.5

---

# Scheduled work order maintenance jobs

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

The **Scheduled work order maintenance jobs** page is used to get an overview of the work orders allocated to a resource. Work orders using resource types "Human resources", "Tool", and "Machine" are shown in the list. The list can be used to get an overview of work orders allocated to a specific resource. You can also use it to quickly find a work order allocated to a maintenance worker who, for example, called in sick this morning, and then quickly allocate another maintenance worker to the job.

## View scheduled work order maintenance jobs

1. Click **Asset management** > **Common** > **Work orders** > **Scheduled work order maintenance jobs**. You see a list of all work orders set to work order lifecycle state "Scheduled" or "In progress".

2. You can sort the list, for example, by maintenance worker. You can also use the filter to limit the list to display work orders allocated to a specific resource or maintenance worker.

3. You can see notes on the work order and, if required, add new notes by selecting the work order job in the list and clicking **Notes**.

4. If you want to allocate one maintenance worker to a work order, select the work order in the list, and click **Work order**.

5. The **Work order** page opens. Click **Dispatch** to schedule the work order to a specific maintenance worker.

>[!NOTE]
>Read more about scheduling several work orders or one work order in [Schedule work orders](../work-order-scheduling/schedule-work-orders.md) and [Dispatch work order](../work-order-scheduling/dispatch-work-order.md).

The figure below shows an example of the **Scheduled work order maintenance jobs** page.

![Figure 1](media/07-work-order-scheduling.png)

