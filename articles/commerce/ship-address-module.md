---
# required metadata

title: Shipping address module
description: This topic covers the shipping address module and explains how to configure it in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 08/05/2020
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

This topic describes covers the shipping address module and explains how to configure it in Microsoft Dynamics 365 Commerce.

## Overview

The shipping address module lets customers add or select the shipping address for an order during the checkout flow. If a customer is signed in, any addresses that were previously saved for that customer are shown, and the customer can select among them. The customer can also add a new address. The shipping address module is used for all items on an order that require shipping.

Shipping address formats can be defined in Commerce headquarters for each country or region, and the shipping address module then enforces country/region-specific rules.

When customers enter a shipping address during the checkout flow, they have the option to save the address as a primary address. This option is shown only if a customer is signed in.

Although the shipping address module doesn't provide address validation, this functionality can be implemented through customization.

The following illustration shows an example of a new shipping address module on a checkout page.

![Example of a shipping address module on a checkout page](./media/ecommerce-shippingaddress.PNG)

## Module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Heading | Heading text and a heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | An optional heading for the shipping address module. |
| Show address type | **True** or **False** | If this optional property is set to **True**, an address type, such as **Home** or **Business**, will be shown. If no address type is specified, the address will automatically be saved as **Type**=**Other**. |

## Add a shipping address module to a checkout page and set the required properties

A shipping address module can be added only to a checkout module. For more information about how to configure the shipping address module and add it to a checkout page, see [Checkout module](add-checkout-module.md).

## Additional resources

[Cart module](add-cart-module.md)

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Delivery options module](delivery-options-module.md)

[Order details module](order-confirmation-module.md)

[Gift card module](add-giftcard.md)
