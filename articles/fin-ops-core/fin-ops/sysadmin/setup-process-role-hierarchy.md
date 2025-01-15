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

This feature allows a different perspective to set up company's security by following a **position based roles** and **process based duties/privileges**. This approach helps build new roles based on an organization’s hierarchy and existing positions. This helps create roles that are optimal considering UI effectiveness, license levels and data security. The feature extracts business processes from positions and converts these processes into security roles to make it easy to understand and define. This leads to a sizable optimization in the license cost and limits the data fraud risk to a minimum. Also, users with fewer buttons or functions on the screen are less distracted. The end goal is to implement roles where each role represent a very specific set of tasks and privileges required to perform a unique job in Dynamics 365 finance and operations. 

## Set up process hierarchy 

The most important step in setting up the accurate security configuration is defining the process hierarchy which closely represents your company functional hierarchy. This is the first step in the process of setting up the security configuration. If needed, it can be modified in future but that requires a significant amount of work.

To set up a process hierarchy, follow these steps:
1. Go to **System administration** > **Security** > **Security governance** > **Security process role maintain**.
2. Select a category to define the hierarchy by selecting **Security category** field and specify the desired value. 

[!NOTE]
> Select the desired tree level within the selected category before moving to next step.  

3. On the Action Pane, click **New process**.
4. In the **Process name** field, enter a unique name for the process and other details like **Description** and **Version**.	 

### Creating tasks for the process

To define tasks for a process level, there are multiple approaches. You can either create a new task and manually define the entry points or you can utilize an existing task recording which represents the functional behavior of any desired role. A task represent the smallest end-to-end functional steps that a role is going to perform.
1. Go to **System administration** > **Security** > **Security governance** > **Security process role maintain**.
2. Under the grid **Security tasks**, click **New**.
3. In the **Name** field, enter a value.
4. In the **description** field, enter a value.
5. Click **Create new duty** to create a new duty for the task.
6. In the **Duty name** and **Description** fields, enter a value.
7. After you create the duty, a privilege is automatically created for the duty with the same name in the background.

### Assigning entry point 

Entry points are the starting point of a task or a duty to perform the function. Entry points are assigned to a task to define the starting point of the task. Menu items, web content items, and service operations are referred to collectively as entry points. A task can have multiple entry points.

To assign an entry point, follow these steps:
1. Go to **System administration** > **Security** > **Security governance** > **Security process role maintain**.
2. Go to **Security tasks**, select the task to assign the entry point.
3. Go to **Entry points**, click **Add an entry point**.
4. In the **Type** field, click the drop-down button to open the lookup and select one of the type of **Menu items**.
5. In the **Name** field, click the drop-down button to open the lookup and select the desired identifier or multiple identifiers.
6. Each identifier in this list represents a unique menu item, web content item, or service operation.
7. Use the selections under each of permission level to define the **Read**, **Update**, **Create**, **Correct**, **Delete**, and **Invoke**.
8. Follow the same process to add more entry points to the task.
9. When you are done, click **Save privilege entry point**.

### Create new role

Roles are the collection of duties and privileges which are required to perform a specific job. Roles are created by combining multiple duties and privileges. After you have defined the process hierarchy, tasks, and entry points, you can create a new role.

To create a role, follow these steps:
1. For the selected process hierarchy level, **Process definition** fast tab, click **Create a new role**.
2. In the **Role name** field, type a value.
3. In the **description** field, type a value.
4. Save the role.


