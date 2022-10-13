---
# required metadata

title: Set up tasks in Task management 
description: This article explains how to set up tasks in Task management that is available in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 10/12/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-06-09
ms.dyn365.ops.version: Human Resources

---

# Set up tasks in Task management 

[!INCLUDE [PEAP](../includes/peap-1.md)]

In versions prior to Dynamics 365 Human Resource 10.0.30, when editing a task, the users would need to go to each checklist that contained the task and update the tasks individually.

Beginning in Dynamics 365 Human Resources version 10.0.30, users can select to how edited tasks are handled. When a task is edited and the task is in a checklist, for the checklist to use the edited task, the **Enable task management upgrade** option must be selected on the **Human resources shared parameters** page. 

[![Human resources shared parameters.](./media/task-update.png)](./media/task-update.png)

If edits to tasks should be applied to all associated checklist tasks, a relationship must already exist between the task in the task library and the task in the checklist.  An option was added to create the relationship between the library task and the checklist task.

You can create tasks individually and then reuse them in multiple checklists. To create a task, on the **Onboarding setup** page, on the **Tasks** tab, select **New**.

## Set up tasks

You can select a created task and assign it to multiple checklists by selecting **Apply to checklists** from the menu.

Alternatively, you can add tasks directly to a checklist. To add a task to a checklist, on the **Onboarding setup** page, on the **Checklist** tab, either create a new checklist to add the task to, or add the task to an existing checklist.

To edit a library task, select **Edit** from the task library menu. If the task is associated to any checklists, those checklists will display in the **Edit task** page. If you would like the tasks in the checklists to be updated with the edits, select the checklists where the task should be updated in the **Apply to checklists** section.

To delete tasks from the library select **Delete**. If the task is in an associated checklist, this action won't delete the task from the checklist. The task must be removed from the checklist in a separate action.

### Setting up checklists

A checklist is a group of tasks. You can create as many checklists as you require, and you can assign the same tasks to multiple checklists. 

To create a new task within a checklist, select **New** from the tasks menu bar. When creating a new task, you can optionally select to add the task to the task library so that it can be shared across multiple checklists. To add the task to the library, the **Apply task to library** switch must be set to **Yes**. If you choose not to add the task to the library, it will exist only in the checklist in which you are creating it in. If you choose to add the task to the task library, you can also choose to add the task to other checklists at the same time by selecting the checklists in the **Apply to checklists** section.

To edit a task in the checklist, select **Edit** from the task menu. If the task is associated to any checklists, those checklists will display in the **Edit task** page. If you would like the tasks in the other checklists to be updated with the edits, select the checklists where the task should be updated in the **Apply to checklists** section.

To remove tasks from the checklist, select **Remove**. This will remove the task from the checklist. This action will not delete the task from the task library. To delete a task from the library, navigate to the **Task library** page and select **Delete**. When you create a checklist, you specify an owner and a calendar.

