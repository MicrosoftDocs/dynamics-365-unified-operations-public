---
# required metadata

title: Customize transactional emails by mode of delivery 
description: This topic describes how to set up custom email templates for specific notification types and modes of delivery
author: stuharg
manager: annbe
ms.date: 10/26/2020
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

This topic describes how to set up custom email templates for specific notification types and modes of delivery

## Overview

Transactional emails can now be customized by a combination of notification type (e.g. order created, order packed, order invoiced etc), and mode of delivery (e.g. Overnight, in-store pickup, curbside pickup etc) which enables Retailers to provide order fulfillment experiences for their customers that are tailored to the order's mode of delivery. For example, the Order Packed event can be customized to provide curbside pickup instructions when customers choose curbside pickup, or shipping carrier and delivery information for customers who choose to have their order shipped.

Emails can be customized by mode of delivery for the following notification types:

| **Notification type**      | **Notes**                                                    |
| -------------------------- | ------------------------------------------------------------ |
| Order cancellation         | New email  notification type                                 |
| Order created              |                                                              |
| Order confirmed            |                                                              |
| Order invoiced             | New email  notification type. This notification type can be used in place of the Order  shipped notification type, which will send a notification for any invoice  event with a shipped mode of delivery (i.e. not modes of delivery for pickup,  carryout and electronic) |
| Order picked               |                                                              |
| Order packed               |                                                              |
| Order ready for  pickup    | This notification  type is only customizable by mode of delivery if the Support for multiple  Pickup delivery modes feature switch is enabled. When enabled, this  notification type is functionally equivalent to the order packed notification  type. |
| Payment failed             |                                                              |
| Replacement order  created |                                                              |

> [!NOTE]
> In order to leverage this feature, you will need to enable the **Customize transactional email templates by mode of delivery** feature switch, which is found in Commerce headquarters at **Workspaces \> Feature management**. 

## Configure email templates for specific delivery modes

To customize transactional emails by mode of delivery for a specific notification type, follow the instructions below. 

These instructions assume that you have already created and added your new, custom email templates to **Organization email templates**. Learn more about creating and uploading email templates in [Create email templates for transactional events](email-templates-transactions.md).

To configure email templates for specific delivery modes, follow these steps.

1. In Dynamics 365 headquarters, navigate to Commerce email notification profile
1. Select an existing notification type, or add a new one.
1. While the notification type is selected, click on **Configure modes of delivery**.
1. Click **+New** and select a mode of delivery in the dropdown in the mode of delivery row you just created
1. Select the email template you wish to map to the specific mode of delivery in the dropdown in the Email ID column for the row you just created
1. Check the checkbox in the Active column
1. Add additional modes of delivery and repeat steps 4 through 6, or click OK. 

> [!NOTE]
> - When more than one mode of delivery is present across lines in a sales order, the default template will be used. The default template is the one mapped to the notification type on the Commerce email notification profile page.
> - If a sales order has a mode of delivery that has not been configured for a custom email template, the default email template will be used. 

## Additional resources

[Create call center orders](/tasks/create-call-center-orders.md)

[Change mode of delivery in POS](pos-change-delivery-mode.md)
