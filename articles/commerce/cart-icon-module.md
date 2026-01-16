---
title: Cart icon module
description: Learn how to to add the cart icon module to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/16/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Cart icon module

[!include [banner](includes/banner.md)]

This article explains how to add the cart icon module to site pages in Microsoft Dynamics 365 Commerce.

The cart icon module represents the cart in the header module of the page, and shows the number of items in the cart. The cart icon module also displays a cart summary (also known as a mini cart) when the cart icon is hovered over. The mini cart provides the user with a summary of the items in the cart without having to navigate to the cart page. It also allows the user to proceed directly to the checkout page if they're happy with the summary. This flow reduces the number of page navigation clicks and makes checkout faster.

The following image shows an example of a cart icon module that displays a mini cart in the Fabrikam header.

:::image type="content" source="./media/ecommerce-Minicart.PNG" alt-text="Screenshot of a cart icon module displaying a mini cart in the Fabrikam header.":::

## Module properties

- **Show mini cart** – When you set this property to **True**, a cart summary (mini cart) is shown when users hover over the cart icon. This functionality is supported only for desktop view ports.
- **Allow anonymous checkout** – When you set this property to **True**, the mini cart allows users who aren't signed in to do a guest checkout. Starting in Commerce version 10.0.45, you must enable the **Allow anonymous checkout** configuration in the functionality profile associated with the online channel.

    > [!IMPORTANT]
    > The **Allow anonymous checkout** configuration in the functionality profile is disabled by default.

- **Order of items** – This property controls the order in which items appear in the mini cart. When you select the **New items added to top of the list** option, new items added to the cart appear at the top of the list of mini cart items. When you select the default option **New items added to bottom of the list**, new items added to the cart appear at the bottom of the list of mini cart items. This property is available as part of the Commerce module library package starting with Commerce version 10.0.21.

## Module properties and slots in the Adventure Works theme

In the Adventure Works theme, the cart icon module includes two extra slots for the mini cart. The module definition extension includes these slots.

- **Empty cart promotions** – This slot takes a content block module. When the cart is empty, the specified content block module appears. Use the content block module for promotions, marketing content, and links to category pages, to help customers continue their shopping journey.
- **Promotional content** – Use this slot to showcase promotions, such as "Free shipping on orders over $100." Content block, text block, and image list modules can be used in the promotional content slot.

The following image shows an example of a cart icon module in the Adventure Works theme that displays promotional content on the mini cart.

:::image type="content" source="./media/AW_minicart.PNG" alt-text="Screenshot of a cart icon module in the Adventure Works theme displaying promotional content on the mini cart.":::

> [!IMPORTANT]
> The Adventure Works theme slots are available as of the Dynamics 365 Commerce version 10.0.20 release.

## Add a cart icon module to a page

For information about how to add a cart icon module, see [Header module](author-header-module.md).

## Additional resources

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Delivery options module](delivery-options-module.md)

[Pickup information module](pickup-info-module.md)

[Order details module](order-confirmation-module.md)

[Gift card module](add-giftcard.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
