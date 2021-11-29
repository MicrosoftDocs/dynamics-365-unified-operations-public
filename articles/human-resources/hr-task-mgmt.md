---
# required metadata

title: Task management overview
description: This topic explains the task management functionality that is available in Dynamics 365 Human Resources.
author: twheelo
ms.date: 11/29/2021
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


Using Onboarding, Offboarding and Transition checklists

Checklist Overview

Task Management Workspace

Configure checklists

Setup Tasks

Setup Calendar

Setup Assignment Groups (Optional)

Setup Task Groups (Optional)

Setup Checklists

Using checklists

Completing tasks

# Checklist Overview

The checklist functionality consists of onboarding, offboarding, and transition checklists. The checklists contain tasks that are assigned to individuals. These tasks help 
facilitate in the hiring, transferring, or offboarding of employees. The checklist functionality is very similar between these three areas. Listed below, is an example of how 
checklists are used within the onboarding process. However, this same functionality can be applied to the transition or termination process as well.

As part of the onboarding process HR professionals can create tasks that track the onboarding progress of pending employees, as well as of recently hired employees. 
The onboarding process may change based on the employee's positions or geographic location. You can create multiple onboarding checklists that can be applied to each unique 
hiring scenario. For example, some tasks, such as completing certain tax withholding forms, must be completed for every employee that is hired in the United States. Other tasks 
might only be applicable to a few positions, such as assigning a company car to executive-level staff. In this example, two onboarding checklists can be created: US based 
employees and Executives only. When hiring a mid-level manager, the 'US based employees' checklist can be selected. However, when hiring an executive in the US both checklists 
would be selected to ensure that all onboarding activities will be completed.

# Task Management Workspace

The Task Management workspace lists all tasks assigned to individuals in the onboarding, offboarding and transition processes. Within the task management workspace, the tasks 
for each for each of these processes can be viewed by selecting the Onboarding, Transitions or Offboarding tabs in the upper left corner. By default, only HR professionals can
view the **Task management workspace**.

The **onboarding** section has two lists of workers; workers that are **starting soon** and **recent hires**. Within these lists a single employee can be selected. Once an 
employee is selected, the tasks related to that employee's onboarding will be displayed on the right side of the page. Also within the onboarding section is a list of 
**all tasks** for all the starting soon or recently hired employees. There is also a list of **overdue tasks**, and tasks specifically assigned to the user that is logged 
into the system.

The **offboarding** section has two lists of workers; workers that are **exiting** the company and those that have already **exited.** Within these lists a single employee 
can be selected. Once an employee is selected, the tasks related to that employee's offboarding will be displayed on the right side of the page. Also, within the offboarding 
section is a list of **all tasks** for all of the exiting or exited employees. There is also a list of **overdue tasks**, and tasks specifically assigned to the user that is
logged into the system.

The **transitions section** has a list of **all tasks** for all employees that will be changing positions or have recently changed a position. There is also a list of 
**overdue tasks**, and tasks specifically assigned to the user that is logged into the system.

In each of these sections HR assistants and managers can perform the following functions:

**Apply a checklist** to an employee

**Update the status** of the task

**Reassign** the task

**Update** the due date

Note: By default, the **onboarding** section shows workers who were hired in the last seven days. To change this setting, navigate to the **Human Resources parameters** page, 
select the **General** tab, and define a time frame for **Recent hires**. The data in the **Recent hires** section can be shown for a specific number of days, months, or years.
For example, to view the list of workers who were hired in the last 14 days, set the **Period** field to **14** and the **Unit** field to **Days**. The Exited and Exiting 
workers lists can also have the date range updated within the Human Resource parameters page. Also note that these settings apply to the Personnel Management workspace.

# Configure Checklists

A **checklist** is a group of **tasks**. You can create as many checklists as you need and assign the same tasks to multiple checklists. For example, a company may want to 
create separate checklists for seasonal employees and regular full-time employees. These checklists may have some of the same tasks, such as verifying the arrival time of the
new employee. However, some additional tasks might only apply to the full-time employees. To address this situation, you can create two checklists that include some of the same
tasks, as well as tasks specific to the employee type. The **checklist** is flexible way to group tasks and you can reuse when you hire additional employees.

## 

## Tasks

A checklist contains a grouping of tasks. Tasks can be created individually and re-applied across multiple checklists. To create a task, navigate to the Onboarding Setup page,
select the Tasks tab and select new. Tasks can also be added directly to a checklist. To create a task directly within a checklist, navigate to Onboarding Setup, select the 
Checklist tab and either create a new checklist to add the task to or add the task to an existing checklist.

Note: When adding a task directly to a checklist, it will not be available for selection in other checklists.

Within a task there are the following fields:

| Task name       | Name of the task.                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Description     | Description of the task                                                                                                                                        |
| Optional        | This indicates that this task is Optional. This is informational only.                                                                                         |
| Task link       | This can be a URL to an external site or a specific page within the application that the user should navigate to.                                              |
| Assignment type | Tasks can be assigned to a specific Worker, a Position, a Group, Manager, or to the Employee that is part of the onboarding, offboarding or transition 
process |
| Assigned To     | This is the worker, position, or group that the task is assigned to                                                                                            |
| Contact Person  | If there are questions about a task, this is the person that should be contacted                                                                               |
| Due date offset | The number of days before or after the onboarding, termination, or transition date that the task is due.                                                       |
| Instructions    | Instructions that should be followed to complete the task.                                                                                                     |

### More about task links:

**Tasks links** provide a link to a URL or to a specific page within the Dynamics 365 application. A task link would be used if you want the person assigned to the task to 
navigate to a specific web page or D365 application page to complete the task. When creating a **task link** there will be an option to select a **Menu item, URL, or Worker 
details**. If **Menu item** is selected a list of all pages within the application will be displayed. If **URL** is selected, enter in the URL that you would like receiver of
the task to navigate to. This can be a URL that is not part of the Dynamics 365 application. Lastly, if 'Worker details' is selected, the user will be presented with two 
options: **Employee self Service actions** or **Worker management actions.** The **Employee self-service actions** option provides a list of all pages that are available in
Employee Self-Service. You would select this option if the task were being assigned to the onboarded employee needs to be completed in ESS. As an example, you may want the
employee to fill out their personal contact information. To enable this scenario, select '**Employee Self Service Actions'** and then select 
**Personal Details&gt;Personal Information.** Alternatively, the **Worker management actions** option provides a list of all pages that are related to the worker's record that
are not accessible to the employee. For example, you may want the receiver of the task to enter information that is specific to an onboarded worker such as compensation.
To enable this scenario select '**Worker management actions'** and then select **Compensation&gt;Fixed compensation**.

### More about assignment types

As discussed previously checklists group tasks together. When an employee is hired, terminated, or transferred one or more checklists can be selected. Once the checklist is
selected, and the hiring, terminating, or transition process is completed, tasks will be created and assigned to users to track progress for the process. When a task is created
it will be assigned to a specific user in the system. The user that is assigned the task is dependent upon the **Assignment type** selected in the task. The options for the
assignment type are **Worker**, **Position, Group (of positions)**, the affected employee's **Manager** or the **Employee** that is being hired/terminated/transitioned. 
For example, an IT engineer will always be the person that prepares the laptops for a new employee. When creating this task, select **Position** for the **Assignment type**,
and then select IT engineer from the **Position** list. When an employee is hired, and the checklist is assigned, the laptop configuration task will be assigned to the worker
who is in the IT engineer position at the time the hire action was entered in the system. You can also assign a task to a specific worker by selecting **Worker** in the
**Assignment type** field, and then selecting the appropriate individual. If **Manager** is selected, the manager of the employee that is being hired, terminated, or
transitioned will receive the task.

Important: If the hired/terminated/transitioned employee does not have a position assigned at the time a checklist is applied, the manager cannot be determined, and the task
will be assigned to the checklist owner.

Lastly, if '**Employee self-service'** is selected as the assignment type, the employee that is being hired/terminated/transitioned will be assigned the task.

### 

### More about task due dates and the due date offset field

Task due dates are based on the employment start date, termination date, or date of transition. Some tasks must be completed before an employee's start date, while others can
be completed later. When defining a task, you'll enter a due date that is relative to the start date, termination date or transition date in the **Due date offset** field. 
For example, assume that an IT engineer must prepare a new employee's laptop two days before their start date. The task created will have a due date offset from start date 
of -2. Therefore, if an employee's start date is May 5<sup>th</sup>, the IT task will be due on May 3<sup>rd</sup>. Note: Due dates can also be adjusted after the task is 
created.

Note: Working and non-working days can be defined in calendar setup. Working days are included in calculating the due date. Non-working days are excluded. Learn more about
Calendars(hyperlink needed)

More about instructions

Complex tasks might require multiple steps or need the individual performing the tasks to provide additional information. You can add **Instructions** to the task, and 
include rich text formatting for the instructions, as well. The instructions can provide additional information on how to complete the task to the person who is assigned 
to complete it.

## 

## Setup Calendar 

The calendar is used to calculate the due date of the tasks. Calendars allow certain days to be skipped in calculating due dates – such as weekends or holidays. Calendars 
are then associated to a checklist so that all tasks in the checklist use the same logic for calculating due dates. Multiple calendars can be setup in the system but only 
one can be associated to a checklist

## Setup Assignment Groups (Optional)

Sometimes there are a group of individuals that are responsible for a task. For example, you may have a group of individuals who are responsible for setting up laptops 
for new hires. A group called **IT Laptop** can be created.

Within the **Group assignment** page, select New. Give the group a name (IT Laptop) and a description and select **Save.** Navigate to the **Members** fast tab and 
select **'Add'.** Select all **Positions** that are responsible for setting up laptops. Once the group is created, it is available for selection when creating a **task**.
To select a specific **group** in a task, the **assignment type** must be set to '**Group**'. Once 'Group' is selected for the assignment type, the '**Assigned to'** field 
will list the IT Laptop group that was created.

**Important things to note:**

-   When a task is assigned to a group, the task becomes completed when ONE person in the group completes the task.

-   At discussed earlier, at the time of hire/termination/transition, tasks are created. During this process, the assignment group will be read, and tasks will be created
-    for the users that are assigned to the positions contained in the group.

## Setup Checklists

A **checklist** is a group of tasks. You can create as many checklists as you need and assign the same tasks to multiple checklists. For example, a company may want to 
create separate checklists for seasonal employees and regular full-time employees. These checklists may have some of the same tasks, such as verifying the arrival time of the 
new employee. However, some additional tasks might only apply to the full-time employees. To address this situation, you can create two checklists that include some of the same
tasks, as well as tasks specific to the employee type. The **checklist** is flexible way to group tasks and you can reuse when you hire additional employees.

When create a checklist you will set an **owner** and a **calendar**.

The owner will be assigned tasks when an individual cannot be assigned a task. This can happen when task assignment is set to position, manager or group, and an individual
cannot be derived from this assignment type. Some scenarios that can cause this are:

-   The employee being hired or terminated does not have a position assigned. Without a position assignment, their manager cannot be determined.

-   The assignment type is set to position, but there isn't an employee assigned to the position at the time the tasks are created. Example: The Setup Laptop task is
-    assigned to Position Number 000876/Technical Support Specialist. At the time an employee is hired, there isn't an employee that is assigned to 000876. A task will be
-     created for the checklist owner in this scenario.

-   The assignment type is set to group, but there isn't an employee assigned to the position(s) contained in the group at the time the tasks are created. This is the same
-    scenario as above, but the position is part of a group of positions.

The calendar is used to calculate the due date of the tasks. Calendars allow certain days to be skipped in calculating due dates – such as weekends or holidays. 
Calendars are then associated to a checklist template so that all tasks in the checklist use the same logic for calculating due dates. Multiple calendars can be setup in 
the system but only one can be associated to a checklist.

## Setup Task Groups (Optional)

An onboarding process can encompass many tasks. You can create optional task groups that help categorize related tasks and make it easier to assign all the tasks to a
checklist that are needed to bring a new employee into your organization. For example, there are tasks that HR, IT, and Payroll each need to complete. **Task groups** are user
defined, so the following tasks groups could be created: HR, IT, and Payroll. When creating a task, one of these **tasks' groups** can be associated with that task. Therefore, 
when you add the task to a checklist, the list of tasks can be filtered by the group that it's assigned to. For example, when creating a Checklist template, all IT tasks in the
IT Group can be viewed and only the relevant IT tasks selected.

## 

## Using Onboarding checklists

When a worker is hired, terminated or changes positions one or more checklists can be selected. Task due dates and worker assignments get created once the hiring, termination
or change position process is complete. For example, when you select the hire or hire and add details button tasks will be created for individuals based on the assignment type
in the task setup. A due date will also be assigned to each task by adding or subtracting the offset days from the employee's start date (see the information regarding offset
days in the task section). If you are using personnel actions, the tasks will be created when the Complete button is selected or when the action is approved.

Within the Task management workspace a checklist can be applied to the worker by selecting the employee in the simple list and details page, and selecting Apply checklist. 
A Target date needs to be entered. The Target date is the date that will be used for calculating the due dates of the tasks. Typically, this date should match the hire, 
termination, or transition date of the employee.

Checklists and tasks can also be added to the worker by navigating to the Worker page and selecting Checklists from the menu. A checklist can be applied to the worker by 
selecting Apply checklist. A Target date needs to be entered. The Target date is the date that will be used for calculating the due dates of the tasks. Typically, this date
should match the hire, termination, or transition date of the employee.

## 

## Completing tasks

When a task is assigned to an employee, their assigned tasks can be viewed on the Employee self-service page. Employees that have been assigned a task can see the task, its
description, instructions, contact person, and they can open the associated Dynamics 365 page or external web page from their Employee self-service page. Tasks can be marked 
as in progress, canceled, or completed. Tasks can also be reassigned.

If the task was assigned to a Group, the task will be set to completed when ONE person in the group completes the task.



