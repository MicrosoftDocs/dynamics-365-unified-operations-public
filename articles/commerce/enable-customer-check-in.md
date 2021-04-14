---
# required metadata

title: Enable customer check-in notifications in point of sale (POS)
description: This topic describes how to enable customer check-in notifications in Microsoft Dynamics 365 Commerce point of sale (POS).
author: bicyclingfool
ms.date: 04/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
# ms.search.industry: Retail
ms.author: stuharg
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.19

---

# Enable customer check-in notifications in point of sale (POS)

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to enable customer check-in notifications in Microsoft Dynamics 365 Commerce point of sale (POS).

Organizations can provide a link or button in "order ready for pickup" emails that let their customers notify the store that they are on the premises and waiting for their package to be brought out to them. When customers notify the store that they are present, they will receive a check-in confirmation and the store will receive a notification as a task in their POS application. This task serves as a prompt for a sales associate to deliver the order to the customer's vehicle without the customer having to enter the store.

The customer check-in workflow can also be configured to collect additional information from the customer such as parking spot number, automobile make/model/color, and delivery instructions that the retail store attendant can use to facilitate order fulfillment.

## Enable customer check-in

When the customer check-in feature is enabled, Commerce generates a order confirmation ID (also known as the channel reference ID), and also generates order confirmation IDs for orders created through point of sale (POS) or call center channels. 

To enable the customer check-in feature in Commerce headquarters, follow these steps.

1. Go to **Workspaces \> Feature management**.
2. Search for the **Generate a consistent channel reference ID format across channels** feature. 
3. Select the feature, and then select **Enable now** in the properties pane. 

## Create a check-in confirmation page

You'll need to create a new page on your e-commerce site that will serve as the check-in confirmation experience. With additional configuration, the page can also include a form for collecting additional information from customers to facilitate order fulfillment. For information on how to set up the page and module, see [Customer check-in module](check-in-pickup-module.md).

## Configure the transactional email template

You will need to add an "I am here" link or button to the template for the transactional email that customers receive when their order has been readied for pickup. Customers will use this link or button to notify the store they have arrived to pick up their order. 

Add the link or button to the template that is mapped to the **Packing completed** notification type and the mode of delivery that you are using for curbside order fulfillment. Within the template, create an HTML link or button that points to the URL of the check-in confirmation page you created, as shown in the following example:

```
<a href="https://[YOUR_SITE_DOMAIN]/[CHECK-IN_CONFIRMATION_PAGE]?channelReferenceId=%channelreferenceid%&channelId=%channelid%&packingSlipId=%packingslipid%" target="_blank">I am here!</a>
```
For more information about configuring email templates, see [Customize transactional emails by mode of delivery](customize-email-delivery-mode.md). 

## Check-in confirmation task created in POS

After a customer notifies a store that they are present for pickup and receive a check-in confirmation, a task is created in the tasks list in POS for the store where they're picking up the order. The task contains all the necessary customer and order information needed to fulfill the order. Any information collected from the customer in the additional information screen will be displayed in the instructions field within the task. 

## Additional resources

[Customer check-in module](check-in-pickup-module.md)

