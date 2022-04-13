---
# required metadata

title: PayPal Cart Checkout for Dynamics 365 Commerce
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

## PayPal Cart Checkout in Commerce

### Pre-requisites
Follow the PayPal Wallet setup instructions for your environment as described in the [Dynamics 365 Payment Connector for PayPal](../paypal.md) article. 

If using PayPal as an option in the regular checkout flow (the checkout section in which a user enters their order information without the Express pre-fill actions), follow the setup instructions for the [Payment Module](../payment-module.md) article. Setting up the regular checkout section will remain the same as described in the referenced payment module article.

### Introducing the Payment Express module with PayPal
The **Payment Express** module works with supporting payment methods to offer site customers the option to checkout faster using their payment service account information in the checkout process. The module references the configured connector button and returns the user selected order details (addresses, contact information, and paying against the underlying payment method selected) to pre-populate the checkout form.

With PayPal Cart Checkout, selecting the PayPal button in the Payment Express section will launch the PayPal payment iFrame window. A user will log in to their PayPal account and can use their account shipping address, billing address, email, and PayPal payment method of choice to pay for the transaction.

As the user completes the action in PayPal, they are directed to the Commerce site checkout page with the checkout form pre-populated with their chosen details. In the Payment Express flow, the first **Delivery Option** available for the shipping address returned will be pre-selected for the customer.  The customer has the option to review the order, change checkout order details if desired, and will then select the **Place order** button to finalize the order.


### Set up the Payment Express fragment with PayPal in Site Builder

To set up the Payment Express fragment with PayPal for the online store, follow these steps.

1. In Site Builder, select the site and navigate to the **Fragments** menu and select **New**
2. In the New Fragment dialogue, find and select the **Payment express** module in the module select menu, and give your Fragment a name (example: Checkout Express). 
3. Click **Ok** to create the fragment.
3. In the module tree, select the new module (pre-labeled 'Checkout express' under your fragment object)
4. In the Properties section, update the Header to a heading you want to display for the express checkout section in your site (Example: Express Checkout)
5. You can set or adjust the **Height of the iFrame** in pixels (Example: 60)
6. Add "PayPal" to the **Supported tender types** field
7. Select **Save** to save your changes, and click **Finish editing** to complete editing the fragment
8. Click **Publish** to publish the fragment for use

### Set up the Checkout page with the Payment Express fragment

To set up the Payment Express fragment with PayPal in the Checkout page, follow these steps.

1. In Site Builder, with your site context set, navigate to the **Pages** menu and select your Checkout page.
2. Click **Edit** to edit the page
3. In the **Main slot**, select the ellipsis (...), and then select **Add Module**
4. In the **Add Module** dialogue box, add the **Container** module
5. Note: If a Container already exists for your site with the **checkout** fragment- to have the Payment Express section  render above the normal checkout container, position it above the existing checkout container within the **Main slot** section. You can move container positions by selecting their ellipsis (...), and choosing the "Move up" or "Move down" options.
5. In the **Container** module properties, it is recommended to use the following property settings:
- Container Layout: Stacked
- Width: Fill container
- Children Shown: Three
6. With the **Container** module still selected in the module tree, select the ellipsis (...), and then select **Add Fragment**
7. In the **Add Fragment** dialogue box, find and select your named created express payment fragment and click **OK**
8. Click the **Save** button to save your changes.
9. Click on **Finish editing** to complete editing the page, and **Publish** to publish your changes live.


### Set up the Cart page with the Payment Express fragment

To set up the Payment Express fragment with PayPal in the Cart page, follow these steps.

1. In Site Builder, with your site context set, navigate to the **Pages** menu and select your Cart page.
2. Click **Edit** to edit the page
3. Expand the **Main slot** in the tree view and locate the container which includes **Cart** module. The **Cart** module will contain a new specific slot for **Payment Express**
4. In the **Cart** module, select the **Payment Express** slot and select the ellipsis (...), and then select **Add Module**
5. In the **Add Module** dialogue box, add the **Payment express** module and click **OK**
6. With the express fragment still selected, in Properties add "Paypal" to the **Supported tender types** property.
7. Click the **Save** button to save your changes.
8. Click on **Finish editing** to complete editing the page, and **Publish** to publish your changes live.

### Modes of Delivery
With the Payment Express module using PayPal, the first delivery option returned against the shipping address selected from the PayPal account will be pre-selected. Users will have a chance to click **change** and adjust the shipping address to a different option if desired. 

The order of the delivery methods is configured in HQ on the Channel's **Modes of delivery** section. Additional information on setting up modes of delivery can be found in the [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery) article. The checkout module will also use the **delivery options module** when rendering modes of delivery during checkout. See additional details in the [delivery options module](../delivery-options-module.md) article.

Modes of delivery are displayed as added to the list in the Online Store. In Headquarters, navigate to **Retail and Commerce > Channels > online stores** and select the channel ID for your store. Under the **Setup** menu section, select **Modes of delivery**. The module modes of delivery will be displayed on the site similarly to the configuration shown. Use the **Manage modes of delivery** action item to add or remove modes of delivery for a Retail Channel or a Product.


## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)
