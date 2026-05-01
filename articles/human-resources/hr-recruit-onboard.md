---
# required metadata

title: Onboard users to use the HR Recruiting app 
description: This article explains how to onboard users so that they can use the HR Recruiting app in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/11/2025
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

# Onboard users to use the HR Recruiting app 

This article explains how to onboard users so they can use the HR Recruiting app in Microsoft Dynamics 365 Human Resources.

Users who have licenses are seamlessly onboarded to your Dataverse instance in the background, through automatic synchronization with Microsoft Entra ID.

- If your Microsoft Power Platform setup doesn't include a security group, the system automatically synchronizes all licensed users in your tenant.
- If your setup includes a security group (recommended), the system automatically synchronizes only licensed users in that group to Microsoft Power Platform.

## Synchronize users

To synchronize users, configure the security group.

- Add users to the appropriate security group in Microsoft Entra ID.
- Grant users the correct Microsoft Power Platform license.

**Automatic synchronization timing**

- After you complete the setup, wait a few hours for automatic synchronization to finish.
- For larger groups, synchronization might take more time, depending on the number of users and other factors.

**Manual synchronization option**

As required, select **Refresh** to manually trigger the synchronization process.

By correctly setting up and configuring synchronization, you ensure that users are automatically integrated into your Microsoft Power Platform environment.

For more information, see the following articles:
- [Create a security group and add members to the security group](/power-platform/admin/control-user-access#create-a-security-group-and-add-members-to-the-security-group)
- [Associate a security group with an environment](/power-platform/admin/control-user-access#associate-a-security-group-with-an-environment)

## Roles

The Recruiting add-on includes the following roles.

| Role | Scope |
|------|-------|
| System administrator (Dataverse built-in role) | This role supports all functionality of the hiring process and configuration. |
| Recruiting administrator | This role supports all functionality of the hiring process and configuration. Users assigned the Recruiting administrator role need to be present in Dynamics 365 finance and operations and must also have the Recruiting Application role assigned Dynamics 365 finance and operations. | 
| Recruiter | Users who have this role can create job ads, assign interviewers, schedule interviews, set the candidates to hire, and invite prospects. Users assigned the **Recruiting** role need to be present in Dynamics 365 finance and operations and must also have the Recruiting application role assigned Dynamics 365 finance and operations. |
| Hiring manager | Users who have this role can view the hiring process. Users assigned the Hiring manager role need to be present in Dynamics 365 finance and operations and must also have the Recruiting application role assigned Dynamics 365 finance and operations.  |
| Panel member | Users who have this role can provide feedback. |
| Job ad approver | Users who have this role can approve job ads. |

To create your own roles, sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as a system administrator.

## Add multiple roles to users

To add multiple roles to multiple users in Microsoft Power Platform, follow these steps:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as a system administrator.
1. Select your environment.
1. Select **Users**.
1. Select **Manage users in Dynamics 365**.
1. Select one or more users.
1. Select **Manage roles**.
1. Select one or more roles.
