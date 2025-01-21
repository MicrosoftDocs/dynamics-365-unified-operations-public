--- 
title: Available reports for security 
description: Learn about the available reports in security.  
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

# Available reports for security 
There are various reports that are available to help with security, licenses, roles. and duties. 
The following reports are available:
 - User activity aging - tracks login information.
 - License summary - displays how many entry points for each license level.
 - Role audit trail - view the history of a role that are assigned and unassigned to users.
 - Security analysis - provides information about various roles and their privileges access levels, how many users belong to each role and change history of duties, roles and privileges.

## User activity aging report

[!include[banner](../../../finance/includes/banner.md)]

The **User activity aging** report facilitates tracking login information into Dynamics 365 finance and operations, enabling administrators to monitor user activity effectively. 
Some of the most common monitoring days are 10, 30, 60, 90, 120. This data can be used to optimize licensing costs. These day ranges are configurable and can be customized to suit the organization's needs.

In order to define and customize time ranges for **User activity aging**, follow these steps:
1. Go to **System administration** > **Security governance setup** > **Parameters**.
2. On the **User aging periods** tab.
3. Configure all five periods as needed.
4. Click **Save**.

## License summary report
This report helps users understand how many entry points for each license level are applied to **User**, **Role**, **Duty**, and **Privilege**. This helps to find possible optimization within the organization.

 - **Recalculate prices** - recalculates the prices of the licenses used for **Users**, **Roles**, **Duties**, and **Privileges**.
 - **Rebuild licenses** - rebuilds the licenses used for **Users**, **Roles**, **Duties**, and **Privileges**. Potentially, all users with a small number of **Entry points** with the operational license level might be moved into Activity or Team Member level by redesigning their access.
 - User license - a list of all users with details regarding licenses, operations, activities, etc. This checks each user’s access and verifies the license level.
 - Role license - a list of all the **Roles** and details regarding licenses, operations, activities, etc. This allows you to check each role's access and verifies the license level.
 - Duty license - a list of all **Duties** and details regarding licenses, operations, activities, etc. This allows you to check each duty’s access and verifies the license level.
 - Privilege license - a list of all the **Privileges** and details regarding licenses, operations, activities, etc. This checks each privilege’s accesses and verifies what license they have.
 - User license summary - analyze user licenses and verifies the details needed to assign licenses and optimize them for their usability.
 - Security summary - analyze user licenses, roles, duties, and privileges to optimize the environment so that each user or a group of users is granted appropriate access.

## Role audit trail report
Role audit trail provides a history of the role that have been assigned and unassigned to users. This includes the time of assignment and the individual who assigned them. Data is collected from the assignment and deallocation of roles. To see the **Role audit trail** report, follow these steps:
Go to **System administration** > **Users** > **User's role**
  or
**System administration** > **Security** > **Security governance** > **Temporary role management**.

## Security analysis report
The security analysis report displays information about various roles and their privileges access levels, how many users belong to each role and change history of duties, roles and privileges. To refresh the report data, click on **Rebuild**

### Navigate the report
Users can find **Security elements** based on the name. Permission levels are displayed by **Read**, **Create**, **Correct**, **Update**, **Invoke**, and **Delete**. Roles and their mappings to user licenses is displayed.

 - Entry points - A list of all **Roles**, **Sub-roles**, **Duties**, and **Privileges** in the system. Users can see all the roles and their duties and privileges in a the single place.
 - User entry points - Provides a complete security profile of a selected user to see what roles are assigned, what duties and privileges are assigned to the roles, and what entry points are accessible to the user. Users can see other users within the company have similar access level.
 - Entry points history - Provides a complete history of changes made to the security configuration. Various data points like **Created date and time** and **Created by** are captured for **Roles**, **Duty**, and **Privilege**. Users can also see **XML** and **Difference** with the previous version of the same object.
