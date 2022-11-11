---
# required metadata

title: Set up Apple Pay with Adyen in Dynamics 365 Commerce
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
| Apple Pay | Also known as the Apple Pay "button", Apple Pay is a wallet payment offering supported through the Adyen connector that allows the customer experience and integration supported by the Microsoft Dynamics 365 Apple Pay Connector. |
| Wallet | A payment type that does not include traditional payment characteristics, such as the Bank Identification Number (BIN) range and expiration date, that are used to differentiate among credit and debit card types. |

Dynamics 365 Commerce offers an out-of-the-box integration for Apple Pay when using the Adyen payment gateway service. Apple Pay is a digital wallet payment method that uses an Apple Pay merchant account in coordination with the Adyen payment service. When configured, the Apple Pay button is a selectable payment method that is part of an online store's order checkout page. The Apple Pay button is only presented as a payment option for supported Apple Pay devices. When users select **Apple Pay** from a supported browser or device, they are directed to the Apple Pay service to complete their payment directly, and are then returned to the online storefront for order completion. The Dynamics 365 Payment Connector for Apple Pay connector reference is used in addition to the Dynamics 365 Payment Connector for Adyen to enable Apple Pay and credit card payments on a site. Apple Pay can also be configured to use in stores with Adyen payment terminals that use the Dynamics 365 Payment Connector for Adyen (which handles the Apple Payment device tap through the terminal) with the Commerce point of sale (POS).

## Prerequisites

Using Apple Pay with Adyen in Commerce requires an Apple merchant account. For information regarding setting up Apple Pay in your test customer area, see [Apple Pay Drop-in integration](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#set-up-apple-pay). For information on what to do when you are ready to go live in your production environment, see [Going live](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#going-live).

The Apple Pay payment method must also be integrated with your Adyen account. Adyen can assist both in setting up the payment method and ensuring that the domains you will use the certificate for are assigned for use with the certificate.

To enable the enhanced wallet feature flag in Commerce headquarters, go to **Workspaces \> Feature management** and search for the **Enhanced wallet support and payment improvements** feature. Select the feature, and then select **Enable**. After the feature has been enabled, run the **1110** distribution schedule to make the change available in all channels.

## Map the Apple Pay payment method

Apple Pay is a digital wallet payment method. For information on setting up payment mapping for Apple Pay, see [Wallet payment support](../wallets.md). 

To map the Apple Pay payment method in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup z\> Payment methods \> Card types**. 
1. Select **New** and add a line for Apple Pay with the following values assigned: 
  - **ID** = ApplePay
  - **Electronic payment name** = Apple Pay
  - **Type** = Wallet
  - **Issuer** = Apple
1. Select **Processor mapping** to bring up the **Processor payment mapping methods** dialog box. In the **Unmapped Processor Payment Methods** center column, you'll see supported payment methods listed against each of the connectors available (Adyen, PayPal, Apple). 
1. Map any of the supported payment methods you want against both the **Dynamics 365 Payment Connector for Adyen** (for use at POS) and the **Dynamics 365 Payment Connector for Apple Pay** (for online channel) connectors.  
1. For each mapping line, select the line to support in the **Unmapped Processor Payment Methods** column, and then select **Add** to move the selections to the **Mapped Processor Payment Methods** column.
1. Select **OK**, and then on the **Card Types** page, select **Save**. 

## Set up the Apple Pay certificate for your site

For each site, you will need to upload the domain association file (also known as the Apple Pay certificate) as described in the [Adyen Apple Pay documentation](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#going-live). The domain association file can be uploaded to the Media Library for your site using site builder.

In the base domain for the sites in Site Builder, use :

To set up the Apple Pay certificate in site builder, follow these steps.

1. Download the certificate (domain association file) from [Adyen](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#going-live).
1. Add a .txt  extension to the domain association file.
1. In site builder, [upload](../upload-serve-static-files.md) the domain association file to your site's Media Library. 
1. Go to **URLs**.
1. Select **New \> New URL**.
1. In the **New URL** dialog box, select **Media library asset**.
1. In the **URL path** field, enter the URL path (if not already prepopulated). From the domain base, enter the required Apple pattern: `<domain>/.well-known/apple-developer-merchantid-domain-association.txt`.
1. Select **Next**. The Media Library shows all uploaded media assets of the type **document** (.txt).
1. Select the domain association file that should be served for requests to the URL that you defined in step 5. 
1. Select **Create**. 

At this point, the URL that you created is in a draft state. Publish the URL to complete the process. The file that the URL points to won't be returned until you publish the URL.

## Configure a Commerce online store for Apple Pay

To configure a Commerce online store for Apple Pay, follow these steps.

1. In Commerce headquarters, navigate to the **Retail and Commerce \> Channels \> Online stores**. 
1. Select your site's online store channel's **Retail Channel Id**. 
1. Open the **Payment accounts** FastTab. If it's not already set up, add the **Dynamics 365 Payment Connector for Adyen** according to the instructions in [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md).
1. Once the Adyen Connector is configured, select **Add** to add the **Dynamics 365 Payment Connector for Apple Pay**. 
1. Enter values for the following connector merchant properties:


| Field                  | Description                                                  | Required | Automatically set | Sample value         |
| ---------------------- | ------------------------------------------------------------ | -------- | ----------------- | -------------------- |
| Assembly Name          | Autopopulated name of the assembly for the Dynamics 365 Payment Connector for Apple Pay. | Yes      | Yes               | *Binary name*        |
| Service Account ID     | Autopopulated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes      | Yes               | *Guid*               |
| Merchant Account ID    | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in [Sign up with Adyen](adyen-connector-setup.md#sign-up-with-adyen). | Yes      | No                | *MerchantIdentifier* |
| Cloud API Key          | Enter the Adyen cloud API key. You can obtain this key by following the instructions in [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key). | Yes      | No                | *abcdefg*            |
| Gateway Environment    | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes      | Yes               | *Live*               |
| Supported Currencies   | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to obtain a list of supported currencies. | Yes      | Yes               | *USD;EUR*            |
| Supported Tender Types | Enter the tender types that the connector should process.    | Yes      | Yes               | *ApplePay*           |

6. Once the merchant information has been filled, run the **1070** channel configuration distribution schedule job.

## Configure Commerce POS for Apple Pay

The POS configuration uses the hardware profile's **EFT service** field configuration for the Dynamics 365 Payment Connector for Adyen. In headquarters, configure the EFT service for Dynamics 365 Payment Connector for Adyen as described in [Set up a Dynamics 365 POS hardware profile section](adyen-connector-setup.md#set-up-a-dynamics-365-pos-hardware-profile). 

Ensure that you add "ApplePay" to the list of **Supported Tender Types** (which are separated by semi-colons).

The previous processor mapping maps for the Adyen connector will capture the wallet card types used by Apple Pay at the POS terminal. 

### Configure your content security policies in site builder

Before configuring your fragments or pages to use Apple Pay, you must ensure that your content security policies (CSPs) are configured in Commerce site builder for your site.

To configure your content security policies in site builder, follow these steps.

- Go to **Site Settings \> Extensions**. 
- On the **Content security policy** tab, select **Add**, and then add a line with "https://applepay.cdn-apple.com/jsapi/v1/apple-pay-sdk.js" to the **child-src**, **connect-src**, **frame-src**, **img-src**, **script-src**, and **style-src** sections.
- When done, select **Save and publish** to commit the changes.

### Set up Apple Pay as a checkout payment option

To set up Apple Pay as a payment button in the Checkout (non-express) form, follow these steps:

1. In site builder, with your site context set, navigate to the **Fragments** menu and select the **Checkout** fragment.
2. Click **Edit** to edit the page.
3. Expand the **Checkout \> Checkout information \> Checkout section container** in the tree view and select the ellipsis ("**...**") for the **Checkout section container** and select **Add module**.
4. Select the **Apple Pay** module, and then select **OK**.
5. Review and select **Save** or **Finish editing** to commit the changes to the unpublished edit.
6. When you're ready to commit the changes to the public published version of the checkout fragment, select **Publish**.

Settings for the **Apple Pay** module are built-in to the module and connect back specifically to the configured **Dynamics 365 Payment Connector for Apple Pay** connector set for the online channel in headquarters.

### Apple Pay payment behavior

The **Apple Pay** payment button will only be shown on supported Apple Pay devices (iPhones, iPads, and Safari browsers that support Apple Pay). When not using these devices, the button will be hidden from view as a payment option to the user.

Clicking on the **Apple Pay** payment button will launch an Apple Pay dialogue to allow the user to authenticate against their Apple Pay device or browser, with experience showing a summary of the order amount and which selected payment method the user has configured against their Apple Wallet. Users can review and select the "Pay" button within the Apple Pay dialogue to complete the payment. Once completed, a user will be directed back to the "Order Complete" page on the site showing them their order detailed summary for the completed transaction.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)
  
[Payment module](../payment-module.md)
