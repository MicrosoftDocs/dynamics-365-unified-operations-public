--- 
title: Roles violating segregation of duties
description: Learn about how the to utilize this feature to identify segregation of duties violation within system. 
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

# Roles violating segregation of duties

[!include[banner](../../../finance/includes/banner.md)]

This view displays which roles within the system are in violation of **Segregation of Duties** (SoD) rules and how many such violations exist for each role. 
By clicking on a specific rule name in the **SEGREGATION OF DUTIES RULES** table, you will be able to see the specific **Segregation of role rule** that the selected role breaches.


It is also possible to check the list of all violations by going to **System administration** > **Security** > **Security governance** > **Role violating segregation of duties** > **List**.

This report utilized the **Segregation of duties** rules that are defined in the system and it keeps monitoring all duties against these rules. If at any point a duty is assigned to a role that violates any of these rules, it will be displayed in this report.