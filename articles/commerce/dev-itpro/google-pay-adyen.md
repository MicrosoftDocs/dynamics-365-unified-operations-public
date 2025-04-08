---
# required metadata

title: Configure Google Pay with Adyen
description: This article describes how to configure Google Pay with Adyen in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 06/14/2023
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2017-06-20
ms.custom: 
  - bap-template
---

# Configure Google Pay with Adyen

[!include [banner](../includes/banner.md)]

> [!WARNING]
> The Dynamics 365 Commerce pattern for Google Pay Express is currently not recommended for regions enforcing Payment Services Directive Two (PSD2) requirements. The payment module for Google Pay support calculates the final order price after returning to the Commerce checkout page when it has acquired the delivery address information for a user's order. PSD2 recommends that users see the full order total price within the authentication window of the digital wallet. Commerce will track future work to update the newer Google Pay direct module available to support express flows by updating order details within the Google Pay payment window when a delivery address is selected.

This article describes how to configure Google Pay with Adyen in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce offers an out-of-box integration for Google Pay when the Adyen payment gateway service is used. Google Pay is a digital wallet payment method that uses a Google Pay Merchant account in coordination with the Adyen payment service. When configured, the Google Pay button becomes available as a selectable payment method during online order checkout. When users select **Google Pay** in a supported browser or device, they're directed to complete their payment directly with the Google Pay service. They're then returned to the online storefront for order completion.

When Google Pay is used with the express checkout module in Commerce, the user's payment account information is automatically prepopulated in the checkout form to help customers get through the checkout process faster. Commerce includes a *payment express* module that enables express checkout behavior. Payment express modules can be used on the checkout or cart pages. Google Pay can also be configured with Adyen payment terminals and the Commerce point of sale (POS) for in-store use. For information on the variations of supportability available in Commerce for using Google Pay modules with payment express patterns, see [Configure the cart page for express payment using Google Pay](#configure-the-cart-page-for-express-payment-using-google-pay).

## Key terms

| Term | Description |
|---|---|
| Google Pay | Also known as the Google Pay "button," Google Pay is a wallet payment offering that is supported via the Adyen connector. It enables the customer experience and integration that are supported by the Dynamics Google Pay Connector. |
| Wallet | A payment type that doesn't include traditional payment characteristics, such as the bank identification number (BIN) range and expiration date that are used to differentiate credit and debit card types. |
| Payment express module | A Dynamics 365 Commerce module that supports faster checkout behavior with supported payment methods. |

## Prerequisites

- Using Google Pay with Adyen in Commerce requires a Google Merchant account. For information about how to set up your Google Merchant account, see the [Adyen documentation on Google Pay](https://docs.adyen.com/payment-methods/google-pay/).
- Follow steps 2 and 3 of [Adyen Google Pay Drop-in integration - Before you begin](https://docs.adyen.com/payment-methods/google-pay/web-drop-in#before-you-begin).
- Review steps 1 and 2 of [Adyen Google Pay Drop-in integration - Before you go live](https://docs.adyen.com/payment-methods/google-pay/web-drop-in#before-you-go-live).
- The Google Pay payment method must be integrated with your Adyen account. For instructions, see [Adyen Google Pay](https://www.adyen.com/payment-methods/google-pay).
- You must enable the enhanced wallet feature in Dynamics 365 Commerce headquarters. Go to **Workspaces \> Feature management**, search for the **Enhanced wallet support and payment improvements** feature, select the feature, and then select **Enable**. After the feature is enabled, run the **1110** distribution schedule to make the change available in all channels.
- Google Pay requires that you enable the **Enable single payment authorization checkout** property in site builder at **Site \> Site settings \> Extensions \> Cart and checkout**.

## Map the Google Pay payment method

Google Pay is a digital wallet payment method. For information about how to set up payment mapping for Google Pay, see [Wallet payment support](../wallets.md).

To map the Google Pay payment method to card tender types for both POS and online channels, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> Payment methods \> Card types**.
1. Select **New** to add a line for Google Pay.
1. In the **ID** field, enter **GooglePay**.
1. In the **Electronic payment name** field, enter "Google Pay".
1. In the **Type** field, enter **Wallet**.
1. In the **Issuer** field, enter **Google**.
1. On the action pane, select **Processor mapping** to open the **Processor payment mapping methods** dialog box.
1. Under **Unmapped Processor Payment Methods**, there's a list of unmapped processor payment methods, each of which is paired with the appropriate connector. To map unmapped Google Pay processor payment methods to card tender types, follow these steps for each card tender type:

    1. Under **Card tender types**, select a card tender type.
    1. In the **Unmapped Processor Payment Methods** column, select both the **Dynamics 365 Payment Connector for Adyen** connector (for use at the POS) and the **Dynamics 365 Payment Connector for Google Pay** connector (for use in online channels).
    1. Select **Add**. The selections are added to the **Mapped Processor Payment Methods** column.

1. When you're done mapping payment methods, select **Save**.
1. On the **Card types** page, select **Save**.

## Configure a Commerce online store with Google Pay

As of version 10.0.36, Commerce offers a direct Google Pay module for presenting Google Pay for online storefronts for the regular checkout flow. The payment module can also be configured for Google Pay. This section describes module configurations for both approaches. The direct Google Pay module is recommended for configuration because it will receive additional feature capabilities in future iterations.

### Add Google Pay as a new store payment method

To add Google Pay as a new payment method for your channel in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Payment methods**.
1. Select **New**.
1. Set the **Default function** option to **Wallet**.
1. Enter a **Payment method** value (the ID for the payment method, usually the next available payment method number in the payment method number series).
1. Enter a **Payment method name** (for example, **GooglePay**).
1. Set the **Default function** option to **Wallet**.
1. Select **Save**.
1. Go to your channel (**Retail and Commerce \> Channels \> Online stores** or, for POS, **Retail and Commerce \> Channels \> All stores**). 
1. On the action pane, on the **Set up** tab, in the **Set Up** group, select **Payment methods**.
1. Select **New**.
1. In the **Payment method** field, select the Google Pay payment method that you set up earlier. The **Payment method name** and **Function** fields should automatically be set by using the payment method values that you configured.
1. On the **General** FastTab, in the **Commerce** section, set the **Operation name** field to **Pay card**.
1. In the **Commerce** section, set the **Connector name** field. For online stores, select **Dynamics 365 Payment Connector for Google Pay**. For POS stores, select **Dynamics 365 Payment Connector for Adyen**.
1. On the **Posting** FastTab, enter any required **Account type** (for example, "Ledger account"), **Difference account**, and **Big difference account** settings.
1. Select **Save**.
1. With the Google Pay payment method selected, on the action pane, on the **Electronic payment setup** tab, select **New**. 
1. Under **Electronic payment types**, in the **ID** field, select the **GooglePay** card type.
1. Select **Save**.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**, and run the **1070 Channel configuration** job.

### Configure a Commerce online store to use Google Pay with the Google Pay module

To configure a Commerce online store to use Google Pay with the Google Pay module, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channels \> Online stores**.
1. Select your site's online store channel by selecting the channel's **Retail Channel Id** value.
1. On the **Payment accounts** FastTab, under **Connector**, confirm that the **Dynamics 365 Payment Connector for Adyen** connector is listed. If it isn't listed, follow the instructions in [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md) to add it.

    > [!NOTE]
    > In most cases, the **Dynamics 365 Payment Connector for Adyen** connector must be listed as the first connector for your channel (the first connector is also known as the primary connector). It must then be followed by other connectors that will be used, such as the **Dynamics 365 Payment Connector for PayPal** and **Dynamics 365 Payment Connector for Google Pay** connectors.

1. After the **Dynamics 365 Payment Connector for Adyen** connector is added, select **Add** to add the **Dynamics 365 Payment Connector for GooglePay** connector. Then set the following properties for the connector.

    | Field                  | Description | Required | Automatically set | Sample value |
    | ---------------------- | ----------- | -------- | ----------------- | ------------ |
    | Assembly Name          | The name of the assembly for the Dynamics 365 Payment Connector for GooglePay. | Yes | Yes | *Binary name* |
    | Service account ID     | The unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *GUID* |
    | Optional Domain | Enter the domain to use when payment requests are sent to Adyen. This domain is the unique identifier for your live environment in the format *\<random hexadecimal-encoded string\>-\<your company name\>*, and is present as the prefix inside the API URLs under **Account \> API URLs** in your company's live account on the Adyen Customer Area portal. For more information, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints). | Live only | No | Contact Adyen |
    | Google merchant ID     | Enter the Google Merchant ID that is assigned to your Google Merchant account. This property is required for production environments but is optional for test environments. For more information, visit <https://pay.google.com/>. | Yes | No | *Numeric identifier* |
    | Merchant account ID    | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in [Sign up with Adyen](adyen-connector-setup.md#sign-up-with-adyen). | Yes | No | *Merchant Identifier* |
    | Cloud API Key          | Enter the Adyen cloud API key. To obtain this key, follow the instructions in [Generate your API key](https://docs.adyen.com/development-resources/api-credentials#generate-api-key). | Yes | No | "abcdefg" |
    | Gateway environment    | The Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | "Live" |
    | Supported Currencies   | The currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | "USD;EUR" |
    | Supported Tender Types | The tender types that the connector should process. | Yes | Yes | "GooglePay" |
    | Authorization stale period (days) | Number of days before an authorization is considered stale and should be declined before going to the processor for capture. For more information, see [Manage payment authorizations](manage-payment-authorizations.md#adyen-connector-authorization-stale-period-parameter).| Yes | Yes | "14" |
    | Use the Dedicated Google Pay Payment Module | When you're using the direct Google Pay module, this property should be set to **True**. This setting informs the Google Pay connector to interact with the direct module instead of the payment module. | Yes (for this configuration with Google Pay module) | No | **True** |

1. After you're finished setting the connector properties, run the **1070 (Channel configuration**) distribution schedule job.

### Configure the checkout fragment with the Google Pay module

You can set up Google Pay as an option in the checkout payment section for payment-only, nonexpress functionality. The checkout form is filled in by the user, and the Google Pay payment page only readies the checkout for payment by Google Pay. No Google account information is used to overwrite the filled-in checkout details.

> [!NOTE]
> The following procedure assumes that your site uses a checkout fragment that is configured with pickup information, a shipping address, delivery options, contact information, optional terms and conditions, and a section for checkout elements. The default module library checkout module is released with a checkout section container that has text block, loyalty points, gift card, and payment modules. For more information, see [Payment module](../payment-module.md).

To set up Google Pay as a regular payment option in the **Payment Method** section of the checkout page using the Google Pay module, follow these steps.

1. Go to **Fragments**.
1. Select the **Checkout** fragment, and then select **Edit**.
1. In the **Checkout section container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog, select **Google Pay**, and then select **OK**.
1. In the Google pay module's properties pane, update the module properties as needed: 
    1. To rename the module for easier identification in the **Outline** view, select the pencil symbol next to the module name, enter a new name, and then select the **Apply** check mark symbol. 
    1. The **Supported tender types** value can be left blank unless there are multiple Google Pay payment connector instances set for the channel (a rare scenario). Otherwise, this value must match the **Supported Tender Types** string as set in the specific connector within the channel to which it's linked.
    1. A CSS class name can also be specified for **Custom CSS class name** to implement custom CSS styling for this module.
    2. Setting the **Render when module scrolls into view** property is recommended for modules that are hidden below the customer's view when interacting within the page. When set, the module renders on the customer's client device once the viewport is reached on the page. This setting can help improve overall initial page load times.

Once the Google Pay module is configured, select **Save**, select **Finish editing**, and then select **Publish** to publish the changes to the site.

#### Payment express support with the Google Pay module

Currently, the direct Google Pay module doesn't directly support the payment express functionality. If setting up payment express for a region storefront that isn't PSD2 enforced, the payment module can be used for the payment express behavior in the cart and checkout pages. The payment module in express behavior mode launches the Google Pay payment window for a user to authenticate to their Google account. In this pattern, the order subtotal without final tax, shipping, and fees associated is presented to the customer. When the customer completes the shipping address and payment selections in Google Pay, they're redirected to the Commerce storefront where final calculations for the order total use the shipping address information supplied by the payment express interaction. Future support will update the Google Pay module to handle direct in-payment-window updates of order pricing for customers to see and agree to final order totals within the payment method authentication window directly. 

To set up payment express functionality using the payment module, see [Configure the cart page for express payment using Google Pay](#configure-the-cart-page-for-express-payment-using-google-pay).

### Configure Commerce online store to use Google Pay with the payment module (Legacy)

To configure a Commerce online store to use Google Pay with the payment module, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channels \> Online stores**.
1. Select your site's online store channel by selecting the channel's **Retail Channel ID** value.
1. On the **Payment accounts** FastTab, under **Connector**, confirm that the **Dynamics 365 Payment Connector for Adyen** connector is listed. If it isn't listed, to add it follow the instructions in [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md).

    > [!NOTE]
    > In most cases, the Dynamics 365 Payment Connector for Adyen must be listed as the first connector for your channel (also known as the primary connector). It should then be followed by other connectors such as the Dynamics 365 Payment Connector for PayPal and the Dynamics 365 Payment Connector for Google Pay.

1. After you add the **Dynamics 365 Payment Connector for Adyen** connector, select **Add** to add the Dynamics 365 Payment Connector for GooglePay connector. Then set the following properties for the connector.

    | Field                  | Description | Required | Automatically set | Sample value |
    | ---------------------- | ----------- | -------- | ----------------- | ------------ |
    | Assembly name          | The name of the assembly for the Dynamics 365 Payment Connector for GooglePay. | Yes | Yes | *Binary name* |
    | Service account ID     | The unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *GUID* |
    | Optional domain | Enter the domain to use when payment requests are made to Adyen. This domain is the unique identifier for your live environment in the format *\<random hexadecimal string\>-\<your company name\>*, and is present as the prefix inside the API URLs under **Account \> API URLs** in your company's live account on the Adyen Customer Area portal. For more information, see [Live endpoints](https://docs.adyen.com/development-resources/live-endpoints). | Live only | No | Contact Adyen |
    | Google Merchant ID     | The Google Merchant ID that is assigned to your Google Merchant account. This property is required for production environments but is optional for test environments. For more information, see <https://pay.google.com>(https://pay.google.com). | Yes | No | *Numeric identifier* |
    | Merchant account ID    | The unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in [Sign up with Adyen](adyen-connector-setup.md#sign-up-with-adyen). | Yes | No | *Merchant Identifier* |
    | Cloud API Key          | The Adyen cloud API key. To obtain this key, follow the instructions in [Generate your API key](https://docs.adyen.com/development-resources/api-credentials#generate-api-key). | Yes | No | "abcdefg" |
    | Gateway environment    | The Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | "Live" |
    | Supported currencies   | The currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes | Yes | "USD;EUR" |
    | Supported tender types | The tender types that the connector should process. | Yes | Yes | "GooglePay" |
    | Authorization stale period (days) | Number of days before an authorization is considered stale and should be declined before going to the processor for capture. For more inforamtion, see [Manage payment authorizations](manage-payment-authorizations.md#adyen-connector-authorization-stale-period-parameter). | Yes | Yes | "14" |
    | Use the Dedicated Google Pay Payment Module | When you use the direct payment module, this property should be set to **False** (or left blank). This property informs the Google Pay connector to interact with the payment module instead of the Google Pay module | No (blank defaults to **False**) | No | **False** |

1. After you finish setting the connector properties, run the **1070 (Channel configuration**) distribution schedule job.

#### Use the payment express section in the cart and checkout pages with Google Pay using the payment module

> [!WARNING]
> The Dynamics 365 Commerce pattern for Google Pay Express is currently not recommended for regions enforcing PSD2 requirements. The payment module for Google Pay support calculates the final order price after return to the Commerce checkout page when it has acquired the delivery address information for a user's order. PSD2 recommends the user see the full order total price within the authentication window of the digital wallet. Commerce will track future work to update the newer Google Pay direct module available to support express flows by updating order details within the Google Pay payment window when a delivery address is selected. A page can't support using both the payment module for express checkout and the newer Google Pay module for the checkout section. Either only the payment module can be used for both express and regular checkout flows, or only the Google Pay module can be used for the normal checkout payment (nonexpress) flows.

The Commerce payment module payment express patterns give site customers the option to check out faster by using their payment service account information during the checkout process. The payment module payment express actions reference the linked payment connector via the **Supported tender types** string used in the same attribute of the payment connector. Express payment with the payments module then returns the user-selected order details (address, contact information, and payment method) to prefill the checkout form.

When the payment module is used with express patterns with Google Pay, if customers select **Google Pay** in the **Payment Express** section, the Google Pay payment window opens. Users can then sign in to their Google account to use their account shipping address, billing address, email address, and Google Pay payment method of choice to pay for the transaction.

When users complete the action in the Google Pay window, they're directed to the Commerce site checkout page, where the checkout form is prefilled with their Google Pay account details. After users return to the checkout page from the Google Pay window, they'll see the following details:

- In the payment express flow, the first delivery option that is available for the shipping address that was returned is preselected for the customer.
- The shipping address and contact information, such as the customer's email address, are populated in the checkout form. If they're using express checkout, the email address from the express account is used.
- The payment method is selected from the customer's digital Google Pay wallet.

Customers can review orders and change checkout order details before they select **Place order** to finalize the order.

#### Configure the checkout fragment for express using Google Pay with the payment module

To set up the checkout fragment for express payment using Google Pay in site builder, follow these steps.

1. Go to **Fragments**.
1. Select the **Checkout** fragment, and then select **Edit**.
1. In the **Checkout express payment container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select **Payment express**, and then select **OK**.
1. In the Payment express module's properties pane, update the module properties as needed: 

    1. To rename the module for easier identification in the outline view, select the pencil symbol next to the module name, enter a new name, and then select the **Apply** check mark symbol.
    1. For the **Height of the iFrame** property, set a height in pixels that meets your page design needs (for example, enter "65" to set a height of 65 pixels).
    1. Set the **Supported tender types** value to **GooglePay**. This value must match the **Supported Tender Types** string in the connector set up for the channel.
    1. The **Payment style override** value is used to apply CSS code styling to the module. Site builder CSS overrides and styles don't apply to this module via this property. This styling doesn't affect the inner-window styles within the payment iFrame element rendered by the payment service.
    1. A **Custom CSS class name** can also be referenced to apply to this module. This value can be the class name as defined in the theme pack. This styling doesn't affect the inner-window styles within the payment iFrame element rendered by the payment service.
    1. Setting the **Render when module scrolls into view** property is recommended for modules that are hidden below the customer's view when interacting within the page. When set, the module renders on the customer's client device once the viewport is reached on the page. This setting can help improve overall initial page load times.

1. Optional: In the **Checkout express payment container** module, add a text block module that includes instructions or disclosure information for the express payment section of your site. After you add the module, in the properties pane, enter the desired text in the **Rich text** field. You can position the text above or below the payment express modules by selecting the ellipsis (**...**) in the **Text block** slot, and then selecting **Move up** or **Move down**.
1. Select **Save** to save your changes, and then select **Finish editing**.
1. Select **Publish** to publish the fragment.

#### Configure the cart page for express payment using Google Pay

To set up the cart page for express payment using Google Pay in site builder, follow these steps.

1. Go to **Pages**.
1. Select your site's cart page, and then select **Edit**.
1. Under the **Main slot**, find the container that contains the **Cart** module.
1. Under the **Cart** module, select the **Payment express** section.
1. In the **Payment express** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select **Payment express**, and then select **OK**.
1. In the Payment express module's properties pane, update the module properties as needed: 
    1. To rename the module for easier identification in the outline view, select the pencil symbol next to the module name, enter a new name, and then select the **Apply** checkmark symbol.
    1. For the **Height of the iFrame** property, set a height in pixels that meets your page design needs (for example, enter "50" to set a height of 50 pixels).
    1. Set the **Supported tender types** value to **GooglePay**. This value must match the **Supported Tender Types** string in the connector set up for the channel.
    1. Use the **Payment style override** property to apply CSS code styling to the module. Site builder CSS overrides and styles don't apply to this module via this property. This styling doesn't affect the inner-window styles within the payment iFrame element rendered by the payment service.
    1. A **Custom CSS class name** can also be referenced to apply to this module. This value can be the class name as defined in the theme pack. This styling doesn't affect the inner-window styles within the payment iFrame element rendered by the payment service.
    1. Setting the **Render when module scrolls into view** property is recommended for modules that are hidden below the customer's view when interacting within the page. When set, the module renders on the customer's client device once the viewport is reached on the page. This setting can help improve overall initial page load time.
1. Optional: In the **Checkout express payment container** module, add a text block module that includes instructions or disclosure information for the express payment section of your site. After you add the module, in the properties pane, enter the desired text in the **Rich text** field. You can position the text above or below the payment express modules by selecting the ellipsis (**...**) in the **Text block** slot, and then selecting **Move up** or **Move down**.
1. Select **Save** to save your changes, and then select **Finish editing**.
1. Select **Publish** to publish the page.

Users can include up to three supported **Payment Express** modules (in other words, three available supported payment options) in the cart **Payment Express** slot.

#### Modes of delivery

With the payment express module that uses Google Pay, the first delivery option returned against the selected shipping address from the Google Pay account is preselected. Users have an opportunity to adjust the shipping address to a different option if they want to.

The order in which the delivery methods are displayed in the payment express module is configured on the channel's **Modes of delivery** page in Commerce headquarters. In Commerce headquarters, go to **Retail and Commerce \> Channels \> Online stores**, and select the **Retail channel ID** value for your store. On the action pane, on the **Setup** tab,  select **Modes of delivery**. The modes of delivery listed are displayed in the same order in the payment express module. Select **Manage modes of delivery** on the action pane to add or remove modes of delivery for a retail channel or product. For more information about how to set up modes of delivery, see [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

The checkout module also uses the delivery options module when modes of delivery are rendered during checkout. For more information, see [Delivery options module](../delivery-options-module.md).

Modes of delivery are displayed as they're added to the **Modes of delivery** list in the online store.

### Set up Google Pay as an option in the checkout payment section of the payment module

You can set up Google Pay as an option in the checkout payment section for payment-only, nonexpress functionality. The checkout form is filled in by the user, and the Google Pay payment page only readies the checkout for payment by Google Pay. No Google account information is used to overwrite the filled-in checkout details.

> [!NOTE]
> The following procedure assumes that your site uses a checkout fragment that is configured with pickup information, a shipping address, delivery options, contact information, optional terms and conditions, and a section for checkout elements. The default module library checkout module is released with a checkout section container that has text block, loyalty points, gift card, and payment modules. For more information, see [Payment module](../payment-module.md).

To set up Google Pay as a regular payment option in the **Payment Method** section of the checkout page, follow these steps.

1. In site builder, go to **Fragments**, and then select your site's checkout fragment.
1. Select **Edit**.
1. In the **Checkout information** slot, select the **Checkout section container**, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Payment** module, and then select **OK**.
1. In the **Payment** module's properties pane on the right, set the properties for the container module:
    - **Heading** – Enter a heading to display for the express checkout section of your site (for example, "Google Pay").
    - **Height of the iFrame** – Change the value to your preferred design height in pixels (for example, "75"). 
    - **Supported tender types** – Enter "GooglePay" to match the configuration for the Google Pay connector in Commerce headquarters.
    - **Is primary payment** – Leave the checkbox cleared. (This property is typically enabled for the Adyen checkout module.)
    - **Payment style override** – This property isn't supported for the Google Pay configuration.
    - **Use connector id** – This property must be selected if multiple payment connectors are used on the page.
    - **Use browser set language code for iFrame** – This property isn't supported for the Google Pay configuration.
    - A **Custom CSS class name** can also be referenced to apply to this module. This value can be the class name as defined in the theme pack. This styling doesn't affect the inner-window styles within the payment iframe rendered by the payment service.
    - Setting the **Render when module scrolls into view** property is recommended for modules that are hidden below the customer's view when interacting within the page. When set, the module renders on the customer's client device once the viewport is reached on the page. This setting can help improve overall initial page load times.
1. Position the module above or below other payment modules by selecting the ellipsis (**...**) in the **Payment** slot, and then selecting **Move up** or **Move down**.
1. Select **Save** to save your changes, and then select **Finish editing**.
1. Select **Publish**.

### Configure Google Pay in site builder settings 

Before you configure your fragments or pages with Google Pay, you must ensure that the content security policies (CSP) for your site are configured in Commerce site builder.

To ensure that your content security policies are set in site builder, follow these steps.

1. For your site, go to **Site settings \> Extensions**.
1. On the **Content security policy** tab, add a line for `*.google.com` to the **child-src**, **connect-src**, **frame-ancestors**, **frame-src**, **img-src**, **script-src**, and **style-src** directives.
1. When finished, select **Save and publish**.

Additionally, select the **Enable single payment authorization checkout** property in site builder at **Site settings \> Extensions \> Cart and checkout**.

## Configure Commerce POS for Google Pay

The POS configuration uses the setting of the hardware profile's **EFT service** field for the Dynamics 365 Payment Connector for Adyen. For information about how to configure the electronic funds transfer (EFT) service for the Dynamics 365 Payment Connector for Adyen in Commerce headquarters, see [Set up a Dynamics 365 POS hardware profile](adyen-connector-setup.md#set-up-a-dynamics-365-pos-hardware-profile).

The processor mapping for the Adyen connector captures the wallet card types that Google Pay uses at the POS terminal. Map for the desired card type against the **Dynamics 365 Payment Connector for Adyen** and **Processor payment** options. The mapping steps resemble the steps in the [Map the Google Payment method](#map-the-google-pay-payment-method) section. Because POS supports only a single connector as configured for the store, the payment connector maps against the **Processor payment** value returned by Adyen.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)
