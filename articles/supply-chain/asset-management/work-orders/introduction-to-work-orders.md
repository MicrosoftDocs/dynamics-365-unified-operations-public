---
# required metadata

title: Introduction to work orders
description: This topic provides an overview of work orders in Enterprise Asset Management.
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

# Introduction to work orders



This topic provides an overview of work orders in Enterprise Asset Management. Work orders are used to manage, provide required information for, and register consumption on maintenance jobs. A work order may contain one or more work order lines, and one or more objects can be connected to a work order. Each work order line defines a maintenance job scheduled on the object.

Work orders can be created automatically or manually:

- Automatically using the **Schedule maintenance sequences** form, for calendar-based sequences set to "Auto create" (refer to [Preventive and reactive maintenance](../preventive-and-reactive-maintenance/preventive-maintenance-overview.md)).  

- Automatically using the **Schedule rounds** form, for rounds set to "Auto create" (refer to [Preventive and reactive maintenance](../preventive-and-reactive-maintenance/preventive-maintenance-overview.md)).  

- Create from object calendar (refer to the [Object calendar](../preventive-and-reactive-maintenance/object-calendar.md) section), which can be preventive maintenance jobs or requests.  

- Create a work order manually.  

- Create a work order from the **All requests** or **Active requests** or **My functional location requests**.

>[!NOTE]
>Work order lines related to the same object are related to the same project ID.

## All work orders

Click **Enterprise asset management** > **Common** > **Work orders** > **All Work orders** to open the list. **All work orders** contain a list of all work orders and displays some of the information related to a work order.

![Figure 1](media/01-work-orders.png)

- Click **Enterprise asset management** > **Common** > **Work orders** > **Active work orders** to see a list of active work orders.

- Click **Enterprise asset management** > **Common** > **Work orders** > **My functional location work order lines** to see a list of work order lines containing objects installed on functional locations, you are related to as a worker (set up in [Workers and worker groups](../setup-for-objects/workers-and-worker-groups.md)).

- In the **All Work orders** list (grid view), click on a link in the **Work order** column to show the Details view of the selected record. Click the **Edit** button to open for editing.  

- In the Details view, you see detailed information related to the work order.  

- In the Details view, select the **Lines** link to see work order line details, or select the **Header** link to see work order details.  

- The vertical **Related information** pane to the right of the screen contains additional work order-related information. Expand the pane to see related information for the selected work order.  

The figure below shows a screenshot of the interface.

![Figure 2](media/02-work-orders.png)

The action pane buttons are organized in tabs on the action pane. Here is a brief description of the buttons relating to Enterprise Asset Management:

| Button name                     | Description                                                                                                                                                                                                                                                             |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Edit                            | Edit the selected work order.                                                                                                                                                                                                                                           |
| New                             | Create new work order.                                                                                                                                                                                                                                                  |
| Delete                          | Delete the selected work order.                                                                                                                                                                                                                                         |
| Work order pool                 | Add selected work order to a work order pool, or remove from work order pool.                                                                                                                                                                                           |
| Adjust                          | Adjust information about expected start and end, priority, responsible worker, or responsible worker group on selected work orders.                                                                                                                                     |
| Related work order              | Create a new work order related to the selected work order line. This is useful if you want to register primary and secondary work orders.                                                                                                                              |
| Copy work order                 | Create a new work order based on an existing work order.                                                                                                                                                                                                                |
| Notes                           | Create a description, or insert notes or remarks, on a work order. Start by clicking the **Add timestamp** button to add your user name and a timestamp to the note. Notes are displayed in the **Work order** form > **Line details** FastTab > **Description** tab. |
| Tools                           | Create a list of required tools on a work order. Tools are set up as resources in **Organization administration** > **Common** > **Resources** > **Resources**.                                                                                                      |
| Checklist                       | View checklist for the object connected to the work order.                                                                                                                                                                                                              |
| Object fault                    | View or register fault information on an object to be used for error management.                                                                                                                                                                                        |
| Production stop                 | Specify production stop for a work order.                                                                                                                                                                                                                               |
| Condition assessment            | Register condition assessment measurements on a work order.                                                                                                                                                                                                             |
| Object counters                 | Create or view counter registrations on the object.                                                                                                                                                                                                                     |
| Forecast                        | View or create forecasts on a work order.                                                                                                                                                                                                                               |
| Journals                        | View or create work order journals. Journal lines can be copied from forecasts.                                                                                                                                                                                         |
| Project transactions            | View all posted transactions related to work orders created for the object.                                                                                                                                                                                             |
| Work order stage                | Update work order stage.                                                                                                                                                                                                                                                |
| Stage log                       | Log displaying the stages of the selected work order.                                                                                                                                                                                                                   |
| Object documents                | View list of documents attached to objects related to a work order. These documents are set up in **Enterprise asset management** > **Setup** > **Object documents**.                                                                                                 |
| Schedule                        | Schedule the selected work orders.                                                                                                                                                                                                                                      |
| Schedule exclusively            | Schedule the selected work order for one worker.                                                                                                                                                                                                                        |
| Delete schedule                 | Delete scheduling for the selected work order.                                                                                                                                                                                                                          |
| Work order calendar             | Open the **Work order calendar** list page.                                                                                                                                                                                                                             |
| Work order purchase requisition | Open the **Work order purchase requisition** list page.                                                                                                                                                                                                                 |
| Work order purchase             | Open the **Work order purchase** list page.                                                                                                                                                                                                                             |
| Cost control                    | Compare budget costs and actual costs on the work order.                                                                                                                                                                                                                |
| Work order report               | Print work order report.                                                                                                                                                                                                                                                |
| Work order consumption          | Print consumption report.                                                                                                                                                                                                                                               |
| Work order times                | Print work order times report.                                                                                                                                                                                                                                          |

The buttons on the **Work order** tab > **Project** section relate to functionality in the **Project management and accounting** module regarding forecasts, journals and invoicing.

>[!NOTE]
>Forecasts created on a work order can be included when running master scheduling by using the forecast model selected in the **Enterprise asset management parameters** form.
