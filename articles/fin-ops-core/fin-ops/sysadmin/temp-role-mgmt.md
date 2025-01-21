---
title: Temporary role management
description: Learn how you can use temporary role management to assign temporary roles and responsibilities to active users.
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

# Temporary role management

[!include[banner](../../../finance/includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Temporary role management lets system administrators assign temporary roles to a specific user account for a specific amount of time (known as a *session*). This feature is useful when a user in a company is away from work for a period, or if a role must temporarily be divided among multiple users. When the session ends, the user account returns to its original roles.

## Session approval and processing

Only users who have the **System administrator** role can initiate new temporary role sessions.

The process for temporary role sessions has these steps.

1. Select **New** to create a request for a new session. The request has a status of **Draft**. Wait for a system administrator to approve the request. System administrators can approve or edit session requests.
1. To approve the session request, in the **Change status** field, select **Planned**.
1. The background process picks up the session request for processing. Alternatively, a system administrator can manually process it by selecting **Process**.
1. When the session begins, the selected user account obtains temporary roles in finance and operations apps.
1. When the session ends, the user account returns to its original roles.

> [!NOTE]
> There is no limit on the length of a temporary role session.

## Session types

When you create a new temporary role session, set the type to **Merge** or **Replace**.

- **Merge** – Add the temporary roles to the existing roles of the user account.
- **Replace** – Replace the existing roles of the user account with the temporary roles.

For both session types, the user account returns to its original roles when the session ends.

## Assign temporary roles

For a new temporary role session, select **Assign roles** to assign the temporary roles to the selected user account. You can also select **Assign organizations** to assign the temporary roles to the selected organization only, not to all organizations.

## Audit logs

Use the **Audit logs** to view all actions that are performed on a given session request. The grid captures the following details:

- The change in status
- The date
- The timestamp of the action
- Who made the change
- Whether the batch process or a system administrator processed the request

## User log

The **User log** captures all sessions when any selected user accounts sign in to finance and operations apps during the active temporary role session. This log helps track user activities and the time that is spent on each session. It also captures when the current session ends.

> [!NOTE]
> The **User log** captures the logging sessions that were performed during an active temporary role session. Nothing outside the session is captured, even if the same user account was active in the system earlier and was signing in.

## User role change log

The **User role change log** captures all the role changes that were performed during the active temporary role session. This log helps track the role changes for a specific user account.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
