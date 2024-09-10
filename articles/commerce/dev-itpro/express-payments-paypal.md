---
# required metadata

title: Configure express payments for PayPal
description: This article describes how to configure express payments for PayPal to enable faster checkout capabilities in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 05/11/2022
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2017-06-20
ms.custom: 
  - bap-template
---

# Configure express payments for PayPal

[!include [banner](../includes/banner.md)]

This article describes how to configure express payments for PayPal to enable faster checkout capabilities in Microsoft Dynamics 365 Commerce.

## Key terms

| Term | Description |
|---|---|
| PayPal Wallet | The customer experience and integration that are supported by the PayPal connector. It's also known as the PayPal button. |
| Wallet | A payment type that doesn't include traditional payment characteristics, such as the Bank Identification Number (BIN) range and expiration date, which are used to differentiate credit and debit card types. |
| Payment express | A Commerce module that supports faster checkout behavior when supported payment methods are used. This article covers use of the payment express module with PayPal. |

Dynamics 365 Commerce offers an out-of-box integration for PayPal Wallet. When the Dynamics 365 Payment Connector for PayPal is configured, the PayPal button appears as a selectable payment method during online order checkout. When users select PayPal, they are directed to complete their payment directly through PayPal and are then returned to the online storefront to complete their order. PayPal cart checkout lets customers use their payment account information to prefill the checkout form, so that they can complete the checkout process more quickly.

Commerce has added a payment express module to facilitate express checkouts. The payment express module can be used in a fragment that can be included on a checkout or cart page. When PayPal is configured, the same Dynamics 365 Payment Connector for PayPal connector reference is used for both the payment express option and the regular checkout option.

## PayPal checkout in Commerce

### Prerequisites

Set up the PayPal Wallet for your environment as described in [Dynamics 365 Payment Connector for PayPal](../paypal.md).

If you're using PayPal as an option in the regular checkout flow (where users manually enter their account information without using the payment express prefill actions), follow the setup instructions in [Payment module](../payment-module.md).

### Payment express module with PayPal

The payment express module works with supporting payment methods to offer site customers the option to check out more quickly by prefilling their payment service account information during the checkout process. The payment express module uses the configured payment connector to prefill the checkout form with user account details such as the address, contact information, and selected payment method.

When PayPal express checkout is used, and a user selects the PayPal button in the payment express section of the checkout page, a PayPal payment iFrame window is opened. The user then signs in to their PayPal account to use their account's shipping address, billing address, email address, and PayPal payment method of choice to pay for the transaction.

After the user completes the action in the PayPal window, they are directed back to the Commerce site checkout page, where the checkout form is prefilled with their selected details. In the payment express flow, the first delivery option that is available for the shipping address that is returned will be prefilled for the user. The user then has the option to review the order and change checkout order details before they select **Place order** to finalize the order.

### Add the payment express module with PayPal to a fragment

To add the payment express module with PayPal to a fragment in Commerce site builder, follow these steps.

1. Navigate to your site.
1. In the left navigation pane, select **Fragments**, and then select **New**.
1. In the **New Fragment** dialog box, find and select the **Payment express** module, and then, under **Fragment name**, enter a name for the fragment (for example, **Express checkout**).
1. Select **OK** to create the fragment.
1. In the outline view, select the slot of the payment express module that you created.
1. In the properties pane, select **Heading**.
1. In the **Heading** dialog box, in the **Heading text** field, enter the heading text that you want to show for the express checkout section of your site (for example, **Express checkout**).
1. Under **Heading level**, select the heading level (for example, **H2**).
1. Select **OK**.
1. In the properties pane, in the **Height of the iFrame** field, enter or adjust the height of the iFrame element (for example, **60**).
1. In the **Supported tender types** field, enter **PayPal**.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.

### Add the payment express fragment to the checkout page

To add the payment express fragment to the checkout page in site builder, follow these steps.

1. Navigate to your site.
1. In the left navigation pane, select **Pages**, and then select your site's checkout page.
1. Select **Edit** to edit the page.
1. In the **Main** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.

    > [!NOTE]
    > If a container module that contains a checkout fragment already exists, move the payment express section so that it appears above existing checkout container in the **Main** slot. The payment express section will then be rendered above the normal checkout container. To move a container module up or down, select the ellipsis (**...**), and then select **Move up** or **Move down**.

1. In the **Container** properties pane, we recommend that you configure the property settings in the following way:

    - **Container Layout** – Select **Stacked**.
    - **Width** – Select **Fill container**.
    - **Children Shown** – Select **Three**.

1. In the **Container** slot, select the ellipsis (**...**), and then select **Add Fragment**.
1. In the **Select a fragment** dialog box, find and select the express payment fragment that you created, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Add the payment express fragment to the cart page

To add the payment express fragment to the cart page in site builder, follow these steps.

1. Navigate to your site.
1. In the left navigation pane, select **Pages**, and then select your site's cart page.
1. Select **Edit** to edit the page.
1. In the **Main** slot, find the container that contains the **Cart** module. The **Cart** module will contain a **Payment express** slot.
1. Select the **Payment Express** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Select modules** dialog box, select the **Payment express** module, and then select **OK**.
1. In the properties pane, in the **Supported tender types** field, enter **Paypal**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Modes of delivery

When the payment express module is configured to use PayPal, the first delivery option that is returned for the shipping address that was selected for the PayPal account will be prefilled. Users will be able to change the shipping address if they want.

The order of the mode of delivery is configured in the **Modes of delivery** section for the channel in Commerce headquarters. For more information, see [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

The checkout module will also use the delivery options module when modes of delivery are rendered during checkout. For more information, see [Delivery options module](../delivery-options-module.md).

Modes of delivery are added to the list for the online store in Commerce headquarters. Go to **Retail and Commerce \> Channels \> Online stores**, and select the channel ID for your store. Then select **Setup \> Modes of delivery**. The module modes of delivery that are shown in the configuration will appear in a similar manner on the site. To add or remove modes of delivery for a retail channel or product, select **Manage modes of delivery** on the Action Pane.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)

[Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)

[Delivery options module](../delivery-options-module.md)
