---
title: Privileged user management
description: Learn about how you can use Privileged user management to control the enabling/ disabling of privileged user accounts within your company.
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

# Privileged user management

[!include[banner](../../../finance/includes/banner.md)]

Privileged user management allows System administrators to be able to schedule a session for selected user account and record all user interactions within Dynamics365 Finance and Operations during the entire session. This feature is useful for scenarios where some elevated privileged accounts can be utilized for auditing purposes and to ensure that the user is not performing any unauthorized activities within the system.
You can also control to enable or disable the account once the session starts. As soon as the session ends, the account will go back to it's original state.


## Session approval and Process
A new session can only be initiated by a System administrator by selecting the **New** button. The request will go in the **Draft** status and wait for the system administrator for approval. Anyone with **System administrator** role will be able to approve or edit the request. To approve the request, use the **Change status** field and select **Approve**. At this point, the request will either be picked up by the **background process** or else system administrator can process it manually by using the **Process** action button at the top. The system administrator can also schedule the session for the user account. The system administrator can also enable or disable the account once the session starts. As soon as the session ends, the account will go back to it's original state.
[!NOTE]
> Maximum duration for a **Privileged user session** can be 24 hours.
## Audit log

Use the **Audit logs** to see all actions performed on a given session request. This table captures change in status, the date and time stamp of the action and who made the change, whether it is **system administrator** or the background **batch process**.

## User log

**User log** will capture all the sessions that selected user account has been logged into **Finance and Operations** during the active Privileged user session. This will help you to track the user activities and the time spent on each session. 
> [!NOTE]
> The **User log** will only capture the logging sessions which were performed during an active privileged user session. Anything outside of the session will not be captured even if the same user account is active in the system earlier and has been logging in. 
## Recordings
Each user session within **Finance & Operations** will be recorded by using the **task recording** framework and stored in the **Recordings** tab for system administrator to download using the **Download** button. This will help you to review the user interactions performed by user during the session and also help in supporting any audits for compliance.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
