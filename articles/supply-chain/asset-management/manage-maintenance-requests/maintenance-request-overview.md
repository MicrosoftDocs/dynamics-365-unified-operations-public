---
# required metadata

title: Requests
description: This topic provides an overview for managing maintenance requests in Asset Management
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

# Manage maintenance requests

Contents of this session:

- Create maintenance requests  
- Register asset loan  
- View list of asset loans  
- Register inbound and outbound assets  


## Maintenance requests

Maintenance requests are notes or declarations that can be created to make a manager or planner aware that an asset may require a maintenance or repair job - without creating a work order. A work order may subsequently be created based on a maintenance request if the contents of the maintenance request are considered to be valid for a work order to be created.

Maintenance requests can be created for any asset in **Asset Management**. Various maintenance request types can be created, depending on how your company uses maintenance requests. Here are some examples:


- Maintenance requests  
- Notes  
- Corrections / Enhancements  
- Investments  
- Depot repair - for the purpose of managing repair of assets that you receive from another location to carry out a maintenance or repair job, and then return the asset after the job is completed.


### All maintenance requests

Click **Asset management** > **Common** > **Maintenance requests** > **All maintenance requests** or **Active maintenance requests** or **My functional location maintenance requests**. The list displays some of the information related to a maintenance request.

![Figure 1](media/01-manage-maintenance-requests.png)

>[!NOTE]
>Click **Asset management** > **Common** > **Maintenance requests** > **My functional location maintenance requests** to see a list of maintenance requests containing functional locations, or assets installed on functional locations, you are related to as a worker (set up in [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md)).  
- Customer account information is available in Asset Service Management (external maintenance), but not in Enterprise Asset Management (internal maintenance).  

In the **All maintenance requests** list (grid view), click on a link in the **Maintenance request** column to show the Details view of the selected record.

![Figure 2](media/02-manage-maintenance-requests.png)

The action pane buttons are organized in tabs on the action pane. Here is a brief description of the buttons relating to Asset Management:

| Button name        | Description                                                                                |
|--------------------|--------------------------------------------------------------------------------------------|
| Edit               | Edit the selected maintenance request.                                                                 |
| New                | Create a new maintenance request.                                                                      |
| Delete             | Delete the selected maintenance request.                                                               |
| Work order pool    | Connect the selected maintenance request to a work order pool.                                         |
| Work order         | Create a work order based on the selected maintenance request.                                         |
| Asset fault        | Open **Asset faults** and create a fault registration on the maintenance request.                     |
| Work orders        | Show a list of all work orders connected to the maintenance request.                                   |
| Update maintenance request state      | Update maintenance request state.                                                                      |
| Lifecycle state log          | Log displaying the lifecycle states of the selected maintenance request.                                         |
| Maintenance request details    | Print a report displaying details of the selected maintenance request.                                 |
| Send loan asset    | Select a loan asset to be a temporary replacement for the asset selected on the maintenance request. |
| Return loan asset    | Register the loan asset as returned. |

