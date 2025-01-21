--- 
title: Security entry points under process hierarchy
description: Learn about various functionalities related to process hierarchy entry points under user security governance. 
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 02715/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-20
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0 
---

# Security entry points under process hierarchy

[!include[banner](../../../finance/includes/banner.md)]

The security entry points under the process hierarchy are critical for defining and designing the access level and privileges for any given role. Some of the key functionalities around entry points which are supported under security governance are:

## Explode entry point
System administrators can expand permissions of a given role by including all the other entry points related to the menu item. The menu item associated with the entry point is retreived using its name and type and then fetchs all the other entry points associated with the menu item. If the menu item exists, sets the access rights and label for the entry point. If the record type is a menu item, sets additional properties like user licenses and manual permissions. 
> [!IMPORTANT] 
> This function adds all neighborhood entry points from selected entry point It's recommended to use with workspaces.

## Update permissions
System administrators can update the permissions of a given role by changing the permission levels for each entry point. One can re-configure the **Unselect**, **Grant** or **Deny** permissions for each entry point at the following levels:
 - **Read**
 - **Create**
 - **Update**
 - **Correct**
 - **Invoke**
 - **Delete** 
