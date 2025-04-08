---
title: Enable customer check-in notifications in point of sale (POS)
description: This article describes how to enable customer check-in notifications in Microsoft Dynamics 365 Commerce point of sale (POS).
author: bicyclingfool
ms.date: 08/02/2024
ms.topic: how-to
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: global
ms.author: anvenkat
ms.search.validFrom: 2021-04-01
ms.custom: 
  - bap-template 
---

# Enable customer check-in notifications in point of sale (POS)

[!include [banner](includes/banner.md)]

This article describes how to enable customer check-in notifications in Microsoft Dynamics 365 Commerce point of sale (POS).

In their "order ready for pickup" emails, organizations can provide a link or button that lets customers notify the store that they are on the premises and waiting for their package to be brought out to them. Customers then receive a check-in confirmation, and the store receives a notification as a task in its POS application. This task serves as a prompt for a sales associate to deliver the order to the customer's vehicle. Therefore, the customer doesn't have to enter the store.

The customer check-in workflow can also be configured to collect additional information from customers, such as their parking spot number, the make, model, and color of their vehicle, and delivery instructions. The retail store attendant can use this information to facilitate order fulfillment.

## Enable customer check-in

When the customer check-in feature is turned on, Commerce generates an order confirmation ID (also known as the channel reference ID). It also generates order confirmation IDs for orders that are created through point of sale (POS) or call center channels. 

To turn on the customer check-in feature in Commerce headquarters, follow these steps.

1. Go to **Workspaces \> Feature management**.
2. Search for the **Generate a consistent channel reference ID format across channels** feature. 
3. Select the feature, and then select **Enable now** in the properties pane. 

## Create a check-in confirmation page

On your e-commerce site, you must create a new page that will serve as the check-in confirmation experience. Through additional configuration, the page can also include a form that collects additional information from customers to facilitate order fulfillment. For information about how to set up the page and module, see [Customer check-in module](check-in-pickup-module.md).

## Configure the transactional email template

You must add an **I am here** link or button to the template for the transactional email that customers receive when their order is ready for pickup. Customers will use this link or button to notify the store that they have arrived to pick up their order. 

Add the link or button to the template that is mapped to the **Packing completed** notification type and the mode of delivery that you're using for curbside order fulfillment. In the template, create an HTML link or button that points to the URL of the check-in confirmation page that you created, and that includes the parameter names and values, as shown in the following example.

`<a href="https://[YOUR_SITE_DOMAIN]/[CHECK-IN_CONFIRMATION_PAGE]?channelReferenceId=%confirmationid%&channelId=%channelid%&packingSlipId=%packingslipid%" target="_blank">I am here!</a>`

For more information about how to configure email templates, see [Customize transactional emails by mode of delivery](customize-email-delivery-mode.md). 

## A check-in confirmation task is created in POS

After a customer notifies the store that they are present for pickup, the check-in page shows a confirmation message and an optional QR code that contains the customer's order confirmation ID. At the same time, a task is created in the tasks list in POS for the store where the customer is picking up the order. That task contains all the customer and order information that is required to fulfill the order. The instructions field of the task shows any information that was collected from the customer through the additional information form.

## End-to-end testing

Customer check-in requires that specific parameters and values be passed to the check-in page and then to the customer check-in API. Therefore, the easiest approach is to test the feature in an environment where a test order can be created and packed. In that way, an "order ready for pickup" email can be generated that has a URL that contains the required parameter names and values.

To test the customer check-in feature, follow these steps.

1. Create the customer check-in page, and then add and configure the customer check-in module. For more information, see [Check-in for pickup module](check-in-pickup-module.md). 
1. Check in the page, but don't publish it.
1. Add the following link to an email template that is invoked by the packing complete notification type for a pick-up mode of delivery. For more information, see [Create email templates for transactional events](email-templates-transactions.md).

    - **For pre-production (UAT) environments:** Add the code snippet from the [Configure the transactional email template](#configure-the-transactional-email-template) section earlier in this article.
    - **For production environments:** Add the following commented code so that existing customers aren't affected.

        `<!-- https://[DOMAIN]/[CHECK_IN_PAGE]?channelReferenceId=%confirmationid%&channelId=%pickupchannelid%&packingSlipId=%packingslipid%&preview=inprogress -->`

1. Create an order where the pick-up mode of delivery is specified.
1. When you receive the email that is triggered by the packing complete notification type, test the check-in flow by opening the check-in page that has the URL that you added earlier. Because the URL includes the `&preview=inprogress` flag, you will be prompted to authenticate before you can view the page.
1. Enter any additional information that is required to configure the module.
1. Verify that the check-in confirmation view is shown correctly.
1. Open a POS terminal for the store where the order will be picked up.
1. Select the **Orders to pick up** tile, and verify that the order appears.
1. Verify that any additional information that was configured in the check-in module appears in the details pane.

After you've verified that the customer check-in feature works from end to end, follow these steps.

1. Publish the check-in page.
1. If you're testing in a production environment, uncomment the URL in the "order ready for pickup" email template, so that the **I am here** link or button is shown. Then reupload the template.

## Additional resources

[Check-in for pickup module](check-in-pickup-module.md)

[Customize transactional emails by mode of delivery](customize-email-delivery-mode.md)

[Create email templates for transactional events](email-templates-transactions.md)
