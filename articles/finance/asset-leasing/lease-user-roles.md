---
# required metadata

title: Assign lease user roles
description: This topic describes the security roles used in Asset leasing and lists the steps for assigning users to those roles.  
author: moaamer
manager: Ann Beebe
ms.date: 07/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-07-22
ms.dyn365.ops.version: 10.0.14

---

# Assign lease user roles (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the security roles used in Asset leasing and lists the steps for assigning users to those roles. There are three user roles differentiate access with Asset leasing. The roles are appropriate to maintaining leases, viewing leases, and to a lease clerk's duties. Each role contains specific permissions for all lease forms and that lets  users view, create, edit, or delete leases according to their job duties. 

|     Role              	|     Description                                                                                                                                                                                                                                                                                                                                  	|
|-----------------------	|------------------------------------------------------------------------	|
|     Maintain Lease    	|     Users in this role have access to add, edit, delete, and view leases. This role is designed for daily users whose tasks include creating and posting monthly journal entries, and adding new leases. This role allows access to all Asset leasing functionality.                                                                          	|
|     View Lease        	|     Users in this role have access only for viewing lease records, schedules, and run reports. Users assigned to this role cannot create new leases, nor edit  existing leases. This role does not let users create journal entries against leases. The role is designed for a user who needs only to view leases, lease schedules, and the transactions against those leases.    	|
|     Lease Clerk       	|     Users in this role have access only to create new leases. Users assigned to this role don't have access to modify or delete existing leases. This role is   intended for someone in a data entry capacity, and doesn't include permission to view the lease schedules or to post leasing journal entries.                                                                             	|

Complete the following steps to assign users to the roles used in Asset leasing.

1. Open the Assign users to roles page (**System administration > Security > Assign users to roles**).
2.	Choose either **Maintain lease**, **Lease clerk** or **View lease**, and then select **Manually assign/exclude users**.
3.	Select the user to assign to the role, and then click **Assign to role**.

