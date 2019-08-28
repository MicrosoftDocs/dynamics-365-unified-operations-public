---
# required metadata

title: Add a checkout module to a page
description: This topic describes how to add a checkout module to a page and set the required properties.
author: anupamar-ms
manager: annbe
ms.date: 10/01/2019
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

# e-Commerce checkout 

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to add a checkout module to a page and set the required properties.

## Overview

A checkout module is container that is used for hosting all the modules that are necessary to create an order. A checkout module can include modules that handle shipping address, shipping methods, billing information, order summary, and other infomation related to a customer order. It presents a step-by-step flow for the customer to enter all the relevant information needed to make a purchase.  

A checkout module renders data based on the cart ID, which is saved as a browser cookie. This cart id required to render the information on checkout module - items in the order, total amount, discounts etc.

## Checkout module properties

Checkout module is a special container that hosts a set of modules within it. A width property can be configured to specify if items in the module should fit to width or fill the screen.  

A checkout module has multiple slots that can contain other modules such as a checkout information module, order summary module, or place order module. Each slot supports a set of modules that will appear in a specific layout on the page. For example, the checkout information slot contains all of the modules needed to trigger a checkout, such as shipping address and payment method. The order summary slot shows the order summary and place order action. The place order slot also supports place order action. To optimize placing orders from various platforms, there are two slots where place order modules can be defined.  

### Modules available for use in the checkout module 

**Shipping address:** This module enables a customer to add or select the shipping address for the order. If the customer is signed in, any address that was previously saved will be displayed for the customer to choose from. The customer can also add a new address. The shipping address is for all items in the order that require shipping and cannot be customized on a line item basis. Shipping address formats are defined per country, and these rules are enforced by the shipping address module. The module does not provide address validation, although address validation can be implemented using customization. If the order has only items for pick-up in store, this module will be automatically hidden. 

**Delivery options:** This module enables the customer to choose a delivery option for the order. Delivery options are based on the shipping address. If the shipping address is changed, the delivery options must retrieved again.  If the order has only items for pick-up in store, this module will be automatically hidden. 

**Checkout section container:** This module is a container that allows multiple modules to be placed inside to create a section within the checkout flow.  For example, all payment modules can be configured inside this container to make them appear as one section. This container is only added to control the layout of the flow. 

**Gift card:** This module enables the customer to pay for the order using a gift card. This module only supports Dynamics 365 Commerce gift cards. One or more gift cards can be applied to an order. If the gift card balance is not sufficient, it can be combined with another payment method method.  Gift card can be redeemed only if the user is signed-in. 

**Loyalty points:** This module enables the customer to pay for the order using loyalty points. It provides a summary of available points and expiring points, and allows the customer to choose the amount of points they want to redeem. If the customer is not signed in or not a loyalty member, this module will be hidden. 

**Credit card:** This module enables the customer to pay for the order using a credit card. Credit card integration is provided using the Adyen payment connector. See [Adyen payment connector](https://) for more details on how to use this connector. 

**Billing address**:** This module enables the customer to provide billing information, which is processed (along with credit card information) by Adyen. It has an option to use the customer's billing address as the shipping address if the customer prefers to do so.  
**Contact information:** This module enables the customer to add or change the contact information (email) for the order. 

**Place order**: This module enables the customer to place the order. 

**Content rich block**: This module is used to contain any CMS-driven messaging, for example "For issues with your order, please contact 1-800-FABRIKAM." 

**Order summary**: This module is used to show the cost breakdown of the order. 

**Order line items:** This module is used to show a summary of the items that will be included in the order.

## Retail server interaction 

Checkout information such as shipping address and shipping method are stored in the cart and processed as part of the order. The only exception is the credit card information, which is processed directly using the Adyen payment connector. The payment is authorized but not charged. 

## Add a checkout module to a new page and set the required properties  

To add a checkout module to a new page and set the required properties, do the following.

1. Go to **Fragment > New Fragment** and name the new fragment "Checkout fragment."
2. Add a checkout module to the fragment. Add a heading to the module
3. In the **Checkout information** slot, add shipping address, delivery options, checkout section container, and contact information modules. There should now be four sections in the **Checkout information** slot.
4. In the **Checkout section container** module, add gift card, loyalty and credit card modules. This will ensure that all payment methods appear within a section. 
5. In the **Order summary** slot, add order summary, place order, and content rich block modules. 
6. In the content rich block module, add the text "For questions about your order, contact 1-800-FABRIKAM."
7. In the **Place order** slot, add a place order module.
8. Save. Some modules may not render in preview as they don't have a cart context.
9. Check in and publish the fragment.
10. Create a template with the Checkout fragment
11. Create a Checkout page with this template
  
