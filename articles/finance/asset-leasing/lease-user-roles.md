---
# required metadata

title: Assign lease user roles
description: This topic lists the steps for creating number sequences for Lease IDs, as well as unique IDs that are used in the index revaluation process. 
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

There are three user roles designed to give users rights inside the asset leasing module. The Asset leasing module contains three user roles relating to leasing – Maintain lease, View lease, and Lease clerk. Each role contains specific permissions for all lease forms and functions allowing users to view, create, edit, or delete leases according to their job duties.

|     Role              	|     Description                                                                                                                                                                                                                                                                                                                                  	|
|-----------------------	|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
|     Maintain Lease    	|     User has access to add, edit, delete, and view leases.   This role is designed for daily users who are tasked with creating and   posting monthly journal entries and adding new leases. This role allows   access to all functionality of the leasing application.                                                                          	|
|     View Lease        	|     User only has access to view lease records, schedules, and   run reports. The user cannot create a new lease or edit an existing lease.   This role does not allow users to create journal entries against leases. The   role is designed for a user to solely view leases, their schedules, and the   transactions against those leases.    	|
|     Lease Clerk       	|     User only has access to create a new lease. The user does   not have access to modify or delete any existing leases. This role is   designed for a data entry role and does not have permission to view the   leasing schedules or post leasing journal entries.                                                                             	|

Complete the following steps to assign users to the roles used in Asset leasing.

1. Ope the Assign users to roles page (**System administration > Security > Assign users to roles**).
2.	Choose either Maintain lease, Lease clerk or view Lease and then select Manually assign/exclude users
3.	Select the user to assign the role to and then click Assign to role.
