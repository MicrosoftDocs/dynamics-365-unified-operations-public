---
# required metadata

title: Welcome email is not sent when new customers are created
description: This topic provides troubleshooting guidance that can help if a welcome email notification isn't sent when a new customer is created in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 02/24/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-02-10
---

# Welcome email is not sent when new customers are created

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance that can help if a welcome email notification isn't sent when a new customer is created in Microsoft Dynamics 365 Commerce.

## Description

When a new customer is created in Commerce headquarters, a welcome email isn't sent to the customer, even though an email notification is configured for the **Customer created** email notification type.

## Resolution

### Set the correct Email ID value for the Customer created email notification type

To set the correct **Email ID** value for the **Customer created** email notification type in headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Commerce email notification profile**.
1. In the left navigation pane, select the email notification profile.
1. Under **Retail event notifications settings**, for the **Customer created** email notification type, set the **Email ID** field to **NewCust**.

## Additional resources

[Set up an email notification profile](../email-notification-profiles.md)
