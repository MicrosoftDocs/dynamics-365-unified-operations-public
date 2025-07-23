---
title: User security governance license usage summary
description: Learn about user security governance license usage summary report
author: ceian
ms.author: ceian
ms.topic: concept-article
ms.date: 07/25/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-07-25
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# Understand the User License Summary (Preview) in User Security Governance

If you're unfamiliar with how Dynamics 365 licenses work or want to review the licensing model, please visit the official [Dynamics 365 Licensing Resources](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all) for the most up-to-date details on licensing.

The **User License Summary** page in the **User Security Governance (USG)** workspace helps administrators understand how security roles and respective permissions define the license requirements across their Dynamics 365 Finance and Operations environment.

:::image type="content" source="security-governance-sysadmin-license-usage-summary-overview.png" alt-text="License Usage summary overview." lightbox="media/security-governance-sysadmin-license-usage-summary-overview.png":::

This form provides a telemetry-driven view of user activities and calculates the effective license requirements based on actual usage—enabling organizations to align licensing with Microsoft’s current licensing guide.

> ⚠️ **Note**: The User License Summary is currently available in **preview**. Functionality and layout may change before general availability.

## Availability

The User Security Governance feature and its related license usage summary tools will start being available in version **10.0.44** of Dynamics 365 Finance and Operations apps.

### Enabling USG

Before accessing the USG workspace, you must activate it in **Feature Management**:

1. Go to **System administration > Feature management**
2. Search for:
   - *User security governance*
   - *User security governance license usage summary report*
3. Select and enable both features.

:::image type="content" source="media/security-governance-sysadmin-license-usage-summary-feature-enable.png" alt-text="Security governance in the system admin user experience." lightbox="media/security-governance-sysadmin-license-usage-summary-feature-enable.png":::

### Navigation

To access the **User License Summary** form:

1. Sign in to your Dynamics 365 Finance and Operations environment.
2. Navigate to:  
   **System administration > Security > Security Governance > License usage summary**

---

## What Does This Form Show?

The User Security Governance (USG) reports provide a layered view of:

- How system permissions are exercised
- Which responsibilities map to different role types

This enables deeper visibility into user access patterns and ensures that roles align with intended responsibilities.

> For a consolidated view across all environments within the same tenant, refer to the reports in the **Power Platform Admin Center**.

The report offers summaries across multiple dimensions:

- **User**: Individual usage patterns from telemetry
- **User Role License**: Role-to-license tier mapping
- **Role**: Aggregate role-level permissions
- **Duty**: Functional areas or grouped operations
- **Privilege**: Specific actions/menu items tied to user tasks

---

## Key Attributes to Understand

Each **securable object** is tagged with:

- **License type**: Associated license level
- **Entitled**: Included in the current license’s scope
- **Not Entitled**: Not included in the mapped license
- **Not Required**: Doesn’t affect license assessment (e.g., system functions)

These simplify reviews and help ensure that security access matches business needs.

---

## Detailed License Contributors

The **bottom panel** breaks down license requirements at the securable object level:

- **SecurableType** (e.g., Menu item display)
- **AOT Name / Child Name**: From Application Object Tree
- **Access Level** (e.g., Read, Write)

### Example:

- The user *Cassie* requires:
  - Finance (Base)
  - Project Operations (Attach)
  - SCM (Attach)

- In the **SKU Name** column:
  - 3,574 securable objects are entitled by the Finance license
  - 192 are satisfied in a different license

Use the bottom panel to inspect specific objects and identify contributors to higher-tier licenses.

---

## Use Cases

Organizations can use this summary to:

- Validate that security roles reflect actual user responsibilities  
- Identify and remediate excessive or outdated role assignments  
- Improve governance by aligning usage with internal controls  
- Prepare for future compliance and audits  

---

## Next Steps

From this form, administrators can:

- Evaluate roles for review or refinement  
- Identify Segregation of Duties (SoD) risks  
- Export data for audit, license planning, or governance  

> **Tip**: Each panel's data can be exported to Excel to support compliance or reporting needs.
