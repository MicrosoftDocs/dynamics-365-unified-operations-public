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

# Add a checkout module to a page 

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to add a checkout module to a page and set the required properties.

## Overview

A checkout module is a special container that hosts all the modules that are required to create an order. A checkout module can include modules that handle the shipping address, shipping methods, billing information, order summary, and other information that is related to a customer order. It presents a step-by-step flow that a customer uses to enter all the relevant information to make a purchase.

A checkout module renders data based on the cart ID. This cart ID is saved as a browser cookie. A cart ID is required to render information in the checkout module, such as the items in the order, the total amount, and discounts.

## Checkout module properties

A checkout module hosts a set of modules inside it. A width property lets you specify whether the items in the checkout module should fit the width of it or fill the screen.

A checkout module has multiple slots, such as a **Checkout information** slot, an **Order summary** slot, and a **Place order** slot. Each slot supports a set of modules that will appear in a specific layout on the page. For example, the **Checkout information** slot contains all the modules that are required to trigger a checkout, such as modules for the shipping address and payment method. The **Order summary** slot shows an order summary and supports the action for placing the order. The **Place order** slot also supports the action for placing the order. Place order modules can be defined in two slots to optimize the process of placing orders from various platforms.

### Modules that can be used in the checkout module

- **Shipping address** – This module lets a customer add or select the shipping address for an order. If the customer is signed in, any addresses that were previously saved for that customer are shown. The customer can then select among those addresses. The customer can also add a new address. The shipping address is used for all the items in the order that require shipping. It can't be customized for individual line items. Shipping address formats are defined for each country or region, and the country/region-specific rules are enforced by this module. Although this module doesn't provide address validation, address validation can be implemented through customization. If the order includes only items that will be picked up in the store, this module is automatically hidden.
- **Delivery options** – This module lets a customer select a delivery option for an order. Delivery options are based on the shipping address. If the shipping address is changed, the delivery options must be retrieved again. If the order includes only items that will be picked up in the store, this module is automatically hidden.
- **Checkout section container** – This module is a container that you can put multiple modules inside to create a section within the checkout flow. For example, you can put all payment-related modules inside this container to make them appear as one section. This module affects only the layout of the flow.
- **Gift card** – This module lets a customer pay for an order by using a gift card. It supports only Microsoft Dynamics 365 Commerce gift cards. One or more gift cards can be applied to an order. If the balance of the gift card doesn't cover the amount in the cart, the gift card can be combined with another payment method. Gift cards can be redeemed only if the customer is signed in.
- **Loyalty points** – This module lets a customer pay for an order by using loyalty points. It provides a summary of available points and expiring points, and lets the customer select the number of points to redeem. If the customer isn't signed in or isn't a loyalty member, or if the total amount in the cart is 0 (zero), this module is automatically hidden.
- **Credit card** – This module lets a customer pay for an order by using a credit card. If the total amount in the cart is covered by loyalty points or a gift card, or if it's 0 (zero), this module is automatically hidden. Credit card integration is provided by the Adyen payment connector. For more information about how to use this connector, see [Adyen payment connector](https://).
- **Billing address** – This module lets a customer provide billing information. This information is processed, together with the credit card information, by Adyen. This module includes an option that lets customers use their billing address as the shipping address.
- **Contact information** – This module lets a customer add or change the contact information (email address) for an order.
- **Place order** – This module lets a customer place an order.
- **Content rich block** – This module contains any messaging that is driven by the content management system (CMS). For example, it might contain a message that states, "For issues with your order, please contact 1-800-FABRIKAM." 
- **Order summary** – This module shows the cost breakdown of an order.
- **Order line items** – This module shows a summary of the items that will be included in an order.

## Retail server interaction

Most of the checkout information, such as the shipping address and shipping method, is stored in the cart and processed as part of the order. The only exception is the credit card information. This information is processed directly by using the Adyen payment connector. The payment is authorized but isn't charged.

## Add a checkout module to a new page and set the required properties

To add a checkout module to a new page and set the required properties, follow these steps.

1. Go to **Fragment \> New Fragment**, and name the new fragment **Checkout fragment**.
1. Add a checkout module to the fragment.
1. Add a heading to the checkout module.
1. In the **Checkout information** slot, add shipping address, delivery options, checkout section container, and contact information modules. There should now be four sections in the **Checkout information** slot.
1. In the checkout section container module, add gift card, loyalty points, and credit card modules. In this way, you make sure that all the payment methods appear together in a section.
1. In the **Order summary** slot, add order summary, place order, and content rich block modules.
1. In the content rich block module, add the following text: **For questions about your order, contact 1-800-FABRIKAM.**
1. In the **Place order** slot, add a place order module.
1. Select **Save**. Some modules might not be rendered in the preview, because they don't have a cart context.
1. Check the fragment in, and publish it.
1. Create a template that uses the new checkout fragment.
1. Create a checkout page that uses the new template.
