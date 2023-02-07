---
# required metadata

title: Maintenance workers and worker groups
description: This article explains maintenance workers and worker groups in Asset Management.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetWorkerGroupCopyFromResourceGroup, EntAssetWorkerGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Maintenance workers and worker groups

[!include [banner](../../includes/banner.md)]

 

This article explains maintenance workers and worker groups in Asset Management. In Asset Management, you can connect maintenance workers to functional locations. (For more information about functional locations, see [Create functional locations](../functional-locations/create-functional-locations.md).) This functionality might be useful if, for example, you're scheduling a maintenance job on a machine that is located in functional location 01, and you want to allocate maintenance workers from the same location to perform the job.

You can also create maintenance worker groups and associate maintenance workers with them. This functionality is useful when you do simple work order scheduling, and you want to schedule a group of maintenance workers on a work order. You can use maintenance workers and maintenance worker groups to set up preferred maintenance workers and responsible maintenance workers. 


## Create workers

1. Select **Asset management** \> **Setup** \> **Workers** \> **Workers**.
2. Select **New** to add a worker to the list.
3. In the **Worker** field, select the worker.
4. Set the **Active** option to **Yes** to schedule the worker on work orders.

    On the **General** FastTab, the **Resource** and **Description** fields are automatically filled in if a resource has been selected for the worker. The **Calendar** field is also automatically filled in, provided that you've set up the worker as a resource and allocated a calendar to that resource on the **Resources** page (**Organization administration** \> **Resources** \> **Resources**).

5. On the **Groups** FastTab, select **Add**, and then select a maintenance worker group for the worker. A worker can be affiliated with more than one group.
6. In the standard setup, a worker's affiliation with a group is effective from the date when you add the group, and it never expires. This date is shown in the **Effective** field. To see the **Effective** field, select **View** \> **All**. If the worker's affiliation with a group should be limited to a specific period, use the **Effective** and **Expiration** fields to define the period.
7. On the **Functional locations** FastTab, select **Add**, and then select a functional location for the maintenance worker. Also specify which location is the primary functional location for the worker.

    > [!NOTE]
    > When you add functional locations to a worker, all active assets that are related to those functional locations appear on various menu items, such as **My active assets** and **My active functional locations**. They also appear in the asset lookups that are shown when you create a new asset, maintenance request, or work order.

    The fields on the **Details** FastTab show the number of maintenance worker groups and functional locations that the selected maintenance worker is related to.

## Create worker groups

1. Select **Asset management** \> **Setup** \> **Workers** \> **Maintenance worker groups**.
2. Select **New** to add a worker group to the list.
3. In the **Maintenance worker group** field, enter a group ID.
4. In the **Name** field, enter a name.
5. On the **Workers** FastTab, select **Add**, and then select a maintenance worker for the worker group. For information about the **Effective** and **Expiration** fields, see step 6 in the previous procedure.
6. If a resource group should be related to the selected maintenance worker group, select **Copy from resource group**. In the **Group** field, select the resource group to copy calendar settings from. Then, in the **Worker group** field, select the worker group to copy the resource group's calendar settings to. This step is relevant only if you want maintenance workers to use the calendar that is related to a resource (work center) during work order scheduling.

    The field on the **Details** FastTab shows the number of maintenance workers that have been set up on the selected maintenance worker group.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]