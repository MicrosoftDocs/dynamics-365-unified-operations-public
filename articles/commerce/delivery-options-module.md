---
# required metadata

title: Delivery options module
description: This topic covers delivery options modules and explains how to configure them in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/23/2020
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
ms.dyn365.ops.version: Release 10.0.13

---

# Delivery options module

[!include [banner](includes/banner.md)]

This topic covers delivery options modules and explains how to configure them in Microsoft Dynamics 365 Commerce.

## Overview

Delivery options modules let customers select a mode of delivery such as shipping or pickup for their online order. A shipping address is required to determine the mode of delivery. If the shipping address changes, the delivery options must be retrieved again. If an order includes only items that will be picked up in a store, this module is automatically hidden.

For information about how to configure modes of delivery, see [Online channel setup](channel-setup-online.md) and [Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

Each delivery mode can have an associated charge. For more information about how to configure charges for an online store, see [Omni-channel Advanced auto-charges](omni-auto-charges.md).

In Commerce version 10.0.13, the delivery options module has been updated to support the **Header charges without proration** and **Shipping as a line charge** features. If proration is turned off, the expectation is that the e-Commerce workflow won't allow a mixed mode of delivery for the items in the cart (that is, some items are selected for shipment, but others are selected for pickup). The **Header charges without proration** feature requires that the **Enable consistent delivery mode handling in channel** flag be turned on in Commerce headquarters. When that flag is turned on, shipping charges will be applied at either the header level or the line level, depending on the configuration in Commerce headquarters.

The Fabrikam theme supports a mixed mode of delivery, where some items are selected for shipment but others are selected for pickup. In this mode, shipping charges will be prorated for all items that are selected for the shipping mode of delivery. For a mixed mode of delivery to work, you must first configure the **Header charges with proration** feature in Commerce headquarters. For more information about this configuration, see [Prorate header charges to match sales lines](pro-rate-charges-matching-lines.md).

If shipping charges apply to line items, they can be shown on the cart line for each item. This functionality requires that the **Show shipping charges on line item** property be turned on for both the cart module and the checkout module. For more information, see [Cart module](add-cart-module.md) and [Checkout module](add-checkout-module.md).

The following illustration shows an example of a delivery options module on a checkout page.

![Example of a delivery options module on a checkout page](./media/ecommerce-deliveryoptions.PNG)

## Delivery options module properties

| Property | Values | Description |
|----------|--------|-------------|
| Heading | Heading text and a heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | An optional heading for the delivery options module. |
| Custom CSS class name | Text | A custom Cascading Style Sheets (CSS) class name that will be used to render this module, if applicable. |
| Filter Delivery Mode Option | **Do not filter** or **Non-shipping modes** | A value that specifies whether the delivery options module should filter out all non-shipping delivery modes. |

## Add a delivery options module to a checkout page and set the required properties

A delivery options module can be added only to a checkout module. For more information about how to configure the delivery options module and add it to a checkout page, see [Checkout module](add-checkout-module.md).

## Additional resources

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Order details module](order-confirmation-module.md)

[Gift card module](add-giftcard.md)

[Online channel setup](channel-setup-online.md)

[Omni-channel Advanced auto-charges](omni-auto-charges.md)

[Prorate header charges to match sales lines](pro-rate-charges-matching-lines.md)

[Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)
