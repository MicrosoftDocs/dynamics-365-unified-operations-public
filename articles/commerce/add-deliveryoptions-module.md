---
# required metadata

title: Delivery options module
description: This topic describes how to add a Delivery options module to a checkout page and set the required properties.
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

# Delivery options module


[!include [banner](includes/banner.md)]

This topic describes how to add a Delivery options  module to a checkout page and set the required properties.

## Overview

Delivery options module lets a customer select a mode of delivery for their order. Delivery options module requires a shipping address to determine the modes of delivery. If the shipping address is changed, the delivery options must be retrieved again. If the order includes only items that will be picked up in the store, this module is automatically hidden. 

To configure modes of delviery, See [Online channel setup](channel-setup-online.md) and [Set up modes of delivery](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery). In addition, each delivery mode can have an associated charge. Refer to [Omni-channel Advanced auto-charges](omni-auto-charges.md) to learn more about configuring charges for the online store.

The Fabrikam theme, supports a mixed mode of delivery where some items can be selected for shipping and some can be pickup. For a mixed mode of delivery to work, its required to configure **Header Charges with proration** see [Prorate header chanrges to match sales lines](pro-rate-charges-matching-lines.md) for more details on this configuration.  In this mode Shipping charges will be pro-rated for all the items that are selected for Shipping mode of delivery.

In 10.0.13, the module has been updated to also support **Header charges without proration** and **Line charge as shipping charge**. When using this mode the expectation is that the ecommerce workflow does not allow mixed mode of delivery for the items in the cart.  This feature is behind a feature flag and requires requires "XYZ" flag in HQ to be turned on. When the flag is turned on, shipping charge will be applied at the header level or the line level depending on how its configured in HQ. 

If a shipping charges apply to line items, it can be displayed on the cart line for each item. This requires **Show shipping charges on line item** to be set to True on both **Cart and Checkout** modules. See [Cart module](add-cart-module.md) and [Checkout module](add-checkout-module.md) for more details on this configuration.

     The following image shows an example of a delivery options module on a checkout page.
    ![Example of a delivery options module](./media/ecommerce-deliveryoptions.PNG)

## Module configuration
Filter delivery modes - This option allows a retailer to choose if a Delivery options module should filter all the non-shipping delviery modes. E.g. Fabrikam theme.

## Add a Delivery options module to a checkout page and set the required properties

A Delivery options module can only be added to a Checkout container. See [Checkout module](add-checkout-module.md] for details on configuring the module to a page.

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

