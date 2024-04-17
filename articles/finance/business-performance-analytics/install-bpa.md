---
# required metadata

title: Install Business performance analytics
description: This article describes how to install Business performance analytics
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 12/12/2023
ms.topic: conceptual
ms.custom:
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
ms.audience: administrator
---

# Install Business performance analytics

>[!NOTE]
>The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview of Business performance analytics, contact contact <bpaquestions@service.microsoft.com>.

This article describes how to install Business performance analytics. The administrator who completed the configuration steps should sign in.    

## Install Business performance analytics 

Before installing Business performance analytics, check to make sure [all the prerequisites are completed](configure-bpa.md).

>[!Important]
>Always deploy environments using an unnamed account. This account must be from the customer domain, such as dynadmin@customer.com or dynadmin@customer.onmicrosoft.com. We strongly recommend using the same dedicated environment admin account on all environments. This avoids situations where an individual admin user leaving the organization disrupts administration operations in the Business performance analytics app. 


To install Business performance analytics, follow these steps. 

1. Select the link that Microsoft provides from Step 6 above. 
2. Select **Get it now**. The page will navigate to the Power Platform admin center. 
3. In the Power Platform admin center, select the Microsoft Power Platform environment to install the application into. 
4. Accept the terms and conditions, and then select **Install**. This will start the installation of Business performance analytics in the selected environment. 
5. Go to the environment page for the selected environment, click **Dynamics 365 apps** to check status of the installation. During installation the status is **Installing**. On completion, the status will change to **Installed**. Refer to the Frequently Asked Questions if the status has a different value. 

>[!NOTE]
>If you uninstall and install Business performance analytics, any new reports that were created won't be saved.

## Access Reports in Business performance analytics

To access reports in Business performance analytics, follow these steps. 

1. Go to the [Maker portal](https://make.preview.powerapps.com/) of environment where Business performance analytics is installed.
2. Select **Apps** to open Business performance analytics.
3. The available reports will be displayed. 
4. For more information about setting up security, see [Set up security in Business performance analytics](set-up-security.md).
