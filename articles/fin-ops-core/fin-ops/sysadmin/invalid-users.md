---
title: Invalid users in Dynamics 365 Finance
description: Learn about how to address invalid users in Microsoft Dynamics 365 Finance, including outlines on different types of invalid users.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 5/03/2024
ms.custom:
ms.reviewer: twheeloc
---

# Invalid users in Dynamics 365 Finance

Users in any Microsoft Dynamics 365 finance and operations environment must comply with Microsoft guidelines to avoid sign-in failures. As of Dynamics 365 Finance version 10.0.39, administrators can use the **Invalid users** page to view details about invalid users.

To view invalid users, follow these steps.

1. Go **System administration** \> **Invalid users**.
2. Select **Refresh**. This page shows a list of users who require attention from the system administrator. If there are no invalid users, the page is blank.

After the administrator addresses the users in the list, select **Refresh** to confirm that there are no invalid users.

The following sections describe the three types of invalid users that must be addressed.

## Users who aren't found in Microsoft Entra ID

All finance and operations apps users must be present in your Microsoft Entra ID tenant. (Microsoft Entra ID was previously known as Azure Active Directory \[Azure AD\].) Administrators can directly add users to your tenant through the Azure portal. For more information, see [Add or delete users](/entra/fundamentals/add-users).   

You can use business-to-business (B2B) functionality to include these users in Microsoft Entra ID. For more information, see [Export business-to-business (B2B) users to Azure Active Directory](../../dev-itpro/sysadmin/implement-b2b.md).

## Users whose telemetry ID doesn't match the object ID from Microsoft Entra ID

For sign-in functionality to work correctly, the telemetry ID of a user in finance and operations apps must be aligned with the object ID of the same user in Microsoft Entra ID. If the IDs don't match, we recommend that you delete and then reimport the user. For more information, see [Find the user object ID](/partner-center/find-ids-and-domain-names.md#find-the-user-object-id).

1. Verify that a user who has the corresponding email address exists in your Microsoft Entra ID.
2. Delete the user from finance and operations apps. Note the user roles before deleting so the roles can be added back after reimporting the users. 
3. Reimport the user. For more information, see [Create new users](create-new-users.md).

If this process is challenging or requires substantial effort, administrators can update the email address on the **Users** page to a different user email that is present in Entra and change it back to the original email of the user. That change repopulates the object ID for the new email.

## Users whose email address contains an invalid "MAIL#" prefix

Previously, some customers who had trouble signing in were advised to append the prefix "MAIL\#" to their Gmail or Live email address. Because the issue has now been fixed, an administrator must follow these steps to remove the prefix from email addresses.

1. Go to **Users**.
2. Select **Edit** to remove the prefix from the email addresses.
