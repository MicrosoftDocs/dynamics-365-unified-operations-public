---

# required metadata

title: Cart icon module
description: This topic covers the cart icon module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Cart icon module

[!include [banner](includes/banner.md)]

This topic covers the cart icon module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

The cart icon module represents the cart in the header module of the page, and shows the number of items in the cart. The cart icon module also displays a cart summary (also known as a mini cart) when the cart icon is hovered over. The mini cart provides the user with a summary of the items in the cart without having to navigate to the cart page. In addition, it also allows the user to directly go to checkout page if they are happy with the summary. This reduces the number of page navigations and makes checkout faster. 

> [!NOTE]
> Support for the cart icon module is available in the Dynamics 365 Commerce 10.0.11 release.

The following image shows an example of a cart icon module that displays a mini cart in the Fabrikam header.

![Example of a cart icon module](./media/ecommerce-Minicart.PNG)

## Module properties

- **Show mini cart** – When true, this property enables a cart summary (mini cart) to be displayed when the cart icon is hovered over. This functionality is only supported for desktop view ports.

## Add a cart icon module to a page

To add a cart icon module, see [Header module](author-header-module.md).

## Additional resources

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Delivery options module](delivery-options-module.md)

[Order details module](order-confirmation-module.md)

[Gift card module](add-giftcard.md)
