---
title: Stay compliant with user licensing requirements
description: Learn about how you can stay compliant with the user licensing requirements for finance and operations apps per role.
author: ianceicys-msft
ms.author: ceian
ms.topic: how-to
ms.date: 01/02/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2018-05-30
ms.dyn365.ops.version: AX 7.0
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Stay compliant with user licensing requirements

[!include [banner](../includes/banner.md)]

This article provides an overview of how you can stay compliant with the user licensing requirements for finance and operations apps. These apps include Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Commerce.

The security roles that you assign to enabled users determine the licensing requirements for users. Developers build security roles based on a hierarchy of the following elements:

- Subroles
- Duties
- Privileges
- Directly referenced securable objects

For more information, see [Role-based security](./role-based-security.md).

You determine the licensing requirements for users at the organization or tenant level. This article focuses on the requirements for a single environment. If you have multiple environments, you must analyze the requirements across all of them.

You assign a licensing requirement to every securable object or resource that's included in a user role.

The rest of this article describes the different tools that you can use to ensure that the actual licensing complies with the expected licensing requirements. The first thing to verify is that the user roles have the expected licensing requirements and are assigned to the appropriate users.

For more information about security role to duty and privilege mapping that aligns to Microsoft’s licensing policy and to understand the licenses you need, see [User Security Governance](/dynamics365/fin-ops-core/fin-ops/sysadmin/security-gov-overview).

## Available and assigned licenses

You can view available and assigned licenses under **Licenses** in the [Microsoft 365 admin center](https://admin.cloud.microsoft/).

:::image type="content" source="media/M365-admin-center.png" alt-text="Screenshot of Licenses screen showing available licenses and assigned licenses." lightbox="media/M365-admin-center.png":::

## Assign licenses to users

Customers must acquire and assign appropriate subscription licenses for their users in the [Microsoft 365 admin center](https://admin.cloud.microsoft/), following Microsoft's [product terms](https://go.microsoft.com/fwlink/?linkid=2339737). 

### Option 1 - Assign a license to an individual user

Go to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).

Sign in as a **Global admin** or **License admin**.

1. In the left navigation, select [Users → Active users](https://admin.cloud.microsoft/#/users).

1. Select the user's name.

1. Select **Licenses and apps**.

1. Toggle on the license you want.

Example: **Dynamics 365 Commerce**, **Dynamics 365 Finance**, **Dynamics 365 Supply Chain Management**, **Dynamics 365 Team Members**, and more.

:::image type="content" source="media/stay-compliant-assign-user-license.png" alt-text="Screenshot of assigning a license to a user." lightbox="media/stay-compliant-assign-user-license.png":::

> [!NOTE]
> The license applies after a short propagation delay of up to one hour.

> [!NOTE]
> Follow base-then-attach sequencing. For example, assign **Dynamics 365 Finance** first.
>
> Then assign the specific attach license with **Attach to Qualifying Dynamics 365 Base Offer** if the user needs both.

> [!TIP]
> If the user still can't sign in, check these three things:
> 1. **The user signed in before the license finished propagating (less than one hour).**
> 1. **The user doesn't have the right security role assigned in Dynamics.**
> 1. **The user is missing a required attach license.**

### Option 2 - Assign licenses using groups

Go to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).

Sign in as a **Global admin** or **License admin**.

1. In the [Microsoft 365 admin center](https://admin.cloud.microsoft.com/), go to [Teams & groups → Active teams & groups](https://admin.cloud.microsoft.com/?#/groups).

1. Go to [Security Groups](https://admin.cloud.microsoft.com/?#/groups/_/CombinedSecurityGroup).

1. Open the security group.

1. Go to **Licenses and apps**.

1. Assign the license to the security group.

Example: **Dynamics 365 Commerce**, **Dynamics 365 Finance**, **Dynamics 365 Supply Chain Management**, **Dynamics 365 Team Members**, and more.

:::image type="content" source="media/stay-compliant-assign-license-to-group.png" alt-text="Screenshot of assigning a license to group." lightbox="media/stay-compliant-assign-license-to-group.png":::

> [!NOTE]
> The license applies after a short propagation delay of up to one hour.

> [!NOTE]
> Follow base-then-attach sequencing. For example, give **Dynamics 365 Finance** first.
>
> Then assign the specific attach license with **Attach to Qualifying Dynamics 365 Base Offer** if the group needs both.

> [!NOTE]
> Assigning a license:
>
> ✅ **Allows the user to legally access the product**
>
> ❌ **Doesn't grant permissions inside Dynamics**
>
> **You still must:**
> **[Assign security roles to the user or group in Dynamics 365](/dynamics365/fin-ops-core/fin-ops/sysadmin/assign-users-security-roles)**

## License requirement per role

The **Assign roles to user** dialog box, which you open from **System Administration** \> **Security** \> **Users**, helps you understand the impact on user licensing when you assign roles. It also provides an overview of the licensing requirements for each role. You can use the dialog box itself or export data to Excel for further analysis. Custom roles can require licenses for more than one application.

If a role has unexpected licensing requirements, use the **User Security Governance** workspace to understand what security roles and respective permissions drive the requirements.

## Licensing requirements by using User Security Governance

Use the **User license summary** page in the **User security governance** workspace to understand how security roles and respective permissions define the license requirements across your Dynamics 365 finance and operations environment.

:::image type="content" source="../sysadmin/media/security-governance-license-usage-summary-overview.png" alt-text="Screenshot of License Usage summary overview." lightbox="../sysadmin/media/security-governance-license-usage-summary-overview.png":::

To access the **User License Summary** page, follow these steps:

1. Sign in to finance and operations apps.
1. Go to **System administration > Security > Security Governance > License usage summary**.

The User security governance license usage summary page provides a layered view of:

- How system permissions are exercised
- How responsibilities map to different role types

These details give you deeper visibility into user access patterns and ensure that roles align with intended responsibilities.

## Users per role

Use the **System Administration** \> **Security** \> **Assign users to role** page to view all users who are assigned a specific role.

:::image type="content" source="../sysadmin/media/Assign-users-to-roles.png" alt-text="Screenshot of Assign users to role page.":::

## Enabled users

For internal security and to help avoid licensing requirements for users who leave or aren't actively using the finance and operations apps, disable those users on the **Users** page.

> [!NOTE]
> The System Administrator role is a special role in finance and operations apps that grants users full access to manage system artifacts. Other roles can't restrict or modify users assigned to this role. Users with this role are exempt from licensing requirements. This exemption means that individuals with this role don't need to purchase more licenses to configure and administer Dynamics 365 applications.

## Audit and monitor

Regularly audit your current security settings and monitor the system after an update to ensure compliance with the licensing requirements.

## Related information

For information about how to buy and license finance and operations apps, see [Microsoft Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

For information about how to assign licenses to users in the Microsoft 365 admin center, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).

More user licenses are required when multiple implementation projects exist for the same tenant. For more information, see [Multiple Lifecycle Services projects and production environments on one Microsoft Entra tenant](../../fin-ops/get-started/implement-multiple-projects-aad-tenant.md#licensing-requirements).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
