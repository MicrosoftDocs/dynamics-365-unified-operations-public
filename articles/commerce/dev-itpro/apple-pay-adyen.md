---
# required metadata

title: Set up Apple Pay with Adyen in Dynamics 365 Commerce
description: This article describes how to set up Apple Pay with Adyen in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 02/22/2024
ms.topic: article
audience: Developer, IT Pro
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
| Apple Pay | Also known as the Apple Pay "button", Apple Pay is a wallet payment offering that's supported through the Adyen connector. It enables the customer experience and integration supported by the Microsoft Dynamics 365 Apple Pay Connector. |
| Wallet | A payment type that doesn't include traditional payment characteristics, such as the Bank Identification Number (BIN) range and expiration date that are used to differentiate credit and debit card types. |

Dynamics 365 Commerce offers an out-of-box integration for Apple Pay when the Adyen payment gateway service is used. Apple Pay is a digital wallet payment method that uses an Apple Pay merchant account in coordination with the Adyen payment service. When configured, the Apple Pay button is a selectable payment method that's part of an online store's order checkout page. The Apple Pay button is presented as a payment option only for supported Apple Pay devices. When users select **Apple Pay** on a supported browser or device, they're directed to the Apple Pay service to complete their payment directly. They're then returned to the online storefront for order completion.

The Dynamics 365 Payment Connector for Apple Pay connector reference is used in addition to the Dynamics 365 Payment Connector for Adyen to enable Apple Pay and credit card payments on a site. Apple Pay can also be configured for use in stores that have Adyen payment terminals that use the Dynamics 365 Payment Connector for Adyen with the Commerce point of sale (POS). In this case, the Dynamics 365 Payment Connector for Adyen handles the Apple Payment device tap through the terminal.

## Prerequisites

An Apple merchant account is required to use Apple Pay with Adyen in Commerce. For information about how to set up Apple Pay in your test customer area, see [Apple Pay Drop-in integration](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#set-up-apple-pay). For information about what to do when you're ready to go live in your production environment, see [Going live](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#going-live).

> [!IMPORTANT]
> If you use the same merchant account to configure Apple Pay that you use for the main Adyen credit card iFrame element, when you configure the **Dynamics 365 Payment Connector for Adyen** connector option, the value of the connector's **Omitted payment methods** field must include the Apple Pay payment method name as it's configured in your Adyen merchant account. Otherwise, the main Adyen credit card iFrame element on the checkout page might try to load the Apple Pay button and fail because of the security criteria of the iFrame element. The **Omitted payment methods** value can include other payment method names that you don't want to be shown. Separate the names with semicolons (for example, `applepay;googlepay`).

The Apple Pay payment method must also be integrated with your Adyen account. Adyen can help you set up the payment method and can also help ensure that the domains for which you use the certificate are assigned for use with the certificate.

To enable the enhanced wallet feature flag in Commerce headquarters, go to **Workspaces \> Feature management**, and search for the **Enhanced wallet support and payment improvements** feature. Select the feature, and then select **Enable**. After the feature is enabled, run the **1110** distribution schedule to make the change available in all channels.

To use Apple Pay, you must also enable the **Enable single payment authorization checkout** property in site builder at **Site \> Site settings \> Extensions \> Cart and checkout**.

## Map the Apple Pay payment method

Apple Pay is a digital wallet payment method. For information about how to set up payment mapping for Apple Pay, see [Wallet payment support](../wallets.md).

To map the Apple Pay payment method in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Payment methods \> Card types**.
1. Select **New** to add a line for Apple Pay, and set the following values:

    - **ID:** ApplePay
    - **Electronic payment name:** Apple Pay
    - **Type:** Wallet
    - **Issuer:** Apple

1. Select **Processor mapping** to open the **Processor payment mapping methods** dialog box. The **Unmapped Processor Payment Methods** column lists the supported payment methods for each available connector (Adyen, PayPal, and Apple).
1. Map the supported payment methods that you want for both the **Dynamics 365 Payment Connector for Adyen** connector (for use at the POS) and the **Dynamics 365 Payment Connector for Apple Pay** connector (for the online channel).
1. For each mapping line, in the **Unmapped Processor Payment Methods** column, select the line to support, and then select **Add** to move the selections to the **Mapped Processor Payment Methods** column.
1. Select **OK**, and then, on the **Card Types** page, select **Save**.

## Set up the Apple Pay certificate for your site

For each site, you must upload the domain association file (also known as the Apple Pay certificate) as described in the [Adyen Apple Pay documentation](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#going-live). You can use Commerce site builder to upload the domain association file to the Media Library for your site.

To set up the Apple Pay certificate in site builder, follow these steps.

1. Download the certificate (domain association file) from [Adyen](https://docs.adyen.com/payment-methods/apple-pay/web-drop-in#going-live).
1. Add the .txt extension to the domain association file.
1. In site builder, [upload](../upload-serve-static-files.md) the domain association file to your site's Media Library.
1. Go to **URLs**.
1. Select **New \> New URL**.
1. In the **New URL** dialog box, select **Media Library asset**.
1. In the **URL path** field, enter the URL path (if it isn't already entered). After the domain base URL, enter the following required Apple string: `<domain>/.well-known/apple-developer-merchantid-domain-association.txt`.
1. Select **Next**. The Media Library shows all uploaded media assets of the **document** (.txt) type.
1. Select the domain association file that should be served for requests to the URL that you defined earlier.
1. Select **Create**.

At this point, the URL that you created is in a draft state. To complete the process, publish the URL. The file that the URL points to isn't returned until you publish the URL.

## Configure a Commerce online store for Apple Pay

To configure a Commerce online store for Apple Pay, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channels \> Online stores**.
1. Select the **Retail Channel ID** value of your site's online store channel.
1. On the **Payment accounts** FastTab, add the **Dynamics 365 Payment Connector for Adyen** connector, if it isn't already set up, by following the instructions in [Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md).
1. After the Adyen connector is configured, select **Add** to add the **Dynamics 365 Payment Connector for Apple Pay** connector.
1. Enter values for the connector merchant properties.

    | Property               | Description | Required | Automatically set | Sample value |
    | ---------------------- | ----------- | -------- | ----------------- | ------------ |
    | Assembly Name          | The name of the assembly for the Dynamics 365 Payment Connector for Apple Pay. | Yes | Yes | Binary name |
    | Service Account ID     | The unique identifier of the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | Guid |
    | Merchant Account ID    | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in [Sign up with Adyen](adyen-connector-setup.md#sign-up-with-adyen). | Yes | No | MerchantIdentifier |
    | Cloud API Key          | Enter the Adyen cloud API key. You can obtain this key by following the instructions in [Generate an API key](https://docs.adyen.com/development-resources/api-credentials#generate-api-key). | Yes | No | abcdefg |
    | Gateway Environment    | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Supported Currencies   | Enter the currencies that the connector should process. In card-present scenarios, Adyen can support additional currencies through [dynamic currency conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. Contact Adyen support to obtain a list of supported currencies. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. | Yes | Yes | ApplePay |

1. After you enter the merchant information, run the **1070** channel configuration distribution schedule job.


#### Add Apple Pay to the store payment method

To add Apple Pay as a new payment method in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Payment methods**.
1. Select **New**.
1. Set the **Default function** option to **Wallet**.
1. Enter a **Payment method** value (the ID for the payment method, usually the next available payment method number in the payment method number series).
1. Enter a **Payment method name** value (for example, **ApplePay**).
1. Set the **Default function** option to **Wallet**.
1. Select **Save**.
1. Go to your channel (**Retail and Commerce \> Channels \> Online stores** or, for POS, **Retail and Commerce \> Channels \> All stores**).
1. On the Action Pane, on the **Set up** tab, in the **Set Up** group, select **Payment methods**.
1. Select **New**.
1. In the **Payment method** field, select the Apple Pay payment method that you set up earlier. The **Payment method name** and **Function** fields should automatically be set by using the payment method values that you configured.
1. On the **General** FastTab, in the **Commerce** section, set the **Operation name** field to **Pay card**.
1. In the **Commerce** section, set the **Connector name** field. For online stores, specify **Dynamics 365 Payment Connector for Apple Pay**. For POS stores, specify **Dynamics 365 Payment Connector for Adyen**.
1. On the **Posting** FastTab, enter any required **Account type** ("Ledger account"), **Difference account**, and **Big difference account** settings.
1. Select **Save**.
1. While the new Apple Pay payment method is selected, on the Action Pane, on the **Electronic payment setup** tab, select **New**.
1. Under **Electronic payment types**, in the **ID** field, select the ApplePay card type.
1. Select **Save**.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**, and run the **1070 Channel configuration** job.

### Configure content security policies in site builder

Before you configure your fragments or pages to use Apple Pay, you must configure the content security policies (CSPs) in site builder for your site.

To configure content security policies in site builder, follow these steps.

1. Go to **Site Settings \> Extensions**.
1. On the **Content security policy** tab, select **Add** to add a line that has `https://applepay.cdn-apple.com/jsapi/v1/apple-pay-sdk.js` to the **child-src**, **connect-src**, **frame-src**, **img-src**, **script-src**, and **style-src** sections.
1. Select **Save and publish** to commit the changes.

### Enable single payment authorization checkout in site builder

To use Apple Pay, you must select the **Enable single payment authorization checkout** property in site builder at **Site \> Site settings \> Extensions \> Cart and checkout**.

### Set up Apple Pay as a checkout payment option

To set up Apple Pay as a checkout payment option on your site's (nonexpress) checkout page, follow these steps.

1. In site builder, go to **Fragments**, and select your site's checkout fragment.
1. Select **Edit**.
1. In the **Checkout section container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Apple Pay** module, and then select **OK**.
1. Select **Save**.
1. Select **Finish editing** to check in the fragment, and then select **Publish** to publish it.

Settings for the **Apple Pay** module are built into the module and connect with the configured Dynamics 365 Payment Connector for Apple Pay connector that's set up for the online channel in Commerce headquarters.

#### Apple Pay payment module style

The Commerce module library includes the Apple Pay module in the sample packaging, and there are references to the Apple Pay module in the default themes included with the Commerce sample sites. If you use Apple Pay and maintain your own theme set, to ensure your theme applies to the Apple Pay module you must include a **checkout-apple-pay.scss** style for your theme.

### Use the payment express module with Apple Pay

The Commerce payment express module works with supporting payment methods to give online shoppers the option to check out faster by using their saved payment service account information during the checkout process. The payment express module references the configured connector button for Apple Pay on the checkout and cart pages.

#### Set up Apple Pay in the checkout page payment express module

To set up Apple Pay in the checkout page payment express module in site builder, follow these steps.

1. Go to **Fragments**.
1. Select the **Checkout** fragment, and then select **Edit**.
1. In the **Checkout express payment container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select **Apple Pay**, and then select **OK**. The Apple Pay express module is preconfigured to use the Dynamics 365 Payment Connector for Adyen that was set up earlier in headquarters.
1. In the Apple Pay module's properties pane, to have the connector return the shipping address from the Apple Pay wallet at checkout, select the **Request shipping address** property.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.

#### Set up Apple Pay in the cart page payment express module

To add Apple Pay to the cart page payment express module in site builder, follow these steps.

1. Go to **Pages**, and then select your site's cart page.
1. Select **Edit**.
1. Under the **Main slot**, find the container that contains the **Cart** module.
1. Under the **Cart** module, select the **Payment express** module.
1. In the **Payment express** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select **Apple Pay**, and then select **OK**. The Apple Pay express module is preconfigured to use the Dynamics 365 Payment Connector for Adyen that was set up earlier in headquarters.
1. In the Apple Pay module's properties pane, to have the connector return the shipping address from the Apple Pay wallet at checkout, select the **Request shipping address** property.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.

### Apple Pay payment behavior

The **Apple Pay** payment button is shown only on supported Apple Pay devices (iPhones, iPads, and Safari browsers that support Apple Pay). If a user isn't using one of these devices, the **Apple Pay** payment button is hidden from view.

When a user selects the **Apple Pay** payment button, an **Apple Pay** dialog box appears. There, the user can authenticate against their Apple Pay device or browser. The **Apple Pay** dialog box shows a summary of the order amount and the payment method that the user configured against their Apple Wallet. The user can review these details and then select **Pay** to complete the payment. After the payment is completed, the user is directed to the **Order Complete** site page that shows a detailed order summary for the completed transaction.

As of Commerce version 10.0.34, Apple Pay express payments are included to enable shoppers to check out directly from the Apple Pay payment window. Shoppers who use supported Apple Pay devices can select the Apple Pay button in the express pay section of the site. The Apple Pay window authenticates the Apple account holder and enables the shopper to select the payment card or method on their Apple Pay account, their contact information (including email address and phone number), their shipping address, and the shipping method. After payment, Apple Pay reauthenticates against the account holder. The order is then placed, and the online shopper is directed to the order completion page, where they can view their order summary. This functionality eliminates the need to manually fill in the checkout form, so that shoppers have a faster checkout experience.

## Configure Commerce POS for Apple Pay

The POS configuration uses the configuration of the hardware profile's **EFT service** field for the Dynamics 365 Payment Connector for Adyen. In Commerce headquarters, configure the EFT service for Dynamics 365 Payment Connector for Adyen as described in [Set up a Dynamics 365 POS hardware profile](adyen-connector-setup.md#set-up-a-dynamics-365-pos-hardware-profile).

Ensure that you add **ApplePay** to the list of tender types in the **Supported Tender Types** field. Use semicolons (;) to separate tender types in the list.

The processor mapping for the Adyen connector captures the wallet card types that are used by Apple Pay at the POS terminal.

## Additional resources

[Payments FAQ](payments-retail.md)

[Checkout module](../add-checkout-module.md)

[Payment module](../payment-module.md)
