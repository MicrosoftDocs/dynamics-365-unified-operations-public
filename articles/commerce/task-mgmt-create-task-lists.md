---
# required metadata

title: Create task lists and add tasks
description: This topic describes how to create task lists and add tasks to them in Dynamics 365 Commerce.
author: gvrmohanreddy
manager: annbe
ms.date: 02/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Release 10.0.9
---

# Create task lists and add tasks

[!include [banner](includes/banner.md)]

This topic describes how to create task lists and add tasks to them in Dynamics 365 Commerce.

## Overview

A task list is a collection of tasks that must be completed as part of a business process. For example, there might be a task list that a new worker must complete while onboarding, a task list for an evening shift cashier to complete, or a task list to prepare the store for an upcoming holiday season. In Dynamics 365 Commerce, a task list with a target date can be assigned to any number of stores or employees, and can be configured to recur. 

A task defines a specific piece of work or an action that someone must complete on or before the specified due date. In Dynamics 365 Commerce, a task can include detailed instructions, contact person information, and links to back office operations, point of sale (POS) operations, or site pages to improve productivity and get the task owner the context needed to complete the task efficiently. Managers and workers can creates task lists in Commerce back office and assign them to a set of stores. 

## Create a task list

To create a task list, follow these steps.

1. Go to **Retail and Commerce \> Task management \> Task management administration** .
1. Select **+ New** and enter information for **Name, Description** and **Owner**.
1. Select **Save**.

## Add tasks to a task list

To add tasks to a task list, follow these steps.
 
1. Under the **Tasks** tab of an existing task list, select **+ New** to add a task.
1. On the **Create a new task** flyout menu, enter task details.
1. Enter a **Name** for the task. 
1. Enter a +/- integer value for **Due data offset from target date**, for example enter **-2** if you want the task to be completed two days before the task list's due date.    
1. For **Notes**, provide detailed instructions. 
1. For **Contact person**, provide the name of a subject matter expert in case the task owner needs help.
1. For **Task link**, provide a link based on the nature of the task.
   
> [!TIP] 
> Though it's technically feasible to assign a task to someone while creating a task list, try to avoid assigning tasks during task list creation. You can assign the tasks once the list is instantiated for individual stores. 

## Use task links to improve workers productivity
 
Dynamics 365 Commerce offers a way to link a task to a specific POS operation, for example a "run sales" report, an online training video for new employee orientation task, or a back office operation. This feature helps task owners get the information they need to efficiently complete a task.

To add task links while creating a task, follow these steps.

1. Under the **Tasks** tab of an existing task list, select **Edit**.
1. Select the **Task link** drop down menu, and then do one or more of the following steps.
    - Select **Menu item** to configure a back office operation, for example "Product kits."
    - Select **POS operation** to configure a POS operation, for example "Sales reports."
    - Select **URL** to configure an absolute URL.

The following image shows the selection of task links on the **Edit task** flyout menu.

![Task management - Selection of task links](media/HQ-POS-Tasks-Linking.png)

**Enable a POS operation to be linkable to a task**

To enable a POS operation to be linked with a task, follow these steps:

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Operations**.
1. Select **Edit**, identify the preferred POS operation, and then select the **Enable Task Management** check box. 

## Additional resources

[Task management overview](task-mgmt-overview.md)

[Configure task management](task-mgmt-configure.md)

[Assign task lists to stores or employees](task-mgmt-assign-lists.md)

[POS task management](task-mgmt-POS.md)


