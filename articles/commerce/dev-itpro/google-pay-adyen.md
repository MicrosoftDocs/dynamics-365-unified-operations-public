---
# required metadata

title: Configure Google Pay with Adyen
description: This article describes how to configure Google Pay with Adyen in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 07/05/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2017-06-20

---

# Configure Google Pay with Adyen

[!include [banner](../includes/banner.md)]

This article describes how to configure Google Pay with Adyen in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce offers an out-of-box integration for Google Pay when the Adyen payment gateway service is used. Google Pay is a digital wallet payment method that uses a Google Pay Merchant account in coordination with the Adyen payment service. When it's configured, the Google Pay button is available as a selectable payment method during online order checkout. When users select **Google Pay** in a supported browser or device, they're directed to complete their payment directly with the Google Pay service. They're then returned to the online storefront to complete the order.

When Google Pay is used with the express checkout module in Commerce, the user's payment account information automatically is prefilled in the checkout form to help the user get through the checkout process faster. Commerce includes a payment express module that enables express checkout behavior. The payment express module can be used in a fragment that is included on the checkout or cart page. The Dynamics 365 Payment Connector for Google Pay connector reference is used in addition to the Dynamics 365 Payment Connector for Adyen to enable both the payment express and regular checkout options when PayPal is configured. Google Pay can also be configured with Adyen payment terminals and the Commerce point of sale (POS) for in-store use.

## Key terms

| Term | Description |
|---|---|
| Google Pay | Also known as the Google Pay "button," Google Pay is a wallet payment offering that is supported via the Adyen connector. It enables the customer experience and integration that are supported by the Dynamics Google Pay Connector. |
| Wallet | A payment type that doesn't include traditional payment characteristics, such as the bank identification number (BIN) range and expiration date that are used to differentiate credit and debit card types. |
| Payment express module | A Dynamics 365 Commerce module that supports faster checkout behavior with supported payment methods. |

## Prerequisites

Using Google Pay with Adyen in Commerce requires a Google Merchant account. For information about how to set up your Google Merchant account, see the [Adyen documentation on Google Pay](https://docs.adyen.com/payment-methods/google-pay/) and Google's [Integration checklist](https://developers.google.com/pay/api/web/guides/test-and-deploy/integration-checklist).

The Google Pay payment method must also be integrated with your Adyen account. For integration link instructions, see [Adyen Google Pay](https://www.adyen.com/payment-methods/google-pay).

You must also enable the enhanced wallet feature in Dynamics 365 Commerce headquarters. Go to **Workspaces \> Feature management**, search for the **Enhanced wallet support and payment improvements** feature, select the feature, and then select **Enable**. After the feature has been enabled, run the **1110** distribution schedule to make the change available in all channels.

## Map the Google Pay payment method

Google Pay is a digital wallet payment method. For information about how to set up payment mapping for Google Pay, see [Wallet payment support](../wallets.md).

To map the Google Pay payment method to card tender types for both POS and online channels, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> Payment methods \> Card types**.
1. Select **New** to add a line for Google Pay.
1. In the **ID** field, enter **GooglePay**.
1. In the **Electronic payment name** field, enter **Google Pay**.
1. In the **Type** field, enter **Wallet**.
1. In the **Issuer** field, enter **Google**.
1. On the Action Pane, select **Processor mapping** to open the **Processor payment mapping methods** dialog box.
1. Under **Unmapped Processor Payment Methods**, you'll see a list of unmapped processor payment methods, each of which is paired with the appropriate connector. To map unmapped Google Pay processor payment methods to card tender types, follow these steps for each card tender type:

    1. Under **Card tender types**, select a card tender type.
    1. In the **Unmapped Processor Payment Methods** column, select both the **Dynamics 365 Payment Connector for Adyen** connector (for use at the POS) and the **Dynamics 365 Payment Connector for Google Pay** connector (for use in online channels).
    1. Select **Add**. The selections are added to the **Mapped Processor Payment Methods** column.

1. When you've finished mapping payment methods, select **Save**.
1. On the **Card types** page, select **Save**.

## Configure a Commerce online store for Google Pay

To configure a Commerce online store to use Google Pay, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channels \> Online stores**.
1. Select your site's online store channel by selecting the channel's **Retail Channel Id** value.
1. On the **Payment accounts** FastTab, under **Connector**, confirm that the **Dynamics 365 Payment Connector for Adyen** connector is listed. If it isn't listed, follow the instructions in [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md) to add it.

    > [!NOTE]
    > In most cases, the **Dynamics 365 Payment Connector for Adyen** connector must be listed as the first connector for your channel (the first connector is also known as the primary connector). It must then be followed by other connectors that will be used, such as the **Dynamics 365 Payment Connector for PayPal** and **Dynamics 365 Payment Connector for GooglePay** connectors.

1. After the **Dynamics 365 Payment Connector for Adyen** connector has been added, select **Add** to add the **Dynamics 365 Payment Connector for GooglePay** connector. Then set the following properties for the connector.

    | Field                  | Description | Required | Automatically set | Sample value |
    | ---------------------- | ----------- | -------- | ----------------- | ------------ |
    | Assembly Name          | The name of the assembly for the Dynamics 365 Payment Connector for GooglePay. | Yes | Yes | *Binary name* |
    | Service account ID     | The unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *GUID* |
    | Google merchant ID     | Enter the Google Merchant ID that is assigned to your Google Merchant account. This property is required for production environments but is optional for test environments. For more information, visit <https://pay.google.com/>. | Yes | No | *Numeric identifier* |
    | Merchant account ID    | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in [Sign up with Adyen](adyen-connector-setup.md#sign-up-with-adyen). | Yes | No | *Merchant Identifier* |
    | Cloud API Key          | Enter the Adyen cloud API key. To obtain this key, follow the instructions in [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key). | Yes | No | "abcdefg" |
    | Gateway environment    | The Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | "Live" |
    | Supported Currencies   | The currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | "USD;EUR" |
    | Supported Tender Types | The tender types that the connector should process. | Yes | Yes | "GooglePay" |

1. After you've finished setting the connector properties, run the **1070 (Channel configuration**) distribution schedule job.

## Configure Commerce POS for Google Pay

The POS configuration uses the setting of the hardware profile's **EFT service** field for the Dynamics 365 Payment Connector for Adyen. For information about how to configure the electronic funds transfer (EFT) service for the Dynamics 365 Payment Connector for Adyen in Commerce headquarters, see [Set up a Dynamics 365 POS hardware profile section](adyen-connector-setup.md#set-up-a-dynamics-365-pos-hardware-profile).

The processor mapping for the Adyen connector captures the wallet card types that Google Pay uses at the POS terminal.

### Use the payment express module with Google Pay

The Commerce payment express module works with supporting payment methods to give site customers the option to check out faster by using their payment service account information during the checkout process. The payment express module references the configured connector button and returns the user-selected order details (address, contact information, and payment method) to prefill the checkout form.

When the payment express module is used with Google Pay, if customers select the Google Pay button in the **Payment Express** section, the Google Pay iframe window is opened. Users can then sign in to their Google account to use their account shipping address, billing address, email address, and Google Pay payment method of choice to pay for the transaction.

When users complete the action in the Google Pay window, they're directed to the Commerce site checkout page, where the checkout form is prefilled with their Google Pay account details. After users return to the checkout page from the Google Pay window, they'll see the following details:

- In the payment express flow, the first delivery option that is available for the shipping address that was returned will be preselected for the customer.
- When Google Pay is used, no contact email address is returned. Guest checkout users will have to enter an email address in the contact section of the checkout page. Signed-in users will have their contact data automatically filled in from their Dynamics customer account (the primary email address that they used for authentication).

Customers have the option to review orders and change checkout order details before they select **Place order** to finalize the order.

### Configure Google Pay in site builder 

Before you configure your fragments or pages with Google Pay, you must ensure that your content security policies for your site are set in Commerce site builder.

To ensure that your content security policies are set in site builder, follow these steps.

1. In your site, go to **Site settings \> Extensions**.
1. On the **Content security policy** tab, add a line for `*.google.com` to the **child-src**, **connect-src**, **frame-ancestors**, **frame-src**, **img-src**, **script-src**, and **style-src** directives.
1. When you've finished, select **Save and publish**.

### Configure the payment express fragment with Google Pay in site builder

To set up the payment express fragment with Google Pay for the online store, follow these steps.

1. In site builder, go to **Fragments**.
1. Select **New**.
1. In the **New fragment** dialog box, select the **Container** module, enter a fragment name (for example, **Express Checkout**), and then select **OK**. 
1. Select the new fragment's **Default Container** slot.
1. In the properties pane on the right, set the properties for the container module:

    - **Heading** – Enter a heading to display for the express checkout section of your site (for example, **Express Checkout**).
    - **Container layout** – Select **Flow**.
    - **Width** – Select **Fill container**.
    - **Children shown** – Select **Three** to specify the number of children that will fit in a row of the express checkout section of the checkout page (for example, a text box, payment express for PayPal, and payment express for Google Pay).
    - **CSS class name** – Enter **msc-express-payment-container** (required).

    > [!IMPORTANT]
    > - The **CSS class name** value must be set to **msc-express-payment-container** to control the behavior of the container during checkout. This behavior includes hiding, collapsing, and other actions that apply to the express checkout section during the checkout flow. The **msc-express-payment-container** class works with the default operations that are released with the module library checkout module.
    > - Additional styles can be included against the **CSS class name**. If you customize the behavior of the module, cross-check the style controls if you're using the same module library coded behavior in the checkout module for express checkout behavior.

1. In the **Default container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Payment express** module, and then select **OK**.
1. In the **Payment express** module properties pane, set or adjust the **Height of the iFrame** value in pixels (for example, **60**).
1. In the **Supported tender types** field, enter **GooglePay**. The value must match the **Supported Tender Types** string in the connector that is set up for the channel (as described in the [Configure a Commerce online store for Google Pay](#configure-a-commerce-online-store-for-google-pay) section earlier in this article).

    > [!NOTE]
    > You can repeat steps 6 through 9 to add **Payment express** modules for other payment methods. Align the **Supported tender types** value with the additional configured payment types (for example, **Paypal**).

1. Optional: You can add a text block module to the default container module to include instructions or disclosure information. After you add the module, in the properties pane, enter the desired text in the **Rich text** field. You can position the text above or below the payment express modules by selecting the ellipsis (**...**) in the **Text block** slot, and then selecting **Move up** or **Move down**.
1. Select **Save** to save your changes, and then select **Finish editing**.
1. Select **Publish** to publish the fragment.

### Add the payment express fragment to the checkout page

To add the payment express fragment to the checkout page, follow these steps.

1. In site builder, go to **Pages**, and then select your site's checkout page.
1. Select **Edit**.
1. In the **Main slot**, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.
1. In the properties pane on the right, set the properties for the container module:

    - **Container Layout** – Select **Stacked**.
    - **Width** – Select **Fill container**.
    - **Children Shown** – Select **Three** to specify the number of children that will fit in a row of the express checkout section of the checkout page (for example, a text box, payment express for PayPal, and payment express for Google Pay).

1. In the **Container** module slot, select the ellipsis (**...**), and then select **Add fragment**.
1. In the **Select a fragment** dialog box, select the express payment fragment that you created, and then select **OK**.
1. Select **Save** to save your changes, and then select **Finish editing**.
1. Select **Publish** to publish the page.

> [!NOTE]
> If the checkout page already includes a container that has the checkout fragment, and you want the payment express module to be rendered above the normal checkout container, you can position it above or below the existing checkout by selecting the ellipsis (**...**) in the **Main slot**, and then selecting **Move up** or **Move down**.

### Add the payment express fragment to the cart page

To add the payment express fragment to the cart page, follow these steps.

1. In site builder, go to **Pages**, and then select your site's cart page.
2. Select **Edit**.
3. In the outline view, expand the **Main slot** in the tree view, and find the container that contains the **Cart** module.
4. In the **Cart** module, select the **Payment Express** slot, select the ellipsis (**...**), and then select **Add module**.
5. In the **Select modules** dialog box, select the **Payment express** module, and then select **OK**.
6. Select the **Payment express** module slot. Then, in the properties pane on the right, under **Supported tender types**, enter **GooglePay**. The value must match the **Supported Tender Types** string in the connector that was set up for the channel (as described in the [Configure a Commerce online store for Google Pay](#configure-a-commerce-online-store-for-google-pay) section earlier in this article).
1. Select **Save** to save your changes, and then select **Finish editing**.
1. Select **Publish** to publish the page.

Users can include up to three supported **Payment Express** modules (in other words, three available supported payment options) in the cart **Payment Express** slot.

### Set up Google Pay as an option in the checkout payment section

You can set up Google Pay as an option in the checkout payment section for payment-only, non-express functionality. The checkout form will be filled in by the user, and the Google Pay payment page will only ready the checkout for payment by Google Pay. No Google account information will be used to overwrite the filled-in checkout details.

> [!NOTE]
> The following procedure assumes that your site uses a checkout fragment that is configured with pickup information, a shipping address, delivery options, contact information, optional terms and conditions, and a section for checkout elements. The default module library checkout module is released with a checkout section container that has text block, loyalty points, gift card, and payment modules. For more information, see [Payment module](../payment-module.md).

To set up Google Pay as a regular payment option in the **Payment Method** section of the checkout page, follow these steps.

1. In site builder, go to **Fragments**, and then select your site's checkout fragment.
1. Select **Edit**.
1. In the **Checkout information** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Payment** module, and then select **OK**.
1. In the **Payment** module's properties pane on the right, set the properties for the container module:

    - **Heading** – Enter a heading to display for the express checkout section of your site (for example, **Google Pay**).
    - **Height of the iFrame** – Change the value to your preferred design height in pixels (for example, **75**). 
    - **Supported tender types** – Enter **GooglePay** to match the configuration for the Google Pay connector in Commerce headquarters.
    - **Is primary payment** – Leave the checkbox cleared. (This property is typically enabled for the Adyen checkout module.)
    - **Payment style override** – This property isn't supported for the Google Pay configuration.
    - **Use connector id** – This property must be selected if multiple payment connectors are used on the page.

1. Position the module above or below other payment modules by selecting the ellipsis (**...**) in the **Payment** slot, and then selecting **Move up** or **Move down**.
1. Select **Save** to save your changes, and then select **Finish editing**.
1. Select **Publish**.

### Modes of delivery

With the payment express module that uses Google Pay, the first delivery option that is returned against the selected shipping address from the Google Pay account will be preselected. Users have an opportunity to adjust the shipping address to a different option if they want.

The order in which the delivery methods are displayed in the payment express module is configured on the channel's **Modes of delivery** page in Commerce headquarters. In Commerce headquarters, go to **Retail and Commerce \> Channels \> Online stores**, and select the **Retail channel ID** value for your store. On the Action Pane, on the **Setup** tab,  select **Modes of delivery**. The modes of delivery that are listed will be displayed in the same order in the payment express module. Select **Manage modes of delivery** on the Action Pane to add or remove modes of delivery for a retail channel or product. For more information about how to set up modes of delivery, see [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

The checkout module also uses the delivery options module when modes of delivery are rendered during checkout. For more information, see [Delivery options module](../delivery-options-module.md).

Modes of delivery are displayed as they're added to the **Modes of delivery** list in the online store.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)
