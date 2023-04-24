---
# required metadata

title: Install business performance analytics
description: This article describes how to install business performance analytics
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 04/24/2023
ms.topic: conceptual
ms.prod: 
ms.technology:
ms.custom:

---

# Install business performance analytics

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview of business performance analytics, contact <bpateam@microsoft.com>.

This article describes how to install business performance analytics. The administrator who completed the configuration steps should sign in.

> [!NOTE]
> For the public preview, Microsoft will email a link after you join the preview group.

## Install the business performance analytics app

1. Select the link that Microsoft provides.
2. Select **Get it now**.
3. In Power Platform admin center, select the Microsoft Dataverse environment to install the app in.
4. Accept the terms and conditions, and then select **Install**. App installation begins in the selected environment.
5. You can check the installation status in Power Platform admin center. After installation is completed, the status will be **Installed**.
6. After the app is installed, confirm that the following service principal is provisioned.
    The following Azure Active Directory (Azure AD) application should be registered in Azure AD.

    | Application | App ID |
    |-------------|--------|
    | far-dataverse-pipeline | 0e3659ee-3f34-4d0f-be21-d11f7141572f |

    To confirm that the application is registered in Azure AD, review the **All applications** list in Azure AD. For more information, see [View enterprise applications](//azure/active-directory/manage-apps/view-applications-portal). If the application isn't registered in Azure AD, contact support.
