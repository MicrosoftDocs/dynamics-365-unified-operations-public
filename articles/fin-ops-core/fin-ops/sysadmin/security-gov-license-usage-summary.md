---
title: User security governance license usage summary
description: Learn about the user security governance license usage summary report.
author: ceian  
ms.author: ceian
ms.topic: concept-article
ms.date: 12/29/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-09-02
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# Understand the User license summary in User security governance

[!INCLUDE[banner](../includes/banner.md)]

If you're unfamiliar with how Dynamics 365 licenses work or want to review the licensing model, see [Dynamics 365 Licensing Resources](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all) for the most up-to-date details on licensing.

The **User license summary** page in the **User security governance** workspace helps administrators understand how security roles and respective permissions define the license requirements across their Dynamics 365 finance and operations environment.

:::image type="content" source="media/security-governance-license-usage-summary-overview.png" alt-text="Screenshot of License Usage summary overview." lightbox="media/security-governance-license-usage-summary-overview.png":::

This page provides a telemetry-driven view of user activities and calculates the effective license requirements based on actual usage. By using this information, organizations can align licensing with Microsoft's current licensing guide.

## Availability

The User security governance feature and its related license usage summary tools are available in Dynamics 365 finance and operations version 10.0.44.

### Enable the workspace

Before you access the **User security governance** workspace, activate it in **Feature management**:

1. Go to **System administration > Feature management**.
1. Search for:
   - *User security governance*
   - *User security governance license usage summary report*
1. Select and enable both features.

:::image type="content" source="media/security-governance-license-usage-summary-feature-enable.png" alt-text="Screenshot of Security governance in the system admin user experience." lightbox="media/security-governance-license-usage-summary-feature-enable.png":::

### Access the workspace

To access the **User License Summary** page, follow these steps:

1. Sign in to Dynamics 365 finance and operations.
1. Go to **System administration > Security > Security Governance > License usage summary**.

## Workspace details

The User security governance license usage summary page provides a layered view of:

- How system permissions are exercised
- How responsibilities map to different role types

These details give you deeper visibility into user access patterns and help you make sure that roles align with intended responsibilities.

For a consolidated view across all environments within the same tenant, see the reports in the **Power Platform admin center**.

The workspace offers summaries across multiple dimensions:

- **User** - Individual usage patterns from telemetry
- **User Role License** - Role-to-license tier mapping
- **Role** - Aggregate role-level permissions
- **Duty** - Functional areas or grouped operations
- **Privilege** - Specific actions or menu items tied to user tasks

## Key attributes

Each securable object has these attributes:

- **License type** - Associated license level
- **Entitled** - Included in the mapped license scope
- **Not Entitled** - Not included in the mapped license (requires different license)
- **Not Required** - Actions or privilege inherited in system user, not included in license computation

These attributes simplify reviews and make sure that security access matches business needs.

## Detailed license contributors

The bottom panel shows license requirements for each securable object:

- **SecurableType** - Menu item display
- **AOT Name / Child Name** - From the application object tree
- **Access Level** - Read or write

### Example

:::image type="content" source="media/security-governance-license-usage-summary-example.png" alt-text="Screenshot of License Usage summary example." lightbox="media/security-governance-license-usage-summary-example.png":::

The user *Cade.Armanda.Olander* requires one **Finance** license:

| Role Name              | License                 | License Quantity | Notes |
|------------------------|-------------------------|------------------|-------|
| Accountant              | Finance                 | 1                | This security role has the highest priority license requirement |
| Retail Store Manager    | Operations - Activity   | 0                | No additional license requirement for this role, for this user, if the user is assigned a Finance license |
| System User             | None                    | 0                | No additional license requirement for this role, for this user, if the user is assigned a Finance license |

Select the **Role License** tab, and select **Accountant** role to inspect specific objects (*3362*) Entitled security objects contributing to the requirement of a **Finance** license. For more detailed analysis, select **Open in Microsoft Office** to download a detailed view in Excel.

**Role License** tab:

| SKU Name | Securable Object Count | Entitlement | Notes |
|----------|------------------------|--------------------|-------|
| Finance  | 3,362                  | **Entitled** | Included in the mapped license scope |
| Finance  | 1,557                  | **Not Entitled** | Not included in the mapped license (requires different license) |

:::image type="content" source="media/security-governance-license-usage-summary-example-role-license.png" alt-text="Screenshot of License Usage Summary Role License detailed." lightbox="media/security-governance-license-usage-summary-example-role-license.png":::

>[!Tip]
> To see which permissions are excluded when evaluating license requirements, duplicate the security role or duty by using the [Duplicate a security role or duty with a license filter](/dynamics365/fin-ops-core/dev-itpro/sysadmin/security-role-duplicate-with-license-filter) feature.

>[!Tip]
>You can also use [Security analysis](/dynamics365/fin-ops-core/fin-ops/sysadmin/security-reports) to find where specific privileged entry points are introduced into roles, and Security configuration to adjust security roles.

### Use cases

Organizations can use this summary to:

- Validate that security roles match actual user responsibilities.  
- Find and fix role assignments that are excessive or outdated.  
- Improve governance by aligning usage with internal controls.  
- Get ready for future compliance and audits.  

Administrators can use this page to:

- Evaluate roles for review or refinement.  
- Identify segregation of duties risks.
- Export data for audit, license planning, or governance.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
