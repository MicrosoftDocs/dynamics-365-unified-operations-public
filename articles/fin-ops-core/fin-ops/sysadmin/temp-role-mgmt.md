---
title: Temporary role management
description: Learn about how you can use temporary role management to assign temporary roles and responsibilities to active users.
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 01/13/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-13
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# Temporary role management

[!include[banner](../../../finance/includes/banner.md)]

Temporary role management allows system administrators to assign temporary roles to the selected user account for a desired duration. This feature is useful when a user in a company is out for a duration or if similar role has to be divided among multiple folks for a temporarily manner. As soon as the session ends, the user account goes back to it's original roles.


## Session approval and process
A new session can only be initiated by a system administrator.

To initiate a new session, follow these steps:
1. Click **New** and the request has a **Draft** status and wait for the system administrator for approval. Users with **System administrator** role can approve or edit the request.
2. To approve the request, in the **Change status** field and select **Planned**.
3. The request is either picked up by the background process or the system administrator processes it manually by clicking **Process**.
4. When the session starts, the selected user obtains temporary roles in Dynamics 365 finance and operations.
5. When the session ends, the user accounts go back to their original roles.
[!NOTE]
> There is no maximum limit for a temporary role session.


## Merge and replace types
When creating a new session, select a **Merge** or **Replace** type. 
 - **Merge** - adds the temporary roles to the existing roles of the user account.
 - **Replace** - replaces the existing roles of the user account with the temporary roles. When the session ends, both these types revert to the original roles of the user account.

## Assigning temporary role
For the new session, click **Assign roles** to assign the temporary roles to the selected user account. You can also click **Assign organizations** to assign the temporary role to the selected organization only and not all organizations. 

## Audit log

Use the **Audit logs** to see all actions performed on a given session request. This table captures:
 - change in status
 - the date
 - time stamp of the action
 - who made the change
 - Was it the system administrator or the batch process

## User log

**User log** captures all sessions when any selected user accounts log into Dynamics 365 finance and operations during the active temporary role session. This helps track user activities and the time spent on each session. It also captures when the current session ends. 

> [!NOTE]
> The **User log** captures the logging sessions that were performed during an active temporary role session. Anything outside of the session isn't captured even if the same user account is active in the system earlier and has been logging in.


## User role change log
**User role change log** captures all the role changes that were performed during the active temporary role session. This helps track the role changes for a given user account.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

