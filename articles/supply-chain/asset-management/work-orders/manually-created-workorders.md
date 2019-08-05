---
# required metadata

title: Manually created work orders
description: This topic explains how to create work orders manually in Enterprise Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/27/2019
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

# Manually created work orders



This topic explains how to create work orders manually in Enterprise Asset Management. You can create work orders manually in two ways:

- in **All work orders** or **Active work orders**  
- in **All requests** or **Active requests** or **My functional location requests**  

## Create work order

1. Click **Enterprise asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders**.

2. Click the **New** button.

3. In the **Create work order** drop-down, select a work order type.

4. If required, select a description and a customer account in the related fields.

5. Select the object for the work order as well as the related job type.

>[!NOTE]
>When you select an object, three tabs are available: The **My objects** tab contains objects related to the functional locations to which you (the worker who is logged on the system) may be allocated (set up in [Workers and worker groups](../setup-for-objects/workers-and-worker-groups.md)). If no functional locations are set up on a worker in [Workers and worker groups](../setup-for-objects/workers-and-worker-groups.md), the **My objects** tab will not be visible. The **Active objects** tab contains a list of all objects with object stage "Active". The **Object view** tab displays a tree view of functional locations and objects installed on those locations.

6. If required, select **Variant** and **Trade**.

7. If required, you can change the work order priority in the **Priority** field.

8. Select expected start and end dates in the related fields.

9. Click **OK** to create a new work order.

10. Edit the work order in **All work orders**, if required.

- In **All work orders**, You can add several objects to a work order in Details view by adding lines on the **Work order lines** FastTab. On an object, you can only select the job types that are defined on the object type related to the object.  
- If you have changed an object priority or an object criticality after you have used them on a work order (refer to [Object priorities](../setup-for-objects/object-priorities.md) and [Object criticalities](../setup-for-objects/object-criticalities.md)), the priority or criticality on the work order is not updated accordingly.
- Criticality on a work order is re-calculated each time a work order line is added or deleted on the work order.
- In **All work orders** Details view > **Header** view > **Schedule** FastTab, you can select a responsible worker group or a responsible worker in the **Responsible group** or **Responsible** fields. These settings can be changed as long as the work order is active, for example, when the work order stage changes. The automatic selection made during work order creation is based on the setup in **Responsible workers**. If you add or remove work order lines after you have created a work order, and the **Responsible group** field and the **Responsible** field are blank when you update e work order, Enterprise Asset Management searches for a possible match in the setup form for a responsible group or a responsible worker. If the **Responsible group** field or the **Responsible** field is already filled out when you update the work order, no changes are made. Read more about responsible workers and worker groups in [Responsible workers](../setup-for-requests/responsible-workers.md).

- In [Maintenance status](../controlling-and-reporting/maintenance-status.md), you can make a calculation to get an overview of workload regarding incoming and completed work orders.  

- On the **Line details** FastTab, use the **Latitude** and **Longitude** fields to add geographic coordinates for the object selected on the work order line.  

## Create related work order

You can create a related work order to an existing work order if, for example, you want to work with primary and secondary work orders. A new work order is based on a work order line from an existing work order.

1. Click **Enterprise asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders**.

2. Select the work order for which you want to make a related work order.

3. Click **Related work order**.

4. In the **Create related work order** drop-down, select the work order line for which you want to create a related work order in the **Work order line** field.

5. Select a job type in the **Job type** field and, if required, a related job variant and job trade in the **Variant** and **Trade** fields.

6. If this is the first related work order you make, click the **New work order** radio button.

7. Select a **Work order type** and a **Description** in the related fields.

8. If required, change the work order priority in the **Priority** field.

9. Insert expected start and end dates in the related fields.

10. Click **OK**. The new related work order is shown in the **All work orders** list.

11. If you create a related work order on a work order that already has related work orders, you can add the work order line to an already related work order. This is done by clicking the **Add to related work order** radio button in step 6. Then you select the related work order to which you want to add a new work order line. Edit the **Priority**, **Expected start**, and **Expected end** fields, if required, and click **OK**. The work order line is added to the existing related work order.

The figure below shows a screenshot of the interface.

![Figure 1](media/03-work-orders.png)

**Note:** If you have set up a related work order mask in **Enterprise asset management parameters** > **Work orders** link > **Related work order mask** field, work order IDs will be created in accordance with the mask setup. If no related work order mask is set up, the next available work order ID will be used for related work orders.

## Copy work order

It is possible to quickly create a new work order from an existing work order. This way of working with work orders is different from creating work orders based on [Maintenance sequences](../preventive-and-reactive-maintenance/maintenance-sequences.md). It is useful if, for example, you have a work order containing many work order lines with various jobs on different objects that should be completed at regular intervals.

1. Click **Enterprise asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders**.

2. Select the work order from which you want to copy content.

3. Click **Copy work order**. The work order setup from the selected work order is
shown. If required, you can edit some of the fields.

4. Click **OK** to create the new work order.

5. Edit the work order in **All work orders**, if required.

>[!NOTE]
>When the new work order is created, some information is copied directly from the existing work order. Information regarding forecasts, tools, checklists, functional location, addresses, and scheduling is not copied, but initialized from the current setup in Enterprise Asset Management. This means that if changes were made in those data from the time of creation of the first work order until the time you made a copy of the work order, those changes are included in the new work order you have created. Examples are changes in forecasts or updated checklists.

The figure below shows a screenshot of the interface.

![Figure 2](media/04-work-orders.png)

## Create work order based on a request

1. Click **Enterprise asset management** > **Common** > **Requests** > **All requests** or **Active requests**.

2. Select the request for which you want to create a work order, and click **Edit**.

3. In **All requests**, click **Work order**.

4. Fill out the **Work order** drop-down. If a job type has been selected in the request, you are able to select another job type, if required, when you create the work order.

5. Click **OK**. You will see a message informing you that the work order has been created.

6. If you want to see which work orders are connected to a request, select the request in the **All requests** or **Active requests** lists, and click the **Work orders** button.

>[!NOTE]
>Work orders can also be created automatically by scheduling maintenance sequences jobs, or by setting up "Auto create" maintenance sequences or rounds on an object. Read more about automatically created work orders in the [Maintenance sequences](../preventive-and-reactive-maintenance/preventive-maintenance-overview.md) chapter. Work orders created from requests in the **Object calendar** are created with the job types selected in the requests.
