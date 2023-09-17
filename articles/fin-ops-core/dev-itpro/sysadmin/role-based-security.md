---
# required metadata

title: Role-based security
description: This article provides an overview of the elements of role-based security. 
author: peakerbl
ms.date: 01/27/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysSecRolesEditUsers, SysSecConfiguration, SysUserGroupInfo, SysSecRoleExcludeUsers
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 48cfdd5a-7d04-4969-93ac-6cd6d10d5a09
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Role-based security

[!include [banner](../includes/banner.md)]

This article provides an overview of the elements of role-based security in finance and operations. 

In role-based security, access is not granted to individual users, only to security roles. Users are assigned to roles. A user who is assigned to a security role has access to the set of privileges that is associated with that role. A user who is not assigned to any role has no privileges. 

In finance and operations apps, role-based security is aligned with the structure of the business. Users are assigned to security roles based on their responsibilities in the organization and their participation in business processes. The administrator grants access to the duties that users in a role perform, not to the program elements that users must use. 

Because rules can be set up for automatic role assignment, the administrator does not have to be involved every time that a user's responsibilities change. After security roles and rules have been set up, business managers can control day-to-day user access based on business data.

## Overview of role-based security

This section provides an overview of the elements of role-based security. The security model is hierarchical, and each element in the hierarchy represents a different level of detail. Permissions represent access to individual securable objects, such as menu items and tables. Privileges are composed of permissions and represent access to tasks, such as canceling payments and processing deposits. Duties are composed of privileges and represent parts of a business process, such as maintaining bank transactions. Both duties and privileges can be assigned to roles to grant access to finance and operations. 

The following illustration shows the elements of role-based security and their relationships. 

[![Example of role-based security framework.](./media/rbs.png)](./media/rbs.png)

## Security roles

All users must be assigned to at least one security role in order to have access to finance and operations. The security roles that are assigned to a user determine the duties that the user can perform and the parts of the user interface that the user can view. 

Administrators can apply data security policies to limit the data that the users in a role have access to. For example, a user in a role may have access to data only from a single organization. The administrator can also specify the level of access that the users in a role have to current, past, and future records. For example, users in a role can be assigned privileges that allow them to view records for all periods, but that allow them to modify records only for the current period. 

By managing access through security roles, administrators save time because they do not have to manage access separately for each user. Security roles are defined one time for all organizations. In addition, users can be automatically assigned to roles based on business data. For example, the administrator can set up a rule that associates a Human resources position with a security role. Any time that users are assigned to that position, those users are automatically added to the appropriate security roles. 

Security roles can be organized into a hierarchy. The role hierarchy allows the administrator to define a role based on another role. For example, the sales manager role could be defined as a parent role of the manager role and the salesperson role. A parent role automatically inherits the duties, privileges, and conditions that are assigned to its child roles. Therefore, a user who is assigned to the parent role can perform all of the tasks that users in the child roles can perform. A role can have one or more child roles or one or more parent roles. 

By default, sample security roles are provided. All functionality is associated with at least one of the sample security roles. The administrator can assign users to the sample security roles, modify the sample security roles to fit the needs of the business, or create new security roles. By default, the sample roles are not arranged in a hierarchy.

## Duties
Duties correspond to parts of a business process. The administrator assigns duties to security roles. A duty can be assigned to more than one role. 

In the security model, duties contain privileges. For example, the **Maintain bank transactions** duty contains the **Generate deposit slips** and **Cancel payments** privileges. Although both duties and privileges can be assigned to security roles, we recommend that you use duties to grant access to finance and operations. 

You can assign related duties to separate roles. These duties are said to be segregated. By segregating duties, you can better comply with regulatory requirements, such as those from Sarbanes-Oxley (SOX), International Financial Reporting Standards (IFRS), and the United States Food and Drug Administration (FDA). In addition, segregation of duties helps reduce the risk of fraud, and helps you detect errors or irregularities. 

Default duties are provided. The administrator can modify the privileges that are associated with a duty, or create new duties.

## Privileges
In the security model, a privilege specifies the level of access that is required to perform a job, solve a problem, or complete an assignment. Privileges can be assigned directly to roles, however we recommend that you only assign duties to roles. This is so that the privileges are first grouped together into a duty, which makes it easier to maintain. 

A privilege contains permissions to individual application objects, such as user interface elements and tables. For example, the **Cancel payments** privilege contains permissions to the menu items, fields, and tables that are required to cancel payments. 

By default, privileges are provided for all features in finance and operations. The administrator can modify the permissions that are associated with a privilege, or create new privileges.

## Permissions
Each function, such as a form or a service, is accessed through an entry point. Menu items, web content items, and service operations are referred to collectively as entry points. 

In the security model, permissions group the securable objects and access levels that are required to run a function. This includes any tables, fields, forms, or server side methods that are accessed through the entry point.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
