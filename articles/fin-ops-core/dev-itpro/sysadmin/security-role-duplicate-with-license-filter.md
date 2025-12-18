---
title: Security Role Duplicate with license filter
description: The 'Duplicate Security Role / Duty with License Filter' feature in finance and operations apps helps administrators create compliant security roles and duties aligned with the selected license. This feature reduces the manual effort required to adjust security configurations and ensures that roles comply with Microsoft licensing policies.
author: ianceicys-msft
ms.author: ceian
ms.topic: article
ms.date: 12/18/2025
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

The **Duplicate with license filter** capability helps reduce that effort by duplicating a role (or duty) while **excluding** references that aren't fully entitled by the selected license. The result is a new security role you can publish and assign, along with an Excel **Excluded References** report for anything that was **excluded** for further auditing and analysis.

## Why this feature matters

Manually "right-sizing" a role to a license is time-consuming and error-prone. This feature provides:

- **Faster custom security role creation** by automatically filtering role references (subroles, duties, privileges) based on the selected license.
- **More predictable custom security role to license alignment** by excluding objects that require entitlements outside the chosen license.
- **Transparency for cleanup** via an Excel **Excluded References** report listing the excluded references.

 :::image type="content" source="media/security-role-copy-with-license-filter-duplicate-button.png" alt-text="Screenshot of Security Configuration with Duplicate function." lightbox="media/security-role-copy-with-license-filter-duplicate-button.png":::

> [!NOTE]
> This feature helps you build **license-aligned security configurations**, but it doesn't assign licenses or change license requirements. You remain responsible for ensuring that users are properly licensed according to [Microsoft Product Terms](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDynamics365Services/all). For more information, see [**Dynamics 365 Licensing Guide**](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409) and [**Dynamics 365 Licensing Deck**](https://go.microsoft.com/fwlink/?linkid=2279233).

## Who should use this feature

This feature is intended for:

- **Finance and operations apps administrators** who manage security roles and want to reduce the effort required to create license-aligned roles.
- **Licensing administrators and auditors** who validate that security configurations align with assigned licenses and internal policy.

## Prerequisites

Before you begin, verify that you:

- Have permissions to manage security in finance and operations apps (for example, **System administrator** or **Security administrator**).
- Know the **license** you want the duplicated security object to align with (for example, Commerce, Supply Chain Management, Team Members, Operations - Activity, and so on).

## Availability and setup

Microsoft delivers this feature through finance and operations apps servicing, including the latest Proactive Quality Updates. The schedule and build details for Proactive Quality Updates (PQU) are published close to each train start and can change. Microsoft typically publishes the detailed schedule for each PQU train and corresponding build information **five days before the train starts**. Standard servicing communications notify customers about these updates.

For the latest Proactive Quality Update (PQU) schedule, see:

- [Release schedule for proactive quality updates](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule)

The following table reflects the servicing trains, exact builds, rollout dates, and official PQU schedule page that includes the **Duplicate with license filter** functionality.

| Release        | Platform Release          | Build        | Proactive Quality Update Train Duration                     |
|----------------|----------------|------------|----------------------------------------|
| [10.0.45 PQU-4](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule)| 7.0.7690.96   | 10.0.2345.130     | January 5, 2026 to February 8, 2026  |
| [10.0.44 PQU-7](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule)| 7.0.7606.174   | 10.0.2263.187     | January 5, 2026 to February 8, 2026    |
| [10.0.43 PQU-9](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule) | 7.0.7521.283   | 10.0.2177.214    | January 5, 2026 to February 8, 2026    |

For an overview of role-based security, see [Role-based security](role-based-security.md).

To enable and use the **Duplicate with license filter** feature:

1. Update your environment to the [latest finance and operations apps proactive quality update](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule?context=%2Fdynamics365%2Fcontext%2Fcommerce#high-level-pqu-train-schedule) that includes this feature.
1. Go to **System administration → Security → Security Configuration**.

For background on security concepts, see [Role-based security](role-based-security.md).

## How the duplicate license filter works

When you duplicate a role or duty with a selected license:

- Finance and operations apps copy the security object.
- The system evaluates referenced objects, such as subroles, duties, and privileges.
- The system includes only references whose entitlements are **fully** covered by the selected license.
- The system excludes references that require entitlements **outside** the selected license, including mixed-entitlement objects. It includes these references in an Excel **Excluded References** report.

> [!IMPORTANT]
> This feature doesn't deep-copy or create new duties or privileges. It reuses existing security objects and reports what it **excluded**. This approach preserves alignment with out-of-box security functionality.

## Use the Duplicate with license filter feature

Follow these steps to use the **Duplicate Security Role with License Filter** feature:

:::image type="content" source="media/security-role-copy-with-license-filter-overview.png" alt-text="Screenshot of Duplicate function overview." lightbox="media/security-role-copy-with-license-filter-overview.png":::

1. In finance and operations apps, go to **System administration → Security → Security Configuration**.
1. Select the role (or duty) you want to duplicate.
1. Select **Duplicate**.
1. In the dialog, enter:
   - A **new name** for the copied security object. Include the name of the license in parentheses, for example _(Team Members)_.
   - Select a **licensing SKU** for the new security object, such as Team Members or Operations - Activity.

:::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-1.png" alt-text="Screenshot of Duplicate dialog prompting for a new name and license." lightbox="media/security-role-copy-with-license-filter-detailed-step-series-1.png":::

1. If the process can't include some references, a warning appears indicating "**Some references were excluded**" for the duplicated role and specified license.
   - Select **Message details** to open a side pane showing the count of excluded references.
   - Download the Excel Excluded Reference report for further auditing and analysis.

 :::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-2.png" alt-text="Screenshot of Some References were excluded." lightbox="media/security-role-copy-with-license-filter-detailed-step-series-2.png":::

1. Review the list of duties and privileges that the selected license **excluded**. The Excel report displays **excluded** objects that don't meet the specified license.

 :::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-3.png" alt-text="Screenshot of Excluded References from duplicated security role." lightbox="media/security-role-copy-with-license-filter-detailed-step-series-3.png":::

1. Select **Publish selection** to publish the role. Then, [**assign users to the new security role**](/dynamics365/fin-ops-core/fin-ops/sysadmin/assign-users-security-roles) to validate end-to-end user license requirements.

 :::image type="content" source="media/security-role-copy-with-license-filter-detailed-step-series-4.png" alt-text="Screenshot of Publish selection of duplicate security role." lightbox="media/security-role-copy-with-license-filter-detailed-step-series-4.png":::

## Operational guidance and follow-up

 After duplication:

- Use the Excel **Excluded References** report for further auditing and analysis:
  - Remove high-privilege duties from the intended "lower license" experience, or
  - Create separate roles aligned to higher license for users who need them.
- Plan a validation pass in a sandbox environment before applying role changes broadly in production.

## Important considerations

- You can only duplicate roles within the same finance and operations apps environment.
- Duties and privileges are included only if **all** entitlements comply with the selected license.
- The Excel **Excluded References** report lists duties or privileges containing mixed license entitlements, which are **excluded**.
- The feature doesn't create or modify duties or privileges; it only reuses existing ones.
- The feature avoids deep copying to maintain alignment with standard (out-of-box) functionality and upgrades.
- The feature doesn't support cross-environment or cross-tenant copying.

## Related information

- [Release schedule for proactive quality updates](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
