--- 
title: Security tasks under process hierarchy
description: Learn how to process hierarchy security tasks. 
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 01/25/2025
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
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The security tasks under the process hierarchy are the key steps performed in Dynamics 365 finance and operations by any given role, to perform the specific duties. With this feature, system administrators converts these processes into individual tasks and multiple functionalities supported with these tasks. 

## Segregation of duties
Segregation of duties prevents different duties with overlapping privileges and roles with overlapping responsibilities. Users can enabling segregation of duties on the **Parameters** page. After creating a new task and assign entry points to the task, you can validate the percentage of overlapping duties. You can set up segregation of duties rules to prevent users from saving conflicting duties.

### Privilege separation validation
The goal of privilege separation validation is more focused on the privileges assigned to the roles. After a new task is created and assign entry points to the task, you can validate the percentage of overlapping privileges.

### Load from task recordings
Creates new task from existing task recordings generated through the task recorder utility and user interface interactions. Users can record core business actions and share it with system administrators to convert them into security tasks within security configuration. This is an efficient way to create new tasks.

### Load from user or role
Utilize existing user accounts or existing roles to convert them into security tasks. After an existing user account or role is selected, the entry points are extracted and converted into tasks. System administrators can modify the privileges of extracted entry points or change them. System administrators have a starting point to design new security roles based on existing users or roles. 

## Load from existing task
Utilize existing tasks to create new tasks and provides a starting point. 

## Entry points subtraction
Create a new duty based on an existing entry point by removing specific processes from it. Click **Entry points subtraction** and then select an existing user account, role, privilege, or duty to see entry points. You can remove the entry points which you don't want to create in the new tasks. 

## Load from file
Use an existing XML backup file to create new tasks. When copying tasks from one company to another company, export the tasks from one company into XML formal and import them into another company.
