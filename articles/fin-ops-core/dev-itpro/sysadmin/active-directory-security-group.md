---
title: Entra ID security groups
description: Learn about the Microsoft Entra ID security groups feature, including an overview on known limitations when the Entra ID security groups feature is used.
author: pnghub
ms.author: jiwo
ms.topic: article
ms.date: 01/06/2025
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2022-11-10
ms.dyn365.ops.version: AX 7.0
---

# Microsoft Entra ID security groups

[!include [banner](../includes/banner.md)]

**Microsoft Entra ID security groups** is a legacy feature that enables roles and organizations to be assigned to users, based on their memberships in Microsoft Entra ID security groups. (For more information about Entra ID security groups, see [Entra ID security groups](/windows-server/identity/ad-ds/manage/understand-security-groups).) The feature also enables just-in-time (JIT) provisioning of users when they sign in to the finance and operations environment for the first time.

Group-based role assignments are applied by using manual and automatic rule-based assignments for a user. The union of assigned roles determines the actual data access.

## Known limitations when the Entra ID security groups feature is used

Before you enable the **Microsoft Entra ID security groups** feature, it's important that you are aware of the following known limitations. Several of the limitations affect internal control and auditing.

- No database logging can be done for these role assignments.
- Security and licensing reports don't include these role assignments.
- Segregation of duties engine is not compatible with these role assignments.
- Pages that show role assignments, the **Assign users to role** page, and the **Roles for selected user** FactBox don't include these role assignments.
- External users aren't supported. They can't use JIT provisioning, and no roles can be assigned to them based on group memberships.
- Workflows that depend on assigned roles don't consider these role assignments.
- Disabling a group in system administration doesn't stop JIT provisioning or role assignment.
- The **User Id** value of users that are created through JIT provisioning has a leading dollar sign ($) and numbers.
- Publishing views to security roles doesn't consider the role assignments made to Entra ID security groups. 
- Legal entity assignments are applied to the entire Entra ID security group.
- Starting with FR version 10.0.42, role and privilege assignments made through imported Entra ID security groups will no longer be supported in Financial Reporting (FR). User roles and privileges must be assigned directly to FnO user accounts for access to FR.

Microsoft doesn't expect to address these known limitations until the group experience is unified with the more comprehensive feature in Dataverse. For more information, see [Manage group teams](/power-platform/admin/manage-group-teams).

## Enable the Entra ID security groups feature

To enable the feature, go to **System administration \> Setup \> License configuration**. You can find the **Entra ID security group** configuration key in the **Administration** folder.

Configuration keys can be edited only in maintenance mode. For more information, see [Maintenance mode](../sysadmin/maintenance-mode.md).

## Import and configure Entra ID security groups

After the feature is enabled, a new **Groups** page is available at **System administration \> Users \> Groups**. To start to import Azure Directory security groups, select **Import groups**, and then select the groups to import.

After the import is completed, you can maintain role and organization assignments on the **Groups** page. The process resembles the process that's used on the **Users** page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
