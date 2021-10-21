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

This topic describes how to enable customer check-in notifications in Microsoft Dynamics 365 Commerce point of sale (POS).

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

Add the link or button to the template that is mapped to the **Packing completed** notification type and the mode of delivery that you're using for curbside order fulfillment. In the template, create an HTML link or button that points to the URL of the check-in confirmation page that you created and includes the parameter names and values shown in this example.

```
<a href="https://[YOUR_SITE_DOMAIN]/[CHECK-IN_CONFIRMATION_PAGE]?channelReferenceId=%confirmationid%&channelId=%channelid%&packingSlipId=%packingslipid%" target="_blank">I am here!</a>
```
For more information about how to configure email templates, see [Customize transactional emails by mode of delivery](customize-email-delivery-mode.md). 

## A check-in confirmation task is created in POS

After a customer notifies the store that they are present for pickup, the check in page displays a confirmation message and optional QR code that contains their order confirmation id. At the same time, a task is created in the tasks list in POS for the store where the customer is picking up the order. The task contains all the customer and order information that is required to fulfill the order. In the task, the instructions field shows any information that was collected from the customer through the additional information form.

## End-to-end testing

Customer check-in relies on the passing of certain parameters and values to the check-in page, and then on to the customer check-in API. Because of this, it is easiest to test the feature in an environment where a test order can be created and packed so that an order ready pick-up email can be generated with a URL that contains the necessary parameter names and values.

To test the customer check-in feature: 

1. Create customer check-in page, add the customer check-in module and configure it. See the [Check-in for pickup module](check-in-pickup-module.md) help topic for additional information. 

2. Check in the page (but don’t publish it).

3. Add the following link to an email template that is invoked by the packing complete notification type for a pick-up mode of delivery. See the [Create email templates for transactional events](email-templates-transactions.md) help topic for instructions:

4. - **Pre-production (UAT) environments**: add the code snippet from the Configure the transactional email templates section above.

5. - **Production environments:** add the following commented code so that existing customers aren't affected: 
     `<!-- https://[DOMAIN]/[CHECK_IN_PAGE]?channelReferenceId=%confirmationid%&channelId=%pickupchannelid%&packingSlipId=%packingslipid%&preview=inprogress -->`

6. Create an order whose mode of delivery is a pick-up mode of delivery.

7. When you receive the email triggered by the packing complete notification type, test the check-in flow by navigating to the check-in page with the URL you added above. You will be asked to authenticate in order to see the page because the URL has the &preview=inprogress flag.

8. Enter the additional information if configured in the module.

9. Verify that the check-in confirmation view displays correctly.

10. Launch a point of sale terminal for the store where the order will be picked up.

11. Click the **Orders to pick up** tile and verify that the order appears.

12. Verify that the additional information appears in the details pane, if configured in the module.

Once you’ve verified that customer check-in is working end-to-end:

1. Publish the check-in page.
2. If testing in production, uncomment the URL in the ready for pickup email template to display the "I am here" link or button and re-upload the template. 

## Additional resources

[Check-in for pickup module](check-in-pickup-module.md)

[Customize transactional emails by mode of delivery](customize-email-delivery-mode.md)

[Create email templates for transactional events](email-templates-transactions.md)

