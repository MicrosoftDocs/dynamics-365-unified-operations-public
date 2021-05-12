---

# required metadata

title: Cart icon module
description: This topic covers the cart icon module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 10/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
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

The cart icon module represents the cart in the header module of the page, and shows the number of items in the cart. The cart icon module also displays a cart summary (also known as a mini cart) when the cart icon is hovered over. The mini cart provides the user with a summary of the items in the cart without having to navigate to the cart page. In addition, it also allows the user to directly go to checkout page if they are happy with the summary. This reduces the number of page navigations and makes checkout faster. 

The following image shows an example of a cart icon module that displays a mini cart in the Fabrikam header.

![Example of a cart icon module](./media/ecommerce-Minicart.PNG)


## Module properties

- **Show mini cart** – When true, this property enables a cart summary (mini cart) to be displayed when the cart icon is hovered over. This functionality is only supported for desktop view ports.


## Module properties in Adventure works theme

In Adventure works theme, the module includes two additional slots for the mini cart. These slots are included as a module definition extension.

-**Empty cart promotions** - This slot takes Content block module. When the cart contents are empty, this content block module will be displayed. It can be used for any promotions, marketing content, links to category pages etc to help the user continue their shopping journey.

-**Promotional content** - This slot can be used to showcase promotions such as "Free Shipping on orders over $100". Content block, Text block or Image list modules can be used for this.

The following image shows an example of a cart icon module in Adventure works theme showcasing content in the above slots.

![Example of a cart icon module in Adventure works theme](./media/AW_minicart.PNG)

>[IMPORTANT]
>These slots are introduced  in Dynamics 365 Commerce 10.0.20 release and showcased on Adventure works theme.


## Add a cart icon module to a page

To add a cart icon module, see [Header module](author-header-module.md).

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
