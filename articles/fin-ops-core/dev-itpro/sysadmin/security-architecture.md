---
title: Security architecture
description: Learn about the security architecture of finance and operations, including overviews on authentication, authorization, data security, and auditing user logins.
author: pnghub
ms.author: gned
ms.topic: article
ms.date: 08/14/2023
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: SysSecConfiguration, SysUserGroupInfo, SysSecRoleExcludeUsers
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: bea829b3-38ce-463c-a7e3-c9393b79d559
---

# Security architecture
[!include [banner](../includes/banner.md)]

This article provides an overview of the security architecture of finance and operations.

When you understand the security architecture, you can more easily customize security to fit the requirements of your business. The following diagram provides a high-level overview of the security architecture. 

[![Diagram showing overview of security architecture.](./media/security-architecture.png)](./media/security-architecture.png)

## Authentication
By default, only authenticated users who have user rights can establish a connection. 

Microsoft Entra ID is a primary identity provider. To access the system, users must be provisioned into a finance and operations instance and should have a valid Microsoft Entra account in an authorized tenant.

## Authorization
Authorization is the control of access to finance and operations applications. Security permissions are used to control access to individual elements of the program: menus, menu items, action and command buttons, reports, service operations, web URL menu items, web controls, and fields in the finance and operations client. 

Individual security permissions are combined into privileges, and privileges are combined into duties. The administrator grants security roles access to the program by assigning duties and privileges to those roles. 

Context-based security controls access to securable objects. When a privilege is associated with an entry point (such as a menu item or a service operation), a level of access, such as **Read** or **Delete**, is specified. The authorization subsystem detects the access at run time when that entry point is accessed, and applies the specified level of access to the securable object that the entry point leads to. This functionality helps to ensure that there isn't any over-permissioning, and the developer gets the access that was intended. 

For more information, see [Role-based security](role-based-security.md).

## Data security
Authorization is used to grant access to elements of the program. By contrast, data security is used to deny access to tables, fields, and rows in the database.

Use the extensible data security framework to supplement role-based security by restricting access to table records based on security policies. A security permission, as part of a user role, increases the access a user has to data, while a security policy decreases access to data.

For more information, see [Extensible data security policies](extensible-data-security-policies.md).

Additionally, the Table Permissions Framework helps protect some data. Data security for specific tables is enforced by Application Object Server (AOS).

## Auditing user logins
A system administrator or security administrator can access the user logins logs. For more information, see [Track user sign-ins](../lifecycle-services/user-logins.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]