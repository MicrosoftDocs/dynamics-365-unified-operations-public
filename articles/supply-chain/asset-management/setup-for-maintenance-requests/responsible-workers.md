---
# required metadata

title: Responsible workers
description: This topic explains how to set up responsible workers in Enterprise Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/26/2019
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

# Responsible workers



This topic explains how to set up responsible workers in Enterprise Asset Management. Responsible workers can be related to object types, objects, functional locations, job groups, job types, variants, and trades to make a worker preference on work orders and requests regarding which workers should be responsible for a work order (but not necessarily the ones scheduled to carry out a work order). The use of this functionality is optional. For example, it can be used to select responsible workers or worker groups for specific work types or work areas. During a work order life cycle or a request life cycle, it is possible to change or update responsible workers, which could be related to, for example, a change in request stage or work order stage. The setup in **Responsible workers** is *not* used during work order scheduling.

Before you can set up responsible workers, you must first set up the workers and worker groups that should be available for selection. Refer to the [Workers and worker groups](../setup-for-objects/workers-and-worker-groups.md) section for a description on how to set up workers and worker groups.

## Set up responsible workers

A responsible worker or worker group can be related to a specific

- Job trade  
- Job variant  
- Job type  
- Job group  
- Object  
- Object type  
- Functional location

or a combination of those selections. The more selections you make for the same
record, the more specific your setup becomes.

1. Click **Enterprise asset management** > **Setup** > **Workers** > **Responsible workers**.
2. Click **New** to create a new record.
3. Start by creating a "default" worker or worker group setup that has no selections in the fields shown in the bullet list above. This means that you only make a selection in the **Responsible worker group** field and/or the **Responsible worker** field. In the figure below, you see an example in the first record in which "Requests" is selected as responsible worker group.

[!NOTE]
>The default setup will be used during work order scheduling in case no other, more specific, combination matches the contents of the work order during work order scheduling.

4. Repeat step 2 to create a new record. Make the required selections, depending on the detail level for the responsible worker or worker group. *Example:* In the figure below, in the third record, the worker Dana Birkby is selected as responsible worker. She will automatically be selected if you create a request or a work order for the object "C0002".

[!NOTE]
>During creation of a request, when a responsible worker or responsible worker group is made available for selection in **All requests**, Enterprise Asset Management goes through all responsible worker records to check for a possible match, always checking the most specific combination first. This means that, first, a possible match regarding **Trade** is checked. If no match is found, **Variant** is checked. If no match is found, **Job type** is checked, and so on. As you can see in the layout, this means that Enterprise Asset Management checks each record from right to left for a match (**Trade**, then **Variant**, then **Job type**, **Job group**, **Functional location**, **Object**, and **Object type**) to find the most specific combination. If no match is found, the "default" record with no selections in those seven fields is used.

The figure below shows a screenshot of the interface.

![Figure 1](media/08-setup-for-requests.png)

>[!NOTE]
>In Enterprise Asset Management, you can also set up preferred workers, who may be allocated on work orders during work order scheduling. Refer to [Set up preferred workers](../work-order-scheduling/set-up-preferred-workers.md) for more information.
