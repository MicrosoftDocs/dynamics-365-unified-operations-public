---
# required metadata

title: Order details module
description: This topic covers order details modules and describes how to use them in Microsoft Dynamics 365 Commerce.
author: anupamar
manager: annbe
ms.date: 06/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations

# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar-ms
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Order details module

[!include [banner](includes/banner.md)]

This topic covers order details modules and describes how to use them in Microsoft Dynamics 365 Commerce.

## Overview

The order details module is used to show order confirmation details after an order has been placed. It shows the order confirmation ID, order contact information, and other order details, such as the items that were purchased, payment information, and the shipping method.

## Order details module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | The order details module can have a heading. By default, the **H2** heading tag is used for the heading. However, the tag can be changed to meet accessibility requirements. |
| Contact number | Text | A contact number can be provided for order-related questions. |

## Modules that can be used on an order details page

When you create an order details page, you can add other relevant modules in addition to the order details module. Here are some examples:

- **Recommendations module** – The recommendations module can be added to the order details page to suggest other products to the customer.
- **Marketing modules** – Any marketing module can be added to the order details page to show marketing content.

## Add an order details module to a page

To add an order details module to a new page and set the required properties, follow these steps.

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New Template** dialog box, under **Template name**, enter the name **Order details template**, and then select **OK**.
1. In the **Body** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Default page** module, and then select **OK**.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Order details** module, and then select **OK**.
1. Select **Save**, and then select **Preview** to preview the template. The order details module won't be rendered, because it requires the context of the order confirmation number.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Choose a template** dialog box, select **Order details template**. Under **Page name**, enter **Order details page**, and then select **OK**.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Order details** module, and then select **OK**.
1. In the properties pane for the order details module, select **Heading** next to the pencil symbol.
1. In the **Heading Text** field of the **Heading** dialog box, enter the heading text **Order details**, and then select **OK**.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Cart module](add-cart-module.md)

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Delivery options module](delivery-options-module.md)

[Gift card module](add-giftcard.md)
