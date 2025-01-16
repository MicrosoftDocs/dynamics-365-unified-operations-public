--- 
title: Security entry points under process hierarchy
description: Learn about various functionalities related to process hierarchy entry points under user security governance. 
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 01/15/2025
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

The security entry points under process hierarchy are critical for defining and designing the access level and privileges for any given role. Some of the key functionalities around entry points which are supported under security governance are:

## Explode entry point
This feature offers the system administrators to intelligently expand permissions of a given role by including all the other entry points related to the menu item. The way this feature works is by retrieving the menu item associated with the entry point using its name and type and then recursively fetching all the other entry points associated with the menu item.If the menu item exists, sets the access rights and label for the entry point. Also, if the record type is a menu item, sets additional properties like user licenses and manual permissions. 
> [!IMPORTANT] 
> This function adds all neighborhood entry points from selected entry point Recommended to use against workspaces.

## Update permissions
 This feature allows the system administrators to update the permissions of a given role by changing the permission levels for each entry point. One can re-configure the **unselect**, **grant** or **deny** permissions for each entry point at **read**, **create**, **update**, **correct**, **invoke** and **delete** levels.