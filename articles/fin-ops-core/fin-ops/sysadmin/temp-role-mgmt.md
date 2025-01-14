---
title: Temporary role management
description: Learn about how you can use Temporary role management to assign temporary roles and responsibilities to all active users within Finance and operations.
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

Temporary role management allows **System administrators** to be able to assign temporary roles to the selected user account for a desired duration. This feature is useful for scenarios where someone within a company is out for a duration or if similar role has to be divided among multiple folks for a temporarily manner.
As soon as the session ends, the user account will go back to it's original roles.


## Session approval and Process
A new session can only be initiated by a System administrator by selecting the **New** button. The request will go in the **Draft** status and wait for the system administrator for approval. Anyone with **System administrator** role will be able to approve or edit the request. To approve the request, use the **Change status** field and select **Planned**. After this point, the request will either be picked up by the **background process** to execute or else system administrator can process it manually by using the **Process** action button at the top. Once the session will start, selected user will obtain temporary roles in **Finance & Operations** and once the session ends, the user account will go back to it's original roles.
[!NOTE]
> There is no maximum limit for a temporary role session.
## Merge vs. Replace type
When creating a new session, you can select the **Merge** or **Replace** type. Merge type will add the temporary roles to the existing roles of the user account. Replace type will replace the existing roles of the user account with the temporary roles. Once the session ends, both these types revert to the original roles of the user account.

## Assigning temporary role
For the new session, you can select the **Assign roles** button to assign the temporary roles to the selected user account. You can also select the **Assign organizations** button to assign the temporary role to the selected organization only and not to all organizations. 

## Audit log

Use the **Audit logs** to see all actions performed on a given session request. This table captures change in status, the date and time stamp of the action and who made the change, whether it is **system administrator** or the background **batch process**.

## User log

**User log** will capture all sessions whenever any selected user account log into **Finance and Operations** during the active temporary role session. This will help you to track the user activities and the time spent on each session. It also captures when the currently logged in session ends. 
> [!NOTE]
> The **User log** will only capture the logging sessions which were performed during an active temporary role session. Anything outside of the session will not be captured even if the same user account is active in the system earlier and has been logging in. 
## User role change log
**User role change log** will capture all the role changes that were performed during the active temporary role session. This will help you to track the role changes for a given user account.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
Footer
© 2025 GitHub, Inc.
Footer navigation
Terms
Privacy
Security
Status
