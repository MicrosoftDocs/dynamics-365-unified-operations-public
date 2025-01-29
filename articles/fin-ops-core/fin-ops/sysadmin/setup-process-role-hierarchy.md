--- 
title: Set up a process hierarchy, roles, and privileges
description: Learn how to set up a process hierarchy, assign various tasks, and define roles, entry points, and privileges.
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

# Set up a process hierarchy, roles, and privileges

[!include [banner](../../../finance/includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

A *process hierarchy* provides a way to organize and manage the business processes in your company. After you define the process hierarchy for your company, you can assign various tasks, and define roles, entry points, and privileges according to the business requirements.

This feature helps you set up your company's security configuration based on position-based roles and duties/privileges. New roles can be created based on the organization's hierarchy and existing positions. Therefore, the feature helps you create optimal roles that take into account user interface (UI) effectiveness, license levels, and data security.

The feature extracts business processes from positions and converts them into security roles. Therefore, the roles are easy to understand and define. The goal is to implement roles that represent the specific set of tasks and privileges that are required to perform a unique job in finance and operations apps.

The benefits of this feature are optimization of license costs and reduced risk of data fraud.

## Set up a process hierarchy 

The first and most important step in the process of setting up an accurate security configuration is to define a process hierarchy that closely represents your company's functional hierarchy. Although the process hierarchy that you define can be modified later, modification requires a significant amount of work.

To set up a process hierarchy, follow these steps.

1. Go to **System administration** \> **Security** \> **Security governance** \> **Security process role maintain**.
1. In the **Security category** field, select a category, and then select the desired tree level within that category.
1. On the Action Pane, select **New process**.
1. In the **Process name** field, enter a unique name for the process.
1. Specify other details, such as a description and version information.

## Create tasks for the process

A *task* represents the smallest end-to-end functional steps that a role performs. There are two ways to define the tasks for a process level:

- Create a new task, and manually define the entry points.
- Use an existing task recording that represents the functional behavior of any desired role.

Follow these steps to create a new task.

1. Go to **System administration** \> **Security** \> **Security governance** \> **Security process role maintain**.
1. Under **Security tasks**, select **New**.
1. In the **Name** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **Create new duty** to create a duty for the task.
1. In the **Duty name** field, enter a value.
1. In the **Description** field, enter a value.
1. After you create the duty, a privilege is automatically created for it. This privilege has the same name as the duty that it's created for.

## Assign an entry point 

Menu items, web content items, and service operations are referred to collectively as *entry points*. Entry points define the starting points for a task or a duty in the performance of a function. Each task can have multiple entry points assigned to it.

To assign an entry point to a task, follow these steps.

1. Go to **System administration** \> **Security** \> **Security governance** \> **Security process role maintain**.
1. Go to **Security tasks**, and select the task to assign the entry point to.
1. Go to **Entry points**, and select **Add an entry point**.
1. In the **Type** field, select one of the types of menu items.
1. In the **Name** field, select one or more identifiers. Each identifier represents a unique menu item, web content item, or service operation.
1. Under each permission level, define the **Read**, **Update**, **Create**, **Correct**, **Delete**, and **Invoke** permissions.
1. Repeat steps 3 through 6 to add more entry points to the task.
1. When you're finished, select **Save privilege entry point**.

## Create a new role

A *role* is the collections of duties and privileges that are required to perform a specific job. Roles are created by combining multiple duties and privileges. After the process hierarchy, tasks, and entry points are defined, you can create new roles.

To create a role, follow these steps.

1. Select a process hierarchy level, and then, on the **Process definition** FastTab, select **Create a new role**.
1. In the **Role name** field, enter a value.
1. In the **Description** field, enter a value.
1. Save the role.
