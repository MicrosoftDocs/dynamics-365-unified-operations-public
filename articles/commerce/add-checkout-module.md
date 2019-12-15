---
# required metadata

title: Checkout module
description: This topic describes how to add a checkout module to a page and set the required properties.
author: anupamar-ms
manager: annbe
ms.date: 10/31/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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

# Checkout module

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic describes how to add a checkout module to a page and set the required properties.

## Overview

A checkout module is a special container that hosts all the modules that are required to create an order. A checkout module captures shipping address, shipping methods, billing information. It provides order summary, and other information that is related to a customer order. It presents a step-by-step flow that a customer uses to enter all the relevant information to make a purchase.

A checkout module renders data based on the cart ID. This cart ID is saved as a browser cookie. A cart ID is required to render information in the checkout module, such as the items in the order, the total amount, and discounts.

## Checkout module properties

A checkout module shows Order summary and has a Place order action. For all other information that needs to be captured before placing an order, the respective modules need to be added. This gives the flexibilty to add custom modules and/or not show certain modules on the Checkout flow based on the needs of the retailer.


### Modules that can be used in the checkout module

- **Shipping address** – This module lets a customer add or select the shipping address for an order. If the customer is signed in, any addresses that were previously saved for that customer are shown. The customer can then select among those addresses. The customer can also add a new address. The shipping address is used for all the items in the order that require shipping. It can't be customized for individual line items. Shipping address formats are defined for each country or region, and the country/region-specific rules are enforced by this module. Although this module doesn't provide address validation, address validation can be implemented through customization. If the order includes only items that will be picked up in the store, this module is automatically hidden.
- **Delivery options** – This module lets a customer select a delivery option for an order. Delivery options are based on the shipping address. If the shipping address is changed, the delivery options must be retrieved again. If the order includes only items that will be picked up in the store, this module is automatically hidden.
- **Checkout section container** – This module is a container that you can put multiple modules inside to create a section within the checkout flow. For example, you can put all payment-related modules inside this container to make them appear as one section. This module affects only the layout of the flow.
- **Gift card** – This module lets a customer pay for an order by using a gift card. It supports only Microsoft Dynamics 365 Commerce gift cards. One or more gift cards can be applied to an order. If the balance of the gift card doesn't cover the amount in the cart, the gift card can be combined with another payment method. Gift cards can be redeemed only if the customer is signed in.
- **Loyalty points** – This module lets a customer pay for an order by using loyalty points. It provides a summary of available points and expiring points, and lets the customer select the number of points to redeem. If the customer isn't signed in or isn't a loyalty member, or if the total amount in the cart is 0 (zero), this module is automatically hidden.
- **Payment** – This module lets a customer pay for an order by using a credit card. If the total amount in the cart is covered by loyalty points or a gift card, or if it's 0 (zero), this module is automatically hidden. Credit card integration is provided by the Adyen payment connector for this module. For more information about how to use this connector, see [Adyen payment connector](https://).
- **Billing address** – This module lets a customer provide billing information. This information is processed, together with the credit card information, by Adyen. This module includes an option that lets customers use their billing address as the shipping address.
- **Contact information** – This module lets a customer add or change the contact information (email address) for an order.
- **Textblock** – This module contains any messaging that is driven by the content management system (CMS). For example, it might contain a message that states, "For issues with your order, please contact 1-800-FABRIKAM." 

## Retail server interaction

Most of the checkout information, such as the shipping address and shipping method, is stored in the cart and processed as part of the order. The only exception is the credit card information. This information is processed directly by using the Adyen payment connector. The payment is authorized but isn't charged.

## Add a checkout module to a new page and set the required properties

To add a checkout module to a new page and set the required properties, follow these steps.

1. Go to **Fragment \> New Fragment**, and name the new fragment **Checkout fragment**.
2. Add a checkout module to the fragment.
3. Add a heading to the checkout module.
4. Add shipping address, delivery options, checkout section container, and contact information modules. 
5. In the checkout section container module, add gift card, loyalty points, and  payment modules. In this way, you make sure that all the payment methods appear together in a section.
9. Select **Save**. Some modules might not be rendered in the preview, because they don't have a cart context.
10. Finish editing  and publish it.
11. Create a template that uses the new checkout fragment.
12. Create a checkout page that uses the new template.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
