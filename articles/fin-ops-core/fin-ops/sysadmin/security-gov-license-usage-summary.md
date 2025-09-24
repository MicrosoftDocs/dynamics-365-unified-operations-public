---
title: User security governance license usage summary
description: Learn about the user security governance license usage summary report.
author: ceian  
ms.author: ceian
ms.topic: concept-article
ms.date: 09/02/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-09-02
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# Understand the User license summary in User security governance


If you're unfamiliar with how Dynamics 365 licenses work or want to review the licensing model, see [Dynamics 365 Licensing Resources](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all) for the most up-to-date details on licensing.


The **User license summary** page in the **User security governance** workspace helps administrators understand how security roles and respective permissions define the license requirements across their Dynamics 365 finance and operations environment.

:::image type="content" source="media/security-governance-license-usage-summary-overview.png" alt-text="License Usage summary overview." lightbox="media/security-governance-license-usage-summary-overview.png":::

This page provides a telemetry-driven view of user activities and calculates the effective license requirements based on actual usage—enabling organizations to align licensing with Microsoft’s current licensing guide.


## Availability

The User security governance feature and its related license usage summary tools are available in Dynamics 365 finance and operations version 10.0.44.

### Enable the workspace

Before you access the **User security governance** workspace, you must activate it in **Feature management**:

1. Go to **System administration > Feature management**.
1. Search for:
   - *User security governance*
   - *User security governance license usage summary report*
1. Select and enable both features.

:::image type="content" source="media/security-governance-license-usage-summary-feature-enable.png" alt-text="Security governance in the system admin user experience." lightbox="media/security-governance-license-usage-summary-feature-enable.png":::

### Access the workspace

To access the **User License Summary** page, follow these steps:

1. Sign in to Dynamics 365 finance and operations.
2. Go to **System administration > Security > Security Governance > License usage summary**.

## Workspace details

The User security governance license usage summary page provides a layered view of:
- How system permissions are exercised
- How responsibilities map to different role types

These details enable deeper visibility into user access patterns and ensure that roles align with intended responsibilities.

For a consolidated view across all environments within the same tenant, see the reports in the **Power Platform admin center**.

The workspace offers summaries across multiple dimensions:
- **User** - Individual usage patterns from telemetry
- **User Role License** - Role-to-license tier mapping
- **Role** - Aggregate role-level permissions
- **Duty** - Functional areas or grouped operations
- **Privilege** - Specific actions or menu items tied to user tasks

## Key attributes 

Each securable object is tagged with:
- **License type** - Associated license level
- **Entitled** - Included in the scope of the current license
- **Not Entitled** - Not included in the mapped license
- **Not Required** - Doesn’t affect license assessment 

These attributes simplify reviews and ensure that security access matches business needs.

## Detailed license contributors

The bottom panel breaks down license requirements at the securable object level:
- **SecurableType** - Menu item display
- **AOT Name / Child Name** - From the application object tree
- **Access Level** - Read or write

### Example

:::image type="content" source="media/security-governance-license-usage-summary-example.png" alt-text="License Usage summary example." lightbox="media/security-governance-license-usage-summary-example.png":::

- The user *Cassie* requires:
  - Finance (Base)
  - Project Operations (Attach)
  - SCM (Attach)

- In the **SKU Name** column:
  - 3,574 securable objects are entitled by the Finance license
  - 192 are satisfied in a different license

Use the bottom panel to inspect specific objects and identify contributors to higher-tier licenses.

### Use cases

Organizations can use this summary to:
- Validate that security roles reflect actual user responsibilities.  
- Identify and remediate excessive or outdated role assignments.  
- Improve governance by aligning usage with internal controls.  
- Prepare for future compliance and audits.  

From this page, administrators can:
- Evaluate roles for review or refinement.  
- Identify segregation of duties risks.
- Export data for audit, license planning, or governance.  

>[!Tip]
> You can export the data on each panel to Excel to support compliance or reporting needs.
