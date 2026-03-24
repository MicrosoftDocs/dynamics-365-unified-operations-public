---
title: Entra ID security groups
description: Learn about the Microsoft Entra ID security groups feature, including an overview on known limitations when the Entra ID security groups feature is used.
author: pnghub
ms.author: jiwo
ms.topic: article
ms.date: 03/24/2026
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2022-11-10
ms.dyn365.ops.version: AX 7.0
---

# Microsoft Entra ID security groups

[!include [banner](../includes/banner.md)]

**Microsoft Entra ID security groups** is a legacy feature that organizations use to assign roles and organizations to users based on their memberships in Microsoft Entra ID security groups. Learn more about Microsoft Entra ID security groups in [Microsoft Entra ID security groups](/windows-server/identity/ad-ds/manage/understand-security-groups). The feature also enables just-in-time (JIT) provisioning of users when they sign in to the finance and operations environment for the first time.

You apply group-based role assignments by using manual and automatic rule-based assignments for a user. The union of assigned roles determines the actual data access.

## Known limitations when you use the Microsoft Entra ID security groups feature

Before you enable the **Microsoft Entra ID security groups** feature, be aware of the following known limitations. Several of the limitations affect internal control and auditing.

- You can't do database logging for these role assignments.
- Security and licensing reports don't include these role assignments.
- Segregation of duties engine isn't compatible with these role assignments.
- Pages that show role assignments, the **Assign users to role** page and the **Roles for selected user** FactBox, don't include these role assignments.
- The feature doesn't support external users. They can't use JIT provisioning, and you can't assign roles to them based on group memberships.
- Workflows that depend on assigned roles don't consider these role assignments.
- Disabling a group in system administration doesn't stop JIT provisioning or role assignment.
- The **User Id** value of users that you create through JIT provisioning has a leading dollar sign ($) and numbers.
- Publishing views to security roles doesn't consider the role assignments made to Microsoft Entra ID security groups.
- You apply legal entity assignments to the entire Microsoft Entra ID security group.
- Starting with FR version 10.0.42, Financial Reporting (FR) no longer supports role and privilege assignments made through imported Microsoft Entra ID security groups. You must assign user roles and privileges directly to FnO user accounts for access to FR.

Microsoft doesn't expect to address these known limitations until the group experience is unified with the more comprehensive feature in Dataverse. Learn more in [Manage group teams](/power-platform/admin/manage-group-teams).

## Enable the Microsoft Entra ID security groups feature

To enable the feature, go to **System administration \> Setup \> License configuration**. You can find the **Microsoft Entra ID security group** configuration key in the **Administration** folder.

You can edit configuration keys only in maintenance mode. Lern more in [Maintenance mode](../sysadmin/maintenance-mode.md).

## Import and configure Microsoft Entra ID security groups

After you enable the feature, a new **Groups** page is available at **System administration \> Users \> Groups**. To start importing Microsoft Entra ID security groups, select **Import groups**, and then select the groups to import.

After the import finishes, you can maintain role and organization assignments on the **Groups** page. This process resembles the process that's used on the **Users** page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
