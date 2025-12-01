--- 
title: Manage F&O access for device-based users
description: Learn how to manage users who access Dynamics 365 Finance and Operations applications using licensed devices.
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

# Manage Dynamics 365 Finance and Operations applications access for device-based users

With improved license management and validation users without assigned licenses will no longer have access to Dynamics 365 Finance and Operations applications. They will instead be prompted to request the appropriate licenses from their administrator.

While the vast majority of users require user licenses as a part of their job, there is a small subset of users that may need to access Dynamics 365 Finance and Operations applications using licensed devices instead.

| Job function | Description |
|--- | --- |
| Retail store managers | Retail store managers using a point-of-sale (POS) device with Dynamics 365 Commerce |
| Warehouse workers | Warehouse workers using a warehouse device with Dynamics 365 Supply Chain Management |
| Production floor workers | Production floor workers using a production floor device with Dynamics 365 Supply Chain Management |

In addition to user licenses, Dynamics 365 Finance and Operations also allows specific roles to access using licensed devices. However, device license enforcement is targeted to take effect at a later time.

Therefore to ensure continued access for users who rely solely on licensed devices to access Dynamics 365 Finance and Operations applications, administrators will have to temporarily assign special purpose security roles.

| Job function | Special purpose security role |
|--- | --- |
| Retail store managers | Device based - Retail store manager |
| Warehouse workers | Device based - Warehouse worker |
| Production floor workers | Device based - Production floor worker |

Before assigning these special purpose security roles to users please note the following

- These special purpose security roles are temporary
  - These role are meant to enable access until device license enforcement takes effect.
  - When device license enforcement takes effect Microsoft will validate that the access is coming from a licensed device. These roles will then no longer be needed, will be deprecated, and eventually removed.
- These special purpose security roles should be used only for users in the specific job functions and with specific requirements
  - Retail store managers who need to access Dynamics 365 Commerce functionality beyond the point-of-sale (POS) app.
    - If the functionality in the point-of-sale app is sufficient for a retail store manager to perform their job, they do not need this role.
  - Warehouse workers who need to access Dynamics 365 Supply Chain Management functionality beyond the warehouse management app.
    - If the functionality in the warehouse management app is sufficient for a warehouse worker to perform their job, they do not need this role.
  - Production floor workers who need to access Dynamics 365 Supply Chain Management functionality beyond the production floor execution interface.
    - If the functionality in the production floor execution interface is sufficient for a production floor worker to perform their job, they do not need this role.
- These special purpose security roles should be used only for users who would do not require a user license
  - Any retail store managers, warehouse workers, or production floor workers who require a user license such as Dynamics 365 Operations-Activity or Dynamics 365 Commerce user, or Dynamics 365 Supply Chain Management will already have continued access and do not need this role.
- Users who are assigned these special purpose security roles should ensure scoped access
  - Any retail store managers, warehouse workers, or production floor workers who are assigned these special purpose security roles should not access functionality beyond the scope of their respective role as defined in the Dynamics 365 Licensing guide.
- Microsoft monitoring and notifications to detect misuse
  - Microsoft will be monitoring the assignment of these special purpose security roles as well as users using these special purpose security roles to ensure it meets the requirements as outlined in the Dynamics 365 Licensing guide.  
  - If any misuse is detected, organizations will be notified so that additional information can be gathered, or the appropriate licenses can be acquired for continued access

## Assign users to special purpose security roles
1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
2. In the tree, select one of the special purpose security roles: **Device based - Retail store manager, Device based - Warehouse worker, or Device based - Production floor worker**.
3. In the **Users assigned to role** section, select **Manually assign/exclude users**.
4. In the **Assign users to or exclude users from role** form, select one or more users that should be assigned the role.
5. In the **Action pane**, select **Assign to role**.

## Remove users from special purpose security roles
1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
2. In the tree, select one of the special purpose security roles: **Device based - Retail store manager, Device based - Warehouse worker, or Device based - Production floor worker**.
3. To remove one user, follow these steps:
   1. In the **Users assigned to role** section, select the user that should be removed.
   2. Select **Remove**.
4. To remove multiple users, follow these steps:
   1. In the **Users assigned to role** section, select **Manually assign/exclude users**.
   2. In the **Assign users to or exclude users from role** form , select users that should be removed from the role.
   3. In the **Action pane**, select **Exclude from role**.
