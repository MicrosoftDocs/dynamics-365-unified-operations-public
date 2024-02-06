---
title: Invalid users in Dynamics 365 finance
description: This article describes how to clean up Invalid users in Dynamics 365 finance.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Invalid users in Dynamics 365 Finance  

It is important that the users in any Dynamics 365 finance and operations environments are compliant with Microsoft guidelines, to avoid any login failures for such users.  
Starting in Dynamics 365 Finance version 10.0.39, Administrators can use the **Invalid users** page to get details of invalid users in the environment.
 
To view invalid users, follow these steps:
1. Go **System administration** > **Invalid users**.
2. Click **Refresh**. This page provides a list of users that require attention from the System administrator. This page remains blank if there are no invalid users.  

After the administrator addressed these users, click **Refresh** to verify that there are no invalid users.  

## Fix the invalid users  

There are three types of invalid users hat are the admins will be required to fix.  

User not found in the Microsoft Entra ID  

It is required that all the F&O users must be present in your Microsoft Entra ID tenant (previously known as Microsoft Azure Active Directory).  Administrators can directly add users to your tenant through the
Azure portal. Add or delete users | Microsoft Learn.  Alternatively, you can leverage the B2B functionality to include these users in Microsoft Entra ID. Export business-to-business (B2B) users to Azure Active 
Directory - Finance & Operations | Dynamics 365 | Microsoft Learn.  

 

Telemetry id does not match object id from Microsoft Entra ID  

The telemetry ID of the user in your Finance and Operations application must align with the Object ID for the same user in Microsoft Entra ID to ensure proper login functionality.  

  

Upon verifying that the user with the corresponding email exists in your Microsoft Entra ID, proceed to delete the user from Finance and Operations application and then reimport the user. Create new users - 
Finance & Operations | Dynamics 365 | Microsoft Learn.   

It is recommended to delete the user and subsequently reimport. However, if this proves challenging or requires substantial effort, an alternative is to update the email address on the Users page. This action
will repopulate the Object ID for the new email.  

  

Email contains invalid prefix MAIL#  

In the past, certain customers were advised to append a "MAIL#" prefix to their Gmail or Live email addresses to mitigate login issues. The problem has since been resolved, and it is now necessary to eliminate 
this prefix. Administrators can navigate to the Users page and select "Edit" to remove the prefix from the email addresses.  

 
