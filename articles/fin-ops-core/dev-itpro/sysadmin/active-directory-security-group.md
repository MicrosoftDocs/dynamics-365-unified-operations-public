---
title: Active Directory security groups
description: This article provides information about the Active Directory security groups feature.
author: peakerbl
ms.date: 11/10/2022
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

# Active Directory security group

[!include [banner](../includes/banner.md)]

**Active Directory security group** is a legacy feature that enables assigning roles and organizations to users based on their Active Directory security groups memberships. For more details on Active directory security groups, see [Active directory security groups](/windows-server/identity/ad-ds/manage/understand-security-groups). The feature also enables Just-In-time (JIT) provisioning of users when a user logins into the finance and operations environment for the first time.

Group based role assignments are applied with manual and automatic rule based assignments for a user. The union of assigned roles that determines the actual data access.

## Known limitations when using Active Directory security group

Before enabling the **Active Directory security groups** feature, it's important to be aware of the known limitations. The limitations are because the role assignment is resolved at login and these roles assignments aren't persisted by finance and operations apps. Several of the limitations impact internal control and auditing.

- Segregation of duty reporting won't consider these role assignments
- No database logging is possible for these role assignments
- Security and licensing reports don't include these role assignments
- Pages that show role assignments, the **Assign users to role** page and the **Roles for selected user** FactBox doesn't include these role assignments
- External users aren't supported and won't be able to use JIT or be assigned any roles based on group memberships
- Workflows that are depending on assigned roles won't consider these role assignments
- Disabling a group in system administration won't stop JIT or roles assignment
- **User Id** for JIT created users are created with a leading $ sign and numbers

These known limitations aren't expected to be addressed until the group experiences is unified with the more comprehensive feature in Dataverse. For more information, see [Manage group teams](/power-platform/admin/manage-group-teams.md).

## Enable Active Directory security group

The feature is enabled under **System administration > Setup > License configuration**. The **Active Directory security group** configuration key can be found in the **Administration** folder. Configuration keys can only be edited in maintenance mode, see [Maintenance mode](../sysadmin/maintenance-mode.md). 

## Import and configure Active Directory security groups

Once the feature is enabled, a new **Groups** page is available **System administration > Users > Groups**. To start importing Azure Directory security groups, select **Import groups** and the applicable groups to be imported. After the import is completed, you can maintain role and organization assignments in the similar way as in the **Users** page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
