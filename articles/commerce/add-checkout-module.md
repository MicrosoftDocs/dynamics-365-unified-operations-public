---
# required metadata

title: Checkout module
description: This topic describes how to add a checkout module to a page and set the required properties.
author: anupamar-ms
manager: annbe
ms.date: 07/31/2020
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
[!include [banner](includes/preview-banner.md)]

This topic describes how to add a checkout module to a page and set the required properties.

## Overview

A checkout module is a special container that hosts all modules that are required to create an order. It presents a step-by-step flow that a customer uses to enter all the relevant information to make a purchase. It captures the shipping address, shipping method, and billing information. It also provides an order summary and other information that is related to a customer order.

A checkout module renders data based on the cart ID. This cart ID is saved as a browser cookie. A cart ID is required to render information in the checkout module, such as the items in the order, the total amount, and discounts. 

The following image shows an example of a Fabrikam checkout module on a checkout page.

![Example of a checkout module](./media/Checkout.PNG)

## Checkout module properties

A checkout module shows an order summary and provides the functionality for placing an order. To gather all the customer information that is required before an order can be placed, additional modules must be added to the checkout module. Therefore, retailers have the flexibility to add custome modules to the checkout flow, or to exclude modules, based on their requirements.


| Property name  | Values | Description |
|----------------|--------|-------------|
| Checkout heading | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | Displays a heading for the checkout module. |
| Order summary heading | Heading | Heading for the order summary section of the module|
| Cart line items heading| Heading| Heading for the cart line items shown in the checkout module|
| Show shipping charges on line item| True or False| If True, shows the shipping charges that are applicable for line items on the cart line. If its Header charge with no proration, the shipping charge will be applied at the header level and not line level. This feature was added in 10.0.13|

## Modules that can be used in the checkout module

- **Shipping address** – This module lets a customer add or select the shipping address for an order. For more information on this module, see [Shipping address module](add-shippingaddress-module.md).

    The following image shows an example of a shipping address module on a checkout page.

    ![Example of a shipping address module](./media/ecommerce-shippingaddress.PNG)

- **Delivery options** – This module lets a customer select a mode of delivery for an order. For more information on this module, see [Delivery options module](add-deliveryoptions-module.md).

     The following image shows an example of a delivery options module on a checkout page.
     
    ![Example of a delivery options module](./media/ecommerce-deliveryoptions.PNG)

- **Checkout section container** – This module is a container that you can put multiple modules inside to create a section within the checkout flow. For example, you can put all payment-related modules inside this container to make them appear as one section. This module affects only the layout of the flow.

- **Gift card** – This module lets a customer pay for an order by using a gift card. For more information on this module, see [Gift card module](add-giftcard.md).

- **Loyalty points** – This module lets a customer pay for an order by using loyalty points. It provides a summary of available points and expiring points, and lets the customer select the number of points to redeem. If the customer isn't signed in or isn't a loyalty member, or if the total amount in the cart is 0 (zero), this module is automatically hidden.

- **Payment** – This module lets a customer pay for an order using a credit or debit card. For more information on this module, see [Payment module](add-payment-module.md).

- **Billing address** – This module lets a customer provide billing address for the payment option that they chose. For more information on this module, see [Billing address module](add-payment-module.md).

     The following image shows an example of gift card, loyalty points, payment, and billing address modules on a checkout page.

    ![Example of gift card, loyalty points, payment, and billing address modules](./media/ecommerce-payments.PNG)

- **Contact information** – This module lets a customer add or change the contact information (email address) for an order.

- **Text block** – This module contains any messaging that is driven by the content management system (CMS). For example, it might contain a message that states, "For issues with your order, contact 1-800-Fabrikam." 

- **Checkout terms and conditions** - This module displays rich text to show the terms and conditions and a check box to receive the customer input. The check box is optional and configurable. The information is captured by the module and can be used as a check before order placement is triggered, but is not included in the order summary information. The module can be added to the checkout container, checkout section container, or terms and conditions slots according to business needs. If added to the checkout or checkout section container, it will appear as a step in the checkout process. If added to the terms and conditions slot, it will appear near the place order button.

   ![Example of checkout terms and conditions](./media/ecommerce-checkout-terms.PNG)

## Commerce Scale Unit interaction

Most of the checkout information such as the shipping address and shipping method is stored in the cart and processed as part of the order. The only exception is the credit card information, which is processed directly by using the Adyen payment connector. The payment is authorized but isn't charged until the order is fullfilled.

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
1. In the **Terms and conditions slot**, add a **Checkout terms and conditions** module if needed. In the module properties pane, configure the terms and condition text as appropriate.
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

[Delivery options](add-deliveryoptions-module.md)

[Payment module](add-payment-module.md)

[Gift card module](add-giftcard.md)

[Shipping address module](add-shippingaddress-module.md)
