---
# required metadata

title: Setting up Apple Pay with Adyen in Dynamics 365 Commerce
description: This article describes how to set up Apple Pay with Adyen in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 11/10/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2022-06-20

---

# Set up Apple Pay with Adyen in Dynamics 365 Commerce

[!include [banner](../includes/banner.md)]

This article describes how to set up Apple Pay with Adyen in Microsoft Dynamics 365 Commerce.

## Key terms

| Term | Description |
|---|---|
| Apple Pay | Also known as the Apple Pay "button", Apple Pay is a wallet payment offering supported through the Adyen connector, allowing the customer experience and integration supported by the **Dynamic's 365 Apple Pay Connector**. |
| Wallet | A payment type that does not include traditional payment characteristics, such as the BIN range and expiration date, which are used to differentiate among credit and debit card types. |

Microsoft Dynamics 365 Commerce offers an out-of-box integration for Apple Pay when using the Adyen payment gateway service. Apple Pay is a digital wallet payment method using an Apple Pay merchant account in coordination with the Adyen payment service. When configured, the Apple Pay button is a selectable payment method as part of online store's order checkout. The Apple Pay button will only be presented as a payment option for supported Apple Pay devices. When users select **Apple Pay** from a supported browser or device, they are directed to complete their payment directly with the Apple Pay service and then are returned to the online storefront for order completion. The **Dynamics 365 Payment Connector for Apple Pay** connector reference is used in addition to the **Dynamics 365 Payment Connector for Adyen** to enable Apple Pay and Credit Card payments on a site. Apple Pay can also be configured to use in store with Adyen payment terminals which will utilized the Dynamics 365 Payment Connector for Adyen (which will handle the Apple Payment device tap through the terminal) with the Commerce point-of-sale.

## Prerequisites

Using Apple Pay with Adyen in Commerce requires a Apple merchant account. Please review the [Adyen documentation on Apple Pay]([Apple Pay Drop-in integration | Adyen Docs](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#set-up-apple-pay)) regarding setting up Apple Pay in your test Customer Area. When ready to go live in production, refer to the [Going live](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#going-live) section in the above Adyen article.

The Apple Pay payment method must also be integrated with your Adyen account. Adyen can assist in both setting up the payment method and ensuring the domains you will use the certificate are assigned for use with the certificate.

Enable the enhanced wallet feature flag in Commerce headquarters. Go to **Workspaces > Feature management** and search for the **Enhanced wallet support and payment improvements** feature. Select the feature, and then click **Enable**. After the feature has been enabled, run the **1110** distribution schedule to make the change available in all channels.

## Map the Apple Pay Payment Method

Apple Pay is a digital wallet payment method. For information on setting up payment mapping for Apple Pay, see [Wallet payment support](../wallets.md). 

- In Commerce headquarters, go to **Retail and Commerce > Channel setup > Payment methods > Card types**. 
- Select **New** and add a line for Apple Pay: 
  - ID = ApplePay
  - Electronic payment name = Apple Pay
  - Type = Wallet
  - Issuer = Apple
- Select the **Processor mapping** menu to bring up the Processor payment mapping methods dialogue
- In the **Unmapped Processor Payment Methods** center column, you will see payment methods supported listed against each of the Connectors available (Adyen, PayPal, Apple). 
- Map any of the supported payment methods you wish against both the **Dynamics 365 Payment Connector for Adyen** (for use at POS) and the **Dynamics 365 Payment Connector for Apple Pay** (for online channel) connectors. Select each mapping line to support in the **Unmapped Processor Payment Methods** column and select **Add** to move the selections to the **Mapped Processor Payment Methods** column to map them. 
- Select **OK**, and select **Save** back in the **Card Types** page. 

## Set up the Apple Pay certificate for your site

For each site, you will need to include the obtained domain associated file as described in the [Adyen Apple Pay documentation](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#going-live). This file can be uploaded into the Media Library for your site using Site Builder.

In the base domain for the sites in Site Builder, use the following steps:

1. Go to your site's Media library, and upload the file that should be served by requests to the URL that you will define. Add a .txt extension to the certificate to allow Site Builder to upload as a file type.
2. Go to **URLs** for your site.
3. Select **New > New URL**.
4. In the **New URL** dialog box, select **Media library asset**.
5. In the **URL path** field, enter the URL path (if not pre-populated by SIte Builder already). From the domain base, enter the required Apple pattern: `<domain>/.well-known/apple-developer-merchantid-domain-association.txt`.
6. Select **Next**. The Media library is opened and shows all media assets of the **document** type that have been uploaded.
7. Select the file that should be served for requests to the URL that you defined in step 5. 
8. Select **Create**. 

At this point, the URL that you created is in a draft state. The file that the URL points to won't be returned until you publish the URL. Publish the URL to complete the process.

These steps, along with URL preview prior to validation steps, are utilizing the general [Upload and serve static files](../upload-serve-static-files.md#create-a-site-url-that-returns-a-static-file) instructions for Commerce, provided here as additional reference.

## Configure a Commerce online store for Apple Pay

In Commerce Headquarters, navigate to the **Retail and Commerce > Channels > Online stores** and select your site's online store channel by clicking the channel's **Retail Channel Id**. In the **Set up** menu, drop down the **Payment accounts** section. If not already set up, add the **Dynamics 365 Payment Connector for Adyen** according to the directions described in the [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md) article.

Once the Adyen Connector is configured, click on **Add** to add the **Dynamics 365 Payment Connector for Apple Pay**. Fill in the following merchant properties for the connector:

| Field                  | Description                                                  | Required | Automatically set | Sample value         |
| ---------------------- | ------------------------------------------------------------ | -------- | ----------------- | -------------------- |
| Assembly Name          | Auto populated name of the assembly for the Dynamics 365 Payment Connector for Apple Pay | Yes      | Yes               | *Binary name*        |
| Service account ID     | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes      | Yes               | *Guid*               |
| Merchant account ID    | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](adyen-connector-setup.md#sign-up-with-adyen) section. | Yes      | No                | *MerchantIdentifier* |
| Cloud API Key          | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key) page on the Adyen website. | Yes      | No                | *abcdefg*            |
| Gateway environment    | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes      | Yes               | *Live*               |
| Supported Currencies   | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to get a list of supported currencies. | Yes      | Yes               | *USD;EUR*            |
| Supported Tender Types | Enter the tender types that the connector should process.    | Yes      | Yes               | *ApplePay*           |

Once the merchant information has been filled, run the **1070** Channel configuration distribution schedule.

## Configure Commerce Point-of-Sale for Apple Pay

The Point-of-Sale (POS) configuration will utilize the hardware profile's **EFT service** field configuration for the **Dynamics 365 Payment Connector for Adyen**. In headquarters, configure the EFT service for Dynamics 365 Payment Connector for Adyen as described in the [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md) article's [Set up a Dynamics 365 POS hardware profile section](adyen-connector-setup.md). 

Ensure to add "ApplePay" to the list of **Supported Tender Types** listed (separated by semi-colon).

The previous Card Types > Processor mapping maps for the Adyen connector will capture the wallet card types used by Apple Pay at the POS terminal. 

### Configure your Commerce site builder site for Apple Pay

Before configuring your fragments or pages with Apple Pay, make sure your Content security policy's are set in Commerce site builder for your site. To do this, log in to your Commerce site builder tool:

- Navigate to your site in site builder (choosing the site from the **Home** screen, or selecting the site in the upper right site-picker menu).
- Open **Site Settings** > **Extensions** and go to the **Content security policy** tab.
- Click **Add** and add a line with "https://applepay.cdn-apple.com/jsapi/v1/apple-pay-sdk.js" to the **child-src**, **connect-src**, **frame-src**, **img-src**, **script-src**, and **style-src** sections.

- When completed, click the **Save and publish** button at the top of the page to commit the changes.

### Set up Apple Pay as a Checkout Payment Option

To set up Apple Pay as a payment button in the Checkout (non-express) form, follow these steps:

1. In site builder, with your site context set, navigate to the **Fragments** menu and select the **Checkout** fragment.
2. Click **Edit** to edit the page.
3. Expand the **Checkout>Checkout information>Checkout section container** in the tree view and select the ellipsis (...) for the **Checkout section container** and choose **add module**.
4. Select the **Apple Pay** module and click **OK**
5. Review and click the **Save** or **Finish editing** button to commit the change to the unpublished edit.
6. Click **Publish** when ready to commit the changes to the public published version of the checkout fragment.

Settings for the **Apple Pay** module are built-in to the module and connect back specifically to the configured **Dynamics 365 Payment Connector for Apple Pay** connector set for the online channel in Headquarters. The **Custom CSS class name** can be used to 

### Apple Pay payment behavior

The **Apple Pay** payment button will only be shown on supported Apple Pay devices (iPhones, iPads, and Safari browsers that support Apple Pay). When not using these devices, the button will be hidden from view as a payment option to the user.

Clicking on the **Apple Pay** payment button will launch an Apple Pay dialogue to allow the user to authenticate against their Apple Pay device or browser, with experience showing a summary of the order amount and which selected payment method the user has configured against their Apple Wallet. Users can review and select the "Pay" button within the Apple Pay dialogue to complete the payment. Once completed, a user will be directed back to the "Order Complete" page on the site showing them their order detailed summary for the completed transaction.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)
  
[Payment module](../payment-module.md)
