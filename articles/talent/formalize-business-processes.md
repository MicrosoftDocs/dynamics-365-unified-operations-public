---
# required metadata

title: Formalize business processes
description: This topic explains how you can use the Business process feature to create a business process template for processes that must be completed in your organization.
author: andreabichsel
manager: AnnBe
ms.date: 01/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: PersonnelBusinessProcessGenericWorkspace, BusinessProcessGenericTemplateListpage, BusinessProcessGenericMyTemplates, BusinessProcessGroupAssignment
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-01-09
ms.dyn365.ops.version: AX 7.1.0, Talent October 2017 update

---

# Formalize business processes

The Business process feature lets you create a business process template for business processes that must be completed in your organization. For example, your company completes a Human resources (HR) audit every year. In this case, you can create a template that tracks all the tasks that the audit process consists of. This template can then help guarantee that all the tasks are done every time that the audit is done. Additionally, if the tasks must be completed in a specific order, the template can help guarantee that they are done in the correct order.

Templates can be reused for recurring processes. They can also be copied and used as a starting point to create new templates.

After a business process template is created, a business process can be started and tracked in the **Business process** workspace. When a business process is started, the tasks are assigned to the appropriate people, and they include a due date.

## Business process templates
A business process template lists a group of tasks that make up a business process. By default, HR managers and assistants can create business processes. However, you can change the roles that can create business processes by modifying the **Maintain generic business processes** duty in the security configuration.

For each business process, you can define a process owner. The process owner has visibility into all the tasks for the process, and can reassign tasks or change due dates. For example, the HR director creates a business process template for a benefits review and specifies the Compensation and benefits manager as the process owner. The Compensation and benefits manager then has visibility into the tasks that must be completed as part of the review.

A process owner can't create new business processes or business process templates, or delete active business processes or business process templates.

## Tasks
A business process often consists of multiple tasks. Some tasks, such as a review of internal course offerings, can be completed in Microsoft Dynamics 365 Talent. In this case, an option is selected in the **Task link** field. Other tasks might involve reviewing or completing pages on a website. In this case, **URL** is selected in the **Task link** field, and then the web address can be entered. You can enter URLs for both external and internal sites. You can also create tasks for activities that you complete manually, such as a review of the accessibility of all structures. In this case, a task link isn't required. This flexibility lets you track multiple kinds of tasks in a comprehensive process.

Tasks can be assigned either to a specific worker or to a position. For example, the Compensation and benefits manager will always be the person who does a review of insurance premiums. Therefore, when you create this task, select **Position** in the **Assignment type** field, and then select **Comp and benefit manager** in the **Position** list. When the business process is started, the task is assigned to the worker who is in the **Comp and benefits manager** position. To assign a task to a specific worker, select **Worker** in the **Assignment type** field, and then select the appropriate person.

Due dates for tasks depend on the target date that is entered at the start of the business process. Some tasks must be completed before the target date, and other tasks might be able to be completed after the target date. When you define a task, in the **Due date offset from target date** field, you specify a due date that is relative to the target date. For example, the Compensation and benefits manager must do a review of insurance premiums 10 days before the HR audit is completed. In this case, the task that is created for the review has a **Due date offset from target date** value of **-10**. Therefore, if the business process is started on May 13, the task is due on May 3.

> [!NOTE]
> Due dates can also be adjusted after the business process is started.

Complex tasks might require multiple steps, or the people who perform the tasks might have to provide additional information. For these scenarios, you can add instructions to a task. The instructions can give the person who is assigned to complete the task additional information about how to complete it. You can even include rich text formatting in the instructions.

## Starting a business process
In a business process template, you can start a business process by selecting **Start process**. When a process is started, tasks are created for the selected workers or the positions that are defined in the tasks that are included in the template. A due date is also assigned to each task by adding or subtracting the number of offset days from the target date, as explained in the "Tasks" section. You can view active business processes in the **Business processes** workspace.

## Employee self-service
After a task is assigned to an employee, the employee can view it, and all his or her other assigned tasks, on the **Employee self service** page. For each business process task that is assigned to him or her, the employee can see the name and description of the task, instructions for completing it, and the name of a contact person. From the **Employee self service** page, the employee can also open the associated page in Microsoft Dynamics 365 or the associated webpage, and can mark tasks as in progress, canceled, or completed.

## Business process workspace
HR professionals can view the active business processes in the **Business process** workspace. This workspace lists all active processes and the tasks that are associated with each. The comprehensive task list can be filtered by due date. The workspace also lists overdue tasks and tasks that are assigned specifically to the HR professional. The HR professional can also update the status of all tasks and, as required, can reassign tasks to help keep the overall business process moving forward.

## My business processes workspace
Process owners can view the active business processes that are assigned to them in the **My business process** workspace. This workspace lists all the active processes that the user owns, and the associated tasks. The comprehensive task list can be filtered by due date. The workspace also lists tasks that are assigned specifically to the process owner. The process owner can also update the status of all tasks and reassign any task.

## Navigating business processes
To create or copy a business process template, or to start a business process, navigate to Business processes - links – Business processes administration. You can then perform the following actions:

- Select **New** to create a new business process template.
- Select **Copy from template** to copy the selected template to a new template.
- Select **Start process** to start the selected business process, assign tasks, and calculate due dates.

To view active processes and associated tasks, open the **Business processes** workspace.

