---
title: Cart and checkout pages overview
description: This article provides an overview of the cart and checkout pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/28/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Cart and checkout pages overview

[!include [banner](includes/banner.md)]

This article provides an overview of the cart and checkout pages in Microsoft Dynamics 365 Commerce.

The cart page of an e-commerce website shows all items that a customer added to the cart. The cart page is built by using the cart module. The cart module is a container that hosts all the modules that are required to showcase items in the cart. The cart module can also use other modules to show the order summary and any promotional codes applied to the customer order.

The checkout page of an e-commerce website presents a step-by-step flow that customers follow to enter all the information that is required to place an order. A checkout module can include modules that handle the shipping address, shipping methods, billing information, order summary, and other information that is related to customer orders.

## Cart page

The cart page serves as the shopping bag and includes all the items that the customer adds to the cart.

The following illustration shows an example of a cart page that uses the module library and the "Fabrikam" theme.

:::image type="content" source="./media/cart2.PNG" alt-text="Screenshot of a cart page.":::

The main body of the cart page shows all the items that the customer adds to the cart. The cart page showcases all applicable discounts. These discounts include complex discounts. Examples include "Buy 3 items and get 10% off" or "Buy a bottle and a backpack to get 10% off." The order summary module shows the amount that's due after discounts, shipping, taxes, and other costs. The promo code module lets the customer apply or remove promotional codes.

A customer can shop anonymously or as a signed-in user. If a customer signs in, the cart preserves items between sessions. In this way, the customer can continue to shop from multiple devices.

From the cart, the customer can proceed to checkout. A customer can initiate checkout as a guest user or as a signed-in user.

For information about how to author a cart page, see [Add a cart module to a page](add-cart-module.md).

## Checkout page

Customers enter the information required to place an order on the checkout page.

The following illustration shows an example of a checkout page that uses the module library.

:::image type="content" source="./media/Checkout.PNG" alt-text="Screenshot of a checkout page.":::

The main body of the checkout page collects all the order information. This information includes the shipping address, delivery options, and payment information. Checkout has a step-by-step flow, because the information must be entered in a specific order to be processed. For example, the shipping address must be entered before the shipping costs can be calculated and the payment can be authorized.

### Shipping address

A shipping address is required if you need to ship items. You can configure the format of shipping addresses for each locale in Dynamics 365 Commerce. For example, if the items ship to the United States, the shipping address must include a street address, state, and ZIP Code. The system performs some basic input validation for shipping address fields, such as validation for alphanumeric characters, maximum length, and numbers. Although the system doesn't verify the validity of the address itself, you can add this verification by using customized third-partner services.

The shipping address applies to all items in the cart that you select the **ship** option for. If you use the checkout flow that the module library provides, you can't ship individual cart items to different addresses. If you require this capability, you can implement it through customization of the checkout modules.

After you provide the shipping address, the checkout page shows the shipping methods that are available from the Dynamics 365 Commerce online store. You can configure the shipping methods and the addresses that they support in Commerce.

### Payment

The next step in the checkout flow is payment. In Commerce, multiple methods of payment can be used to place orders, such as credit cards, gift cards, and loyalty points. A combination of these payment methods can also be used. Depending on the payment methods that are used, additional information might be required. For example, a credit card payment requires a billing address. Credit card payments are processed by using the Adyen Payment Connector.

#### Loyalty points

During the checkout flow, a customer who's a member of a loyalty program and accrues loyalty points can redeem those loyalty points for an order. The loyalty points module appears only if the customer has an existing loyalty membership. For nonmembers and guest users, this module is hidden.

#### Gift cards

The module library lets customers redeem internal gift cards for an order. To apply an internal gift card, the customer must sign in. For more security, customize the flow by using a personal identification number (PIN) for internal gift cards.

### Signed-in and guest users

The customer can complete the checkout process as a guest user or a signed-in user. If the customer signs in, the system automatically retrieves account information such as saved shipping addresses and saved credit card details.

### Order summary

Checkout shows a summary of the line items in the cart, so that the customer can verify the order before placing the order. The line items can't be edited during the checkout flow. However, a link to the cart is provided in case the user wants to go back and edit line items.

After the customer provides shipping and billing information, the order summary reflects the amount that's due after loyalty points, gift cards, and other payments are applied.

### Order confirmation and email

When the customer places an order, the system provides a confirmation number. At this point, the payment is authorized but not charged. The payment is charged only when the order is fulfilled (that is, when it's either shipped or picked up).

After an order is created, the system sends an order confirmation email to the customer.

For more information about how to author a checkout page, see [Add a checkout module to a page](add-checkout-module.md).

## Additional resources

[Home page overview](quick-tour-home-page.md)

[Product details pages overview](quick-tour-pdp.md)

[Account management pages overview](quick-tour-account-management.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
