---
# required metadata

title: Update the environment administrator
description: This topic explains how to change the environment administrator for a Finance and Operations apps environment in Microsoft Dynamics Lifecycle Services (LCS).
author: laneswenka
ms.date: 05/10/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global 
# ms.search.industry:
ms.author: laswenka
ms.search.validFrom: 2018-03-05

---

# Update the environment administrator

[!include [banner](../includes/banner.md)]

When you create a Finance and Operations apps environment in Microsoft Dynamics Lifecycle Services (LCS), one of the configuration options requires that you select a user as the environment administrator. This user becomes the email account that is associated with the default **Admin** user record that the System Administrator role is assigned to in Finance and Operations apps.

The Admin user is critical in some situations in the apps, such as when system batch jobs are run. These jobs must run with administrator privileges. They should not be associated with a regular user from your company, because that user's Azure Active Directory (Azure AD) account will be disabled if they leave your organization.

However, we know that the Admin user account is occasionally disabled in Azure AD, and there is no way to change the **Admin** user record in the apps. Previously, this issue was manually supported via a support ticket, but it has now been made a self-service action in LCS.

## Change the environment administrator account

To change the environment administrator, you must be a project owner in the LCS project.

1. In LCS, go to your project, and open your environment details page.
2. Select **Maintain \> Update environment admin**.
3. In the dialog box that appears, select another Project Owner or Environment Admin user from your LCS project.
4. Select **Save**.

> [!IMPORTANT]
> Changes to the environment administrator account cause downtime in the target Finance and Operations apps environment. Therefore, use this capability in the appropriate way and only after you schedule the downtime in your organization.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
