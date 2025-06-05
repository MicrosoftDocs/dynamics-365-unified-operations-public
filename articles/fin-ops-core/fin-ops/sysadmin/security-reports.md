---
title: Available reports for security 
description: Learn about the available reports for security.
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 02/11/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-20
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# Available reports for security 

[!include [banner](../includes/banner.md)]

The following reports are available to help with security, licenses, roles, and duties:

- **User activity aging** – This report tracks sign-in information.
- **Role audit trail** – This report shows the history of a role that is assigned and unassigned to users.
- **Security analysis** – This report provides information about various roles and their privilege access levels. It shows how many users belong to each role and the change history of duties, roles, and privileges.

## User activity aging report

[!include[banner](../../../finance/includes/banner.md)]

The **User activity aging** report tracks information about sign-in to Dynamics 365 finance and operations apps. Therefore, it helps administrators effectively monitor user activity. Some of the most common monitoring ranges are 10, 30, 60, 90, and 120 days. The day ranges are configurable and can be customized to suit the organization's needs. The data on this report can be used to optimize licensing costs.

To define and customize day ranges for the **User activity aging** report, follow these steps.

1. Go to **System administration** \> **Security governance setup** \> **Parameters**.
1. On the **User aging periods** tab, configure all five day ranges as you require.
1. Select **Save**.

## Role audit trail report

The **Role audit trail** report provides a history of the roles that have been assigned and unassigned to users. Details include the time when a role was assigned and the individual who assigned it. Data is collected from the assignment and deallocation of roles.

To view the **Role audit trail** report, follow one of these steps.

- Go to **System administration** \> **Users** \> **User's role**.
- Go to **System administration** \> **Security** \> **Security governance** \> **Temporary role management**.

## Security analysis report

The **Security analysis** report shows information about various roles and their privilege access levels. The information includes the number of users who belong to each role and a change history of duties, roles, and privileges. To update the report data, select **Rebuild**.

### Navigate the report

Users can find security elements based on the name. Permissions are shown by level (**Read**, **Create**, **Correct**, **Update**, **Invoke**, and **Delete**). Roles and their mappings to user licenses are shown.

- **Entry points** – A list of all roles, sub-roles, duties, and privileges in the system. Users can view all the roles, and their duties and privileges, in one place.
- **User entry points** – Get a complete security profile of a selected user. This profile shows what roles are assigned to the user, what duties and privileges are assigned to the roles, and what entry points are accessible to the user. Users can view other users in the company who have a similar access level.
- **Entry points history** – Get a complete history of changes that are made to the security configuration. Various data points, such as **Created date and time** and **Created by**, are captured for roles, duties, and privileges. Users can also view the XML and the differences from the previous version of the same object.
