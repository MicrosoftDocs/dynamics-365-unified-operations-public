---
# required metadata

title: Task management overview
description: This topic explains the task management functionality that is available in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 12/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-29-11
ms.dyn365.ops.version: Human Resources

---
# Task management

Use **Task management** to create tasks that need to be completed for the onboarding, offboarding, and transitions of employees. Task management utilizes the concept of a checklist to group tasks together and to assign tasks to individuals, or groups of individuals. A checklist consists of a list of onboarding, offboarding, and transition tasks. These tasks are assigned to individuals. Tasks help with the hiring, transferring, or offboarding of employees. Checklists are similar between onboarding, offboarding, and transitions. 

## Checklist Overview

The checklist functionality is similar between onboarding, offboarding, and transitions. This overview will provide an example of how checklists are used within the onboarding process.  However, the same functionality can be applied to the transition or termination process.

As part of the onboarding process, Human resources professionals can create tasks that track the onboarding progress of incoming employees, and recently hired employees. The onboarding process may change based on the employee's position or geographic location. You can create multiple onboarding checklists that can be applied to each unique hiring situation. For example, tasks such as filling out tax withholding forms that must be completed for every employee who is hired in the United States. Other tasks 
might only be applicable to a few positions, such as assigning a company car to executive-level staff. In this example, two onboarding checklists can be created: US-based 
employees and Executives only. When hiring a mid-level manager, the 'US-based employees' checklist would be selected. However, when hiring an executive in the US both checklists 
would be selected to ensure that all onboarding activities will be completed.

## Task Management Workspace

The **Task Management** workspace lists all tasks assigned to individuals in the onboarding, offboarding, and transition processes. In the **Task management** workspace, the tasks for each of these processes can be viewed by selecting the **Onboarding**, **Transitions**, or **Offboarding** tabs in the upper left corner. By default, only HR professionals can view the **Task management workspace**.

The **Onboarding** section displays workers that are **Starting soon** and **Recent hires**. A single employee can be selected from these lists. Once an 
employee is selected, the tasks related to that employee's onboarding will be displayed on the right side of the page. The **Onboarding** section also contains a list of 
**All tasks** for the **Starting soon** or **Recently hired** employees. There is also a list of **Overdue tasks**, and tasks assigned to the current user.

The **Offboarding** section contains lists of workers who:
 - Are **Exiting** the company 
 - Have already **Exited**

In the list, a single employee can be selected. Once an employee is selected, the tasks related to the employee's offboarding will be displayed. 
Checklists that are available within the **Offboarding** section include: 
 - **All tasks** for all of the exiting or exited employees
 - **Overdue tasks**
 - Tasks assigned to the current user 

The **Transitions** section has a list of **All tasks** for the employees who will be changing positions or have recently changed a position. There is also a list of 
**Overdue tasks**, and tasks assigned to the current user.

In each of these sections, HR assistants and managers can perform the following functions:
 - **Apply a checklist** to an employee
 - **Update the status** of the task
 - **Reassign** the task
 - **Update** the due date

> [!Note:] 
> The **Onboarding** section shows workers who were hired in the last seven days. To change this setting, go to the **Human resources parameters** page, 
select the **General** tab, and enter a time frame for **Recent hires**. The information in the **Recent hires** section can be shown for a specific number of days, months, or years. For example, to view the list of workers who were hired in the last 14 days, set the **Period** field to **14** and the **Unit** field to **Days**. The list of **Exited** and **Exiting** workers can also have the date range updated on the **Human resource parameters** page. These settings also apply to the **Personnel Management** workspace.

## Configure Checklists

A **Checklist** is a group of **Tasks**. You can create as many checklists as needed and assign the same tasks to multiple checklists. For example, a company may want to 
create separate checklists for seasonal employees and regular full-time employees. These checklists may have some of the same tasks, such as verifying the arrival time of the
new employee. However, some additional tasks might only apply to the full-time employees. You can create two checklists that include some of the same
tasks, and tasks that are specific to the employee type. The checklist is flexible way to group tasks and that can be reused when you hire additional employees.

## Tasks

Tasks can be created individually and be used in multiple checklists. To create a task, go to the **Onboarding setup** page,
select the **Tasks** tab, and select **New**. Tasks can also be added directly to a checklist. To create a task directly within a checklist, go to **Onboarding setup**, select the **Checklist** tab, and either create a new checklist to add the task to or add the task to an existing checklist.

> [!Note:] 
> When adding a task directly to a checklist, you cannot select it in other checklists.

When creating a task, there are the following fields:

|  Field | Description|
|----------------------|----------------------------------------------------------------------------------|
| **Task**            | Name of the task               |
| **Description**     | Description of the task                                                                |
| **Optional**        | This field indicates that this task is optional and is informational only.                                                        |
| **Task link**       | This can be a URL to an external site or a specific page within the application that the user should navigate to.                             |
| **Assignment type** | Tasks can be assigned to a specific **Worker**, **Position**, **Group**, **Manager**, or to an **Employee** that is part of the onboarding, offboarding, or transition process. |
| **Assigned To**     | The **Worker**, **Position**, or **Group** that the task is assigned to.                                                              |
| **Contact Person**  | If there are questions about a task, the person listed in this field is who should be contacted.                               |
| **Due date offset** | The number of days before or after the onboarding, termination, or transition date that the task is due.                  |
| **Instructions**    | Instructions that should be followed to complete the task.                                                                             |

### Task link

**Task link** provide a link to a URL or to a specific page within the Dynamics 365 application. A **Task link** would be used if you want the person assigned to the task to 
navigate to a specific web page or Dynamics 365 application page to complete the task. When creating a **Task link**, there will be an option to select a **Menu item**, **URL**, or **Worker details**. 

If **Menu item** is selected, a list of all pages within the application will be displayed. 
If **URL** is selected, enter the URL that you would like the person assigned to the task to navigate to. This can be a URL that is not part of the Dynamics 365 application. 
If **Worker details** is selected, the user will be presented with two options: 
 - **Employee self service actions** - this option displays a list of pages that are available in **Employee self service**. You would select this option if the task that was assigned to the onboarded employee needs to be completed in **Employee self service**. 
For example, you may want the employee to fill out their personal contact information. To complete this scenario, select **Employee self service actions**, then select **Personal Details&gt;Personal Information.** 
 - **Worker management actions** - this option displays a list of pages that are related to the worker's record that are not accessible to the employee. For example, you may want the task owner to enter information that is specific to an onboarded worker such as compensation. Select '**Worker management actions'** and then **Compensation&gt;Fixed compensation**.

### More about assignment types

When an employee is hired, terminated, or transferred one or more checklists can be selected. Once a checklist is selected, and the hiring, terminating, or transition process is completed, tasks will be created and assigned to users to track progress. 

When a task is created, it will be assigned to a specific user. The user that is assigned the task depends on the **Assignment type** selected in the task. 
The options for the **Assignment type** are: 
 - **Worker**
 - **Position** 
 - **Group (of positions)** 
 - The affected employee's **Manager** 
 - The **Employee** that is affected 

For example, an IT engineer will always be the person that prepares the laptops for a new employee. When creating this task, select **Position** for the **Assignment type**,
and then select IT engineer from the **Position** list. When an employee is hired, and the checklist is assigned. The laptop configuration task will be assigned to the worker
who is in the IT engineer position at the time the hire action was entered. You can also assign a task to a specific worker by selecting **Worker** in the
**Assignment type** field, and then selecting the appropriate individual. If **Manager** is selected, the manager of the employee that is being hired, terminated, or
transitioned will be assigned the task.

> [!Important:] 
> If the hired/terminated/transitioned employee does not have a position assigned at the time a checklist is applied, the manager cannot be determined, and the task
will be assigned to the checklist owner.

If **Employee self service** is selected as the **Assignment type**, the employee that is being hired/terminated/transitioned will be assigned the task.

### Task due dates and the **Due date offset** field

Task due dates are based on the employment start date, termination date, or date of transition. Some tasks must be completed before an employee's start date, while others can
be completed later. When defining a task, you'll enter a due date that is relative to the start date, termination date, or transition date in the **Due date offset** field. 
For example, an IT engineer needs to prepare a new employee's laptop two days before their start date. The task created will have a due date offset from start date 
of -2. Therefore, if an employee's start date is May 5, the IT task will be due on May 3.

> [!Note:] 
> Due dates can be adjusted after the task is created.

### Instructions

Complex tasks might require multiple steps or need the individual performing the tasks to provide additional information. You can add **Instructions** and 
provide additional information on how to complete the task to the person who is assigned to it.

### Setup calendar 

The calendar is used to calculate the due date of the tasks. Calendars allow days to be excluded when calculating due dates – such as weekends or holidays. Calendars 
are associated to a checklist so that all tasks in the checklist calculate the due dates the same. Multiple calendars can be set up but only 
one can be associated to a checklist. 

Working and non-working days are defined in **Calendar setup**. Working days are included in calculating the due date and non-working days are excluded. 

## Setup assignment groups (Optional)

Sometimes there are a group of individuals that are responsible for a task. For example, you may have a group of individuals who are responsible for setting up laptops 
for new hires. A group called 'IT Laptop' can be created.

Within the **Group assignment** page, select **New**. Enter a name (IT Laptop) and a description for the group and select **Save.** Go to the **Members** FastTab and 
select **Add**. Select all **Positions** that are responsible for setting up laptops. Once the group is created, it is available to select when creating a **Task**.
To select a specific **Group** for a task, the **Assignment type** must be set to '**Group**'. Once **Group** is selected for the **Assignment type**, the **Assigned to** field 
will list the 'IT Laptop' group that was created.

> [!Important:] 
> When a task is assigned to a group, the task is completed when one person in the group completes the task.  At the time of hire/termination/transition, tasks are created. Tasks will be created for the users that are assigned to the positions contained in the group.

## Setup checklists

A **Checklist** is a group of tasks. You can create as many checklists as you need and assign the same tasks to multiple checklists. When a checklist is created, you will set an **Owner** and a **Calendar**.

The **Owner** will be assigned tasks when an individual cannot be assigned a task. If the **Task assignment** field is set to **Position**, **Manager** or **Group**, and an individual cannot be derived from the assignment type, the **Owner** will be assigned. 

Some situations that the **Owner** will be assigned are:
-   The employee being hired or terminated does not have a position assigned. Without a position assignment, their manager cannot be determined.
-   The **Assignment type** is set to **Position**, but there isn't an employee assigned to the position at the time the task is created. 
   Example: The **Setup Laptop** task is assigned to Position Number 000876/Technical Support Specialist. At the time an employee is hired, there isn't an employee that is assigned to 000876. A task will then be created for the checklist owner.
-   The **Assignment type** is set to **Group**, but there isn't an employee assigned to the position(s) contained in the group at the time the tasks are created. 

The calendar is used to calculate the due date of tasks. When calendars are set up, certain days can be excluded in calculating due dates – such as weekends or holidays. 
Calendars are then associated to a checklist template so all tasks in the checklist calculate the due dates the same. Multiple calendars can be set up but only one can be associated to a checklist.

## Setup task groups (Optional)

An onboarding process can include many tasks. You can create optional task groups that can categorize related tasks. Task groups can make it easier to assign all the tasks to a
checklist that are needed to hire a new employee. For example, there are tasks that HR, IT, and Payroll each need to complete. **Task groups** are user
defined, so the following **Task groups** could be created: HR, IT, and Payroll. When creating a task, one of these **Task groups** can be associated with that task. 
When you add a task to a checklist, the list of tasks can be filtered by the group that it's assigned to. For example, when creating a "Checklist" template, all IT tasks in the IT Group can be viewed and only the relevant IT tasks selected.

## Using onboarding checklists

When a worker is hired, terminated or changes positions, one or more checklists can be selected. Task due dates and worker assignments are created once the hiring, termination,
or change position process is complete. For example, when you select the **Hire** or **Hire and add details** button, tasks are created for individuals based on the **Assignment type**. 

A **Due date** will be assigned to each task by adding or subtracting the offset days from the employee's start date (See the information regarding **Offset
days** earlier in this topic). If you are using personnel actions, the tasks will be created when the **Complete** button is selected or when the action is approved.

Within the **Task management** workspace, a checklist can be applied to the worker by selecting the employee in the simple list and details page, and selecting **Apply checklist**. The **Target date** is the date that will be used for calculating the due dates of the tasks. Typically, this date should match the hire, 
termination, or transition date of the employee.

Checklists and tasks can also be added to the worker by navigating to the **Worker** page and selecting **Checklists** from the menu. 

## Completing tasks

When a task is assigned to an employee, their assigned tasks can be viewed on the **Employee self service** page. Employees that have been assigned a task can see the **Task**, 
**Description**, **Instructions**, **Contact person**, and can open the associated Dynamics 365 page or external web page from the **Employee self service** page. Tasks can be marked as **In progress**, **Canceled**, or **Completed**. Tasks can also be reassigned.

If the task was assigned to a **Group**, the task will be set to **Completed** when one person in the group completes the task.



