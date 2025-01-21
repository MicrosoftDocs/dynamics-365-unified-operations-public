--- 
title: Roles violating segregation of duties
description: Learn about how to identify viloations of segregation of duties. 
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

# Roles violating segregation of duties

[!include[banner](../../../finance/includes/banner.md)]

This view displays roles that violate **Segregation of duties** rules and how many such violations exist for each role.
1. To view Segration of duties rule violations, go to **Segration of duties rules** table.
2. Click a specific rule name.
3. You will be able to see the specific **Segregation of role rule** that the selected role breaches.

## View all violations
To view a list of all violations, follow these steps:
1. Go to **System administration** > **Security** > **Security governance** > **Role violating segregation of duties** > **List**.
2. This report utilizes the defined **Segregation of duties** rules. All duties are monitored against these rules. If a duty is assigned to a role that violates any of these rules, it's displayed on this report.
