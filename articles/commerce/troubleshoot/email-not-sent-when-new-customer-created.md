---
# required metadata

title: Welcome email isn't sent when new customers are created
description: This topic provides troubleshooting guidance for when a welcome email notification isn't sent when a new customer is created in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 05/31/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-02-10
---

# Welcome email isn't sent when new customers are created

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance for when a welcome email notification isn't sent when a new customer is created in Microsoft Dynamics 365 Commerce.

## Description

When a new customer is created in Commerce headquarters, a welcome email isn't sent to the customer, even though an email notification is configured for the **Customer created** email notification type.

## Resolution

### Associate an email notification profile under Commerce parameters

1. In headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters \> General**.
2. In the **Email notification profile** drop-down list, select the email notification profile that contains a mapping between the customer created notification type and a customer created email template.  

> [!NOTE] 
> When you enable customer created notifications, customers that are created in all channels within the legal entity will receive a customer created email. Currently, customer created notifications can't be limited to a single channel.

For more information, see [Create email templates for transactional events](../email-templates-transactions.md). 

## Additional resources

[Set up an email notification profile](../email-notification-profiles.md)
