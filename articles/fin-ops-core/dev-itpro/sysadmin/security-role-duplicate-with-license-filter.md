---
title: Security Role Duplicate with license filter
description: The 'Duplicate Security Role / Duty with License Filter' feature in Dynamics 365 Finance and Operations helps administrators create compliant security roles and duties aligned with the selected license. This feature reduces the manual effort required to adjust security configurations and ensures that roles comply with Microsoft licensing policies.
author: ianceicys-msft
ms.author: ceian
ms.topic: article
ms.date: 12/17/2025
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2025-12-17
ms.search.form: SysSecConfiguration, SysUserGroupInfo, SysSecRoleExcludeUsers
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 
---

# Duplicate a security role or duty with a license filter

Administrators often need to create **license-aligned** security roles that only contain duties and privileges consistent with a specific license (for example, Team Members, Operations - Activity). Traditionally, that work requires manual review and cleanup across many duties, privileges, and role references, which can mean checking hundreds of objects.

The **Duplicate with license filter** capability helps reduce that effort by duplicating a role (or duty) while **excluding** references that aren't fully entitled by the selected license. The result is a new security role you can publish and assign, along with an Excel **Excluded References** report for anything that was **excluded** for follow-up.

## Why this feature matters

Manually "right-sizing" a role to a license is time-consuming and error-prone. This feature provides:

- **Faster role creation** by automatically filtering role references (sub-roles, duties, privileges) based on the selected license. 
- **More predictable license alignment** by excluding objects that require entitlements outside the chosen license. 
- **Transparency for cleanup** via an exclusion summary and an exportable list of excluded references.

 :::image type="content" source="media/security-role-copy-with-license-filter-duplicate-button.png" alt-text="Security Configuration with Duplicate function" lightbox="media/security-role-copy-with-license-filter-duplicate-button.png":::

> [!NOTE]
> This feature helps you build **license-aligned security configurations**, but it does not assign licenses or change licensing. You remain responsible for ensuring that users are properly licensed according to the [**Dynamics 365 Licensing Guide**](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409) and [**Dynamics 365 Licensing Deck**](https://go.microsoft.com/fwlink/?linkid=2279233).

## Who should use this feature
This feature is intended for:

- **Finance and Operations administrators** who manage security roles and want to reduce the effort required to create license-aligned roles.
- **Licensing administrators and auditors** who validate that security configurations align with assigned licenses and internal policy.

## Prerequisites

Before you begin, verify that:

- You have permissions to manage security in Finance and Operations (for example, **System administrator** / **Security administrator**).
- You know the **license** you want the duplicated security object to align with (for example, Commerce, Supply Chain Management, Team Members, Operations - Activity, etc).

## Availability and setup
This feature is delivered through Finance and Operations servicing (including the latest Proactive Quality Updates(PQU)). Proactive Quality Update (PQU) schedules and train build details are published close to each train start and can change. Microsoft typically publishes the detailed schedule for each PQU train and corresponding build information **five days before the train starts** and notifies customers through standard servicing communications. 

For the latest Proactive Quality Update (PQU) schedule, see:
- [Release schedule for proactive quality updates](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule)

The following table reflects the servicing trains, exact builds and rollout dates and official PQU schedule page that includes the  **Duplicate with license filter** functionality.

| Release        | Build          | Proactive Quality Update        | Proactive Quality Update Train Duration                     |
|----------------|----------------|------------|----------------------------------------|
| [10.0.45 PQU-4 /10.0.2345.130](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule)| 7.0.7690.96   | PQU-4      | January 5, 2026 to February 8, 2026  |
| [10.0.44 PQU-7 / 10.0.2263.187](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule)| 7.0.7606.174   | PQU-7      | January 5, 2026 to February 8, 2026    |
| [10.0.43 PQU-9 / 10.0.2177.214](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule) | 7.0.7521.283   | PQU-9      | January 5, 2026 to February 8, 2026    |

For an Overview of role-based security, see [Role-based security](role-based-security.md).

To enable and use the **Duplicate with license filter** feature:
- Update your environment to the [latest Finance & Operations proactive quality update](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule) that includes this feature.
- Navigate to the **System administration → Security → Security Configuration**

For background on security concepts, see [Role-based security](role-based-security.md).

## How the duplicate license filter works

When you duplicate a role (or duty) with a selected license:

- Finance and Operations copies the security object.
- The system evaluates referenced objects (sub-roles, duties, privileges).
- Only references whose entitlements that are **fully** covered by the selected license are **included**.
- References that require entitlements **outside** the selected license (_including mixed-entitlement objects_) are **excluded** and included in an Excel **Excluded References** report.

> [!IMPORTANT]
> The feature does **not** deep-copy or create new duties or privileges. It re-uses existing security objects and reports what is **excluded**, which preserve alignment with out-of-box security functionality. 

## Use the Duplicate with license filter feature

:::image type="content" source="media/security-role-copy-with-license-filter-overview.png" alt-text="Overview of duplicating a security role with a license filter." lightbox="media/security-role-copy-with-license-filter-overview.png":::

Follow these steps to use the **Duplicate Security Role with License Filter** feature:

:::image type="content" source="media/security-role-copy-with-license-filter-overview.png" alt-text="Duplicate function overview" lightbox="media/security-role-copy-with-license-filter-overview.png":::

1. In Finance and Operations, go to **System administration → Security → Security Configuration**
3. Select the role (or duty) you want to duplicate.
4. Select **Duplicate**.
5. In the dialog, enter:
   - A **new name** for the copied security object (recommendation is to include the name of the license level in () e.g. _(Team Member)_)
   - Select a **licensing SKU** for the new security object (for example, Team Members, Operations - Activity)

:::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-1.png" alt-text="Duplicate dialog prompting for a new name and license." lightbox="media/security-role-copy-with-license-filter-detailed-step-series-1.png":::

6. If some references can’t be included, a warning appears indicating "**Some references were excluded**" for the duplicated role and license.
   - Select **Message details** to open a side pane showing the count of excluded references.
   - Download the excluded reference list to Excel for auditing and cleanup.

 :::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-2.png" alt-text="Some References were excluded." lightbox="media/security-role-copy-with-license-filter-detailed-step-series-2.png":::

7.	Review the list of duties and privileges that were **excluded** from the selected license. The report displays **excluded** objects that did not meet the license specified.

 :::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-3.png" alt-text="Excluded References from duplicated security role" lightbox="media/security-role-copy-with-license-filter-detailed-step-series-3.png":::

8.	Select **Publish selection** to publish the role and then **assign users** to the new security role to validate end-to-end user license requirements. 

 :::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-4.png" alt-text="Publish selection of duplicatd security role" lightbox="media/security-role-copy-with-license-filter-detailed-step-series-4.png":::

 ## Operational guidance and follow-up

 After duplication:

- Use the Excel **Excluded References** report to decide whether to:
  - Remove high-privilege duties from the intended "lower license" experience, or
  - Create separate roles aligned to higher license for users who need them.
- Plan a validation pass in a sandbox environment before applying role changes broadly in production.

## Important considerations
- Roles can only be duplicated within the same Finance & Operations environment.
- Duties and privileges are only included if **all** entitlements are compliant with the selected license.
- Duties or privileges containing mixed license entitlements will be **excluded** and listed in the Excel **Excluded References** report.
- The feature does not create or modify duties or privileges; it only reuses existing ones.
- Deep copying is avoided to maintain alignment with standard (out-of-box) functionality and upgrades.
- The feature does not support cross-environment or cross-tenant copying.

## Related information

- [Release schedule for proactive quality updates](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]