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

Privileged user management lets system administrators schedule a session for selected user accounts. It also records all user interactions in Dynamics 365 finance and operations apps during that session, if the user decides to continue using the Finance & Operations app after reading the consent on the landing page. This feature is useful when some elevated privileged accounts are used for auditing purposes. It helps ensure that users aren't performing any unauthorized activities in the system and keep a recording of it, in case it is later needed for audit or compliance reviews.

System administrators can also choose to enable or disable the given user account once the session begins. As soon as the session ends, the account returns to its original state.

## Session approval and processing

New privileged user sessions are initiated by a system administrator.

1. On the **Privileged user management** page, select **New** to create a request for a new session. The request has a default status of **Draft**.
2. At this point, system administrator can also decide if they want to enable or disable the user account selected for the **privileged user session**. **Enable** means it will change the user account to enabled state, if it was originally disabled. **Disable** will de-activate the user account as soon as the session will start. Once the session is over, user accounts will return to their **original** state. 
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

When a system administrator is scheduling a privileged user session for a user account, they are immediately presented with a notice that the Task recorder utility will be used to record the user's user-interface interactions in finance and operations apps. If system admin decides to proceed with setting up the session for a particular user, it means they are agreering to record the selected user's session on finance and operations app. Task recorder captures the type of user action (for example, button selection, value entry, or navigation). It also captures any data that is related to that action.

When system users who are assigned to a privileged user session sign-in to finance and operations apps, they will be immediately presented with a consent message at the top of the page. After reading the consent message, if they decided to continue the session, it will be considered as agreeing to the consent and in this as they proceed to use the apps, the session is recorded. If they do not agree with the consent, they must immediately close the application.

A separate recording is created for each session. The recordings are stored within the **Recordings** tab of the **Privileged user management** page and all recordings will persist until manually deleted by system administrator. System administrators can download each recording by selecting it and then selecting **Download**. This capability is helpful when audits or compliance reviews must be done for a user's interactions.

Learn more in [Task recorder resources](../../dev-itpro/user-interface/task-recorder.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
