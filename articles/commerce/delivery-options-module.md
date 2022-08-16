---
title: Delivery options module
description: This article covers delivery options modules and explains how to configure them in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 02/24/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.13
ms.custom: 
ms.assetid: 
---

# Delivery options module

[!include [banner](includes/banner.md)]

This article covers delivery options modules and explains how to configure them in Microsoft Dynamics 365 Commerce.

Delivery options modules let customers select a mode of delivery such as shipping or pickup for their online order. A shipping address is required to determine the mode of delivery. If the shipping address changes, the delivery options must be retrieved again. If an order includes only items that will be picked up in a store, this module is automatically hidden.

For information about how to configure modes of delivery, see [Online channel setup](channel-setup-online.md) and [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

Each delivery mode can have an associated charge. For more information about how to configure charges for an online store, see [Omni-channel Advanced auto-charges](omni-auto-charges.md).

In Commerce version 10.0.13, the delivery options module has been updated to support the **Header charges without proration** and **Shipping as a line charge** features. If proration is turned off, the expectation is that the e-Commerce workflow won't allow a mixed mode of delivery for the items in the cart (that is, some items are selected for shipment, but others are selected for pickup). The **Header charges without proration** feature requires that the **Enable consistent delivery mode handling in channel** flag is turned on in Commerce headquarters. When the feature flag is turned on, shipping charges will be applied at either the header level or the line level, depending on the configuration in Commerce headquarters.

The Fabrikam theme supports a mixed mode of delivery, where some items are selected for shipment but others are selected for pickup. In this mode, shipping charges will be prorated for all items that are selected for the shipping mode of delivery. For a mixed mode of delivery to work, you must first configure the **Header charges with proration** feature in Commerce headquarters. For more information about this configuration, see [Prorate header charges to match sales lines](pro-rate-charges-matching-lines.md).

If shipping charges apply to line items, they can be shown on the cart line for each item. This functionality requires that the **Show shipping charges on line item** property be turned on for both the cart module and the checkout module. For more information, see [Cart module](add-cart-module.md) and [Checkout module](add-checkout-module.md).

The following illustration shows an example of a delivery options module on a checkout page.

![Example of a delivery options module on a checkout page.](./media/ecommerce-deliveryoptions.PNG)

## Delivery options module properties

| Property | Values | Description |
|----------|--------|-------------|
| Heading | Heading text and a heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | An optional heading for the delivery options module. |
| Custom CSS class name | Text | A custom Cascading Style Sheets (CSS) class name that will be used to render this module, if applicable. |
| Filter Delivery Mode Option | **Do not filter** or **Non-shipping modes** | A value that specifies whether the delivery options module should filter out all non-shipping delivery modes. |
| Auto select a delivery option | **Do not filter**, **Auto select delivery option and show summary**, or **Auto select delivery option and don't show summary** | This property automatically applies the first available delivery option to checkout without requiring the user to select it. It should be used only if there is one available delivery option. This property is supported as of the Commerce version 10.0.19 release. |

## Add a delivery options module to a checkout page and set the required properties

A delivery options module can be added only to a checkout module. For more information about how to configure the delivery options module and add it to a checkout page, see [Checkout module](add-checkout-module.md).

> [!NOTE]
> You might experience inconsistent delivery handling, or you might not see non-prorated header-level charges in your e-commerce channel. For guidance about how to fix these issues, see [Enable consistent delivery mode handling in e-commerce channels](consistent-delivery-mode-handling.md).

## Additional resources

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Pickup information module](pickup-info-module.md)

[Order details module](order-confirmation-module.md)

[Gift card module](add-giftcard.md)

[Online channel setup](channel-setup-online.md)

[Omni-channel Advanced auto-charges](omni-auto-charges.md)

[Prorate header charges to match sales lines](pro-rate-charges-matching-lines.md)

[Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
