---
title: Customize transactional emails by mode of delivery
description: Learn how to set up custom email templates for specific notification types and modes of delivery in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 01/21/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-10-26
ms.custom: 
  - bap-template
---

# Customize transactional emails by mode of delivery

[!include [banner](includes/banner.md)]

This article describes how to set up custom email templates for specific notification types and modes of delivery in Microsoft Dynamics 365 Commerce.

You can customize transactional emails for a combination of a notification type (for example, **Order created**, **Order packed**, or **Order invoiced**) and a mode of delivery (for example, overnight, in-store pickup, or curbside pickup). When retailers use custom transactional emails, they can provide their customers with order fulfillment experiences that are tailored to the order's mode of delivery. For example, you can customize the "order packed" event so that it provides curbside pickup instructions for customers who choose curbside pickup. Alternatively, it can provide shipping carrier and delivery information for customers who choose to have their order shipped.

> [!NOTE]
> To use the functionality for customized transactional emails, first turn on the **Customize transactional email templates by mode of delivery** feature by going to **Workspaces \> Feature management** in Commerce headquarters.

You can customize emails by mode of delivery for the following notification types:

- **Order cancellation** – This email notification type is new.
- **Order created**
- **Order confirmed**
- **Order invoiced** – This email notification type is new. Use it instead of the **Order shipped** notification type. The **Order shipped** notification type sends a notification for any invoice event that has a shipped mode of delivery (not a pickup, carry out, or electronic mode of delivery).
- **Order picked**
- **Order packed**
- **Order ready for pickup** – You can customize this notification type by mode of delivery only if the **Support for multiple pickup delivery modes** feature is turned on. In that case, this notification type is functionally equivalent to the **Order packed** notification type.
- **Payment failed**
- **Replacement order created**

## Configure email templates for specific modes of delivery

This procedure assumes that you already created your custom email templates and added them to the **Organization email templates** page. For information about how to create and upload email templates, see [Create email templates for transactional events](email-templates-transactions.md).

To configure email templates for specific modes of delivery in Commerce headquarters, follow these steps:

1. Go to **Commerce email notification profile**.
1. Under **Retail event notification settings**, select an existing notification type.
1. While the notification type is still selected, select **Configure modes of delivery**.
1. In the **Modes of delivery** dialog box, select **New**.
1. In the new row, in the **Mode of delivery** field, select a mode of delivery.
1. In the **Email ID** field, select the email template to map to the mode of delivery.
1. Select the **Active** check box.
1. Repeat steps 4 through 7 to add more modes of delivery.
1. When you finish, select **OK**.

> [!NOTE]
> - When more than one mode of delivery is present across lines in a sales order, the default template is used. The default template is the template that is mapped to the notification type on the **Commerce email notification profile** page.
> - If a sales order has a mode of delivery that isn't configured for a custom email template, the default email template is used.

## Additional resources

[Create call center orders](tasks/create-call-center-orders.md)

[Change mode of delivery in POS](pos-change-delivery-mode.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
