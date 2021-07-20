---
# required metadata

title: Assign lease user roles
description: This topic describes the security roles that are used in Asset leasing. It also explains how to assign users to those roles.
author: moaamer
ms.date: 04/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysOperationTemplateForm
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14

---

# Assign lease user roles

[!include [banner](../includes/banner.md)]

This topic describes the security roles that are used in Asset leasing. It also explains how to assign users to those roles.

Three user roles differentiate access in Asset leasing. One role is appropriate for maintaining leases, one is appropriate for viewing leases, and one is appropriate for performing a lease clerk's duties. Each role has specific permissions for all lease pages, and each lets users view, create, edit, or delete leases, according to their job duties.

| Role           | Description |
|----------------|-------------|
| Maintain Lease | Users in this role can add, edit, delete, and view leases. This role is designed for daily users whose tasks include creating and posting monthly journal entries and adding new leases. This role gives access to all Asset leasing functionality. |
| View Lease     | Users in this role can only view lease records, schedules, and run reports. They can't create new leases, edit existing leases, or create journal entries against leases. The role is designed for users who just have to view leases, lease schedules, and the transactions that occur against those leases. |
| Lease Clerk    | Users in this role can only create new leases. They can't edit or delete existing leases, view lease schedules, or post leasing journal entries. This role is designed for users who work in a data entry capacity. |

Follow these steps to assign users to the roles that are used in Asset leasing.

1. Go to **System administration \> Security \> Assign users to roles**.
2. Select the **Maintain lease**, **Lease clerk**, or **View lease** role, and then select **Manually assign/exclude users**.
3. Select the user to assign to the role, and then select **Assign to role**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
