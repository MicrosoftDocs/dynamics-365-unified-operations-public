---
# required metadata

title: Add a checkout module to a page
description: This topic describes how to add a checkout module to a page and set the required properties.
author: anupamar-ms
manager: annbe
ms.date: 0/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Add a checkout module to a page 

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to add a checkout module to a page and set the required properties.

## Overview

A checkout module is container that is used for hosting all the modules that are necessary to create an order. A checkout module can include modules that handle shipping address, shipping methods, billing information, order summary, and other infomation related to a customer order. It presents a step-by-step flow for the customer to enter all the relevant information needed to make a purchase.  

A checkout module renders data based on the cart id, which is derived from the page context. This means that a checkout module cannot be used on a page that does not have the cart context, like a marketing or home page. 

## Properties of the checkout module 

A checkout module appears to the customer as a series of steps that handle information such as shipping address, shipping method, etc. The section heading for each step is authored in the checkout module with a heading tag. A width property can be configured to indicate if items in the module should fit to width or fill the screen.  

A checkout module has multiple slots that can contain other modules such as a checkout information module, order summary module, and place order module. Each slot supports a set of modules that will appear in a specific layout on the page. For example, the checkout information slot contains all of the modules needed to trigger a checkout, such as shipping address and payment method. The order summary slot shows the order summary and place order action. The place order slot also supports place order action. To optimize placing orders from various platforms, there are two slots where place order modules can be defined.  

### Modules available in Checkout 

**Shipping address:** This module enables a customer to add or select the shipping address for the order. If the customer is signed in, any address that was previously saved will be displayed for the customer to choose from. The customer can also add a new address. The shipping address is for all items in the order that require shipping and cannot be customized on a line item basis. Shipping address formats are defined per country, which is respected by the shipping address module. The module does not provide address validation, although address validation can be implemented using a customization. 

**Delivery options:** This module enables the customer to choose a delivery option for the order. Delivery options is based on the shipping address. If the shipping address is changed, the delivery options must retrieved again.  

**Checkout section container:** This module is a container that allows multiple modules to be placed inside to create a section within the Checkout flow.  For example, all payment modules can be configured inside this container to make them appear as one section. This container is added only to control the layout of the flow. 

**Gift card:** This module enables the customer to pay for the order using a gift card. This module supports Dynamics 365 Commerce gift cards only. One or more gift cards can be applied to an order. If the gift card balance is not sufficient, it can be combined with another payment method method.  

**Loyalty points:** This module enables the customer to pay for the order using loyalty points. It provides a summary of available points and expiring points, and allows the customer choose the amount they want to redeem using points. If the customer is not signed in or not a loyalty member, this module will be hidden. 

**Credit card:** This module enables the customer to pay for the order using credit card. Credit card integration is provided using the Adyen payment connector. See [Adyen payment connector](https://) for more details on how to use this connector. 

**Billing address**:** This module enables the customer to provide billing information, which is processed (along with credit card information) by Adyen. It has an option to use the customer's billing address as the shipping address if the customer prefers to do so.  
**Contact information:** This module enables the customer to add or change the contact information (email) for the order. 

**Place order**: This module enables the customer to place the order. A link must be configured in the module to point to the order confirmation page.  

**Content rich block**: This module is used to contain any CMS-driven messaging, for example "For issues with your order, please contact 1-800-FABRIKAM." 

**Order summary**: This module is used to show the cost breakdown of the order. 

**Order line items:** This module is used to show a summary of the items that will be included in the order.

## Retail server interaction 

All the checkout information such as shipping address and shipping methods are stored in the cart and processed as part of the order. The only exception is the credit card information, which is processed directly using Adyen payment connector. The payment is authorized but not charged. 

## Add a checkout module to a new page and set the required properties  

To add a checkout module to a new page and set the required properties, do the following.

1. In tooling, create a new page template “Checkout template”.
2. In the Main slot of the template, add Checkout.
3. Check-in and Publish.
4. Now create a new page with the “Checkout template” and call it “Checkout page”.
5. On the page outline, add Default page.
6. To the Default page, add Checkout module.
7. Add a Heading for the page. Add a section heading for each section of the Checkout – Shipping address, Shipping Methods, Payment information, Contact information.
8. To the Checkout information slot, add Shipping address module.
9. To the Checkout information slot, add Delivery options module.
10. To the Checkout information slot, add Checkout section container module.
11. To the Checkout section container, add Gift Card, Loyalty and Credit card modules. This will ensure all payment methods appear within a section. 
12. To the Checkout information slot, add Contact information module.
13. In the above setup, there should be 4 sections on the Checkout information slot.
14. In the Order summary slot, add  order summary module and place order module.
15. In the order summary slot, add a content rich block with text “For questions on orders, contact 1-800-FABRIKAM”.
16. In the Place order slot, add place order module.
17. Save and Preview. Some modules may not render in preview as they don’t have a Cart context.
18. Check-in and Publish.
    

Checkout can be built as a Fragment <link> since there is only one instance of Checkout. 
