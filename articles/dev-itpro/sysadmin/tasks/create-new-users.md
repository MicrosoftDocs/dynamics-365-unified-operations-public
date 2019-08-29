--- 
# required metadata 
 
title: Create new users
description: Users are internal employees of your organization, or external customers and vendors, who require access to the system to perform their jobs. 
author: maertenm
manager: AnnBe 
ms.date: 07/01/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysUserManagement, SysDataAreaSelectLookup, SysSecUserAddRoles, SysUserMSODSUserImport   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: maertenm
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create new users

[!include [task guide banner](../../includes/task-guide-banner.md)]

Users are internal employees of your organization, or external customers and vendors, who require access to the system to perform their jobs.

## Associate a user with a license (new license types only)
For customers on one of the new Finance and Operations license types added in October 2019, users need to be associated with a license. If a license is associated with a new user, the first time they sign in they will be added as a system user. If a license is not associated with a user, then they will recieve a brief warning.
System administrators can [assign licenses to users](https://docs.microsoft.com/en-us/office365/admin/subscriptions-and-billing/assign-licenses-to-users?view=o365-worldwide) in the [Microsoft 365 Admin Center](https://docs.microsoft.com/en-us/office365/admin/admin-overview/about-the-admin-center?view=o365-worldwide).

## Add a new user
1. Go to **Navigation pane > Modules > System administration > Users > Users**.
2. On the **Action pane**, click **New**.
3. In the **User ID** field, type a value. Enter a unique identifier for the user. A user ID is required.  
4. In the **User name** field, type a value. Enter the user's name.  
5. In the **Domain** field, type a value. Enter the user's domain.  
6. In the **Alias** field, type a value. Enter the user's alias.  
7. In the **Company** field, click the drop-down button to open the lookup.
8. In the list, find and select the desired record. 
9. In the **User's roles** section, click **Assign roles**.
10. In the list, find and select the desired record.
11. Click **OK**.
12. Click **Save**.

## Import users
1. On the **Action pane**, click **Import users**.
2. In the list, mark the selected row.
3. Click **Import users**.
4. Click **Close**.

