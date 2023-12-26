---
# required metadata

title: Financial period close workspace
description: This article provides an overview of the Financial period close workspace and the associated configuration.
author: kweekley
ms.date: 11/15/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerPeriodCloseProjectWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 6ee51758-639b-448e-9cb2-56cf1d804273
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Financial period close workspace

[!include [banner](../includes/banner.md)]

This article provides an overview of the **Financial period close** workspace and the associated configuration.

## Financial period close workspace

The **Financial period close** workspace lets you track your financial closing processes across companies, areas, and people. Depending on your view of the **Financial period close** workspace, you'll see either of all tasks and statuses for a closing schedule, or just the tasks that are assigned to you. 

You must first select a closing schedule at the top of the workspace. All data that is shown on the workspace is then filtered by the selected closing schedule.

### Summary tiles

The **Summary** tiles give an overview of the process, and indicators help you keep the closing process on track. You can see tasks that are past due, remaining tasks for today, tasks that are due today but are blocked because of dependencies, and all remaining tasks for the process. This information is for all companies that are included in the selected closing schedule.

### Tasks and status section

In the **Tasks and status** section, the status of the overall closing schedule is broken down in various ways: status by company, status by area, and status by person who is responsible. You can view the status for all tasks in the closing schedule, just tasks that are due today, or tasks that are past due by changing the filter at the top of the card list. You can also select the company filter to view the status for a specific company. Each status tab gives a breakdown by both the percentage that has been completed and the number of tasks that remain. Click the card or the **View details** action to filter the detailed task list by the selected card. 

The last tab is for the detailed task list. This list shows the full task list and can be filtered so that it shows only the tasks that you're interested in. You can filter the task list in several ways. For example, you can filter by task due date, associated company, and associated area. You can also select to show or hide completed tasks in the task list. 

Two indicators are used for tasks:

-   An exclamation point icon indicates that the task is past due. For tasks that are past due, the due date is also highlighted in red.
-   A padlock icon indicates that the task depends on other tasks that aren't yet completed. A task that is blocked by dependencies can't be marked as completed. You can set dependencies for a task by using the **Set dependency** action.

The task name is a hyperlink to the page where the user must go to complete the work. You can set this hyperlink by using the **Task link** field when you edit or create a task. 

You can attach files, notes, images, and URLs to a task by using the **Attachments** action. For example, you can indicate journal numbers that are used as part of a task, add comments about a specific task, or attach a report file that was printed for a task. An icon appears in the **Attachment** column for the task if an attachment is present. 

The **Task complete** option must be manually selected after the task is completed. When a task is marked as completed, the **Completed date** field is automatically updated to the current date and time. Dependency indicators are also updated as appropriate.

## All financial period close tasks list page
You can view all current and previous period close tasks from the **All financial period close tasks** list page. This list page is best used for historical analysis of your closing process, because it includes information about the scheduled due date, the actual completion date, and the person who completed the task. You can easily export the information on this list page to Microsoft Excel for reporting and auditing purposes.

## Financial period close configuration page
Before you can use the **Financial period close** workspace, you must configure the process using the **Financial period close configuration** page. (Click **General ledger** &gt; **Period close** &gt; **Financial period close configuration**.)

### Resources

On the **Resources** tab, you define the people who are involved in the closing processes. Any employee who will be responsible for a closing task must first be assigned here. You must also specify the employee's view of the workspace. The following options are available:

-   **Only assigned tasks** – The user will see only the tasks that are assigned to them.
-   **All tasks and status** – The user will see all closing tasks and the status of the overall process.

Users who have permissions to view only their assigned tasks won't be able to add tasks to the task list, edit tasks, or remove tasks from the task list.

### Task areas

You use task areas to group closing tasks into logical areas of ownership within your organization. For example, Accounts payable, Accounts receivable, or General ledger might be used as task areas.

### Calendars

Create and edit financial closing calendars using the Calendars tab.  This is where you will define the working days for closing processes, and will be used for scheduling closing tasks.  Create a new calendar, and indicate the working days to be used for task scheduling.  It is best to create a calendar for long period of time, such as a year or multiple years, since it can be edited after creation.  After creating the calendar, click the Edit button to update the calendar for specific days, such as holidays.  Closing tasks will be scheduled on days when the Control value is set to Open.  If closing tasks should not be schedule on a specific day, that day should have the Control value set to Closed.

### Templates

You use a financial close template to define all tasks that are part of a closing process. A closing task is a recurring work effort that is assigned to an individual to complete as part of each closing process. In the template, a relative due date must be defined for each closing task. The relative due date is the number of days before or after the defined period end date that the task will be due each period. A due time is also assigned to each task. The due time is set by using the context of your time zone and will be converted to the time zone for each user. 

You can assign a task in the template to one or more companies where that task applies. If a different person is assigned to complete that work effort in each company, you might find it helpful to create multiple tasks for the same work effort. Create one task for each company. 

The **Task link** menu item is associated with the task work effort and can be used to go directly to the associated page from the task link in the workspace. For example, a closing task to run the currency revaluation process for Accounts payable can be linked to the associated **Foreign currency revaluation** page. You can also link to an external URL. 

> [!TIP]
> If you want to link a specific Management Reporter report to a financial period close task, you can use the report URL. To access the report URL, open the report in the report designer, and then click **File** &gt; **View report** to open the report in a web browser. You can then copy the URL in the browser's address bar and paste it into the **Task link** **URL** field. 

You can define task dependencies in the template. If a task has been set up to depend on one or more tasks, that task can't be marked as completed until all the dependencies have been completed. 

You can create multiple financial close templates. You can then use the various templates to track the closing processes for different period types, such as month end or year end, or to track companies that use different closing processes. After one template is created, you can copy it to a new template and make the required changes. You can assign only one template to each closing schedule.

### Closing schedules

You use a closing schedule to assign a financial close template to a specific financial period that must be closed. The tasks from the template are then automatically generated for the specified period, and the new closing schedule is added to the workspace. When you create a new closing schedule, the **Period end date** field is used to determine the actual due dates for the closing tasks, based on the relative due date that is assigned in the financial close template. 

Assign the calendar appropriate for the closing schedule, to indicate the working days to be used in task scheduling. If you don't define a specific calendar, the task due dates will use all days of the week. 

You must also define the companies that will be associated with the closing schedule. If template tasks are assigned to multiple companies, separate tasks will be created for each company that is in the closing schedule and assigned to the template task. 

After a closing schedule is completed, select the **Closed** option. The task history will still be available from the **All financial period close tasks** list page, but the closing schedule will be removed from the workspace. After a closing schedule has been marked as **Closed**, you won't be able to add tasks to it, edit tasks, or remove tasks from it.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
