---
title: Order confirmation module
description: This article covers order confirmation modules and describes how to use them in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 08/02/2024
ms.topic: how-to
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Order confirmation module

[!include [banner](includes/banner.md)]

This article covers order confirmation modules and describes how to use them in Microsoft Dynamics 365 Commerce.

The order confirmation module is used to show order confirmation details after an order has been placed. It shows the order confirmation ID, order contact information, and other order details, such as the items that were purchased, payment information, pickup options, and the shipping method.

## Order confirmation module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | The order confirmation module can have a heading. By default, the **H2** heading tag is used for the heading. However, the tag can be changed to meet accessibility requirements. |
| Contact number | Text | A contact number can be provided for order-related questions. |
| Show pickup timeslot information | True or False | This property is available in Dynamics 365 Commerce 10.0.15 and higher. When true, it displays the pickup timeslot information if provided for a pickup item|

## Modules that can be used on an order confirmation page

When you create an order confirmation page, you can add other relevant modules in addition to the order confirmation module. Here are some examples:

- **Recommendations module** – The recommendations module can be added to the order confirmation page to suggest other products to the customer.
- **Marketing modules** – Any marketing module can be added to the order confirmation page to show marketing content.

## Add an order confirmation module to a page

To add an order confirmation module to a new page and set the required properties, follow these steps.

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New template** dialog box, under **Template name**, enter the name **Order confirmation template**, and then select **OK**.
1. In the **Body** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Default page** module, and then select **OK**.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Order confirmation** module, and then select **OK**.
1. Select **Save**, and then select **Preview** to preview the template. The order confirmation module won't be rendered, because it requires the context of the order confirmation number.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Create a new page** dialog box, under **Page name**, enter **Order confirmation page** and then select **Next**.
1. Under **Choose a template**, select **Order confirmation template**, and then select **Next**.
1. Under **Choose a layout**, select a page layout (for example, **Flexible layout**), and then select **Next**.
1. Under **Review and finish**, review the page configuration. If you need to edit the page information, select **Back**. If the page information is correct, select **Create page**. 
1. In the **Main** slot of the **Default Page** module, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Order confirmation** module, and then select **OK**.
1. In the properties pane for the order confirmation module, select **Heading** next to the pencil symbol.
1. In the **Heading Text** field of the **Heading** dialog box, enter the heading text **Order confirmation**, and then select **OK**.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Cart module](add-cart-module.md)

[Cart icon module](cart-icon-module.md)

[Checkout module](add-checkout-module.md)

[Payment module](payment-module.md)

[Shipping address module](ship-address-module.md)

[Delivery options module](delivery-options-module.md)

[Pickup information module](pickup-info-module.md)

[Gift card module](add-giftcard.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
