--- 
title: Manage device based user access to Dynamics 365 Finance and Operations applications
description: Learn how to manage users who need to access Dynamics 365 Finance and Operations applications using licensed devices.
author: aneesa
ms.author: aneesa
ms.topic: how-to
ms.date: 11/20/2025
ms.custom:
ms.reviewer: johnmichalak  
audience: System Administrator 
ms.search.region: Global
ms.search.validFrom: 2025-11-20
ms.dyn365.ops.version: Version 7.0.0 
---

# Manage device based user access to Dynamics 365 Finance and Operations applications

With [improved user license management and validation](https://www.microsoft.com/dynamics-365/blog/it-professional/2025/09/25/simplifying-license-management-dynamics-365-finance-operations/) 
administrators can now use [enhanced tools and reporting]*TODO: ADD LINK* to optimize access and licensing within Dynamics 365 Finance and Operations applications. As a part of this change users without assigned licenses will no longer be able access to Dynamics 365 Finance and Operations applications.

While the vast majority of users require user licenses as a part of their job functions, there is a small subset of users that may need to access Dynamics 365 Finance and Operations applications using licensed devices instead.

| Job function | Job function requirements |
|--- | --- |
| Production floor worker | Production floor worker who needs to access Dynamics 365 Supply Chain Management functionality beyond the [production floor execution interface](../../../supply-chain/production-control/production-floor-execution-configure.md). |
| Retail store manager | Retail store manager who needs to access Dynamics 365 Commerce functionality beyond the [point-of-sale (POS) app](../../../commerce/dev-itpro/store-commerce.md). |
| Warehouse worker | Warehouse worker who needs to access Dynamics 365 Supply Chain Management functionality beyond the [warehouse management app](../../../supply-chain/warehousing/install-configure-warehouse-management-app.md). |

To ensure continued access for users who rely solely on licensed devices to access Dynamics 365 Finance and Operations applications, administrators must temporarily assign device based security roles until device license enforcement takes effect at a later date. 

The table below lists the device based security roles that can be assigned for each corresponding job function.

| Job function | Device based security role |
|--- | --- |
| Production floor worker | Device based - Production floor worker |
| Retail store manager | Device based - Retail store manager |
| Warehouse worker | Device based - Warehouse worker |

## Requirements for using device based security roles
Before assigning device based security roles to users administrators must ensure that the following requirements are met.

| Requirement | Description |
|--- | --- |
| Device based security roles must be used only for users in specific job functions and with specific requirements | <ul><li>Production floor worker who needs to access Dynamics 365 Supply Chain Management functionality beyond the [production floor execution interface](../../../supply-chain/production-control/production-floor-execution-configure.md).</li><ul><li>If the functionality in the production floor execution interface is sufficient for the production floor worker to perform their job, they do not need this role.</li></ul><li>Retail store manager who needs to access Dynamics 365 Commerce functionality beyond the [point-of-sale (POS) app](../../../commerce/dev-itpro/store-commerce.md).</li><ul><li>If the functionality in the point-of-sale app is sufficient for the retail store manager to perform their job, they do not need this role.</li></ul><li>Warehouse worker who needs to access Dynamics 365 Supply Chain Management functionality beyond the [warehouse management app](../../../supply-chain/warehousing/install-configure-warehouse-management-app.md).</li><ul><li>If the functionality in the warehouse management app is sufficient for the warehouse worker to perform their job, they do not need this role.</li></ul></ul> |
| Device based security roles must be used only for users who would not otherwise require a user license | <ul><li>Any production floor workers, retail store managers, or warehouse workers who require and will be assigned a user license will already have continued access and do not need the device based security role assignment.</li></ul> |
| Users with device based security roles must ensure scoped access | <ul><li>All production floor workers, retail store managers, or warehouse workers who are assigned device based security roles must not access functionality beyond the scope of their respective job function as defined in the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544). |

In addition to the above requirements, administrators should also be aware that
- **Device based security roles are temporary**
  - Device based security roles are meant to enable access until device license enforcement takes effect at a later date.
  - When device license enforcement takes effect Microsoft will validate that the access is coming from a licensed device. These roles will then be deprecated, and eventually removed.
- **Monitoring will be in effect to detect misuse**
  - Microsoft will be monitoring the assignment of device based security roles and users that are using them to ensure that the licensing requirements as outlined in the [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544) are met.  
  - If any misuse is detected, organizations will be notified to gather additional information and/or to acquire the appropriate licenses for continued access.

## Manage users with device based security roles
The steps below outline how administrators can add or remove users from device based security roles.

### Add users to device based security roles
1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
2. In the tree, select one of the device based security roles: **Device based - Production floor worker, Device based - Retail store manager, or Device based - Warehouse worker**.
3. In the **Users assigned to role** section, select **Manually assign/exclude users**.
4. In the **Assign users to or exclude users from role** form, select one or more users that should be assigned the role.
5. In the **Action pane**, select **Assign to role**.

### Remove users from device based security roles
1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
2. In the tree, select one of the device based security roles: **Device based - Production floor worker, Device based - Retail store manager, or Device based - Warehouse worker**.
3. To remove a single user
   1. In the **Users assigned to role** section, select the user that should be removed.
   2. Select **Remove**.
4. To remove multiple users
   1. In the **Users assigned to role** section, select **Manually assign/exclude users**.
   2. In the **Assign users to or exclude users from role** form , select users that should be removed from the role.
   3. In the **Action pane**, select **Exclude from role**.
