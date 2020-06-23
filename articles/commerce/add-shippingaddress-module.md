---
# required metadata

title: Shipping address module
description: This topic describes how to add a Shipping address  module to a checkout page and set the required properties.
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

# Shipping address module


[!include [banner](includes/banner.md)]

This topic describes how to add a Shipping address module to a checkout page and set the required properties.

## Overview

This module lets a customer add or select the shipping address for an order during the checkout flow. If the customer is signed in, any addresses that were previously saved for that customer are shown. The customer can then select among those addresses. The customer can also add a new address. The shipping address is used for all the items in the order that require shipping. 

Shipping address formats can be defined in HQ for each country or region, and the country/region-specific rules are enforced by this module. 

Although this module doesn't provide address validation, address validation can be implemented through customization.


   The following image shows an example of adding a new shipping address on a checkout page.

   ![Example of a shipping address module](./media/ecommerce-shippingaddress.PNG)



## Add a Shipping address module to a checkout page and set the required properties

A Shipping address module can only be added to a Checkout container. See [Checkout module](add-checkout-module.md] for details on configuring the module to a page.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Order confirmation module](order-confirmation-module.md)

[Online channel setup](channel-setup-online.md). 

[Omni-channel Advanced auto-charges](omni-auto-charges.md) 

[Prorate header chanrges to match sales lines](pro-rate-charges-matching-lines.md) 

[Checkout module](add-checkout-module.md]

