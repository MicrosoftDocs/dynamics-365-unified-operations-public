---
# required metadata

title: Welcome email is not sent to new customers is created
description: This topic provides troubleshooting guidance that can help when customer do not receive a welcome email notification when a new customer is created.
author: gvrmohanreddy
ms.date: 02/10/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-02-10
---

# Welcome email is not sent to new customers upon sign up

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance that can help when customer do not receive a welcome email notification when a new customer is created.

## Description

When a new customer is created a welcome email is not sent to the newly created customer despite having an email notification configured for customer created event type in Headquarters.

## Resolution

### Set proper EmailID for customer created event

Commerce email notification profile
Retail and Commerce > Headquarters setup



1. Go to **Retail and Commerce \> Headquarters setup \> Commerce email notification profile **.
1. Select the notification profile in the list. 
1. Under  **Retail event notifications settings** identify the **Customer created** email notification type, and make sure **Email Id** value is given as **NewCust**

## Additional resources

[Set up an email notification profile](../email-notification-profiles.md)

