---
# required metadata

title: Task management
description: This article explains the task management functionality that is available in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/01/2024
ms.topic: article
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-06-09
ms.dyn365.ops.version: Human Resources

---

# Task management
Task management lets you create tasks that must be completed to hire (onboard), terminate (offboard), and transfer (transition) employees. Task management uses the concept of checklists. A checklist is of a list of onboarding, offboarding, or transition tasks. Task management uses checklists to group tasks together, and to assign them to individuals or groups. The checklist functionality for onboarding, offboarding, and transitions is similar.

## Checklist overview

A checklist is a group of tasks. Checklists give you a flexible way to group tasks, and they can be reused (for example, when you hire additional employees). You can create as many checklists as you require, and you can assign the same tasks to multiple checklists.

### Examples

The following examples show how checklists can be used in the onboarding process. However, because the checklist functionality for onboarding, offboarding, and transitions is similar, the information also applies to the offboarding and transition processes.

As part of the onboarding process, Human resources (HR) professionals can create tasks that track the onboarding progress of incoming and recently hired employees. Because the onboarding process might vary, depending on the employee's position or geographic location, you can create multiple onboarding checklists to accommodate different hiring situations.

**Example 1**

Every employee who is hired in the United States must complete tasks such as filling out tax withholding forms. However, tasks such as assigning a company car might be applicable only to executive-level staff. In this case, two onboarding checklists can be created: **US-based employees** and **Executives only**. Then, when a mid-level manager is hired in the United States, the **US-based employees** checklist is selected. However, when an executive is hired in the United States, both checklists are selected to ensure that all the required onboarding tasks are completed.

**Example 2**

A company has both seasonal employees and regular full-time employees. Although some tasks (such as verifying the arrival time of the new employee) apply to employees of both types, some additional tasks apply only to regular full-time employees. In this case, you can create two checklists. Both checklists include the tasks that apply to both seasonal and regular full-time employees, but only one checklist includes the tasks that are specific to regular full-time employees.

## Task management workspace

The **Task management** workspace lists all tasks that have been assigned to individuals in the onboarding, offboarding, and transition processes. To view the tasks for a process, select the appropriate tab in the upper-left corner: **Onboarding**, **Offboarding**, or **Transitions**. By default, only HR professionals can access the **Task management** workspace.

The **Onboarding** tab contains a **Starting soon** list that shows incoming employees and a **Recent hires** list that shows recently hired employees. In both lists, you can select only one employee. When you select an employee, all tasks that are related to that employee's onboarding are shown on the right side of the page. The **Onboarding** tab also contains an **All tasks** list that shows all tasks for all incoming or recently hired employees. Finally, it contains a list of overdue tasks and a list of tasks that are assigned to the current user.

The **Offboarding** tab contains a list of employees who are exiting the company and a list of employees who have already exited the company. In both lists, you can select only one employee. When you select an employee, all tasks that are related to that employee's offboarding are shown. The **Offboarding** tab also contains an **All tasks** list that shows all tasks for all exiting or exited employees. Finally, it contains a list of overdue tasks and a list of tasks that are assigned to the current user.

The **Transitions** tab contains an **All tasks** list that shows all tasks for all employees who will be changing positions or who have recently changed positions. There is also a list of overdue tasks and a list of tasks that are assigned to the current user.

On all three tabs, HR assistants and managers can complete the following activities:
- Apply a checklist to an employee
- Update the status of a task
- Reassign a task
- Update the due date of a task

> [!NOTE]
> By default, the **Onboarding** tab shows employees who were hired in the last seven days. To change this setting, on the **Human resources parameters** page, on the **General** tab, in the **Recent hires** field, enter a time frame. The information in the **Recent hires** list can be shown for a specific number of days, months, or years. For example, to view the list of employees who were hired in the last 14 days, set the **Period** field to **14** and the **Unit** field to **Days**.
> On the **Human resources parameters** page, you can also update the date range for the lists of exiting and exited employees that are shown on the **Offboarding** tab. These settings also apply to the **Personnel management** workspace.

## Setting up tasks

You can create tasks individually and then reuse them in multiple checklists. To create a task, on the **Onboarding setup** page, on the **Tasks** tab, select **New**.

You can assign a created task to multiple checklists by selecting the task and then selecting **Apply to checklists** on the menu.

Alternatively, you can add tasks directly to a checklist. To add a task to a checklist, on the **Onboarding setup** page, on the **Checklist** tab, either create a new checklist to add the task to, or add the task to an existing checklist.

To edit a task in the library, select **Edit** on the task library menu. If the task is associated with any checklists, those checklists will be shown on the **Edit task** page. If you want the tasks in any checklists to be updated with the edits, select those checklists in the **Apply to checklists** section.

To delete tasks from the library, select the **Delete** option. If a task is associated with any checklist, this action won't delete the task from that checklist. The task must be removed from the checklist in a separate action.

> [!NOTE]
> If you add a task directly to a checklist, you can't reuse it in other checklists.

The following table describes the fields that are available when you create a task by either method.

| Field           | Description |
|-----------------|-------------|
| Task            | Enter the name of the task. |
| Description     | Enter a description of the task. |
| Optional        | Specify whether the task is optional and is informational only. |
| Task link       | Enter the URL of an external webpage or a specific page in the app where the user should complete the task. For more information, see the [Task links](#task-links) section. |
| Assignment type | Tasks can be assigned to a specific worker, position, or group of positions, the manager of the affected employee (that is, the employee who is part of the onboarding, offboarding, or transition process), or the affected employee. Select the type of assignment. For more information, see the [Assignment types](#assignment-types) section. |
| Assigned to     | Select the specific worker, position, or group of positions to assign the task to. |
| Contact person  | Specify the person who should be contacted if there are questions about the task. |
| Due date offset | Specify the number of days before or after the onboarding, termination, or transition date that the task is due. For more information, see the [Task due dates and the Due date offset field](#task-due-dates-and-the-due-date-offset-field) section. |
| Instructions    | Enter instructions for completing the task. For more information, see the [Instructions](#instructions) section. |

### Task links

A task link provides a link to an external webpage or a page in the Dynamics 365 app. You can specify a task link if the person who is assigned to a task should go to a specific webpage or a specific page in the Dynamics 365 app to complete that task. When you create a task link, you can select one of the following options:

- **Menu item** – If you select this option, a list of all pages in the Dynamics 365 app is shown. Select a page in the list.
- **URL** – If you select this option, enter the URL of the webpage that you want the person who is assigned to the task to go to. The specified page can be a page that isn't part of the Dynamics 365 app.
- **Worker details** – If you select this option, select one of the following options:

    - **Employee self service actions** – This option shows a list of pages that are available in **Employee self service**. Use it if the task that was assigned to the onboarded employee must be completed in **Employee self service**. For example, if you want the employee to enter their personal contact information, select **Employee self service actions**, and then select **Personal Details&gt;Personal Information**.
    - **Worker management actions** – This option shows a list of pages that are related to the worker's record, but that aren't accessible to the employee. For example, if you want the task owner to enter information that is specific to an onboarded worker, such as compensation information, select **Worker management actions**, and then select **Compensation&gt;Fixed compensation**.

### Assignment types

When an employee is hired, terminated, or transferred, one or more checklists can be selected. After a checklist is selected, and the hiring, termination, or transfer process is completed, tasks are created and assigned to users to track progress.

When a task is created, it's assigned to a specific user. The user that a task is assigned to depends on the assignment type that is selected for that task. The following values are available in the **Assignment type** field:

- **Worker** – Assign the task to a specific worker. After you select this value, select the worker in the **Assigned to** field.
- **Position** – Assign the task to a specific position. After you select this value, select the position in the **Assigned to** field.

    For example, an IT engineer will always be responsible for preparing a laptop for a new employee. In this case, when you create the laptop configuration task, select **Position** as the assignment type, and then select **IT engineer** as the position. Then, when an employee is hired, and the checklist is assigned, the laptop configuration task is assigned to whichever worker is in the IT engineer position at the time when the hire action is entered.

- **Group** – Assign the task to a group of positions (assignment group). After you select this value, select the group in the **Assigned to** field. For more information, see the [Setting up assignment groups (Optional)](#setting-up-assignment-groups-optional) section.
- **Manager** – Assign the task to manager of the employee who is being hired, terminated, or transferred.

    > [!IMPORTANT]
    > When a checklist is applied, if no position is currently assigned to the hired, terminated, or transferred employee, the manager can't be determined. In this case, the task is assigned to the checklist owner. For more information, see the [Setting up checklists](#setting-up-checklists) section.

- **Employee** – Assign the employee who is being hired, terminated, or transferred.

### Task due dates and the Due date offset field

Task due dates are based on the employment start date, termination date, or transition date. Some tasks must be completed before an employee's start date, whereas other tasks can be completed after. When you define a task, you set the **Due date offset** field to specify a due date that is relative to the start date, termination date, or transition date. For example, an IT engineer must prepare a laptop for a new employee two days before that employee's start date. In this case, when you create the laptop configuration task, set the **Due date offset** field to **-2**. Then, if an employee's start date is May 5, the task will be due on May 3.

> [!NOTE]
> Due dates can be adjusted after the task is created.

Due dates are calculated based on the calendar that is associated with the checklist. For more information, see the [Setting up checklists](#setting-up-checklists) section.

### Instructions

Complex tasks might require multiple steps, or the person who is performing the task might have to provide additional information. In the **Instructions** field, you can enter instructions or additional information to help the person who is assigned to the task complete it.

## Setting up checklists

A checklist is a group of tasks. You can create as many checklists as you require, and you can assign the same tasks to multiple checklists.

To create a new task in a checklist, select **New** on the **Tasks** menu bar. When you create a new task, you can select to add it to the task library, so that it can be shared across multiple checklists. You can add the task to the library only if the **Apply task to library** option is set to **Yes**. If you add the task to the task library, you can also add it to other checklists at the same time by selecting those checklists in the **Apply to checklists** section. If you don't add the task to the library, it will exist only in the checklist that you create it in.

To edit a task in the checklist, select **Edit**. If the task is associated with any checklists, those checklists will be shown on the **Edit task** page. If you want the tasks in other checklists to be updated with the edits, select those checklists in the **Apply to checklists** section.

To remove tasks from the checklist, select **Remove**. This action just removes tasks from the checklist. It doesn't delete them from the task library. To delete a task from the library, go to the task library page, and select **Delete**.

When you create a checklist, you specify an owner and a calendar.

If the **Assignment type** field for a task is set to **Position**, **Manager**, or **Group**, but no specific individual can be derived from the assignment type, the task will be assigned to the checklist owner. Here are some examples of situations where tasks will be assigned to the checklist owner:

- No position is assigned to the employee who is being hired or terminated. Because the employee doesn't have a position assignment, their manager can't be determined.
- The **Assignment type** field is set to **Position**, but no employee is assigned to the position at the time when the task is created. For example, the **Setup Laptop** task is assigned to position number 000876 (**Technical Support Specialist**). At the time when an employee is hired, no employee is assigned to position 000876. Therefore, a task will be created for the checklist owner.
- The **Assignment type** field is set to **Group**, but no employee is assigned to the positions in the group at the time when the task is created.

The calendar that is specified for a checklist is used to calculate the due date of tasks that are part of that checklist. Working and non-working days are defined in the calendar setup. Working days are included when the due date of tasks is calculated, and non-working days are excluded. Non-working days include weekends and holidays. 

After a calendar is set up, it's associated with a checklist template. In that way, the due date of every task in the checklist is calculated in the same way. You can set up multiple calendars, but only one calendar can be associated with each checklist.

## Setting up assignment groups (Optional)

Sometimes, a group of individuals is responsible for a task. For example, a group of IT workers might be responsible for preparing laptops for new hires.

To set up an assignment group, follow these steps.

1. On the **Group assignment** page, select **New**.
1. Enter a name (for example, **IT Laptop**) and a description for the group.
1. Select **Save**.
1. On the **Members** FastTab, select **Add**.
1. In the **Positions** field, select all positions that are responsible for the task.

After an assignment group is created, it's available for selection when a task is created. To select a specific group for a task, you must select **Group** in the **Assignment type**. The group that you created will then be available for selection in the **Assigned to** field.

> [!IMPORTANT]
> If a task is assigned to a group, the task is marked as **Completed** when one person in the group completes it. Tasks are created at the time of hire, termination, or transition. They are created for the users who are assigned to the positions that are included in the group.

## Setting up task groups (Optional)

An onboarding, offboarding, or transition process can include many tasks. To make it easier to assign all the required tasks to a checklist, you can create optional task groups to categorize related tasks. For example, the HR, IT, and Payroll departments must each complete specific tasks to hire a new employee. Therefore, you create the following task groups: **HR**, **IT**, and **Payroll**. Then, when you create a task, you can associate one of those task groups with it.

When you want to add a task to a checklist, you can filter the list of tasks by the task group that the desired task is assigned to. For example, when you create a checklist template, you can filter the list so that only the IT tasks that are assigned to the **IT** task group are shown. Therefore, you can ensure that only the relevant IT tasks are selected.

## Using checklists

When a worker is hired, terminated, or transferred, one or more checklists can be selected. Task due dates and worker assignments are created after the hiring, termination, or transition process is completed. For example, when you select the **Hire** or **Hire and add details** button, tasks are created for individuals, based on the assignment type.

A due date is assigned to each task by adding or subtracting the due date offset from the employee's start date. For more information, see the [Task due dates and the Due date offset field](#task-due-dates-and-the-due-date-offset-field) section.

If you're using personnel actions, the tasks are created when the **Complete** button is selected or the action is approved.

In the **Task management** workspace, you can apply a checklist to an employee by selecting the employee on the simple list page or the details page, and then selecting **Apply checklist**. The value of the **Target date** field will be used to calculate the due date of the tasks. Typically, the target date should match the employee's hire, termination, or transition date.

You can also apply a checklist to an employee by opening their **Worker** page and selecting **Checklists** on the menu.

## Completing tasks

On the **Employee self service** page, an employee can view all the tasks that are assigned to them. For each assigned task, **Task**, **Description**, **Instructions**, and **Contact person** values are shown. Additionally, for each task, the employee can open the associated external webpage or the associated page in the Dynamics 365 app.

Tasks can also be displayed on the default dashboard. To display tasks on the default dashboard:
1. Go to **User Options – Preferences – Task Management** 
2. Select the **Display tasks on default dashboard** to **On**.  

>[!Note] 
>The **Task management** feature must be turned on in **Feature management** for the option to display in **User options**.

Tasks can be marked as **In progress**, **Canceled**, or **Completed**. If a task was assigned to a group, it will be marked as **Completed** when one person in the group completes it.

Tasks can also be reassigned.
