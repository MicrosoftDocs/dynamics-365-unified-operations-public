---
# required metadata

title: Create task lists and add tasks
description: This topic describes how to create task lists and add tasks to them in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 02/10/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
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

This topic describes how to create task lists and add tasks to them in Microsoft Dynamics 365 Commerce.

A *task* defines a specific piece of work or an action that someone must complete on or before a specified due date. In Dynamics 365 Commerce, a task can include detailed instructions and information about a contact person. It can also include links to back-office operations, point of sale (POS) operations, or site pages, to help improve productivity and provide the context that the task owner requires to complete the task efficiently.

A *task list* is a collection of tasks that must be completed as part of a business process. For example, there might be a task list that a new worker must complete during onboarding, a task list for cashiers who work evening shifts, or a task list that must be completed to prepare the store for an upcoming holiday season. In Commerce, every task list that has a target date can be assigned to any number of stores or employees, and it can be configured to recur.

Both managers and workers can create task lists in Commerce back office, and then assign them to a set of stores.

## Create a task list

To create a task list, follow these steps.

1. Go to **Retail and Commerce \> Task management \> Task management administration**.
1. Select **New**, and then enter values in the **Name**, **Description**, and **Owner** fields.
1. Select **Save**.

## Add tasks to a task list

To add tasks to a task list, follow these steps.
 
1. On the **Tasks** FastTab of an existing task list, select **New** to add a task.
1. In the **Create a new task** dialog box, in the **Name** field, enter a name for the task.
1. In the **Due data offset from target date** field, enter a positive or negative integer value. For example, enter **-2** if the task should be completed two days before the task list's due date.
1. In the **Notes** field, enter detailed instructions.
1. In the **Contact person** field, enter the name of a subject matter expert that the task owner can contact if the task owner needs help.
1. In the **Task link** field, enter a link, based on the nature of the task.

> [!TIP]
> Although you can use the **Assigned to** field to assign tasks to someone while you're creating a task list, we recommend that you avoid assigning tasks during task list creation. Instead, assign the tasks after the list is instantiated for individual stores.

## Use task links to help improve worker productivity

Commerce lets you link tasks to specific POS operations, such as running a sales report, viewing an online training video for new employee orientation, or performing a back-office operation. This feature helps task owners get the information that they need to complete a task efficiently.

To add task links while you create a task, follow these steps.

1. On the **Tasks** FastTab of an existing task list, select **Edit**.
1. In the **Edit task** dialog box, in the **Task link** field, select one or more of the following options:

    - Select **Menu item** to configure a back-office operation, such as "Product kits."
    - Select **POS Operation** to configure a POS operation, such as "Sales reports."
    - Select **URL** to configure an absolute URL.

The following illustration shows the selection of task links in the **Edit task** dialog box.

![Selecting task links in the Edit task dialog box.](media/HQ-POS-Tasks-Linking.png)

### Configure a POS operation so that it can be linked to a task

To configure a POS operation so that it can be linked to a task, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> POS operations**.
1. Select **Edit**, find the POS operation, and then select the **Enable Task Management** check box for it.

## Additional resources

[Task management overview](task-mgmt-overview.md)

[Configure task management](task-mgmt-configure.md)

[Assign task lists to stores or employees](task-mgmt-assign-lists.md)

[Task management in POS](task-mgmt-POS.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
