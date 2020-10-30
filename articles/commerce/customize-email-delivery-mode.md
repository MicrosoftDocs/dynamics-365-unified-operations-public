---
# required metadata

title: Customize transactional emails by mode of delivery 
description: This topic describes how to set up custom email templates for specific notification types and modes of delivery in Microsoft Dynamics 365 Commerce.
author: stuharg
manager: annbe
ms.date: 10/30/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Commerce, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2020-10-26
ms.dyn365.ops.version: Release 10.0.16

---

# Customize transactional emails by mode of delivery

[!include [banner](includes/banner.md)]

This topic describes how to set up custom email templates for specific notification types and modes of delivery in Microsoft Dynamics 365 Commerce.

## Overview

Transactional emails can now be customized by a combination of notification type (for example, order created, order packed, or order invoiced) and mode of delivery (for example, overnight, in-store pickup, or curbside pickup). Custom transactional emails enable retailers to provide order fulfillment experiences for their customers that are tailored to the order's mode of delivery. For example, the "order packed" event can be customized to provide curbside pickup instructions when customers choose curbside pickup, or shipping carrier and delivery information for customers who choose to have their order shipped.

Emails can be customized by mode of delivery for the following notification types:

| **Notification type**      | **Notes**                                                    |
| -------------------------- | ------------------------------------------------------------ |
| Order cancellation         | New email notification type                                 |
| Order created              |                                                              |
| Order confirmed            |                                                              |
| Order invoiced             | New email notification type. This notification type can be used in place of the "order shipped" notification type, which will send a notification for any invoice event with a shipped mode of delivery (not for pickup, carry out, and electronic modes of delivery). |
| Order picked               |                                                              |
| Order packed               |                                                              |
| Order ready for pickup    | This notification type is only customizable by mode of delivery if the support for multiple pickup delivery modes feature switch is enabled. When enabled, this notification type is functionally equivalent to the "order packed" notification type. |
| Payment failed             |                                                              |
| Replacement order created |                                                              |

> [!NOTE]
> In order to use the customized transactional email feature, you first must enable the **Customize transactional email templates by mode of delivery** feature switch, which is found in Commerce headquarters at **Workspaces \> Feature management**. 

## Configure email templates for specific delivery modes

These instructions assume that you have already created and added your new, custom email templates to **Organization email templates**. For more information about creating and uploading email templates, see [Create email templates for transactional events](email-templates-transactions.md).

To configure email templates for specific delivery modes in Commerce headquarters, follow these steps.

1. Go to **Commerce email notification profile**.
1. Under **Retail event notification settings**, select an existing notification type, or add a new one.
1. While the notification type is selected, select **Configure modes of delivery**.
1. Select **+New**. A new notification type row appears under **Retail event notification settings**.
1. In the **Email notification type** column, select a mode of delivery from the drop-down menu options.
1. In the **Email ID** column, select the email template you want to map to the specific mode of delivery from the drop-down menu options.
1. In the **Active** column, select the check box. 
1. Add additional modes of delivery by repeating steps 4 through 6 above, or if done select **OK**. 

> [!NOTE]
> - When more than one mode of delivery is present across lines in a sales order, the default template will be used. The default template is the one mapped to the notification type on the Commerce email notification profile page.
> - If a sales order has a mode of delivery that has not been configured for a custom email template, the default email template will be used. 

## Additional resources

[Create call center orders](/tasks/create-call-center-orders.md)

[Change mode of delivery in POS](pos-change-delivery-mode.md)
