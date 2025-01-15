--- 
title: Security tasks under process hierarchy
description: Learn about various functionalities related to process hierarchy security tasks. 
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

# Security tasks under process hierarchy

[!include[banner](../../../finance/includes/banner.md)]

The security tasks under the process hierarchy are basically the key steps performed within **Finance & operation** by any given role, to perform the specific duties. With this feature, **System administrator** is going to convert these processes into individual tasks. 
There are multiple other functionalities supported with these tasks. 

## Segregation of duties
The goal of segregation of duties is to prevent different duties with overlapping privileges and hence roles with overlapping responsibilities. Enabling Segregation of duties is configurable in the system through the **Parameters** form. Once you create a new task and assign entry points to the task, you can utilize this feature to validate the percentage of overlapping duties.You can also setup Segregation of duties rules to prevent users from saving conflicting duties.

## Privilege separation validation
The goal of privilege separation validation is similar to segregation of duties but this is more focused on the privileges assigned to the roles. Again, this is configurable in the system through the **Parameters** form. Once you create a new task and assign entry points to the task, you can utilize this feature to validate the percentage of overlapping privileges.

## Load from Task recordings
This functionality allows you to create new tasks from existing task recordings which are generated through the Task recorder utility and user interface interactions. This is a very useful feature because it will allow people to record their core business actions and then share it with **system administrators** to convert them into security task within security configuration. This is the most efficient way to create new tasks and reflects the concept of **process-based roles**.

## Load from User or Role
This functionality allows you to utilize existing user account or existing role to convert them into security tasks. Once you pick any existing user account or role, it will extract the entry points underneath and convert them into tasks. Generally, after this action, system administrator would either modify the privileges of extracted entry points or change them. The goal of this feature is to give a starting point to system administrators to design the new security role which are inspired by existing users or roles. Ideally, you would not simply just copy the existing roles and create a new role without making any modifications. This will be against the principle of segregation of duties.

## Load from existing task
This functionality allows you to utilize existing tasks to create new tasks. Again, the goal here is to provide a starting point to system administrator and not simply duplicate the existing tasks.

## Entry points subtraction
This feature allows you to create a new duty based on an existing entry point by removing specific processes from it. Once you click on the **Entry points subtraction** button, you will be redirected to another screen where you will be asked to select either existing user account, role, privilege or duty to see their entry points and then you can remove the entry points which you don't want to create the new tasks. 

## Load from file
This feature allows you to use existing XML backup files to create new tasks. This is a very useful feature in scenarios where you are trying to copy tasks from one company to another company. You can simply export the tasks from one company into XML formal and then import them into another company.
