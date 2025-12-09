---
title: Manage device based user access to finance and operations apps
description: Learn how to manage device-based user access for finance and operations apps. Discover steps to assign roles and ensure compliance with licensing requirements.
author: aneesa
ms.author: aneesa
ms.topic: how-to
ms.date: 12/09/2025
ms.custom:
  - bap-template
ms.reviewer: johnmichalak
audience: System Administrator 
ms.search.region: Global
ms.search.validFrom: 2025-11-20
ms.dyn365.ops.version: Version 7.0.0 
---

# Manage device based user access to finance and operations apps

[!INCLUDE[banner](../includes/banner.md)]

With [improved user license management and validation](https://www.microsoft.com/dynamics-365/blog/it-professional/2025/09/25/simplifying-license-management-dynamics-365-finance-operations/),
administrators can now use [enhanced tools and reporting](security-gov-overview.md) to optimize access and licensing within finance and operations apps. As a part of this change, users without assigned licenses can no longer access finance and operations apps.

While most users require user licenses as a part of their job functions, a small subset of users might need to access finance and operations apps by using licensed devices instead.

| Job function | Job function requirements |
|--- | --- |
| Production floor worker | Production floor worker who needs to access Dynamics 365 Supply Chain Management functionality beyond the [production floor execution interface](../../../supply-chain/production-control/production-floor-execution-configure.md). |
| Retail store manager | Retail store manager who needs to access Dynamics 365 Commerce functionality beyond the [point-of-sale (POS) app](../../../commerce/dev-itpro/store-commerce.md). |
| Warehouse worker | Warehouse worker who needs to access Dynamics 365 Supply Chain Management functionality beyond the [warehouse management app](../../../supply-chain/warehousing/install-configure-warehouse-management-app.md). |

To ensure continued access for users who rely solely on licensed devices to access finance and operations apps, administrators must temporarily assign device-based security roles until device license validation takes effect at a later date.

The following table lists the device-based security roles that you can assign for each corresponding job function.

| Job function | Device-based security role |
|--- | --- |
| Production floor worker | Device-based - Production floor worker |
| Retail store manager | Device-based - Retail store manager |
| Warehouse worker | Device-based - Warehouse worker |

## Requirements for using device based security roles

Before assigning device based security roles to users, ensure that the following requirements are met.

| Requirement | Description |
|--- | --- |
| Use device based security roles only for users in specific job functions and with specific requirements. | <ul><li>Production floor worker who needs to access Dynamics 365 Supply Chain Management functionality beyond the [production floor execution interface](../../../supply-chain/production-control/production-floor-execution-configure.md).</li><ul><li>If the functionality in the production floor execution interface is sufficient for the production floor worker to perform their job, they don't need this role.</li></ul><li>Retail store manager who needs to access Dynamics 365 Commerce functionality beyond the [point-of-sale (POS) app](../../../commerce/dev-itpro/store-commerce.md).</li><ul><li>If the functionality in the point-of-sale app is sufficient for the retail store manager to perform their job, they don't need this role.</li></ul><li>Warehouse worker who needs to access Dynamics 365 Supply Chain Management functionality beyond the [warehouse management app](../../../supply-chain/warehousing/install-configure-warehouse-management-app.md).</li><ul><li>If the functionality in the warehouse management app is sufficient for the warehouse worker to perform their job, they don't need this role.</li></ul></ul> |
| Use device based security roles only for users who don't otherwise require a user license. | <ul><li>Any production floor workers, retail store managers, or warehouse workers who require and are assigned to a user license already have continued access and don't need the device based security role assignment.</li></ul> |
| Ensure users with device based security roles have scoped access. | <ul><li>All production floor workers, retail store managers, or warehouse workers who are assigned device based security roles must not access functionality beyond the scope of their respective job function as defined in the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544). |

In addition to the preceding requirements:

- **Device based security roles are temporary**
  - Device based security roles enable access until device license validation takes effect at a later date.
  - When device license validation takes effect, Microsoft validates that the access comes from a licensed device. These roles are then deprecated, and eventually removed.
- **Monitoring is in effect to detect misuse**
  - Microsoft monitors the assignment of device based security roles and users that use them to ensure that the licensing requirements outlined in the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544) are met.  
  - If any misuse is detected, organizations are notified to gather additional information and/or to acquire the appropriate licenses for continued access.

## Manage users with device based security roles

The following steps outline how administrators can add or remove users from device based security roles.

### Add users to device based security roles

To add users to device based security roles, follow these steps:

1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
1. In the tree, select one of the device based security roles: **Device based - Production floor worker, Device based - Retail store manager, or Device based - Warehouse worker**.
1. In the **Users assigned to role** section, select **Manually assign/exclude users**.
1. In the **Assign users to or exclude users from role** form, select the users to assign the role.
1. In the **Action pane**, select **Assign to role**.

### Remove users from device based security roles

To remove users from device based security roles, follow these steps:

1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
1. In the tree, select one of the device based security roles: **Device based - Production floor worker, Device based - Retail store manager, or Device based - Warehouse worker**.
1. To remove a single user
   1. In the **Users assigned to role** section, select the user that you want to remove.
   1. Select **Remove**.
1. To remove multiple users
   1. In the **Users assigned to role** section, select **Manually assign/exclude users**.
   1. In the **Assign users to or exclude users from role** form, select users that you want to remove from the role.
   1. In the **Action pane**, select **Exclude from role**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]