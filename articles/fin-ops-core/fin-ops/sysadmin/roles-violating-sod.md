---
title: Roles violating segregation of duties
description: Learn how to identify violations of the segregation of duties.
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 03/05/2026
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-20
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# Roles violating segregation of duties

[!include[banner](../../../finance/includes/banner.md)]

The **Roles violating segregation of duties** view shows all roles that violate segregation of duties rules. It also shows how many violations of this type exist for each role.

## View violations for a selected role

To view violations of segregation of duties rules, follow these steps:

1. Activate the **Summary** tab on the **Roles violating segregation of duties** view.
1. Under the **Security roles** grid, select the specific role to see segregation of duties violation.
1. On this grid, you see the role name and total count of segregation of rules set up.
1. After selecting a specific role, data is loaded on the grid **Segregation of duties rules**.
1. Go to the **Segregation of duties rules** grid.
1. If there are multiple rules setup for the selected role, there are multiple rows.
1. Select the name of a specific rule to see the violation.
1. The view shows the specific segregation of duties rule that the selected role violates.
1. Under the **Infolog text** column, you see complete details about the violation.

## View all violations

To view a report that lists all violations, go to **System administration** \> **Security** \> **Security governance** \> **Role violating segregation of duties** \> **List**.

The report uses the defined segregation of duties rules. All duties are monitored against these rules. If a duty is assigned to a role that violates any of these rules, it appears on this report.
