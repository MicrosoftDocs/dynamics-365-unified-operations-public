---
# required metadata

title: Maintenance schedule
description: This topic explains maintenance schedule in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Maintenance schedule
The maintenance schedule contains a list of all the expected preventive maintenance plans, maintenance requests, and maintenance rounds to be carried out. Some schedule lines may have been converted to work orders.

The four maintenance schedule views are slightly different, depending on which maintenance schedule lines you want to see.

| Menu item                  | Description of contents                                                                                                                                             |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| All maintenance schedule       | All maintenance schedule lines are shown.     |
| My asset schedule        | All maintenance schedule lines containing assets installed on functional locations to which you are related as a worker (set up in [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md)) are shown in this list. |
| Open maintenance schedule lines | Maintenance schedule lines with status "Created" - meaning they have not yet been converted to a work order or discarded - are shown in this list.                                            |
| Open maintenance schedule pools | Maintenance schedule lines related to a work order pool are shown in this list.                                                                                                                  |

>[!NOTE]
>If a maintenance schedule line is included in several work order pools (refer to [Work order pools](../work-orders/work-order-pools.md)), one record is shown for each pool in **Open maintenance schedule pools**. This is done to optimize filtering options on work order pools.

To open a maintenance schedule:

1. Click **Asset management** > **Common** > **Maintenance schedule** > **All maintenance schedules** or **Open maintenance schedule lines** or **Open maintenance schedule pools**.

2. To update the maintenance schedule, click **Maintenance plan** or **Maintenance rounds**. Refer to [Schedule preventive maintenance](../preventive-and-reactive-maintenance/schedule-maintenance-sequences.md).

3. You can edit a maintenance schedule line by selecting it and clicking **Edit**. For example, you can easily update the service level or the worker responsible on the job. You can only edit maintenance schedule lines that have not yet been connected to a work order.

4. You can delete a maintenance schedule line by selecting it and clicking **Delete**.

5. You can discard a maintenance schedule line by selecting it in the list page and clicking **Discard**. This function is useful if, for example, an object has a 2,000 km maintenance sequence and a 10,000 km maintenance sequence. Then, you may want to discard the 2,000 km maintenance sequence when it coincides with 10,000 km, 20,000 km, 30,000 km, and so on. If you discard a calendar entry related to a maintenance sequence, that calendar line will never again appear when that maintenance sequence is scheduled.

6. You can select a number of entries in **All object calendars** and click **Work order pool**, if you want all selected calendar entries to be included in the same work order pool.

7. You can select a number of entries in **All object calendars** or **Open object calendars** or **Open object calendar pools** and click **Adjust** if you want to make the same adjustments to several entries. You can change expected start and end dates, priority, and the responsible group or responsible worker related to the selected object calendar entries.

- When a calendar entry has been related to a work order, the work order ID will be displayed in the **Work order** field.  
- In **All objects** > **Preventive maintenance** FastTab, you can set up maintenance sequence lines for the selected object. Later, if you delete a maintenance sequence line related to an object in **All objects** , you also automatically delete all object calendar lines with status "Created" that have been created based on that maintenance sequence. See also [Create an
object](../objects/create-an-object.md).

The figure below shows a screenshot of the interface.

![Figure 1](media/16-preventive-maintenance.png)
