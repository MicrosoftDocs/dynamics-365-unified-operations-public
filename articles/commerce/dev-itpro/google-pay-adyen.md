---
# required metadata

title: Configure Google Pay with Adyen
description: This topic describes how to configure Google Pay with Adyen in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 05/24/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2017-06-20

---

# Configure Google Pay with Adyen

[!include [banner](../includes/banner.md)]

This topic describes how to configure Google Pay with Adyen in Microsoft Dynamics 365 Commerce.

## Key terms

| Term | Description |
|---|---|
| Google Pay | Also known as the Google Pay "button", Google Pay is a wallet payment offering supported via the Adyen connector, allowing the customer experience and integration supported by the Dynamics Google Pay Connector. |
| Wallet | A payment type that doesn't include traditional payment characteristics such as the bank identification number (BIN) range and expiration date that are used to differentiate credit and debit card types. |
|Payment Express |An added module in Dynamics 365 Commerce that supports faster checkout behavior with supported payment methods.|

Microsoft Dynamics 365 Commerce offers an out-of-box integration for Google Pay when using the Adyen payment gateway service. Google Pay is a digital wallet payment method that uses a Google Pay merchant account in coordination with the Adyen payment service. When configured, the Google Pay button is a selectable payment method that is available as part of an online order checkout. When users select **Google Pay** from a supported browser or device, they're directed to complete their payment directly with the Google Pay service and then are returned to the online storefront for order completion. 

When using Google Pay with the express checkout module in Commerce, users have their payment account information automatically prefilled on the checkout form to get through the checkout process faster. Commerce includes a payment express module that enables express checkout behavior. The payment express module can be used in a fragment that is included in the checkout or cart page. The Dynamics 365 Payment Connector for Google Pay connector reference is used in addition to the Dynamics 365 Payment Connector for Adyen to enable both the payment express or regular checkout options when PayPal is configured. Google Pay can also be configured with Adyen payment terminals and the Commerce point-of-sale (POS) for in-store use.

## Prerequisites

Using Google Pay with Adyen in Commerce requires a Google merchant account. For information on setting up your Google Merchant account, see the [Adyen documentation on Google Pay](https://docs.adyen.com/payment-methods/google-pay/) and Google's [Integration checklist](https://developers.google.com/pay/api/web/guides/test-and-deploy/integration-checklist).

The Google Pay payment method must also be integrated with your Adyen account. For integration link instructions, see [Adyen Google Pay](https://www.adyen.com/payment-methods/google-pay).

You must also enable the enhanced wallet feature in Dynamics 365 Commerce headquarters. To do so, go to **Workspaces \> Feature management**, search for the **Enhanced wallet support and payment improvements** feature, select the feature, and then select **Enable**. After the feature has been enabled, run the **1110** distribution schedule to make the change available in all channels.

## Map the Google Pay payment method

Google Pay is a digital wallet payment method. For information on setting up payment mapping for Google Pay, see [Wallet payment support](../wallets.md). 

To map the Google Pay payment method to card tender types for both point of sale (POS) and online channels, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> Payment methods \> Card types**. 
1. Select **New** to add a line for GooglePay. 
1. For **ID**, enter **GooglePay**.
1. For **Electronic payment name**, enter **Google Pay**.
1. For **Type**, enter **Wallet**.
1. For **Issuer**, enter **Google**.
1. On the action pane, select **Processor mapping** to bring up the **Processor payment mapping methods** dialog box.
1. Under **Unmapped Processor Payment Methods**, you'll see a list of umapped processor payment methods, each paired with the appropriate connector. To map unmapped Google Pay processor payment methods to card tender types, do the following for each card tender type:
    1. Under **Card tender types**, select a card tender type.
    1. Under **Unmapped Processor Payment Methods**, select both the **Dynamics 365 Payment Connector for Adyen** (for use at POS) and the **Dynamics 365 Payment Connector for Google Pay** (for online channel) connectors.
    1. Select **Add**. This moves the selections to the **Mapped Processor Payment Methods** column.
1. When you're done mapping payment methods, select **Save**.
1. On the **Card types** page, select **Save**.

## Configure a Commerce online store for Google Pay

To configure a Commerce online store to use Google Pay, follow these steps.

1. In Commerce headquarters, navigate to the **Retail and Commerce \> Channels \> Online stores**.
1. Select your site's online store channel by selecting the channel's **Retail Channel Id**. 
1. On the **Payment accounts** FastTab, under **Connector**, check to see if the **Dynamics 365 Payment Connector for Adyen** connector is listed. If not, follow the directions in [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md) to add the connector. 

    > [!NOTE]
    > In most cases, the **Dynamics 365 Payment Connector for Adyen** must be listed as the first connector for your channel (otherwise known as the primary connector), followed by other connectors to be used such as the **Dynamics 365 Payment Connector for PayPal** and **Dynamics 365 Payment Connector for GooglePay** connectors.

1. Once the **Dynamics 365 Payment Connector for Adyen** has been added, select **Add** to add the **Dynamics 365 Payment Connector for GooglePay**, and then set the following properties for the connector:

| Field                                  | Description                                                  | Required | Automatically set | Sample value         |
| -------------------------------------- | ------------------------------------------------------------ | -------- | ----------------- | -------------------- |
| **Assembly Name**                          | The auto populated name of the assembly for the Dynamics 365 Payment Connector for GooglePay. | Yes      | Yes               | *Binary name*        |
| **Service account ID**                     | The auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes      | Yes               | *GUID*               |
| **Google merchant ID** | Required for **Production** environments and optional for test environments, the Google Merchant ID assigned to your Google Merchant account.  (See https://pay.google.com/ for additional details). | Yes      | No                | *Numeric identifier* |
| **Merchant account ID**                    | The unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in [Sign up with Adyen](adyen-connector-setup.md#sign-up-with-adyen). | Yes      | No                | *Merchant Identifier* |
| **Cloud API Key**                          | The Adyen cloud API key. Obtain this key by following the instructions in [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key). | Yes      | No                | "abcdefg"            |
| **Gateway environment**                    | The Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes      | Yes               | "Live"               |
| **Supported Currencies**                   | The currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes      | Yes               | "USD;EUR"            |
| **Supported Tender Types**                 | The tender types that the connector should process.    | Yes      | Yes               | "GooglePay"          |

5. Once the connector properties have been set, run the **1070 (Channel configuration**) distribution schedule job.

## Configure Commerce POS for Google Pay

The POS configuration uses the hardware profile's **EFT service** field configuration for the **Dynamics 365 Payment Connector for Adyen**. For information on configuring the EFT service for the Dynamics 365 Payment Connector for Adyen in headquarters, see [Set up a Dynamics 365 POS hardware profile section](adyen-connector-setup.md#set-up-a-dynamics-365-pos-hardware-profile). 

The processor mapping for the Adyen connector captures the wallet card types used by Google Pay at the POS terminal. 

### Use the payment express module with Google Pay

The Commerce payment express module works with supporting payment methods to offer site customers the option to check out faster using their payment service account information during the checkout process. The payment express module references the configured connector button and returns the user-selected order details (address, contact information, and payment method) to prepopulate the checkout form.

With Google Pay, selecting the Google Pay button in the **Payment Express** section launches the Google Pay iframe window where users can sign in to their Google account to use their account shipping address, billing address, email, and Google Pay payment method of choice to pay for the transaction.

When users complete the action in the Google Pay window, they are directed to the Commerce site checkout page with the checkout form prepopulated with their Google Pay account details. After users return to the checkout page from the Google Pay window:

- In the Payment Express flow, the first **Delivery Option** available for the shipping address returned will be preselected for the customer.  
- With Google Pay, a contact email address is not returned. Guest checkout users will need to enter an email address in the contact section of the checkout page. Signed-in users will have their contact data automatically populated from their Dynamics customer account (their primary email used for authentication).

Customers have the option to review orders and change checkout order details before selecting **Place order** to finalize the order.

### Configure Google Pay in site builder 

Before configuring your fragments or pages with Google Pay, make sure your Content security policy's are set in Commerce site builder for your site. To do this, log in to your Commerce site builder tool:

1. Navigate to your site in site builder (choosing the site from the **Home** screen, or selecting the site in the upper right site-picker menu).
1. Open **Site Settings** > **Extensions** and go to the **Content security policy** tab.
1. Click **Add** and add a line with `*.google.com` to the **child-src**, **connect-src**, **frame-ancestors**, **frame-src**, **img-src**, **script-src**, and **style-src** directives.
1. When completed, click the **Save and publish** button at the top of the page to commit the changes.

### Configure the payment express fragment with Google Pay in site builder

To set up the Payment Express fragment with Google Pay for the online store, follow these steps:

1. In site builder, select the site and navigate to the **Fragments** menu and select **New**
2. In the New Fragment dialogue, find and select the **Container** module in the module select menu, and give your Fragment a name (example: Checkout Express). 
3. Click **Ok** to create the fragment.
4. In the module tree, select the 'Default Container' module (showing under the pre-labeled root node as the fragment name entered in the step above. (example: 'Checkout express').
5. In the Properties section, update the Header to a heading you want to display for the express checkout section in your site (Example: Express Checkout)
6. Set the following properties for the container module:

   - **Container layout**: "Flow"
   - **Width**:"Fill container"
   - **Children shown**: "Three" (typically in use with other Payment express modules, for example a text box, payment express for PayPal, payment express for Google Pay)
   - **CSS class name**: "msc-express-payment-container" {required, see note below}

   >[!IMPORTANT]

   >The **CSS class name** value must maintain the "msc-express-payment-container" style listed to control the behavior of the composable container during checkout. This includes hiding, collapsing, and actions designed for the Express Checkout section during the checkout flow. Additional styles can be included against the **CSS class name**. If customizing the behavior of the module, cross-check the style controls if using the same module library coded behavior in the Checkout module for Express Checkout behavior. The "msc-express-payment-container" reference works with the default operations shipped with the module library starter kit Checkout module.

7. In the module node tree, select the ellipses (...) on the **Default container** and click **add module**.
8. Choose the **Payment Express** module
9. In the **Payment Express** module properties panel, set or adjust the **Height of the iFrame** in pixels (Example: 60)
10. Add "GooglePay" to the **Supported tender types** field. This field must match what was used as the **Supported Tender Types** string supplied in the connector set up for the channel (as described in the section above **Configure a Commerce online store for Google Pay**)

    > [!NOTE]
    > You can repeat the **Payment Express** addition for other payment methods in this section. Align the **Supported tender types** against the configured additional payment types (example: 'Paypal').

11. You may also choose to add a **Text block** module above or below the **Payment express** modules within the **Default Container** to include instructional or disclosure information. Click on the **Default Container** and add a module. Select the **Text block** module and fill out the **Rich text** field with the desired text. You can select the ellipses (...) on the **Text block** and choose to "Move up" or "Move down" to position the text above or below the payment express modules.
12. Select **Save** to save your changes, and click **Finish editing** to complete editing the fragment.
13. Click **Publish** to publish the fragment for use.

### Set up the checkout page with the payment express fragment

To set up the Payment Express fragment with Google Pay in the Checkout page, follow these steps.

1. In site builder, with your site context set, navigate to the **Pages** menu and select your Checkout page.
2. Click **Edit** to edit the page.
3. In the **Main slot**, select the ellipsis (...), and then select **Add Module.**
4. In the **Add Module** dialogue box, add the **Container** module.
5. Note: If a Container already exists for your site with the **checkout** fragment- to have the Payment Express section  render above the normal checkout container, position it above the existing checkout container within the **Main slot** section. You can move container positions by selecting their ellipsis (...), and choosing the "Move up" or "Move down" options.
5. In the **Container** module properties, it's recommended to use the following property settings:
	- **Container Layout**: Stacked
	- **Width**: Fill container
	- **Children Shown**: Three (this figure depends on the number of intended payment express modules and text block based on the visual arrangement desired)
6. With the **Container** module still selected in the module tree, select the ellipsis (...), and then select **Add Fragment**.
7. In the **Add Fragment** dialogue box, find and select your named created express payment fragment and click **OK.**
8. Click the **Save** button to save your changes.
9. Click on **Finish editing** to complete editing the page, and **Publish** to publish your changes live.

### Set up the cart page with the payment express fragment

To set up the Payment Express fragment with Google Pay in the Cart page, follow these steps.

1. In site builder, with your site context set, navigate to the **Pages** menu and select your Cart page.
2. Click **Edit** to edit the page.
3. Expand the **Main slot** in the tree view and locate the container which includes **Cart** module. The **Cart** module will contain a new specific slot for **Payment Express.**
4. In the **Cart** module, select the **Payment Express** slot and select the ellipsis (...), and then select **Add Module.**
5. In the **Add Module** dialogue box, add the **Payment express** module and click **OK.**
6. With the express fragment still selected, in Properties add "GooglePay" to the **Supported tender types** property. This field must match what was used as the **Supported Tender Types** string supplied in the connector set up for the channel (as described in the section above **Configure a Commerce online store for Google Pay**).
7. Click the **Save** button to save your changes.
8. Click on **Finish editing** to complete editing the page, and **Publish** to publish your changes live.

Users can include up to three supported **Payment Express** modules in the cart **Payment Express** slot (Three available supported payment options).

### Set up Google Pay as an option in the checkout payment section

To set up Google Pay as a normal payment option in the **Payment Method** section of the checkout page, follow the steps below. This is for payment-only, non-express functionality (the checkout form will be filled out by the user and returning from the Google Pay payment page will only ready the checkout for payment by Google Pay- no Google account information will be used to overwrite the filled checkout details).

1. In site builder, if using the Checkout fragment, follow the steps similar to the [payment module](../payment-module.md) article. This assumes a Checkout fragment has been created with included Pickup information, Shipping address, Delivery options, Contact information, Terms and Conditions (optional), and a section for Checkout elements. The module library checkout module ships with the **Checkout section container** having a text block for user notice instructions, the loyalty points, gift card, and payment modules. 
2. While in **Edit** mode in the Checkout fragment, select the **Checkout section container** and click **Add module**.
3. Choose the **Payment** module from the Select modules dialogue and click **OK**.
4. You can name this module for site builder user clarity by selecting the pencil in the Properties window next to the module's name reference, renaming the module (example: "Google Pay"), and selecting the check mark to save this update. The module will now appear in the tree view with this friendly name for future reference.
5. Change the value of the **Height of the iFrame** in the module properties panel to meet your desired design height in pixels (example: "75"). 
6. Under **Supported tender types**, enter "GooglePay" to match the headquarters configuration for the Google Pay connector.
7. Leave **Is primary payment** blank (this is typically checked for the Adyen checkout module).
8. The **Payment style override** isn't supported for the Google Pay configuration.
9. Select the **Use connector id**. This property must be selected when using multiple payment connectors on the page (example: Adyen main, PayPal).
10. Position the module where desired with other payment modules by selecting the ellipsis ("**...**") next to the module in the module tree outline, and selecting either **Move up** or **Move down**.
11. Select **Save** to save your changes.
12. Click on **Finish editing** to complete editing the page, and **Publish** to publish your changes live.

### Modes of delivery

With the Payment Express module using Google Pay, the first delivery option returned against the shipping address selected from the Google Pay account will be pre-selected. Users will have a chance to click **change** and adjust the shipping address to a different option if desired. 

The order of the delivery methods is configured in HQ on the Channel's **Modes of delivery** section. Additional information on setting up modes of delivery can be found in the [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery) article. The checkout module will also use the **delivery options module** when rendering modes of delivery during checkout. See additional details in the [delivery options module](../delivery-options-module.md) article.

Modes of delivery are displayed as added to the list in the Online Store. In Headquarters, navigate to **Retail and Commerce > Channels > online stores** and select the channel ID for your store. Under the **Setup** menu section, select **Modes of delivery**. The module modes of delivery will be displayed on the site similarly to the configuration shown. Use the **Manage modes of delivery** action item to add or remove modes of delivery for a Retail Channel or a Product.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)
