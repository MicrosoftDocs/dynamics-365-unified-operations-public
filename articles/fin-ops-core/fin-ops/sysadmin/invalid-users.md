---
title: Invalid users in Dynamics 365 finance
description: This article describes how to address invalid users in Dynamics 365 finance.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Invalid users in Dynamics 365 Finance  

Users in any Dynamics 365 finance and operations environments must be compliant with Microsoft guidelines to avoid any login failures.  
Starting in Dynamics 365 Finance version 10.0.39, Administrators can use the **Invalid users** page to get details of invalid users.
 
To view invalid users, follow these steps:
1. Go **System administration** > **Invalid users**.
2. Click **Refresh**. This page provides a list of users that require attention from the System administrator. This page remains blank if there are no invalid users.  

After the administrator addressed these users, click **Refresh** to verify that there are no invalid users.  

## Fix invalid users  

There are three types of invalid users that need to be fixed.  

### Users not found in Microsoft Entra ID  

It's required that all Dynamics 365 finance and operations users must be present in your Microsoft Entra ID tenant (previously known as Microsoft Azure Active Directory). Administrators can directly add users to your tenant through the Azure portal. 
For more information, see [Add or delete users](/entra/fundamentals/add-users). 
You can leverage B2B functionality that includes these users in Microsoft Entra ID. For more information, see [Export business-to-business (B2B) users to Azure Active Directory](../../dev-itpro/sysadmin/implement-b2b.md).  

 
### Telemetry id doesn't match object id from Microsoft Entra ID  

The telemetry ID of the user in your Dynamics 365 finance and operations must align with the Object ID for the same user in Microsoft Entra ID to ensure proper login functionality.  
It's recommended to delete the user and reimport the user.

1. Verify the user with the corresponding email exists in your Microsoft Entra ID.
2. Delete the user from Dynamics 365 finance and operations.
3. Reimport the user. For more information, see [Create new users](create-new-users.md).   

If this proves challenging or requires substantial effort, administrators can update the email address on the **Users** page. This repopulates the Object ID for the new email.  

### Email contains invalid prefix MAIL#  

Previously, certain customers were advised to append a "MAIL#" prefix to their Gmail or Live email addresses to mitigate login issues. This problem is resolved, and it's necessary to eliminate this prefix. 
1. Administrators go to **Users**.
2. Select **Edit** to remove the prefix from the email addresses.  

 
