---
# required metadata

title: Generate Affordable Care Act reports
description: Functionality is available to assist employers that need to track the information reported on forms 1095-B and 1095-C in support of the Employer Mandate portion of the Affordable Care Act. Note this functionality is only enabled for legal entities in the United States.
author: shielas
manager: AnnBe
ms.date: 01/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: kherr
ms.search.validFrom: 2018-01-09
ms.dyn365.ops.version: AX 7.1.0, Talent October 2017 update

---
# Formalize business processes
The Business process feature allows you to create a business process template for processes that need to be completed within your organization. For example, your company may complete an HR audit each year. A template can be created to track all the tasks that the audit comprises to help ensure that all the tasks are done each time the process is completed, and if necessary, to help ensure that tasks are performed in the correct order. Templates can be re-used for recurring processes or copied to use as a starting point creating new ones.

After a template is created, a process can be started and tracked in the Business process workspace.  When a business process is started, the tasks will be assigned to the appropriate people and will include a due date. We will cover these components in detail below.

## Business process template
A Business process template lists a group of tasks that make up a business process. Human resource managers and assistants can create business processes by default.  However, this can be changed in the security configuration by editing the Maintain generic business processes duty.

A Process owner can be defined for each process.  The process owner will have visibility into all the tasks for the process, and can re-assign tasks or change due dates.  For example, the HR director could create a Business process template for a benefits review.  The Comp and benefits manager can be set as the Process owner, so that he or she can have insight into the tasks that need to be completed as part of the review.  A Process owner cannot create or delete active Business processes or Business process templates.

## Task
A business process often comprises multiple tasks. Some tasks can be completed within Dynamics 365 for Talent[?], such as reviewing internal course offerings. In this instance, a Menu item would be selected in the Task link field. Other tasks might involve reviewing or completing forms on a web site. Selecting URL in the Task link field enables the web address to be entered. You can enter URLs for both external and internal sites in this field. You can also create tasks for activities that you complete manually, such as reviewing the accessibility of all structures. In this instance a task link is not required. This flexibility lets you track multiple kinds of tasks in a comprehensive process.

Tasks can be assigned to a specific worker or to a position. For example, the Comp and benefits manager will always be the person that conducts a review of insurance premiums.   When creating this task, select Position for the Assignment type, and then select Comp and benefit manager from the Position list. When the process starts, the task will be assigned to the worker who is in the Comp and benefits manager position. You can also assign a task to a specific worker by selecting Worker in the Assignment type field, and then selecting the appropriate person.

Task due dates depend on the Target date entered at the start of the process. Some tasks must be completed before the target date, and some might be completed after the target date.  When defining a task, you will enter a due date that is relative to the target date in the Due date offset from target date field. For example, assume that the Comp and benefits manager must perform a review of the insurance premiums 10 days before the HR audit is complete. The task created will have a due date relative to target date of -10. Therefore, if the process is started on May 13th, the task will be due on May 3rd. Note: Due dates can also be adjusted after the process is started.

Complex tasks might require multiple steps, or need the individual performing the tasks to provide additional information. You can add Instructions to the task, and include rich text formatting for the instructions, as well. The instructions can provide additional information on how to complete the task to the person who is assigned to complete it.

Starting a process
A process can be started within a Business process template by selecting Start process.  When a process is started, tasks will be created for the selected workers and/or positions defined in the tasks that are included in the Business process template. A due date will also be assigned to each task by adding or subtracting the offset days from the target date (see the information regarding offset days in the task section). The active Business processes can be viewed in the Business processes workspace. 

## Employee self-service
When a task is assigned to an employee, their assigned tasks can be viewed on the Employee self service page. Employees who have a business process task assigned to them can see the task, its description, instructions for completing it, and the name of a contact person, and they can open the associated Dynamics365 page or web page, from their Employee self-service page. Tasks can be marked as in-progress, canceled or completed.

## Business Process Workspace
HR professionals can view the active business processes from the Business process workspace. The workspace lists all active processes and the tasks that are associated with each one. The comprehensive task list can be filtered by due date. The page also lists overdue tasks, and tasks specifically assigned to the HR professional. They can also update the status of all tasks and if necessary, reassign tasks to help keep the overall business process moving forward.

## My Business Processes Workspace
Process owners can view the active business processes that are assigned to them from the My Business Process workspace. The workspace lists all active processes and associated tasks that that user owns.  The comprehensive task list can be filtered by due date. The page also lists tasks specifically assigned to process owner. The process owner can also update the status of all tasks, as well as reassign any tasks.

## Navigating Business Processes
1.	 To add a Business process template, navigate to Business processes- links – Business processes administration
  a.	New will create a new template
  b.	Copy from template will copy the selected template to a new one.
  c.	Start process will start the selected business process, assign tasks, and calculate due dates.  
2.	To view active processes and associated tasks navigate to the Business processes workspace.
