--- 
title: Security analysis report
description: Security analysis report offers very important and key information to system administrators about what privileges are assigned to each role, how many users belong to each role etc.. 
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

# Security analysis report

[!include [banner](../../../finance/includes/banner.md)]

The security analysis report offers key information to system administrators about various roles and their privileges access levels, how many users belong to each role and change history of duties, roles and privileges. To refresh the report data, click on **Rebuild**

## Permissions

This report shows all Finance & operations security objects in a list format. Users can browse quickly to find **security elements** based on the name. This is useful when we are searching for a security object and we just know its name but not the type. Or, if user want to find all security items around a specific name/area. It display the permission level by **Read**, **Create**, **Correct**, **Update**, **Invoke** and **Delete**. Also, it shows role and their mapping with user licenses.

## Entry points
A list of all **Roles**, **Sub-roles**, **Duties** and **Privileges** in the system. This is useful when we want to see all the roles and their duties and privileges in the system at the single place and filter data based on what you are interested to monitor. 

## User entry points
This report is aimed to provide the complete security profile of a selected user. For system administrators, this report is very useful to see what roles are assigned to a user, what duties and privileges are assigned to the roles and what entry points are accessible to the user. And, how many other users within the company have similar access level. By getting this comparison in single report, now **System administrators** can take decisions to align the company security configuration to reduce overlapping roles and hence optimize the licensing cost. This report can also be print to PDF or Excel format.

## Entry points history
This report is aimed to provide the complete history of changes made to the security configuration of the system. It captures various data points like **Created date and time**, **Created by** etc. for key security objects like **roles, duty, privilege**. You can also go into the details of each object to see the **XML** view  and **Difference** with the previous version of the same object.