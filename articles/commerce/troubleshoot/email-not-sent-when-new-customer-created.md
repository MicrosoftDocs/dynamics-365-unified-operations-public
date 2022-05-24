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

### Associate an email notification profile under Commerce parameters

1. In headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
2. In the email notification profile field under the **General** tab, select the email notification profile that contains a mapping between the customer created notification type and a customer created email template.  

> [!NOTE] 
> When customer created notifications are enabled, customers that are created in all channels within the legal entity will receive a customer created email. Customer created notifications cannot currently be limited to a single channel.

For more information about how to configure the customer created notification type, see the [Customer created](../email-templates-transactions.md#customer-created) section in the [Create email templates for transactional events](../email-templates-transactions.md) help topic. 

## Additional resources

[Set up an email notification profile](../email-notification-profiles.md)
