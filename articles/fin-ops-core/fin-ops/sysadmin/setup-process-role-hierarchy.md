--- 
title: Set up process hierarchy, roles and privileges
description: Learn about how you can set up process hierarchy for your company and then assign various tasks, define roles, entry points and privileges as per the business requirements. 
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 01/13/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-20
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up process hierarchy, roles and privileges

[!include [banner](../../../finance/includes/banner.md)]

The process hierarchy is a way to organize and manage the business processes in your company. You can define the process hierarchy for your company and then assign various tasks, define roles, entry points and privileges as per the business requirements. 
This feature allows a different perspective to system administrators on they can setup their company's security by following a **position based roles** and **process based duties/privileges**. This approach
helps build new roles based on an organization’s hierarchy/ existing positions. Because of this approach, roles are optimal considering UI effectiveness, license levels and data security. 
The underlying idea here is extraction of business processes from positions and the conversion of these processes into security roles to make it easy to understand and define. This would lead to a sizable 
optimization in the license cost and limits the data fraud risk to a minimum. Also, users with fewer buttons or functions on the screen are less distracted. 
The end goal of this feature is to implement roles where each role represent a very specific set of tasks and privileges which are required to perform a unique job in the Finance & operations.This involves multiple steps which are explained in the following sections.

## New Process hierarchy setup

The most important step in setting up the accurate security configuration is to define the process hierarchy which closely represent your company functional hierarchy. This is the first step in the process of setting up the security configuration. If needed, it can be modified in future but that will require a significant amount of work so it is better to get it right the first time.
1. Go to **System administration** > **Security** > **Security governance** > **Security process role maintain**.
2. Select a category for which you are planning to define the hierarchy by selecting **Security category** field and specify the desired value. 
[!NOTE]
> Make sure you **highlight** the desired tree level within the selected category before moving to next step.  

3. On the Action Pane, click **New process** button.
4. In the **Process name** field, enter a unique name for the process and other details like **description** and **version**.	 

### Creating tasks for the process

 To define tasks for a process level, there are multiple approaches. You can either create a new task and manually define the entry points or you can utilize an existing task recording which represents the functional behavior of any desired role. Task represent the smallest end-to-end functional steps that a role is going to perform in the system.
1. Go to **System administration** > **Security** > **Security governance** > **Security process role maintain**.
1. Under the grid **Security tasks**, click **New**.
1. In the **Name** field, type a value.
1. In the **description** field, type a value.
1. There are other ways of creating a task like **Load from task recording** or **load from existing roles** etc. but we will deep dive into other areas in later sections.
1. Use the **Create new duty** button to create a new duty for the task by providing the **Duty name** and **description**.
1. Once you create the duty, there is a privilege automatically created for the duty with the same name in the background.

### Assigning entry point 

Entry points are the starting point of a task or a duty to perform the function. Entry points are assigned to a task to define the starting point of the task. Menu items, web content items, and service operations are referred to collectively as entry points. A task can have multiple entry points.
1. Go to **System administration** > **Security** > **Security governance** > **Security process role maintain**.
1. Under the grid **Security tasks**, select the task for which you want to assign the entry point.
1. Under the grid **Entry points**, click **Add an entry point**.
1. In the **Type** field, click the drop-down button to open the lookup and select one of the type of **Menu items**.
1. In the **Name** field, click the drop-down button to open the lookup and select the desired identifier or multiple identifiers.
1. Each identifier in this list represents a unique menu item, web content item, or service operation in the system.
1. Use the selections under each of permission level to define **Read**, **Update**, **Create**, **Correct**, **Delete**, **Invoke**.
1. Follow the same process to add more entry points to the task.
1. Once you are done, click **Save privilege entry point**.

### Create new role

Roles are the collection of duties and privileges which are required to perform a specific job in the system. Roles are created by combining multiple duties and privileges. After you have defined the process hierarchy, tasks, and entry points, you can create a new role.
1. For the selected process hierarchy level, by this time you have already defined duties and privileges.
1. Under the **Process definition** fast tab, click **Create a new role**.
1. In the **Role name** field, type a value.
1. In the **description** field, type a value.
1. Save the role.


