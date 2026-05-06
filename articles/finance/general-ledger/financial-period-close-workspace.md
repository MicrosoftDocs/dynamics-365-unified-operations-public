---
title: Financial period close workspace
description: Learn about the Financial period close workspace and the associated configuration, including outlines on financial period types.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/01/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerPeriodCloseProjectWorkspace
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 6ee51758-639b-448e-9cb2-56cf1d804273
---

# Financial period close workspace

[!include [banner](../includes/banner.md)]

This article provides an overview of the **Financial period close** workspace and the associated configuration.

## Financial period close workspace

The **Financial period close** workspace helps you track your financial closing processes across companies, areas, and people. Depending on your view of the **Financial period close** workspace, you see either all tasks and statuses for a closing schedule, or just the tasks that are assigned to you.

Select a closing schedule at the top of the workspace. The workspace then filters all data by the selected closing schedule.

### Summary tiles

The **Summary** tiles give an overview of the process, and indicators help you keep the closing process on track. You can see tasks that are past due, remaining tasks for today, tasks that are due today but are blocked because of dependencies, and all remaining tasks for the process. This information is for all companies that are included in the selected closing schedule.

### Tasks and status section

In the **Tasks and status** section, you see the status of the overall closing schedule broken down in various ways: status by company, status by area, and status by person who is responsible. You can view the status for all tasks in the closing schedule, just tasks that are due today, or tasks that are past due by changing the filter at the top of the card list. You can also select the company filter to view the status for a specific company. Each status tab gives a breakdown by both the percentage that is completed and the number of tasks that remain. Select the card or the **View details** action to filter the detailed task list by the selected card.

The last tab is for the detailed task list. This list shows the full task list and you can filter it so that it shows only the tasks that you're interested in. You can filter the task list in several ways. For example, you can filter by task due date, associated company, and associated area. You can also select to show or hide completed tasks in the task list.

Two indicators are used for tasks:

- An exclamation point icon indicates that the task is past due. For tasks that are past due, the due date is also highlighted in red.
- A padlock icon indicates that the task depends on other tasks that aren't yet completed. A task that is blocked by dependencies can't be marked as completed. You can set dependencies for a task by using the **Set dependency** action.

The task name is a hyperlink to the page where the user must go to complete the work. You can set this hyperlink by using the **Task link** field when you edit or create a task.

You can attach files, notes, images, and URLs to a task by using the **Attachments** action. For example, you can indicate journal numbers that are used as part of a task, add comments about a specific task, or attach a report file that was printed for a task. An icon appears in the **Attachment** column for the task if an attachment is present.

Select the **Task complete** option after the task is completed. When you mark a task as completed, the **Completed date** field automatically updates to the current date and time. Dependency indicators are also updated as appropriate.

## All financial period close tasks list page

You can view all current and previous period close tasks from the **All financial period close tasks** list page. Use this list page for historical analysis of your closing process, because it includes information about the scheduled due date, the actual completion date, and the person who completed the task. You can easily export the information on this list page to Microsoft Excel for reporting and auditing purposes.

## Financial period close configuration page

Before you can use the **Financial period close** workspace, you must configure the process by using the **Financial period close configuration** page. (Select **General ledger** &gt; **Period close** &gt; **Financial period close configuration**.)

### Resources

On the **Resources** tab, you define the people who are involved in the closing processes. Assign any employee who is responsible for a closing task. You must also specify the employee's view of the workspace. The following options are available:

- **Only assigned tasks** – The user sees only the tasks that are assigned to them.
- **All tasks and status** – The user sees all closing tasks and the status of the overall process.

Users who have permissions to view only their assigned tasks can't add tasks to the task list, edit tasks, or remove tasks from the task list.

### Task areas

Use task areas to group closing tasks into logical areas of ownership within your organization. For example, Accounts payable, Accounts receivable, or General ledger might be used as task areas.

### Calendars

Create and edit financial closing calendars by using the **Calendars** tab. Define the working days for closing processes, and use the calendar for scheduling closing tasks. Create a new calendar, and indicate the working days to use for task scheduling. It's best to create a calendar for a long period of time, such as a year or multiple years, since you can edit it after creation. After creating the calendar, select **Edit** to update the calendar for specific days, such as holidays. Closing tasks are scheduled on days when the **Control** value is set to **Open**. If closing tasks shouldn't be scheduled on a specific day, set the **Control** value to **Closed** for that day.

### Templates

Use a financial close template to define all tasks that are part of a closing process. A closing task is a recurring work effort that you assign to an individual to complete as part of each closing process. In the template, you must define a relative due date for each closing task. The relative due date is the number of days before or after the defined period end date that the task is due each period. You also assign a due time to each task. Set the due time by using the context of your time zone, and it converts to the time zone for each user.

You can assign a task in the template to one or more companies where that task applies. If a different person is assigned to complete that work effort in each company, you might find it helpful to create multiple tasks for the same work effort. Create one task for each company.

The **Task link** menu item is associated with the task work effort. You can use it to go directly to the associated page from the task link in the workspace. For example, a closing task to run the currency revaluation process for Accounts payable can be linked to the associated **Foreign currency revaluation** page. You can also link to an external URL.

> [!TIP]
> If you want to link a specific Management Reporter report to a financial period close task, use the report URL. To access the report URL, open the report in the report designer, and then select **File** &gt; **View report** to open the report in a web browser. You can then copy the URL in the browser's address bar and paste it into the **Task link** **URL** field.

You can define task dependencies in the template. If you set up a task to depend on one or more tasks, you can't mark that task as completed until all the dependencies are completed.

You can create multiple financial close templates. Use the various templates to track the closing processes for different period types, such as month end or year end, or to track companies that use different closing processes. After you create one template, you can copy it to a new template and make the required changes. You can assign only one template to each closing schedule.

### Closing schedules

You use a closing schedule to assign a financial close template to a specific financial period that must be closed. The tasks from the template are then automatically generated for the specified period, and the new closing schedule is added to the workspace. When you create a new closing schedule, the **Period end date** field is used to determine the actual due dates for the closing tasks, based on the relative due date that is assigned in the financial close template.

Assign the calendar appropriate for the closing schedule to indicate the working days to use in task scheduling. If you don't define a specific calendar, the task due dates use all days of the week.

You must also define the companies that you associate with the closing schedule. If you assign template tasks to multiple companies, the system creates separate tasks for each company that is in the closing schedule and assigned to the template task.

After you complete a closing schedule, select the **Closed** option. The task history remains available from the **All financial period close tasks** list page, but the closing schedule is removed from the workspace. After you mark a closing schedule as **Closed**, you can't add tasks to it, edit tasks, or remove tasks from it.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
