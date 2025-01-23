---
title: Security entry points under the process hierarchy
description: Learn about various functionality that is related to entry points under the process hierarchy in user security governance.
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

# Security entry points under the process hierarchy

[!include[banner](../../../finance/includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The security entry points under the process hierarchy are critical for defining and designing the access level and privileges for any given role. Here are some of the key entry point–related functions that are supported in user security governance:

- Explode entry point
- Update permissions

## Explode entry point

System administrators can expand the permissions of a given role by including all the other entry points that are related to the menu item. The menu item that is associated with the entry point is retrieved by using its name and type. The system then fetches all the other entry points that are associated with that menu item. If the menu item exists, the access rights and labels are set for the entry point. If the record type is a menu item, additional properties are set, such as user licenses and manual permissions.

> [!IMPORTANT]
> This function adds all neighboring entry points from the selected entry point. We recommend that you use it with workspaces.

## Update permissions

System administrators can update the permissions of a given role by changing the permission levels for each entry point.

For each entry point, the **Unselect**, **Grant**, or **Deny** permissions can be reconfigured at the following levels:

- Read
- Create
- Update
- Correct
- Invoke
- Delete
