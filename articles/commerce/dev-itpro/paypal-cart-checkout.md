---
# required metadata

title: PayPal cart checkout for Dynamics 365 Commerce
description: This topic provides an overview of the Microsoft Dynamics 365 Payment support PayPal Cart Checkout for faster checkout capabilities.
author: BrianShook
ms.date: 04/13/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom:
ms.dyn365.ops.version: AX 7.0.1

---

# Dynamics 365 Payment Support for PayPal Cart Checkout

[!include [banner](../includes/banner.md)]

This topic provides an overview of the Microsoft Dynamics 365 payments support for PayPal Cart Checkout capability. It reviews additions of Payment Express modules for faster checkout capabilities, and setup of PayPal Cart Checkout with a Commerce site page.

## Key terms

| Term | Description |
|---|---|
| PayPal Wallet | Also known as the PayPal "button", PayPal Wallet describes the customer experience and integration supported by the PayPal Connector. |
| Wallet | A payment type that does not include traditional payment characteristics, such as the BIN range and expiration date, which are used to differentiate among credit and debit card types. |
|Payment Express |Added module in Dynamics 365 Commerce to support faster checkout behavior with supported payment methods, with this article addressing PayPal|

Microsoft Dynamics 365 Commerce offers an out-of-box integration for PayPal Wallet. When the PayPal Connector is configured, the PayPal button is a selectable payment method as part of online order checkout. When users select **PayPal**, they are directed to complete their payment directly with PayPal and then are returned to the online storefront for order completion. With **PayPal Cart Checkout**, users can utilize their payment account information to pre-fill the checkout form and get through the checkout process faster. Commerce is adding a Payment Express module to allow for express checkout behavior. The Payment Express module can be used in a Fragment and included in the checkout or cart page. The same **Dynamics 365 Payment Connector for PayPal** connector reference is used for a Payment Express or regular checkout option when PayPal is configured.

## PayPal cart checkout in Commerce

### Prerequisites

Follow the PayPal Wallet setup instructions for your environment as described in the [Dynamics 365 Payment Connector for PayPal](../paypal.md) article. 

If using PayPal as an option in the regular checkout flow (the checkout section in which a user enters their order information without the Express pre-fill actions), follow the setup instructions for the [Payment Module](../payment-module.md) article. Setting up the regular checkout section will remain the same as described in the referenced payment module article.

### Payment Express module with PayPal

The **Payment Express** module works with supporting payment methods to offer site customers the option to checkout faster using their payment service account information in the checkout process. The module references the configured connector button and returns the user selected order details (addresses, contact information, and paying against the underlying payment method selected) to pre-populate the checkout form.

With PayPal Cart Checkout, selecting the PayPal button in the Payment Express section will launch the PayPal payment iFrame window. A user will log in to their PayPal account and can use their account shipping address, billing address, email, and PayPal payment method of choice to pay for the transaction.

As the user completes the action in PayPal, they are directed to the Commerce site checkout page with the checkout form pre-populated with their chosen details. In the Payment Express flow, the first **Delivery Option** available for the shipping address returned will be pre-selected for the customer.  The customer has the option to review the order, change checkout order details if desired, and will then select the **Place order** button to finalize the order.

### Add the payment express module with PayPal to a fragment in site builder

Add the payment express module with PayPal to a fragment in site builder, follow these steps.

1. Navigate to your site.
1. In the left navigation pane, select **Fragments**, and then select **New**.
2. In the **New Fragment** dialog box, find and select the **Payment express** module, and then under **Fragment name** enter a name for the fragment (for example, "Express checkout"). 
3. Select **OK** to create the fragment.
3. In the outline view, select the slot of the payment express module you created.
4. In the properties pane, select **Heading**. 
5. In the **Heading** dialog box, for **Heading text** enter the heading text that you want to display for the express checkout section of your site (for example, "Express checkout").
6. Under **Heading level**, select the heading level (for example, "H2"), and then select **OK**.
7. In the properties pane, for **Height of the iFrame** enter or adjust the height of the iFrame element (for example, "60").
8. For **Supported tender types**, enter "PayPal".
9. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.

### Add the payment express fragment to the checkout page 

To add the payment express fragment to the checkout page, follow these steps.

1. Navigate to your site.
1. In the left navigation pane, select **Pages**, and then select your site's checkout page.
1. Select **Edit** to edit the page.
1. In the **Main slot**, select the ellipsis ("**...**"), and then select **Add Module**.
1. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.
    > [!NOTE]
    > If a container module already exists that contains a checkout fragment, to have the payment express section render above the normal checkout container, position it above the existing checkout container within the **Main slot**. To move a container module up or down, select the ellipsis ("**...**"), and then select **Move up** or **Move down**.
1. In the **Container** properties pane, it is recommended to configure the property settings follows:
    - **Container Layout**: Select **Stacked**.
    - **Width**: Select **Fill container**.
    - **Children Shown**: Select **Three**.
1. In the **Container** slot, select the ellipsis ("**...**"), and then select **Add Fragment**.
1. In the **Select a fragment** dialog box, find and select the express payment fragment you created, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Add the payment express fragment to the cart page

Add the payment express fragment to the cart page, follow these steps.

1. Navigate to your site.
1. In the left navigation pane, select **Pages**, and then select your site's cart page.
2. Select **Edit** to edit the page.
3. In the **Main slot**, locate the container that contains the **Cart** module. The **Cart** module will contain a **Payment express** slot.
4. Select the **Payment Express** slot, select the ellipsis ("**...**"), and then select **Add Module**.
5. In the **Select modules** dialog box, select the **Payment express** module, and then select **OK**.
6. In properties pane, for **Supported tender types** enter "Paypal".
8. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Modes of delivery

With the Payment Express module using PayPal, the first delivery option returned against the shipping address selected from the PayPal account will be pre-selected. Users will have a chance to click **change** and adjust the shipping address to a different option if desired. 

The order of the delivery methods is configured in HQ on the Channel's **Modes of delivery** section. Additional information on setting up modes of delivery can be found in the [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery) article. The checkout module will also use the **delivery options module** when rendering modes of delivery during checkout. See additional details in the [delivery options module](../delivery-options-module.md) article.

Modes of delivery are displayed as added to the list in the Online Store. In Headquarters, navigate to **Retail and Commerce > Channels > online stores** and select the channel ID for your store. Under the **Setup** menu section, select **Modes of delivery**. The module modes of delivery will be displayed on the site similarly to the configuration shown. Use the **Manage modes of delivery** action item to add or remove modes of delivery for a Retail Channel or a Product.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)
