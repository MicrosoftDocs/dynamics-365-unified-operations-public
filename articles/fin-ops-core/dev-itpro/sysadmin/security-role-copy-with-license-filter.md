---
title: Security Role Copy with license filter
description: The 'Copy Security Role / Duty with License Filter' feature in Dynamics 365 Finance and Operations helps administrators create compliant security roles and duties aligned with the selected license tier. This feature reduces the manual effort required to adjust security configurations and ensures that roles comply with Microsoft licensing policies.
author: ianceicys-msft
ms.author: anceicys-msft
ms.topic: article
ms.date: 012/17/2025
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2025-12-17
ms.search.form: SysSecConfiguration, SysUserGroupInfo, SysSecRoleExcludeUsers
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: bea829b3-38ce-463c-a7e3-c9393b79d559
---

# Why is this important?
[!include [banner](../includes/banner.md)]

Administrators often spend significant time reviewing and adjusting duties and privileges to ensure they match the appropriate license tier. This process can involve manually checking hundreds of objects. With this new capability, administrators can automatically generate a new role filtered by license tier, reducing manual review and ensuring compliance with licensing policies.

Key benefits include:
- Saves time by automatically filtering duties and privileges based on the selected license.
- Ensures roles are compliant with licensing policy and traceable through the Unified Security Governance (USG) – License Usage Summary report.
- Provides transparency into excluded entitlements and helps organizations optimize license usage and cost.

[![Diagram showing overview of security architecture.](./media/security-architecture.png)](./media/security-architecture.png)

## Who will benefit
This feature is designed primarily for the following personas:

- Finance & Operations administrators: to simplify role management and ensure license compliance.
- Licensing administrators or auditors: to validate that security configurations align with assigned licenses.

## Availability and setup
This feature will be available starting with the upcoming Finance & Operations platform release wave. Administrators will need to ensure their environment is updated to the latest release to access the new functionality, per below. 

| Release        | Build          | Proactive Quality Update        | Proactive Quality Update Train Duration                     |
|----------------|----------------|------------|----------------------------------------|
| PU69 / 10.0.45 | 7.0.7690.76    | PQU-2      | November 10, 2025 to December 14, 2025  |
| PU68 / 10.0.44 | 7.0.7606.174   | PQU-5      | November 3, 2025 to January 11, 2026    |
| PU67 / 10.0.43 | 7.0.7521.283   | PQU-9      | December 1, 2025 to January 18, 2026    |

For more information, see [Role-based security](role-based-security.md).

To enable and use this feature:
- Update your environment to the latest Finance & Operations release that includes this feature.
- Navigate to the System administration workspace.

## How to use
Follow these steps to use the Copy Security Role with License Filter feature:

[![Diagram showing overview of security architecture.](./media/security-architecture.png)](./media/security-architecture.png)

1.	Open the **System administration** module in your Finance & Operations environment.
2.	Go to **Security configuration** and locate the role you want to copy.
3.	Select **Duplicate (License Filter)** from the menu.

[![Diagram showing overview of security architecture.](./media/security-architecture.png)](./media/security-architecture.png)

4.	Enter the new role name for the copied security role and choose a license tier (e.g., Team Members, Activity, or Enterprise) for this new security role.

[![Diagram showing overview of security architecture.](./media/security-architecture.png)](./media/security-architecture.png)

5.	A Warning message will pop-up highlighting that references were removed from the security role during the copy process[AD3.1][AD3.2]. When clicking on the “Message details”, a sidebar will appear with the count of references and an option to download the excluded references in Excel format. 

[![Diagram showing overview of security architecture.](./media/security-architecture.png)](./media/security-architecture.png)

6.	Review the list of duties and privileges that were excluded from the selected license. A summary will display excluded objects that did not meet the entitlement criteria.
7.	Confirm creation of the new role and publish it. 

## Important considerations
- Roles can only be copied within the same Finance & Operations environment.
- Duties and privileges are only included if **all** entitlements are compliant with the selected license tier.
- Duties [AD4.1]or privileges containing mixed license entitlements will be excluded and listed in the post-copy summary.
- The feature does not create or modify duties or privileges; it only reuses existing ones.
- Deep copying is avoided to maintain alignment with standard (out-of-box) functionality and upgrades.
- The feature does not support cross-environment or cross-tenant copying.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]