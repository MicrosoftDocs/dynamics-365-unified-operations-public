---
# required metadata

title: Onboard users to use the Human Resources recruit app (preview)
description: This article describes how to onboard users to use the Human Resources recruit app.
author: twheeloc
ms.date: 07/01/2024
ms.topic: article
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-12-03
ms.dyn365.ops.version: Human Resources

---

# Onboard users to use the Human Resources recruit app (preview)

[This article is prerelease documentation and is subject to change.]

This article describes how to onboard users to use the Human Resources recruit app.

Users with licenses are seamlessly onboarded to your Dataverse instance through automatic synchronization with their MS Entra ID in the background.
 - If there's not a security group in your Power Platform setup, all licensed users within your tenant are automatically synchronized.
 - If there's a security group (recommended), only licensed users within this group are automatically synced to your Power Platform.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## How to synchronize users

To synchronize user, follow these steps: 
1.	Configure the security group:
 - Users must be added to the appropriate security group in MS Entra ID.
 - Grant users the correct Power Platform license.
2.	Automatic sync timing:
    - After setup, allow a few hours for automatic synchronization to complete.
    - For larger groups, synchronization may take additional time, depending on the number of users and other factors.
3.	Manual sync option: If needed, click **Refresh** to manually trigger the synchronization process.

By setting up and configuring correctly, users are automatically integrated into your Power Platform environment.
For more information, see the following articles: 
 - Microsoft Entra
 - Create a security group and add members to the security group.
 - Associate the security group with an environment.


### Roles
The HR recruiting add-on includes following roles: 

|Roles|	Scope|
|-----|------|
|System administrator |	Supports all functionalities of hiring process and configurations.|
|Recruiter	| Create job ads, assigns interviewers, schedule interviews, set the candidate to hire, and invite prospects.|
|Hiring manager	|View hiring process.|
|Panel member|	Provides feedback.|
|Job ad approver	|Approves job ads.|

To make your own roles, sign into the Power platform as a System Administrator.

### Add multiple roles to users

To add multiple roles to multiple users power platform, follow these steps:

1.	Sign in to the Power platform as a System Administrator.
2.	Select your environment.
3.	Select users.
4.	Click **Manage users** in Dynamics 365 Finance.
5.	Select one or multiple users.
6.	Click **Manage roles**.
7.	Select one or multiple roles.

 




