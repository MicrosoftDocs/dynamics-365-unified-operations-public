---
title: Privileged user management
description: This article describes how to use privileged user management to control privileged user accounts.
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 01/25/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-13
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# Privileged user management

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Privileged user management allows system administrators to schedule a session for selected user accounts and records all user interactions within Dynamics 365 finance and operations during the session. This feature is useful when some elevated privileged accounts are utilized for auditing purposes and ensures users aren't performing any unauthorized activities within the system.

You can also enable or disable the account once the session starts. As soon as the session ends, the account goes back to its original state.


## Session approval and process
A new session is initiated by a system administrator.

1. Click **New**. The request has a **Draft** status and the system administrator can approve it.
2. Anyone with **System administrator** role can approve or edit the request.
3. To approve the request, in the **Change status** field and select **Approve**. The request can be picked up by the background process or the system administrator can process it manually. The system administrator can schedule the session for the user account. The system administrator can also enable or disable the account after the session starts. As soon as the session ends, the account goes back to its original state.

[!NOTE]
> Maximum duration for a **Privileged user session** is 24 hours.


## Audit log

Use the **Audit logs** to see all actions performed on a given session request. This table captures:
 - change in status
 - the date and time stamp of the action
 - who made the change
 - if the system administrator or the batch process approved 

## User log

**User log** captures all the sessions that selected user account has been logged in Dynamics 365 finance and operations during the active privileged user session. This helps track the user activities and the time spent on each session. 

> [!NOTE]
> The **User log** captures the logging sessions which were performed during an active privileged user session. Anything outside of the session isn't captured even if the same user account is active in the system earlier and has been logging in. 


## Recordings
When a **System Administrator** is scheduling a privileged user session for an account, they are clearly notified about the condition that during the entire session, user account interactions within **Finance & Operations** will be recorded by using the **Task recorder** utility. Task recorder can capture the type of user action (for example, a button click, value entry, or navigation) and any data that is related to the user action (for example, the input data value and type, form context, or record context). For more information, see [Task recorder](../articles/fin-ops-core/dev-itpro/user-interface/task-recorder.md). The recordings are stored on the **Recordings** tab, system administrators can download by clicking **Download**. This helps review the user interactions performed by user during the session and support any audits for compliance.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
