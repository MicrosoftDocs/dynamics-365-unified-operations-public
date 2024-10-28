---
title: Install Business performance analytics
description: Learn how to install Business performance analytics, including a step-by-step installation process and an outline on accessing reports in Business performance analytics.
author: jinniew
ms.author: jiwo
ms.topic: conceptual
ms.date: 10/30/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Install Business performance analytics

This article describes how to install Business performance analytics. 

>[!Important]
>The administrator who completed the configuration steps should complete the installation steps.    

## Install Business performance analytics 

Before installing Business performance analytics, check to make sure [all the prerequisites are completed](configure-bpa.md).

>[!Important]
>Always deploy environments using an unnamed account. This account must be from the customer domain, such as dynadmin@customer.com or dynadmin@customer.onmicrosoft.com. We strongly recommend using the same dedicated environment admin account on all environments. This avoids situations where an individual admin user leaving the organization disrupts administration operations in the Business performance analytics app. 


To install Business performance analytics, follow these steps. 

1. Request the [install link](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2V_9HFL4cRGtih_PMMDw1dUMFZHOUlUNlpVN1c4V1VJM0RNNlk2UkQ1MC4u) then select the link Microsoft will provide. 
2. Select **Get it now**. The page will navigate to the Power Platform admin center. 
3. In the Power Platform admin center, select the Microsoft Power Platform environment you have configured so far to install the application into. 
4. Accept the terms and conditions, and then select **Install**. This will start the installation of Business performance analytics in the selected environment. 
5. Go to the environment page for the selected environment, click **Dynamics 365 apps** to check status of the installation. During installation the status is **Installing**. On completion, the status will change to **Installed**. Refer to the Frequently Asked Questions if the status has a different value.
6. Set up your users to open Business performance analytics directly from Dynamics 365 finance and operations apps. For more information, see [Access Business performance analytics](access-bpa.md). 
7. Set up security. For more information, see [Set up security in Business performance analytics](set-up-security.md).

>[!NOTE]
>If you uninstall and install Business performance analytics, any new reports that were created won't be saved.

