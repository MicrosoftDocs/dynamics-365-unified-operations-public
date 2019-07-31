---
# required metadata

title: Requests
description: This topic provides an overview for managing requests in Enterprise Asset Management
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

# Requests



This topic provides an overview for managing requests in Enterprise Asset Management. Requests are notes or declarations that can be created to make a manager or planner aware that an object may require a maintenance or repair job - without actually creating a work order. A work order may subsequently be created based on a request if the contents of the request are considered to be valid for a work order to be created.

Requests can be created for any object in **Enterprise Asset Management**.
Various request types can be created, depending on how your company uses
requests. Here are some examples:

- Maintenance requests  
- Notes  
- Corrections / Enhancements  
- Investments  
- Depot repair - for the purpose of managing repair of objects that you receive from another location to carry out a maintenance or repair job, and then return the object after the job is completed.

## All requests

Click **Enterprise asset management** > **Common** > **Requests** > **All requests** or **Active requests** or **My functional location requests**. The list displays some of the information related to a request, as shown in the figure below.

![Figure 1](media/01-manage-requests.png)

- Click **Enterprise asset management** > **Common** > **Requests** > **My functional location requests** to see a list of requests containing functional locations, or objects installed on functional locations, you are related to as a worker (set up in [Workers](../setup-for-objects/workers-and-worker-groups.md)).  
- Customer account information is available in Asset Service Management (external maintenance), but not in Enterprise Asset Management (internal maintenance).  

In the **All requests** list (grid view), click on a link in the **Request** column to show the Details view of the selected record. Click the **Edit** button to open for editing. The figure below shows a screenshot of the interface.

![Figure 2](media/02-manage-requests.png)

The action pane buttons are organized in tabs on the action pane. Here is a brief description of the buttons relating to Enterprise Asset Management:

| Button name        | Description                                                                                |
|--------------------|--------------------------------------------------------------------------------------------|
| Edit               | Edit the selected request.                                                                 |
| New                | Create a new request.                                                                      |
| Delete             | Delete the selected request.                                                               |
| Work order pool    | Connect the selected request to a work order pool.                                         |
| Work order         | Create a work order based on the selected request.                                         |
| Object fault       | Open **Object faults** and create a fault registration on the request.                     |
| Work orders        | Show a list of all work orders connected to the request.                                   |
| Send loan object   | Select a loan object to be a temporary replacement for the object selected on the request. |
| Return loan object | Register the loan object as returned.                                                      |
| Request stage      | Update request stage.                                                                      |
| Stage log          | Log displaying the stages of the selected request.                                         |
| Request details    | Print a report displaying details of the selected request.                                 |
