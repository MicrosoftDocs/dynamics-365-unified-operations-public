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

**Active Directory security group** is a legacy feature that enables assigning roles and organizations to users based on their Active Directory security groups memberships. For more details on Active Directory security groups, see [Active Directory security groups]{/windows-server/identity/ad-ds/manage/understand-security-groups). The feature also enables Just-In-time (JIT) provisioning of users when a user login in to the Finance and Operations environment for the first time.

Group based role assignments are applied in combination with manual and automatic rule based assignments for a user, and it is the union of assinged roles that determines the actual data access.

## Known limitations when using Active Directory security group

Before enabling the **Active Directory security groups** feature it is important to be aware of the known limitations. The limitations are mainly due to the fact the role assignment is resolved at log in, i.e. at runtime, and these roles assignments are not persisted by Finance and Operations apps. Several of the limitations impacts Internal control and auditing.

- Segregation of duty reporting will not consider these role assignments
- No database logging is possible for these role assignments
- Security and licensing reports do not include these role assignments
- Pages that show role assignments, e.g., the **Assign users to role** page and the **Roles for selected user** FactBox does not include these role assignments
- External users are not supported and will not be able to use JIT or be assigned any roles based on group memberships
- Workflows that are depending on assigned roles will not consider these role assignments
- Disabling a group in system administration will not stop JIT or roles assignment
- **User Id** for JIT created users are created with a leading $ sign and numbers

These known limitations are not expected to be addressed until the group experiences is unified with the more comprehensive feature in Dataverse, See [Manage group teams](/power-platform/admin/manage-group-teams.md).

## Enable Active Directory security group

The feature is enabled under **System administration > Setup > License configuration**. The **Active Directory security group** configuration key can be found in the *Administration** folder. Configuration keys can only be edited in maintenance mode, see [Maintenance mode](../sysadmin/maintenance-mode.md). 

## Import and configure Active Directory security groups

Once the feature is enabled a new **Groups** page will be available under **System administration > Users > Groups**. To start importing Azure Directory security groups, select the **Import groups** action menu and select the applicable groups to be imported. After the import is completed, you can maintain role and organization assignments in the similar way as in the **Users** page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
