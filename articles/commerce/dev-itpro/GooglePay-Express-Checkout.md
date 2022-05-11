---
# required metadata

title: Setting up Google Pay with Adyen in Dynamics 365 Commerce
description: This topic provides an overview of the Microsoft Dynamics 365 Payment support for Google Pay with Adyen, including connector setup and using express checkout module for faster checkout capabilities.
author: BrianShook
ms.date: 03/15/2022
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

# Setting up Google Pay with Adyen in Dynamics 365 Commerce
This topic provides an overview of the Microsoft Dynamics 365 payments support for PayPal Cart Checkout capability. It reviews additions of Payment Express modules for faster checkout capabilities, and setup of PayPal Cart Checkout with a Commerce site page.

## Key terms
| Term | Description |
|---|---|
| Google Pay | Also known as the Google Pay "button", Google Pay is a wallet payment offering supported through the Adyen connector, allowing the customer experience and integration supported by the Dynamic's Google Pay Connector. |
| Wallet | A payment type that does not include traditional payment characteristics, such as the BIN range and expiration date, which are used to differentiate among credit and debit card types. |
|Payment Express |Added module in Dynamics 365 Commerce to support faster checkout behavior with supported payment methods, with this article addressing PayPal|

Microsoft Dynamics 365 Commerce offers an out-of-box integration for Google Pay when using the Adyen payment gateway service. Google Pay is a digital wallet payment method using a Google Pay merchant account in coordination with the Adyen payment service. When configured, the Google Pay button is a selectable payment method as part of online order checkout. When users select **Google Pay** from a supported browser or device, they are directed to complete their payment directly with the Google Pay service and then are returned to the online storefront for order completion. Using Google Pay with the express checkout module in Commerce, users can utilize their payment account information to pre-fill the checkout form and get through the checkout process faster. Commerce includes a Payment Express module to allow for express checkout behavior. The Payment Express module can be used in a Fragment and included in the checkout or cart page. The **Dynamics 365 Payment Connector for Google Pay** connector reference is used in addition to the **Dynamics 365 Payment Connector for Adyen** to enable both the Payment Express or regular checkout options when PayPal is configured. Google Pay can also be configured to use in store with Adyen payment terminals and the Commerce point-of-sale.

## Prerequisites
Using Google Pay with Adyen in Commerce requires a Google merchant account. Please review the [Adyen documentation on Google Pay](https://docs.adyen.com/payment-methods/google-pay/), and Google's [Integration checklist](https://developers.google.com/pay/api/web/guides/test-and-deploy/integration-checklist) to set up your Google Merchant account.

The Google Pay payment method must also be integrated with your Adyen account. Follow the integration link instructions on the [Adyen Google Pay](https://www.adyen.com/payment-methods/google-pay) site.

Enable the enhanced wallet feature flag in Commerce headquarters. Go to **Workspaces > Feature management** and search for the **Enhanced wallet support and payment improvements** feature. Select the feature, and then click **Enable**. After the feature has been enabled, run the **1110** distribution schedule to make the change available in all channels.


## Map the Google Pay Payment Method
Google Pay is a digital wallet payment method. Set up payment mapping for Google Pay as described in the [Wallet payment support](https://docs.microsoft.com/en-us/dynamics365/commerce/wallets) article. 

- In Commerce headquarters, go to **Retail and Commerce > Channel setup > Payment methods > Card types**. 
- Select **New** and add a line for GooglePay: 
  - ID = GooglePay
  - Electronic payment name = Google Pay
  - Type = Wallet
  - Issuer = Google
- Select the **Processor mapping** menu to bring up the Processor payment mapping methods dialogue
- In the **Unmapped Processor Payment Methods** center column, you will see payment methods supported listed against each of the Connectors available (Adyen, PayPal, Google). 
- Map any of the supported payment methods you wish against both the **Dynamics 365 Payment Connector for Adyen** (for use at POS) and the **Dynamics 365 Payment Connector for Google Pay** (for online channel) connectors. Select each mapping line to support in the **Unmapped Processor Payment Methods** column and select **Add** to move the selections to the **Mapped Processor Payment Methods** column to map them. 
- Select **OK**, and select **Save** back in the **Card Types** page. 

## Configure a Commerce online store for Google Pay
In Commerce Headquarters, navigate to the **Retail and Commerce > Channels > Online stores** and select your site's online store channel by clicking the channel's **Retail Channel Id**. In the **Set up** menu, drop down the **Payment accounts** section. If not already set up, add the **Dynamics 365 Payment Connector for Adyen** according to the directions described in the [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md) article.

Once the Adyen Connector is configured, click on **Add** to add the **Dynamics 365 Payment Connector for GooglePay**. Fill in the following merchant properties for the connector:

| Field                                  | Description                                                  | Required | Automatically set | Sample value         |
| -------------------------------------- | ------------------------------------------------------------ | -------- | ----------------- | -------------------- |
| Assembly Name                          | Auto populated name of the assembly for the Dynamics 365 Payment Connector for GooglePay | Yes      | Yes               | *Binary name*        |
| Service account ID                     | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes      | Yes               | *Guid*               |
| Google merchant ID (Optional for test) | Required for **Production** environments and optional for test environments, the Google Merchant ID assigned to your Google Merchant account.  (See https://pay.google.com/ for additional details). | Yes      | No                | *numeric Identifier* |
| Merchant account ID                    | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector-setup#sign-up-with-adyen) section. | Yes      | No                | *MerchantIdentifier* |
| Cloud API Key                          | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key) page on the Adyen website. | Yes      | No                | *abcdefg*            |
| Gateway environment                    | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes      | Yes               | *Live*               |
| Supported Currencies                   | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes      | Yes               | *USD;EUR*            |
| Supported Tender Types                 | Enter the tender types that the connector should process.    | Yes      | Yes               | *GooglePay*          |

Once the merchant information has been filled, run the **1070** Channel configuration distribution schedule.



## Configure Commerce Point-of-Sale for Google Pay
The Point-of-Sale (POS) configuration will utilize the hardware profile's **EFT service** field configuration for the **Dynamics 365 Payment Connector for Adyen**. In headquarters, configure the EFT service for Dynamics 365 Payment Connector for Adyen as described in the [Set up Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector-setup) article's [Set up a Dynamics 365 POS hardware profile section](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector-setup). 

Ensure to add "GooglePay" to the list of **Supported Tender Types** listed (separated by semi-colon).

The previous Card Types > Processor mapping maps for the Adyen connector will capture the wallet card types used by Google Pay at the POS terminal. 



### Using the Payment Express module with Google Pay
The **Payment Express** module works with supporting payment methods to offer site customers the option to checkout faster using their payment service account information in the checkout process. The module references the configured connector button and returns the user selected order details (addresses, contact information, and paying against the underlying payment method selected) to pre-populate the checkout form.

With Google Pay, selecting the Google Pay button in the Payment Express section will launch the Google Pay payment iFrame window. A user will log in to their Google account and can use their account shipping address, billing address, email, and Google Pay payment method of choice to pay for the transaction.

As the user completes the action in the Google Pay iFrame, they are directed to the Commerce site checkout page with the checkout form pre-populated with their chosen details. Note upon return of the user from Google Pay to the checkout page:

- In the Payment Express flow, the first **Delivery Option** available for the shipping address returned will be pre-selected for the customer.  
- With Google Pay, a contact **email address** is not returned. Guest checkout users will still need to input an email address in the contact section of the checkout page. Signed-in users will have the data populated from their Dynamics customer account (their primary email used for authentication).

The customer has the option to review the order, change checkout order details if desired, and will then select the **Place order** button to finalize the order.


### Configure your Commerce site builder site for Google Pay
Before configuring your fragments or pages with Google Pay, make sure your Content security policy's are set in Commerce site builder for your site. To do this, log in to your Commerce site builder tool:

- Navigate to your site in site builder (choosing the site from the **Home** screen, or selecting the site in the upper right site-picker menu).

- Open **Site Settings** > **Extensions** and go to the **Content security policy** tab.

- Click **Add** and add a line with "*.google.com" to the **child-src**, **connect-src**, **frame-ancestors**, **frame-src**, **img-src**, **script-src**, and **style-src** sections.

- When completed, click the **Save and publish** button at the top of the page to commit the changes.

  
### Set up the Payment Express fragment with Google Pay in site builder
To set up the Payment Express fragment with Google Pay for the online store, follow these steps:

1. In site builder, select the site and navigate to the **Fragments** menu and select **New**

2. In the New Fragment dialogue, find and select the **Container** module in the module select menu, and give your Fragment a name (example: Checkout Express). 

3. Click **Ok** to create the fragment.

4. In the module tree, select the 'Default Container' module (showing under the pre-labeled root node named per the fragment name given in the step above. (example: 'Checkout express').

5. In the Properties section, update the Header to a heading you want to display for the express checkout section in your site (Example: Express Checkout)

6. Set the following properties for the container module:

   - **Container layout**: "Flow"
   - **Width**:"Fill container"
   - **Children shown**: "Three"
   - **CSS class name**: "msc-express-payment-container" {required, see note below}

   >[!IMPORTANT]

   >The **CSS class name** value must maintain the "msc-express-payment-container" style listed to control the behavior of the composable container during checkout. This includes hiding, collapsing, and actions designed for the Express Checkout section during the checkout flow. Additional styles can be included against the **CSS class name**. If customizing the behavior of the module, cross-check the style controls if using the same module library coded behavior in the Checkout module for Express Checkout behavior.

7. In the module node tree, select the ellipses (...) on the **Default container** and click **add module**.

8. Choose the **Payment Express** module

9. In the **Payment Express** module properties panel, set or adjust the **Height of the iFrame** in pixels (Example: 60)

10. Add "GooglePay" to the **Supported tender types** field. This field must match what was used as the **Supported Tender Types** string supplied in the connector set up for the channel (as described in the section above **Configure a Commerce online store for Google Pay**)

> [!Note]
> You can repeat the **Payment Express** addition for other payment methods in this section. Align the **Supported tender types** against the configured additional payment types (example: 'Paypal').

11. You may also choose to add a **Text block** module above or below the **Payment express** modules within the **Default Container** to include instructional or disclosure information. Click on the **Default Container** and add a module. Select the **Text block** module and fill out the **Rich text** field with the desired text. You can select the ellipses (...) on the **Text block** and choose to "Move up" or "Move down" to position the text above or below the payment express modules.
12. Select **Save** to save your changes, and click **Finish editing** to complete editing the fragment.
13. Click **Publish** to publish the fragment for use.


### Set up the Checkout page with the Payment Express fragment
To set up the Payment Express fragment with Google Pay in the Checkout page, follow these steps.

1. In site builder, with your site context set, navigate to the **Pages** menu and select your Checkout page.
2. Click **Edit** to edit the page.
3. In the **Main slot**, select the ellipsis (...), and then select **Add Module.**
4. In the **Add Module** dialogue box, add the **Container** module.
5. Note: If a Container already exists for your site with the **checkout** fragment- to have the Payment Express section  render above the normal checkout container, position it above the existing checkout container within the **Main slot** section. You can move container positions by selecting their ellipsis (...), and choosing the "Move up" or "Move down" options.
5. In the **Container** module properties, it is recommended to use the following property settings:
	- **Container Layout**: Stacked
	- **Width**: Fill container
	- **Children Shown**: Three
6. With the **Container** module still selected in the module tree, select the ellipsis (...), and then select **Add Fragment**.
7. In the **Add Fragment** dialogue box, find and select your named created express payment fragment and click **OK.**
8. Click the **Save** button to save your changes.
9. Click on **Finish editing** to complete editing the page, and **Publish** to publish your changes live.


### Set up the Cart page with the Payment Express fragment
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


### Set up Google Pay as an option in the Checkout payment section
To set up Google Pay as a normal payment option in the **Payment Method** section of the checkout page, follow the steps below. This is for payment-only, non-express functionality (the checkout form will be filled out by the user and returning from the Google Pay payment page will only ready the checkout for payment by Google Pay- no Google account information will be used to overwrite the filled checkout details).

1. In site builder, if using the Checkout fragment, follow the steps similar to the [payment module](https://docs.microsoft.com/en-us/dynamics365/commerce/payment-module) article. This assumes a Checkout fragment has been created with included Pickup information, Shipping address, Delivery options, Contact information, Terms and Conditions (optional), and a section for Checkout elements. The store starter kit checkout module ships with the **Checkout section container** having a Text block for user notice instructions, the Loyalty points, Gift Card, and payment modules. 
2. While in **Edit** mode in the Checkout fragment, select the **Checkout section container** and click **Add module**.
3. Choose the **Payment** module from the Select modules dialogue and click **OK**.
4. You can name this module for site builder user clarity by selecting the pencil in the Properties window next to the module's name reference, renaming the module (example: "Google Pay"), and selecting the check mark to save this update. The module will now appear in the tree view with this friendly name for future reference.
5. Change the value of the **Height of the iFrame** in the module properties panel to meet your desired design height in pixels (example: "75"). 
6. Under **Supported tender types**, enter "GooglePay" to match the headquarters configuration for the Google Pay connector.
7. Leave **Is primary payment** blank (this is typically checked for the Adyen checkout module).
8. The **Payment style override** is not supported for the Google Pay configuration.
9. Select the **Use connector id**. This property must be selected when using multiple payment connectors on the page (example: Adyen main, PayPal).
10. Position the module where desired with other payment modules by selecting the elipsis (...) next to the module in the module tree outline, and selecting either **Move up** or **Move down**.
11. Select **Save** to save your changes.
12. Click on **Finish editing** to complete editing the page, and **Publish** to publish your changes live.


### Modes of Delivery
With the Payment Express module using Google Pay, the first delivery option returned against the shipping address selected from the Google Pay account will be pre-selected. Users will have a chance to click **change** and adjust the shipping address to a different option if desired. 

The order of the delivery methods is configured in HQ on the Channel's **Modes of delivery** section. Additional information on setting up modes of delivery can be found in the [Set up modes of delivery](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery) article. The checkout module will also use the **delivery options module** when rendering modes of delivery during checkout. See additional details in the [delivery options module](delivery-options-module.md) article.

Modes of delivery are displayed as added to the list in the Online Store. In Headquarters, navigate to **Retail and Commerce > Channels > online stores** and select the channel ID for your store. Under the **Setup** menu section, select **Modes of delivery**. The module modes of delivery will be displayed on the site similarly to the configuration shown. Use the **Manage modes of delivery** action item to add or remove modes of delivery for a Retail Channel or a Product.


## Additional resources
- [Payments FAQ](dev-itpro/payments-retail.md)
- [Checkout module](add-checkout-module.md)
- [Payment module](payment-module.md)
