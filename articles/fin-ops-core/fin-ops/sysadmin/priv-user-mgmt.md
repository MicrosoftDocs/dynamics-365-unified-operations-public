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

Privileged user management lets system administrators schedule a session for selected user accounts. All user interactions are recorded in Dynamics 365 finance and operations apps during that session, if the user decides to continue using Dynamics 365 finance and operations after reading the consent on the landing page. This feature is useful when some elevated privileged accounts are used for auditing purposes. It helps ensure that users aren't performing any unauthorized activities in the system and keeps a recording of it, in case it is later needed for audit or compliance reviews.

System administrators can choose to enable or disable the given user account once the session begins. As soon as the session ends, the account returns to its original state.

## Session approval and processing

New privileged user sessions are initiated by a system administrator.

1. On the **Privileged user management** page, select **New** to create a request for a new session. The request has a default status of **Draft**.
1. The system administrator can decide if they want to enable or disable the user account selected for the **Privileged user session**. **Enable** means it changes the user account to enabled state, if it was originally disabled. **Disable** deactivates the user account as soon as the session starts. After the session is over, user accounts return to their original state. 
1. Anyone who has the **System administrator** role can approve or edit the session request. To approve the request, in the **Change status** field, select **Approve**.
1. The background process picks up the session request for processing. Alternatively, a system administrator can manually process it. The system administrator can schedule the session for the user account. They can also enable or disable the account after the session begins. As soon as the session ends, the account returns to its original state.

> [!NOTE]
> The maximum duration for a privileged user session is 24 hours.

> [!NOTE]
> It's recommended that privileged user sessions should be allocated to only high privileged user accounts within company and each privileged account should have unique functions. It's expected that these privileged accounts remain disabled when not in use. 

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

When a system administrator schedules a privileged user session for a user account, they are immediately presented with a notice that the Task recorder utility will be used to record the user's user interface  interactions in finance and operations apps. If system administrator decides to proceed with setting up the session for a particular user, they are agreeing to record the selected user's session in the finance and operations app. Task recorder captures the type of user action (for example, button selection, value entry, or navigation). It also captures any data that is related to that action.

When system users who are assigned to a privileged user session sign into finance and operations apps, they are immediately presented with a consent message at the top of the page. After reading the consent message, if they decided to continue the session, it's consent and as they use the apps, the session is recorded. If they don't agree with the consent, they must immediately close the application.

A separate recording is created for each session. The recordings are stored on the **Recordings** tab of the **Privileged user management** page and all recordings exist until manually deleted by system administrator. System administrators can download each recording by selecting it and then selecting **Download**. This capability is helpful when audits or compliance reviews must be done for a user's interactions.

Learn more in [Task recorder resources](../../dev-itpro/user-interface/task-recorder.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
