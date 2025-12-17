---
title: Security Role Duplicate with license filter
description: The 'Duplicate Security Role / Duty with License Filter' feature in Dynamics 365 Finance and Operations helps administrators create compliant security roles and duties aligned with the selected license tier. This feature reduces the manual effort required to adjust security configurations and ensures that roles comply with Microsoft licensing policies.
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

# Duplicate a security role or duty with a license filter
[!include [banner](../includes/banner.md)]

Administrators often need to create "license-aligned" security roles—roles that only contain duties and privileges consistent with a specific license tier (for example, Team Members). Traditionally, that work requires manual review and cleanup across many duties, privileges, and role references, which can mean checking hundreds of objects.

The **Duplicate with license filter** capability helps reduce that effort by duplicating a role (or duty) while **excluding** references that aren't fully entitled by the selected license tier. The result is a new security object you can publish and assign, along with a clear summary of anything that was excluded for follow-up.

## Why this feature matters

Manually "right-sizing" a role to a license tier is time-consuming and error-prone. This feature provides:

- **Faster role creation** by automatically filtering role references (sub-roles, duties, privileges) based on the selected license tier. 
- **More predictable license alignment** by excluding objects that require entitlements outside the chosen tier. 
- **Transparency for cleanup** via an exclusion summary and an exportable list of excluded references.

 :::image type="content" source="media/security-role-copy-with-license-filter-duplicate-button.png" alt-text="Security Configuration with Duplicate function" lightbox="media/security-role-copy-with-license-filter-duplicate-button.png":::

> [!NOTE]
> This feature helps you build **license-aligned security configurations**, but it does not assign licenses or change licensing. You remain responsible for ensuring that users are properly licensed according to the **Dynamics 365 Licensing Guide**](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409) and [**Dynamics 365 Licensing Deck**](https://go.microsoft.com/fwlink/?linkid=2279233).

## Who should use this feature
This feature is intended for:

- **Finance and Operations administrators** who manage security roles and want to reduce the effort required to create license-aligned roles.
- **Licensing administrators and auditors** who validate that security configurations align with assigned licenses and internal policy.

## Prerequisites

Before you begin, verify that:

- You have permissions to manage security in Finance and Operations (for example, System administration / security administration permissions).
- You know the **license tier** you want the duplicated security object to align with (for example, Team Members, Activity, Enterprise).

## Availability and setup
This feature is delivered through Finance and Operations servicing (including PQUs). Proactive Quality Update schedules and train build details are published close to each train start and can change. Microsoft typically publishes the detailed schedule for each PQU train and corresponding build information **five days before the train starts** and notifies customers through standard servicing communications. 

For general PQU scheduling guidance, see:
- [Release schedule for proactive quality updates](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule)

The following table reflects the servicing trains, exact builds and rollout dates and official PQU schedule page that includes this functionality.

| Release        | Build          | Proactive Quality Update        | Proactive Quality Update Train Duration                     |
|----------------|----------------|------------|----------------------------------------|
| [10.0.45 PQU-4 /10.0.2345.130](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule)| 7.0.7690.96   | PQU-4      | January 5, 2026 to February 8, 2026  |
| [10.0.44 PQU-7 / 10.0.2263.187](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule)| 7.0.7606.174   | PQU-7      | January 5, 2026 to February 8, 2026    |
| [10.0.43 PU67 / 10.0.2177.214](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule) | 7.0.7521.283 /   | PQU-9      | January 5, 2026 to February 8, 2026    |

For more information, see [Role-based security](role-based-security.md).

To enable and use this feature:
- Update your environment to the latest Finance & Operations release that includes this feature.
- Navigate to the **System administration → Security → Security Configuration**

For background on security concepts, see [Role-based security](role-based-security.md).

## How the duplciate license filter works

When you duplicate a role (or duty) with a selected license tier:

- Finance and Operations copies the security object.
- The system evaluates referenced objects (sub-roles, duties, privileges).
- **Only references whose entitlements are fully covered by the selected license tier are included.**
- References that require entitlements outside the selected tier (including mixed-entitlement objects) are **excluded** and reported.

> [!IMPORTANT]
> The feature does **not** deep-copy or create new duties or privileges. It reuses existing security objects and reports what is excluded, which helps preserve alignment with out-of-box security functionality. 

## Use the Duplicate with license filter feature

:::image type="content" source="media/security-role-copy-with-license-filter-overview.png" alt-text="Overview of duplicating a security role with a license filter." lightbox="media/security-role-copy-with-license-filter-overview.png":::

Follow these steps to use the **Duplicate Security Role with License Filter** feature:

:::image type="content" source="media/security-role-copy-with-license-filter-overview.png" alt-text="Duplicate function overview" lightbox="media/security-role-copy-with-license-filter-overview.png":::

1. In Finance and Operations, open **System administration**.
2. Go to **Security configuration**.
3. Select the role (or duty) you want to duplicate.
4. Select **Duplicate**.
5. In the dialog, enter:
   - A **new name** for the copied security object 
   - A **license tier** for the new security object (for example, Team Members, Activity, or Enterprise)

:::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-1.png" alt-text="Duplicate dialog prompting for a new name and license tier." lightbox="media/security-role-copy-with-license-filter-detailed-step-series-1.png":::

6. If some references can’t be included, a warning appears indicating that references were removed during the copy process.
   - Select **Message details** to open a side pane showing the count of excluded references.
   - Download the excluded reference list to Excel for auditing and cleanup.

 :::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-2.png" alt-text="Some References were excluded." lightbox="media/security-role-copy-with-license-filter-detailed-step-series-2.png":::

7.	Review the list of duties and privileges that were excluded from the selected license. A summary will display excluded objects that did not meet the entitlement criteria.

 :::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-3.png" alt-text="Excluded References from duplicated security role" lightbox="media/security-role-copy-with-license-filter-detailed-step-series-3.png":::

8.	Select **Publish selection** to publish the role and assign users to the new security role. 

 :::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-4.png" alt-text="Publish selection of duplicatd security role" lightbox="media/security-role-copy-with-license-filter-detailed-step-series-4.png":::

 ## Operational guidance and follow-up

 After duplication:

- Use the excluded reference export to decide whether to:
  - Remove high-privilege duties from the intended "lower tier" experience, or
  - Create separate roles aligned to higher tiers for users who need them.
- Plan a validation pass in a sandbox environment before applying role changes broadly.

## Important considerations
- Roles can only be duplicated within the same Finance & Operations environment.
- Duties and privileges are only included if **all** entitlements are compliant with the selected license tier.
- Duties or privileges containing mixed license entitlements will be excluded and listed in the post-copy summary.
- The feature does not create or modify duties or privileges; it only reuses existing ones.
- Deep copying is avoided to maintain alignment with standard (out-of-box) functionality and upgrades.
- The feature does not support cross-environment or cross-tenant copying.

## Related information

- [Release schedule for proactive quality updates](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule) [1](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]