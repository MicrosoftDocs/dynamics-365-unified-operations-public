---
# required metadata

title: Priority and description
description: This topic explains priority and description in Enterprise Asset Management.
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

# Priority and description



This topic explains priority and description in Enterprise Asset Management. When you create a new work order, you may want to prioritize the work order and add a general description to it. You can create priorities and descriptions in the **Priority** and **Work order description** forms.

## Create priority

1. Click **Enterprise asset management** > **Setup** > **Work orders** > **Priority**.
2. Click **New**.
3. Insert a priority, for example a number, in the **Priority** field.
4. Insert a name for the priority in the **Name** field.
5. On the **Work orders** FastTab, you can define expected start and end expected end, which are used for manually created work orders and work orders created on the basis of requests. These fields are used to indicate a time frame in which work orders should be started and ended.
6. In the **Start day** field, insert a number indicating number of days calculated from the creation of the work order in which period the work order should start. Example 1: Insert "0" if you want the work order to start at the time of work order creation. Example 2: Insert "7" if you want the work order to start within one week after creation of the work order.
7. Select "Yes" on the **Set start time** toggle button if you want to insert a start time on the work order together with the start date. If you select "Yes" on this toggle button, insert start time in the **Start time** field. If you select "No" on the **Set start time** toggle button, current time of day is used.
8. In the **End day** field, insert a number indicating number of days calculated from the start date of the work order in which period the work order should end. Example: Insert "7" if you want the work order to end within a week from the start date of the work order.
9. Select "Yes" on the **Set end time** toggle button if you want to insert an end time on the work order together with the end date. If you select "Yes" on this toggle button, insert end time in the **End time** field. If you select "No" on the **Set end time** toggle button, current time of day is used.
10. Click **Save**.

The figure below shows a screenshot of the interface.

![Figure 4](media/20-setup-for-work-orders.png)

## Create description

1. Click **Enterprise asset management** > **Setup** > **Work orders** > **Descriptions**.
2. Click **New**.
3. Insert the description in the **Description** field.
4. Click **Save**.
