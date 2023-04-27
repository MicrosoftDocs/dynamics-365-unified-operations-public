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

>[!NOTE]
>The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview of business performance analytics, contact <bpateam@microsoft.com>.

This article describes how to install business performance analytics. The administrator who completed the configuration steps should sign in.    

>[!NOTE]
>For the public preview, Microsoft will email a link after you join the preview group.

## Install the business performance analytics app

To install business performance analytics, follow these steps. 

1. Select the link that Microsoft provides. 
2. Select **Get it now**. The page will navigate to the Power Platform admin center. 
3. In the Power Platform admin center, select the Microsoft Power Platform environment to install the application into. 
4. Accept the terms and conditions, and then select **Install**. This will start the installation of business performance analytics in the selected environment. 
5. Go to the environment page for the selected environment, click **Dynamics 365 apps** to check status of the installation. During installation the status is **Installing**. On completion, the status will change to **Installed**. Refer to the Frequently Asked Questions if the status has a different value. 
6. After the app is installed successfully, confirm that the following service principal is provisioned: 
     - Open the Microsoft Azure Portal and navigate to the list of Enterprise applications within Azure Active Directory. For more information, see [View enterprise applications](/azure/active-directory/manage-apps/view-applications-portal). If the application isn't registered in Azure AD, contact support. 

     The following Azure Active Directory (Azure AD) application should be registered in Azure AD.

     | Application | App ID |
     |-------------|--------|
     | far-dataverse-pipeline | 0e3659ee-3f34-4d0f-be21-d11f7141572f |

   
