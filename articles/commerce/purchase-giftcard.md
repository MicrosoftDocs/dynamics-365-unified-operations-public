---
# required metadata

title: Purchasing a digital gift card
description: This topic covers purchasing gift card in e-commerce
author: anupamar-ms
manager: annbe
ms.date: 10/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.15

---

# Purhcasing a Gift card on e-commerce

[!include [banner](includes/banner.md)]

This topic covers purchasing a gift card on e-commerce

## Overview
In Dynamics 365 Commerce 10.0.15 release, we support purchase of digital gift cards via e-commerce. 

## Configuring a digital gift card in Headquarters
Product setup - A gift card product should be configured in headquarters Service item, Prices as dimensions, Key in Price for custom price
Delivery Mode setup
Gift card associations
Digital gift cards can be set up in HQ as Service Item. If a product is of type Service item it will not be checked for available inventory before placing an order. 

## Enabling Gift card feature in Headquarters


## e-commerce Experience


| Property | Values | Description |
|----------------|--------|-------------|
| Heading | Heading text and a heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | A heading for the cart, such as "Shopping bag" or "Items in your cart." |
| Show out of stock errors | **True** or **False** | If this property is set to **True**, the cart page will show stock-related errors. We recommend that you set this property to **True** if inventory checks are applied on the site. |
| Show shipping charges for line items | **True** or **False** | If this property is set to **True**, cart line items will show the shipping charges, if this information is available. This feature isn't supported in the Fabrikam theme, because users select shipping only in the checkout flow. However, this feature can be turned on in other workflows if it's applicable. |
| Show available promotions| **True** or **False** | If this property is set to **True**, cart shows available promotions based on items in the Cart. This capability is available in Dynamics 365 Commerce 10.0.16 release |


 
The cart module retrieves product information by using Commerce Scale Unit APIs. The cart ID from the browser cookie is used to retrieve all the product information from Commerce Scale Unit.

## Add a cart module to a page

To add a cart module to a new page and set the required properties, follow these steps.

1. Go to **Fragments**, and select **New** to create a new fragment.
1. In the **New fragment** dialog box, select the **Cart** module.
1. Under **Fragment name**, enter the name **Cart fragment**, and then select **OK**.
1. Select the **Cart** slot.
1. In the properties pane on the right, select the pencil symbol, enter heading text in the field, and then select the check mark symbol.
1. In the **Cart** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Store selector** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.
1. Go to **Templates**, and select **New** to create a new template.
1. In the **New Template** dialog box, under **Template name**, enter a name for the template.
1. In the outline tree, select the **Body** slot, select the ellipsis (**...**), and then select **Add fragment**.
1. In the **Select fragment** dialog box, select the **Cart fragment** fragment, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Choose a template** dialog box, select the template that you created, enter a page name, and then select **OK**.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Delivery options module](delivery-options-module.md)

[Order details module](order-confirmation-module.md)

[Gift card module](add-giftcard.md)

[Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md)

[Create an online functionality profile](online-functionality-profile.md)
