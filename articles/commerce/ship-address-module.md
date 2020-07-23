---
# required metadata

title: Shipping address module
description: This topic describes covers the shipping address module and how to configure it in Dynamics 365 Commerce.
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

# Shipping address module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes covers the shipping address module and how to configure it in Dynamics 365 Commerce.

## Overview

This module allows a customer to add or select the shipping address for an order during the checkout flow. If a customer is signed in, any addresses that were previously saved for the customer are displayed and the customer can then choose from those addresses. The customer can also add a new address. The shipping address module is used for all items in an order that require shipping. 

Shipping address formats can be defined in Commerce headquarters for each country or region, and the country- or region-specific rules are then enforced by the shipping address module. 

When entering a shipping address during the checkout flow, customers are provided with an option to save the address as a primary address. This option is only shown when a customer is signed in.

Although the shipping address module doesn't provide address validation, this functionality can be implemented with customization.

The following image shows an example of a new shipping address module on a checkout page.

![Example of a shipping address module on a checkout page](./media/ecommerce-shippingaddress.PNG)

## Module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | Displays an optional heading for the shipping address module. |
| Show address type | True, False | This optional setting shows an address type such as Home, Business, etc. If not specified, the address will be automatically saved as Type=Other.|

## Add a Shipping address module to a checkout page and set the required properties

A shipping address module can only be added to a checkout module. For more information on configuring the shipping address module and adding it to a checkout page, see [Checkout module](add-checkout-module.md).

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

