---
# required metadata

title: Delivery options module
description: This topic covers delivery options modules and how to configure them in Dynamics 365 Commerce.
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
ms.dyn365.ops.version: Release 10.0.13

---

# Delivery options module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers delivery options modules and how to configure them in Dynamics 365 Commerce.

## Overview

Delivery options modules let customers select a mode of delivery such as shipping or pickup for their online order. A shipping address is required to determine the mode of delivery. If the shipping address changes, the delivery options must be retrieved again. If an order only includes items that will be picked up in a store, this module is automatically hidden. 

For information on configuring modes of delivery, see [Online channel setup](channel-setup-online.md) and [Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery). 

Each delivery mode can have an associated charge. For more information about configuring charges for an online store, see [Omni-channel Advanced auto-charges](omni-auto-charges.md).

In Commerce version 10.0.13, the delivery options module has been updated to support **Header charges without proration** and **Shipping as a line charge** features. If proration is not turned on, the expectation is that the e-Commerce workflow does not allow a mixed mode of delivery (some items shipped, some to be picked up) for the items in the cart. The **Header charges without proration** feature requires that the **Enable consistent delivery mode handling in channel** flag in Commerce headquarters is turned on. When the flag is enabled, shipping charges will be applied at the header or line level, depending the configuration in Commerce headquarters. 

The Fabrikam theme supports a mixed mode of delivery where some items can be selected for shipping and some for pickup. In this mode, shipping charges will be prorated for all items that are selected for the shipping mode of delivery. For a mixed mode of delivery to work, you must first configure the **Header charges with proration** feature in Commerce headquarters, for more information on this configuration see [Prorate header charges to match sales lines](pro-rate-charges-matching-lines.md).  

If shipping charges apply to line items, they can be displayed on the cart line for each item. This requires the **Show shipping charges on line item** property to be enabled on both the cart and checkout modules. For more information, see [Cart module](add-cart-module.md) and [Checkout module](add-checkout-module.md).

The following image shows an example of a delivery options module on a checkout page.

![Example of a delivery options module on a checkout page](./media/ecommerce-deliveryoptions.PNG)

## Delivery options module properties

| Property | Values | Description |
|----------------|--------|-------------|
| Heading | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | Displays an optional heading for the delivery options module. |
| Custom CSS class name | Text | Specifies a custom CSS class name to be used to render this module, if applicable. |
| Filter Delivery Mode Option | Do not filter, Non-shipping modes | Specifies if the delivery options module should filter out all non-shipping delivery modes. |

## Add a delivery options module to a checkout page and set the required properties

A delivery options module can only be added to a checkout module. For more information on configuring the delivery options module and adding it to a checkout page, see [Checkout module](add-checkout-module.md).

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Online channel setup](channel-setup-online.md). 

[Omni-channel Advanced auto-charges](omni-auto-charges.md) 

[Prorate header chanrges to match sales lines](pro-rate-charges-matching-lines.md) 

[Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)

