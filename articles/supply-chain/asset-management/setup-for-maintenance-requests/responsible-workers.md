---
# required metadata

title: Responsible maintenance workers
description: This topic explains how to set up responsible maintenance workers in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 07/24/2019
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
ms.search.validFrom: 2019-07-30
ms.dyn365.ops.version: AX 7.0.0

---

# Responsible maintenance workers

Responsible maintenance workers can be related to asset types, assets, functional locations, maintenance job type category, maintenance job type, maintenance job type variants, and trades to make a maintenance worker preference on work orders and maintenance requests regarding which maintenance workers should be responsible for a work order (but not necessarily the ones scheduled to carry out a work order). The use of this functionality is optional. For example, it can be used to select responsible workers or worker groups for specific work types or work areas. During a work order life cycle or a maintenance request life cycle, it is possible to change or update responsible maintenance workers, which could be related to, for example, a change in maintenance request stage or work order stage.  The setup in **Responsible workers** is *not* used during work order scheduling.

Before you can set up rresponsible maintenance workers, you must first set up the workers and maintenance worker groups that should be available for selection. Refer to the [Workers and worker groups](../setup-for-objects/workers-and-worker-groups.md) section for a description on how to set up workers and worker groups.

## Set up responsible workers

1. Click **Asset management** > **Setup** > **Workers** > **Responsible maintenance workers**.
2. Click **New** to create a new record.
3. Start by creating a "default" responsible worker or responsible maintenance worker worker group setup that has no selections in the **Job trade**, **Job variant**, **Job type**, etc. fields. You will only make a selection in the **Responsible maintenance worker group** field and/or the **Responsible maintenance worker** field. In the figure below, you see an example in the first record in which "Requests" is selected as responsible worker group.

[!NOTES]
>The default setup will be used during work order scheduling in case no other, more specific, combination matches the contents of the work order during work order scheduling.

>During creation of a maintenance request, when a responsible maintenance worker or responsible maintenance worker group is made available for selection in **All maintenance requests**, Asset Management goes through all responsible maintenance worker records to check for a possible match, always checking the most specific combination first. This means that, first, a possible match regarding **Trade** is checked. If no match is found, **Variant** is checked. If no match is found, **Job type** is checked, and so on. As you can see in the layout, this means that Asset Management checks each record from right to left for a match (**Trade**, then **Variant**, then **Job type**, **Job group**, **Functional location**, **Object**, and **Object type**) to find the most specific combination. If no match is found, the "default" record with no selections in those seven fields is used.

> In Asset Management, you can also set up preferred maintenance workers, who may be allocated on work orders during work order scheduling. 

The figure below shows a screenshot of the interface.

![Figure 1](media/08-setup-for-requests.png)


