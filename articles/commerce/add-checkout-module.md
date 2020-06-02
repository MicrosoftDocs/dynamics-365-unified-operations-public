---
# required metadata

title: Checkout module
description: This topic describes how to add a checkout module to a page and set the required properties.
author: anupamar-ms
manager: annbe
ms.date: 05/28/2020
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


[!include [banner](includes/banner.md)]

This topic describes how to add a checkout module to a page and set the required properties.

## Overview

A checkout module is a special container that hosts all modules that are required to create an order. It presents a step-by-step flow that a customer uses to enter all the relevant information to make a purchase. It captures the shipping address, shipping method, and billing information. It also provides an order summary and other information that is related to a customer order.

A checkout module renders data based on the cart ID. This cart ID is saved as a browser cookie. A cart ID is required to render information in the checkout module, such as the items in the order, the total amount, and discounts. 

The following image shows an example of a Fabrikam checkout module on a checkout page.

![Example of a checkout module](./media/Checkout.PNG)

## Checkout module properties

A checkout module shows an order summary and provides the functionality for placing an order. To gather all the customer information that is required before an order can be placed, additional modules must be added to the checkout module. Therefore, retailers have the flexibility to add custom modules to the checkout flow, or to exclude modules, based on their requirements.

### Modules that can be used in the checkout module

- **Shipping address** – This module lets a customer add or select the shipping address for an order. If the customer is signed in, any addresses that were previously saved for that customer are shown. The customer can then select among those addresses. The customer can also add a new address. The shipping address is used for all the items in the order that require shipping. It can't be customized for individual line items. Shipping address formats are defined for each country or region, and the country/region-specific rules are enforced by this module. Although this module doesn't provide address validation, address validation can be implemented through customization. If the order includes only items that will be picked up in the store, this module is automatically hidden.

    The following image shows an example of a shipping address module on a checkout page.

    ![Example of a shipping address module](./media/ecommerce-shippingaddress.PNG)

- **Delivery options** – This module lets a customer select a delivery option for an order. Delivery options are based on the shipping address. If the shipping address is changed, the delivery options must be retrieved again. If the order includes only items that will be picked up in the store, this module is automatically hidden.

    The following image shows an example of a delivery options module on a checkout page.

    ![Example of a delivery options module](./media/ecommerce-deliveryoptions.PNG)

- **Checkout section container** – This module is a container that you can put multiple modules inside to create a section within the checkout flow. For example, you can put all payment-related modules inside this container to make them appear as one section. This module affects only the layout of the flow.
- **Gift card** – This module lets a customer pay for an order by using a gift card. It supports only Microsoft Dynamics 365 Commerce gift cards. One or more gift cards can be applied to an order. If the balance of the gift card doesn't cover the amount in the cart, the gift card can be combined with another payment method. Gift cards can be redeemed only if the customer is signed in.
- **Loyalty points** – This module lets a customer pay for an order by using loyalty points. It provides a summary of available points and expiring points, and lets the customer select the number of points to redeem. If the customer isn't signed in or isn't a loyalty member, or if the total amount in the cart is 0 (zero), this module is automatically hidden.
- **Payment** – This module lets a customer pay for an order by using a credit card. If the total amount in the cart is covered by loyalty points or a gift card, or if it's 0 (zero), this module is automatically hidden. Credit card integration is provided by the Adyen payment connector for this module. For more information about how to use this connector, see [Dynamics 365 Payment Connector for Adyen](dev-itpro/adyen-connector.md).
- **Billing address** – This module lets a customer provide billing information. This information is processed, together with the credit card information, by Adyen. This module includes an option that lets customers use their billing address as the shipping address.

    The following image shows an example of gift card, loyalty points, payment, and billing address modules on a checkout page.

    ![Example of gift card, loyalty points, payment, and billing address modules](./media/ecommerce-payments.PNG)

- **Contact information** – This module lets a customer add or change the contact information (email address) for an order.

- **Text block** – This module contains any messaging that is driven by the content management system (CMS). For example, it might contain a message that states, "For issues with your order, contact 1-800-Fabrikam." 

## Commerce Scale Unit interaction

Most of the checkout information, such as the shipping address and shipping method, is stored in the cart and processed as part of the order. The only exception is the credit card information. This information is processed directly by using the Adyen payment connector. The payment is authorized but isn't charged.

## Add a checkout module to a page and set the required properties

To add a checkout module to a new page and set the required properties, follow these steps.

1. Go to **Page Fragments**, and select **New** to create a new fragment.
1. In the **New Page Fragment** dialog box, select the **Checkout** module.
1. Under **Page Fragment Name**, enter the name **Checkout fragment**, and then select **OK**.
1. Select the **Checkout module** slot.
1. In the properties pane on the right, select the pencil symbol, enter heading text in the field, and then select the check mark symbol.
1. In the **Checkout Information** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Shipping address**, **Delivery options**, **Checkout section container**, and **Contact information** modules, and then select **OK**.
1. In the **Checkout section container** module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Gift card**, **Loyalty**, and **Payment** modules, and then select **OK**. In this way, you make sure that all the payment methods appear together in a section.
1. Select **Save**, and then select **Preview** to preview the fragment. Some modules that don't have a cart context might not be rendered in the preview.
1. Select **Finish editing** to check in the fragment, and then select **Publish** to publish it.
1. Create a template that uses the new checkout fragment.
1. Create a checkout page that uses the new template.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)
