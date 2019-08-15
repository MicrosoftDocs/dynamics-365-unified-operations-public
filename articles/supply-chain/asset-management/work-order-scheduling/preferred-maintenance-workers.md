---
# required metadata

title: Set up preferred maintenance workers
description: This topic explains how to set up preferred maintenance workers in Asset Management.
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

# Preferred maintenance workers

You can make a preference regarding which maintenance workers are allocated to complete work orders during work order scheduling. The use of this functionality is optional, but it can help you make a choice for the most qualified maintenance worker to complete a job, based on worker skills and competencies. Therefore, during work order scheduling, the setup in **Preferred maintenance workers** is used to determine if a specific maintenance worker or worker group should be scheduled for a work order. Only maintenance workers that are available at scheduling time will be scheduled. If a preferred maintenance worker setup matches a work order during scheduling, but the maintenance worker is allocated to other jobs, the work order will be scheduled to another, available, maintenance worker.

Before you can set up preferred maintenance workers, you must first set up the maintenance workers and worker groups that should be available for selection. Refer to [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md) for a description on how to set up maintenance workers and worker groups.

## Set up preferred workers

A preferred maintenance worker or worker group can be related to a specific

- trade  
- maintenance job type variant  
- maintenance job type  
- maintenance job type category  
- asset  
- asset type  

or a combination of those selections. The more selections you make for the same record, the more specific your setup will be.

1. Click **Asset management** > **Setup** > **Workers** > **Preferred maintenance workers**.

2. Click **New** to create a new record.

3. Start by creating a "default" maintenance worker or worker group setup that has no selections in the fields shown in the bullet list above. This means that you only make a selection in the **Preferred maintenance worker group** field or the **Preferred maintenance worker** field. In the figure below, you see an example in the first record in which "Requests" is selected as preferred maintenance worker group.

>[!NOTE]
>The default setup will be used during work order scheduling in case no other, more specific, combination matches the contents of the work order during work order scheduling.

4. Repeat step 2 to create a new record. Make the required selections, depending on the detail level for the preferred worker or worker group. *Example:* In the figure below, in the sixth record, the maintenance worker Shawn Richardson is selected as preferred worker. He will automatically be selected during scheduling of a work order that includes the asset "CH-BP1-03-02 and the maintennace job type "Facility assessment", if he is available at the scheduled time.

>[!NOTE]
>Generally, when a preferred maintenance worker is selected during work order scheduling, Asset Management goes through all **Preferred maintenance workers** records to check for a possible match, always checking the most specific combination first. If no match is found, the "default" record with a selection in either the **Preferred maintenance worker group** field or the **Preferred maintenance worker** field is used.


![Figure 1](media/02-work-order-scheduling.png)

You can also set up responsible maintenance workers who can be selected when a maintenance request or a work order is created. In **All work orders** and **All maintenance requests**, you can edit the selection, if required. Refer to [Responsible maintenance workers](../setup-for-requests/responsible-workers.md) for more information.

During work order scheduling, different scores are calculated to determine which workers should complete the jobs related to a work order (those scores are set up in **Asset management parameters** > **Work order scheduling** link). If two or more preferred maintenance workers or responsible maintenance workers get the same score during work order scheduling, one worker is randomly selected. Otherwise, it is always the worker with the highest scores who is allocated to complete a work order.

