---
title: User security governance overview
description: Learn about user security governance in Microsoft Dynamics 365.
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: concept-article
ms.date: 01/25/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-20
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# User security governance overview

[!include [banner](../../../finance/includes/banner.md)]

User security governance helps organizations create a security architecture that is closely aligned with their business processes. It empowers organizations to apply precise role management, advanced audit capabilities, and comprehensive license optimization tools.

:::image type="content" source="media/security-governance-sysadmin.png" alt-text="Security governance in the system admin user experience." lightbox="media/security-governance-sysadmin.png":::

User security governance provides the following capabilities:

- Detailed reporting about segregation of duties and separation of privileges
- Process-based security roles, duties, and/or privileges
- Creation of new roles/duties from existing objects through import processes
- Temporary role capabilities
- Privileged user management, which enables dedicated accounts to gain time-bound access

## User security governance features

User security governance provides the following functionality:

- Design process-based security roles, duties, and/or privileges. Learn more in [Set up a process hierarchy, roles, and privileges](setup-process-role-hierarchy.md).
- Design position/responsibility-based user roles.
- Create new roles/duties from existing objects through import processes, and merge duties.
- Automate temporary role assignments. Learn more in [Temporary role management](temp-role-mgmt.md).
- Grant time-bound elevated privileges to dedicated accounts through privileged user management. Learn more in [Privileged user management](priv-user-mgmt.md).
- Continuously monitor segregation of duties and separation of privileges. Define a threshold, and control the creation of duties/privileges that have overlapping entry points. Learn more in [Roles violating segregation of duties](roles-violating-sod.md).
- Draft and eventually convert defined roles to an Application Object Tree (AOT) project.
- Use the user aging report.
- Manage versions of roles, duties, and privileges. Learn more in [Security version management](security-version.md).
    - Compare versions.
    - Restore previous versions.

- Use the duty subtraction function.
- Export the security configuration to XML. Learn more in [Security category export/import](security-category-import.md).
- Use the security audit trail to track changes that are made in user security governance. Learn more in [Set up security governance parameters](setup-security-gov-para.md).
- Use new reports that include license indicators by role, duty, privilege, and entry point. Learn more in [Available reports for security](security-reports.md).
