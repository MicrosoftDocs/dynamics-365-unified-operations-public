---
# required metadata

title: Update environment administrator
description: This topic explains how to restart individual services in environments that are deployed through Microsoft Dynamics Lifecycle Services (LCS).
author: laneswenka
ms.date: 05/10/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry:
ms.author: laswenka
ms.search.validFrom: 2018-03-05
ms.dyn365.ops.version: 7.3
---

# Update environment administrator

[!include [banner](../includes/banner.md)]

When creating a Finance and Operations apps environment in Lifecycle Services (LCS), one of the required configuration options is to select an Environment Administrator user.  This becomes the email account associated with the default 'Admin' user record inside of the Finance and Operations application with the System Administrator role assigned.  The Admin user is critical for situations in the application like System Batch Jobs that need to run with administrator privileges and should not be associated to a regular user from your company that could leave your organization and hence have their Azure Active Directory account disabled.

However, we know that from time to time the admin user account is disabled in Azure Active Directory and the ability to change this Admin user record in the application does not exist.  To date this has been supported manually via a support ticket, but has now been made as a self service action in LCS.

## Changing the environment administrator account

To change the environment administrator, you will need to be a Project Owner in the LCS project.  From there, you can visit your environment details page and use the following steps to make the change:

1. Use the **Maintain -> Update environment admin** button.
2. A new slider window opens where you may select another Project Owner or Environment Admin user from your LCS project.
3. Click the **Save** button.

> [!IMPORTANT]
> Changing the environment administrator account causes downtime on the target Finance and Operations apps environment.  Please use this capability appropriately after scheduling the downtime within your organization.

    

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
