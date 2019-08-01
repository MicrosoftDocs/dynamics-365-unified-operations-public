---
# required metadata

title: Create a request
description: This topic explains how to create a request in Enterprise Access Management.
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

# Create a request



This topic explains how to create a request in Enterprise Access Management. Requests can be used if maintenance workers or production workers discover a need for equipment repair, and it is not possible to carry out that repair job right away.

**Example:** A maintenance worker is making a repair. During this repair he discovers that another object at the same location needs to be serviced, but he has no time or spare parts to carry out the repair job. Therefore he creates a request on the object containing a short description of the problem.

In **All Objects** or **Active objects** (**Enterprise asset management** > **Common** > **Objects** > **All Objects** or **Active objects**), you can see the active requests attached to the selected object in the **Related information** pane > **Active requests** section, placed on the right side of the screen.

1. Click **Enterprise asset management** > **Common** > **Requests** > **All requests** or **Active Requests**.
2. Click the **New** button.
3. In the **Create request** drop-down dialog box, select the type in the **Request type** field. A default type is suggested.
4. Insert a name or title that briefly describes the request in the **Description** field.
5. Select **Functional location** or **Object**, or a combination, as required. It is possible to create a request without selecting an object. Then the object is added to the request later. If the worker who is logged in to Dynamics 365 for Finance and Operations is related to a resource, which is related to an object, the **Object** field is automatically filled out.

- If the selected object already has requests attached to it, an info message is shown at the top of the **Create request** drop-down dialog, showing the request ID of an existing request as well as an **Open** button that you can click to open that request. If the object is covered by a warranty or contract agreement, an info message is also shown.  
- When you select an object, two or three tabs are available: The **My objects** tab contains objects related to the functional locations to which you (the worker who is logged on the system) may be allocated. If no functional locations are set up on a worker in [Workers](../setup-for-objects/workers-and-worker-groups.md), the **My objects** tab will not be visible. The **Active objects** tab contains a list of all objects with object stage "Active". The **Object view** tab displays a tree view of functional locations and objects installed on those locations.

6. Select a priority regarding the urgency of the request in the **Priority** field.
7. If you have selected an object, you can create a fault registration by selecting fault data in the **Fault symptom**, **Fault area**, and **Fault type** fields.
8. If the request has caused a production stop, insert start date and time of the production stop in the **Production stop** field.
9. Your name is automatically inserted in the **Started by** field.
10. The **Actual start** field is automatically filled out with current date and time, but you can change it, if required.
11. If required, insert further notes in the **Notes** field.
12. Click **OK**.

The following figure shows a screenshot of the interface.

![Figure 1](media/03-manage-requests.png)

>[!NOTE]
>In [Maintenance status](../controlling-and-reporting/maintenance-status.md), you can make a calculation to get an overview of workload regarding incoming and completed requests.

## Subsequent processing of the request

After the request has been created, and before it is converted to a work order, various data should be updated on the request. This is typically done by a planner or another administrative employee. In **All requests** or **Active Requests**, select the request you want to work with, and click **Edit**.

In the Details view, you can update various information. For example you can

- select and verify the object. If, required it is possible to set the **Object verified** toggle button to "No" later, to select another object.  
- select responsible group and/or responsible worker. For more information on how to set up responsible workers and worker groups, refer to [Responsible workers](../setup-for-requests/responsible-workers.md).  
- select a job type and, if relevant, the related job variant and job trade.  
- insert geographic coordinates in the **Latitude** and **Longitude** fields. If coordinates are added to a request, they are automatically transferred to a related work order. This information is useful if you work with linear asset management.

The figure below shows a screenshot of the interface.

![Figure 2](media/02-manage-requests.png)

>[!NOTE]
>If you select an object when you create the request, you can add one fault to the object. After the request has been created, you can add more faults, if required, by clicking the **Object fault** button in **All Requests**.
