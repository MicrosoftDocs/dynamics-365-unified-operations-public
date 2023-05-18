---
title: Active Directory security groups
description: This article provides information about the Active Directory security groups feature.
author: peakerbl
ms.date: 05/18/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: peakerbl
ms.search.validFrom: 2022-11-10
ms.dyn365.ops.version: AX 7.0
---

# Active Directory security groups

[!include [banner](../includes/banner.md)]

**Active Directory security groups** is a legacy feature that enables roles and organizations to be assigned to users, based on their memberships in Microsoft Active Directory security groups. (For more information about Active Directory security groups, see [Active Directory security groups](/windows-server/identity/ad-ds/manage/understand-security-groups).) The feature also enables just-in-time (JIT) provisioning of users when they sign in to the finance and operations environment for the first time.

Group-based role assignments are applied by using manual and automatic rule-based assignments for a user. The union of assigned roles determines the actual data access.

## Known limitations when the Active Directory security groups feature is used

Before you enable the **Active Directory security groups** feature, it's important that you are aware of the following known limitations. Several of the limitations affect internal control and auditing.

- Segregation of duty reporting doesn't consider these role assignments.
- No database logging can be done for these role assignments.
- Security and licensing reports don't include these role assignments.
- Pages that show role assignments, the **Assign users to role** page, and the **Roles for selected user** FactBox don't include these role assignments.
- External users aren't supported. They can't use JIT provisioning, and no roles can be assigned to them based on group memberships.
- Workflows that depend on assigned roles don't consider these role assignments.
- Disabling a group in system administration doesn't stop JIT provisioning or role assignment.
- The **User Id** value of users that are created through JIT provisioning has a leading dollar sign ($) and numbers.
- Publishing views to security roles doesn't consider the role assignments made to Active directory security groups. 
- Legal entity assignments are applied to the entire Active directory security group. 

Microsoft doesn't expect to address these known limitations until the group experience is unified with the more comprehensive feature in Dataverse. For more information, see [Manage group teams](/power-platform/admin/manage-group-teams).

## Enable the Active Directory security groups feature

To enable the feature, go to **System administration \> Setup \> License configuration**. You can find the **Active Directory security group** configuration key in the **Administration** folder.

Configuration keys can be edited only in maintenance mode. For more information, see [Maintenance mode](../sysadmin/maintenance-mode.md).

## Import and configure Active Directory security groups

After the feature is enabled, a new **Groups** page is available at **System administration \> Users \> Groups**. To start to import Azure Directory security groups, select **Import groups**, and then select the groups to import.

After the import is completed, you can maintain role and organization assignments on the **Groups** page. The process resembles the process that's used on the **Users** page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
