---
# required metadata

title: Dynamics 365 Payment Connector for PayPal
description: This topic provides an overview of the Microsoft Dynamics 365 Payment Connector for PayPal.
author: BrianShook
ms.date: 05/18/2021
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
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: AX 7.0.1

---

# Dynamics 365 Payment Connector for PayPal

[!include [banner](../includes/banner.md)]

This topic provides an overview of the Microsoft Dynamics 365 Payment Connector for PayPal (PayPal connector). It includes a list of supported features and functionality, a guide to setting up and configuring the connector, troubleshooting information, and descriptions of some common issues.

## Key terms

| Term | Description |
|---|---|
| PayPal Wallet | Also known as the PayPal "button", PayPal Wallet describes the customer experience and integration supported by the PayPal Connector. |
| Wallet | A payment type that does not include traditional payment characteristics, such as the BIN range and expiration date, which are used to differentiate among credit and debit card types. |

Microsoft Dynamics 365 Commerce offers an out-of-box integration for PayPal Wallet. When the PayPal Connector is configured, the PayPal button is a selectable payment method as part of online order checkout. When users select **PayPal**, they are directed to complete their payment directly with PayPal and then are returned to the online storefront for order completion.  

The PayPal Connector is implemented using the same payments SDK that is leveraged for credit card payments. To better support PayPal payments, support for non-credit card payments has also been enhanced with the addition of support for "wallet" payment types. Specifically, PayPal payments do not return a BIN range. To support PayPal and other wallet payments, a new mapping for payments has been introduced that does not include BIN range. This new mapping can also be used to augment existing BIN range mapping for credit card payment methods. For more details, see [Wallet payment support](wallets.md). 

The Microsoft Dynamics 365 Payment Connector for PayPal is not available in China. For other locales where Dynamics 365 Commerce is available, there are currently no restrictions. 

## Functional overview

### PayPal Wallet in storefront 

The connector supports the use of the PayPal Wallet, or PayPal button, for e-commerce payments. When the connector is configured for the online storefront, customers will be presented with the option to pay using the PayPal button at the time of payment. When the customer selects the PayPal button, they will be redirected to a PayPal Wallet mini-browser window where they will be authenticated by PayPal and can select their method of payment. Upon successful authentication and selection of a payment method, the customer will be redirected back to the storefront with the PayPal payment loaded into the checkout form. When the order is placed, the PayPal payment will be included as a payment line on the order, and it will by synchronized to Commerce headquarters.

For more information on PayPal Wallet, visit the [PayPal Checkout page](https://www.paypal.com/merchantapps/appcenter/acceptpayments/checkout) hosted by PayPal. 

### Fulfillment

Orders with PayPal payment lines are fulfilled in the same manner as orders that are paid using a credit card. When an order is created, the PayPal payment is added in an "authorized" state. Upon fulfillment, whether the order is shipped to the customer from a distribution center or picked up in a store, the payment authorization associated with the order is then "captured" using the same payments SDK requests used to capture credit card payments. 

Fulfillment for PayPal orders supports incremental capture. This means that if an order is partially fulfilled and invoiced, a portion of the original authorization will be captured and, rather than getting a new authorization for the remainder, the same original authorization will be referenced when the remainder of the order is fulfilled. 

### Authorization expiration

Orders made using the PayPal Payment Connector should be fulfilled within 30 days. If an order cannot be fulfilled or invoiced within 30 days, the original authorization will expire. The PayPal Connector does not currently support billing agreements. Recurring billing agreements, similar to recurring card references/tokens are required to automatically generate new authorizations after original authorization expiration. This means that if an authorization expires, the order will fall into a "do not process" state and the customer must be contacted to arrange for an alternate form of payment. 

Billing agreement support, which allows for creation of new authorizations upon expiration of the original authorization, will be added in a future release. 

## Testing the PayPal Payment Connector

### Creating a PayPal developer account

To test the PayPal Payment Connector, you must first create PayPal developer credentials and a PayPal sandbox environment. 

1. Go to the [Test and go live](https://developer.paypal.com/docs/business/test-and-go-live/) page provided as part of PayPal's development resources. 
2. Select [Get Started](https://developer.paypal.com/docs/platforms/get-started/) on the **Test and go live** page. 
3. On that page, select **Log in to the Developer Dashboard**.
4. If prompted to sign in, select **Sign up**.
5. Select **Business Account**, then select **Next**.
6. Provide the email address you want to associate with your PayPal account and create a password for your PayPal account. 
7. On the next page, enter contact information details, then read the PayPal user agreement and Privacy statement. If you agree to the terms, select **Agree and Create Account**.  

    > [!NOTE]
    > The terms agreed to for the creation of a PayPal developer account are between the organization or individual creating the account and PayPal. Microsoft is in no way liable and makes no warranty as to the terms specified the agreement. These instructions are for informational purposes only. 

8. After you agree to the terms, specify your business type, and select **Continue**.
9. Next, go to the [PayPal Developer page](https://developer.paypal.com/developer/applications) and select **Log in to Dashboard**.
10. Sign in using the credentials used when creating your PayPal account.
11. In the developer dashboard, select the **Default Application** in the list of RestAPI apps.
12. Note the **Client ID** and **Secret** for your Sandbox account. These will be used to set up the connector in Dynamics 365 Commerce.

    > [!NOTE]
    > To collect **Client ID** and **Secret** for a live environment, select the **Live** tab for the selected RestAPI app.

## Set up the connector in Dynamics 365 Commerce

### Map the PayPal wallet payment method to a processor payment method

> [!NOTE]
> Some of these steps leverage a new capability for supporting wallet payment methods. For more information on this feature, see [Wallet payment support](wallets.md).

1. Go to **Retail and Commerce \> Channel Setup \> Payment methods \> Payment methods**.
2. Select **New**.
3. Specify a **Payment method ID** and **Payment method name**, such as **Wallet**. Set the **Default function** to **Wallet**, and then select **Save**.
4. Go to **Retail and Commerce \> Channel Setup \> Payment methods \> Card types**.
5. Select **New**.
6. Specify an **ID**, such as **PayPal**. Set an **Electronic payment name**, such as **PayPal**. Set **Type** to **Wallet**, and then specify a name for the **Issuer**, such as **PayPal**. Select **Save**.
7. Select the entry previously created and select **Processor mapping**.
8. On the **Processor payment method mapping** page, select the previously created **PayPal** card type. In the middle column, select the **Dynamics 365 Payment Connector for PayPal** and select **Add**. 

> [!NOTE]
> The **Processor payment method mapping** capability adds a new table that must be synchronized to the channel database. To add this data to the Commerce scheduler, you need to initialize the Commerce scheduler. For details, please refer to documentation related to [updating commerce scheduler configurations](./dev-itpro/cdx-best-practices.md#update-configurations). 

### Set up the PayPal Payment Connector in payment services

Follow these steps to configure the PayPal payment connector in **Payment Services**.

1. In Commerce headquarters, go to **Accounts receivable \> Payments setup \> Payment services**.
2. On the Action Pane, select **New**, and then on the **Setup** tab, enter the following information.

    | Field | Description | Sample value |
    |---|---|---|
    | Payment service | Enter the name of the payment service to configure. | PayPal |
    | Payment connector | Select the PayPal Payment Connector. | Dynamics 365 Payment Connector for PayPal |
    | Test mode | For the PayPal Connector, in production and test environments you should set this field to **False**. | False |
    | Default processor for credit cards | This should be set to **No** because the call center uses the default processor. | No |
    | Bypass payment processor for zero transactions | Specify whether this payment processor should be skipped for transactions that have a 0 (zero) amount. | Yes |

3. On the **Payment service account** tab, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Auto-populated name of the assembly for the Dynamics 365 Payment Connector for PayPal. | Yes | Yes | *Binary name* |
    | Service account ID | Auto-populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes should use (such as invoicing). | Yes | Yes | *Guid* |
    | Merchant client ID | Enter the Sandbox **Client ID** collected from the PayPal developer dashboard under **Default application**.  | Yes | Yes | *String* |
    | Merchant API key | Enter the Sandbox **Secret** collected from the PayPal developer dashboard under **Default application**. | Yes | Yes | *String* |
    | Supported currencies | Enter the supported currencies, semicolon separated, to be supported for the PayPal connector. The default is **USD**. | Yes | Yes, but can be edited. | USD; CAD |
    | Supported tender types | Other payment connectors may support multiple tender types. For PayPal, the only payment method will be **PayPal**. | Yes | Yes | PayPal |
    | Supported payment method variants | Other payment connectors may return multiple payment method variants. For PayPal, the only variant will be **PayPal**. | Yes | Yes | PayPal |
    | Environment | This field is used to specify whether transactions should be sent to Sandbox or Live environments. | Yes | Yes | *Sandbox* or *Live* |
    
> [!NOTE]
> When testing payments in a Sandbox environment, the **Environment** field should never be set to live and live environment. **Merchant client ID** and **Merchant API keys** must never be used. Sandbox environments are for Sandbox testing only.

### Set up the PayPal Payment Connector for the online store

1. In Commerce headquarters, go to **Retail and Commerce \> Channels \> Online stores**.
2. Select the online store to add the Dynamics 365 Payment Connector for PayPal.
3. On the **Online store** page, on the **Payment accounts** FastTab, select **Add**.
4. In **Connectors**, select **Dynamics 365 Payment Connector for PayPal**.
5. Enter the following additional information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Auto-populated name of the assembly for the Dynamics 365 Payment Connector for PayPal. | Yes | Yes | *Binary name* |
    | Service account ID | Auto-populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes should use (such as invoicing). | Yes | Yes | *Guid* |
    | Merchant client ID | Enter the Sandbox **Client ID** collected from the PayPal developer dashboard under **Default application**.  | Yes | Yes | *String* |
    | Merchant API key | Enter the Sandbox **Secret** collected from the PayPal developer dashboard under **Default application**. | Yes | Yes | *String* |
    | Supported currencies | Enter the supported currencies, semicolon separated, to be supported for the PayPal connector. The default is **USD**. | Yes | Yes, but can be edited. | USD; CAD |
    | Supported tender types | Other payment connectors may support multiple tender types. For PayPal, the only payment method will be **PayPal**. | Yes | Yes | PayPal |
    | Supported payment method variants | Other payment connectors may return multiple payment method variants. For PayPal, the only variant will be **PayPal**. | Yes | Yes | PayPal |
    | Environment | This field is used to specify whether transactions should be sent to Sandbox or Live environments. | Yes | Yes | *Sandbox* or *Live* |

### Set up the PayPal payment method for the online store

To set up the PayPal payment method for the online store, follow these steps.

1. In the online store where the PayPal Payment Connector has been configured, on the **Setup** tab, select **Payment methods**.
1. Select **New** to add a payment method.
1. In the **Payment method** field, select the PayPal payment method that you created earlier. 
1. In the **Operation name** field, select **Pay card**.
1. In the **Connector name** field, select **Dynamics 365 Payment Connector for PayPal**.
1. On the **Posting** FastTab, specify the posting details.
1. Select **Electronic payment setup**, select **New**, and then, in the **ID** field, select the card type that you previously created for PayPal. 
1. Select **Save**, and then close the **Electronic payment types** and **Online stores** pages. 

> [!NOTE]
> When testing payments in a Sandbox environment, the **Environment** field should never be set to live and live environment. **Merchant client ID** and **Merchant API key**s must never be used. Sandbox environments are for Sandbox testing only.

After the above changes have been made in Commerce headquarters, synchronize the changes using the **1070** distribution schedule.

### Configure PayPal for the Storefront checkout module

For details related to configuring storefront to use PayPal in the checkout module, see [Payment module](payment-module.md).  

## Entering a merchant relationship with PayPal

To create a **Live** merchant account with PayPal, visit the [PayPal Checkout page](https://www.paypal.com/merchantapps/appcenter/acceptpayments/checkout) for self-service or [connect with a sales representative](https://www.paypal.com/business/contact-sales) to discuss custom rates. 
 

## Additional resources

- [Payments FAQ](dev-itpro/payments-retail.md)
- [Checkout module](add-checkout-module.md)
- [Payment module](payment-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
