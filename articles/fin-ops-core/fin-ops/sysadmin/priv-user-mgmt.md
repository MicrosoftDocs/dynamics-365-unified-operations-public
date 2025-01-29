---
title: Privileged user management
description: Learn how you can use privileged user management to control privileged user accounts.
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

Privileged user management lets system administrators schedule a session for selected user accounts. It also records all user interactions in Dynamics 365 finance and operations apps during that session. This feature is useful when some elevated privileged accounts are used for auditing purposes. It helps ensure that users aren't performing any unauthorized activities in the system.

System administrators can also enable or disable a user account after the session begins. As soon as the session ends, the account returns to its original state.

## Session approval and processing

New privileged user sessions are initiated by a system administrator.

1. On the **Privileged user management** page, select **New** to create a request for a new session. The request has a status of **Draft**.
1. Anyone who has the **System administrator** role can approve or edit the session request. To approve the request, in the **Change status** field, select **Approve**.
1. The background process picks up the session request for processing. Alternatively, a system administrator can manually process it. The system administrator can schedule the session for the user account. They can also enable or disable the account after the session begins. As soon as the session ends, the account returns to its original state.

> [!NOTE]
> The maximum duration for a privileged user session is 24 hours.

## Audit logs

Use the **Audit logs** to view all actions that are performed on a given session request. The grid captures the following details:

- The change in status
- The date and timestamp of the action
- who made the change
- Whether a system administrator or the batch process approved the request

## User log

The **User log** captures all the sessions where the selected user account signs in to finance and operations apps during the active privileged user session. This log helps track the user's activities and the time that is spent on each session.

> [!NOTE]
> The **User log** captures only the logging sessions that are performed during the active privileged user session. Nothing outside that session is captured, even if the same user account was active in the system earlier and was signing in.

## Recordings

When a system administrator schedules a privileged user session for a user account, they are notified that the Task recorder tool will be used to record the account's interactions in finance and operations apps. Task recorder captures the type of user action (for example, button selection, value entry, or navigation). It also captures any data that is related to that action.

When system users who are assigned to a privileged user session sign in to finance and operations apps, they must consent to having their interactions recorded. If they consent and proceed to use the apps, the session is recorded.

A separate recording is created for each session. The recordings are stored on the **Recordings** tab of the **Privileged user management** page. System administrators can download each recording by selecting it and then selecting **Download**. This capability is helpful when audits or compliance reviews must be done for a user's interactions.

Learn more in [Task recorder resources](../../dev-itpro/user-interface/task-recorder.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
