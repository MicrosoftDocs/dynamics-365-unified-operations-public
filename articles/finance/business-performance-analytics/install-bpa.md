---
# required metadata

title: Install business performance analytics
description: This article describes how to install business performance analytics
author: jinniew
ms.author: jinniew
ms.reviewer: twheeloc 
ms.date: 04/24/2023
ms.topic: conceptual
ms.prod: 
ms.technology:
ms.custom:

---

# Installing business performance analytics

>[!NOTE]
>The functionality noted in this article is available as part of a preview release. The content and the functionality are subject to change. For more information about participating in public preview for business performance analytics, contact bpateam@microsoft.com. 


This article describes how to install business performance analytics. The administrator who has completed the configuration steps should login. 

> [!NOTE]
> For gated public preview, Microsoft will email the link to you after you join the preview group. 
  
## Install the business performance analytics app  
1.  Click on the link provided by Microsoft. 
2.  Click **Get it now**. 
3.  In the Power Platform Admin Center, select the Dataverse environment to install on. 
4.  After the terms and conditions are accepted, click **Install**. The app installation will start on the environment selected. 
5.  You can check the installing status in the Power Platform Admin center. After the installation is complete, the status will be **Installed**.
6.  After the application is installed, confirm the following service principal is provisioned. 

The following Azure AD apps are registered in Azure AD. 
| Application            | App ID                               |
| ---------------------- | ------------------------------------ |
| far-dataverse-pipeline | 0e3659ee-3f34-4d0f-be21-d11f7141572f |

To verify the application is registered in Azure AD, check the All applications list. For more details, see [View enterprise applications](//azure/active-directory/manage-apps/view-applications-portal). If the application isn't registered in Azure AD, contact support. 
