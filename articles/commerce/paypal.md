---
# required metadata

title: Dynamics 365 Payment Connector for PayPal
description: This topic provides an overview of the Microsoft Dynamics 365 Payment Connector for PayPal.
author: rubendel
manager: annbe
ms.date: 08/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Dynamics 365 Payment Connector for PayPal

[!include [banner](../includes/banner.md)]

This topic provides an overview of the Microsoft Dynamics 365 Payment Connector for PayPal(PayPal connector). It includes a list of supported features and functionality, a guide to setting up and configuring the connector, troubleshooting information, and descriptions of some common issues.

## Key terms

| Term | Description |
|---|---|
| PayPal Wallet | Also known as the PayPal "button", PayPal Wallet describes customer experience and integration supported by the PayPal Connector. |
| Wallet | A payment type which does not include traditional payment characteristics, such as the BIN range and expiration date, that are used to differentiate among credit and debit card types. |

## Overview

Microsoft Dynamics 365 Commerce now offers an out of box integration for PayPal Wallet. When the PayPal Connector is configured, the PayPal button is a selectable payment method as part of online order checkout. When users select "PayPal" they are directed to complete their payment directly with PayPal and then returned to the web storefront for order completion.  

The PayPal connector is implemented using the same payments SDK that is leveraged for credit card payments. To better support PayPal payments, support for non-credit card payments has also been enhanced with the addition of support for "Wallet" payment types. Specifically, PayPal payments do not return a BIN range. To support PayPal and other wallet payments, a new mapping has been introduced for payments that do not include BIN range. This new mapping can also be used to augment existing BIN range mapping for credit card payment methods. For more details, visit [**Wallet documentation**](articles/commerce/wallets.md). 

## Availability

The Microsoft Dynamics 365 Payment Connector for PayPal is not available in China. For other locales where Dynamics 365 Commerce is available, there are currently no restrictions. 

## Functional overview

### PayPal Wallet in Storefront 

The connector supports the use of the PayPal Wallet, or PayPal button, for e-commerce payments. When the connector is configured for the web Storefront, at the time of 
customers will be presented with the option to pay using the PayPal button. When the customer selects the PayPal button, they will be redirected to a PayPal Wallet mini browser window where they will be authenticated by PayPal and be able to select their method of payment. Upon succesful authentication and selection of a payment method, the customer will be redirected back to the storefront with the PayPal payment loaded into the checkout form. Once the order is placed, the PayPal payment will be included as a payment line on the order and it will by synchronized to the Commerce back office.

For more information on PayPal Wallet, please visit the [PayPal Checkout page](https://www.paypal.com/merchantapps/appcenter/acceptpayments/checkout) hosted by PayPal. 

### Fulfillment

Orders with PayPal payment lines are fulfilled in the same was as orders that are paid using credit card. When an order is created, the PayPal payment is added in an "Authorized" state. Upon fulfillment, whether the order is shipped to the customer from a distribution center, or picked up in a store, the payment authorization associated with the order is then "Captured" using the same payments SDK requests used to capture credit card payments. 

Fulfillment for PayPal orders supports incremental capture. This means that if an order is partially fulfilled and invoiced, a portion of the original authorization will be captured and, rather than getting a new authorization for the remainder, the same original authorization will be referenced when the remainder of the order is fulfilled. 

### Authorization expiration

Orders made using the PayPal connector should be fulfilled within 30 days. If an order cannot be fulfilled or invoiced within 30 days, the original authorization will expire. The PayPal Connector does not currently support billing agreements. Recurring billing agreements, similar to recurring card references/tokens are required to automatically generate new authorizations after original authorization exipry. This means that if an authorization expires, the order will fall into a 'Do not process' state and customer will need to be contacted to arrange for an alternate form of payment. 

Billing agreement support, which allows for creation of new authorizations upon expiration of the original authorization, will be added in a future release. 

## Testing the PayPal connector

### Creating a PayPal developer account

To test the PayPal connector, you must first create PayPal developer credentials and a PayPal sandbox environment. 

1. Navigate to the [**Test and go live**](https://developer.paypal.com/docs/business/test-and-go-live/) page provided as part of PayPal's development resources. 
2. Click the [**Get Started**](https://developer.paypal.com/docs/platforms/get-started/) link on the **Test and go live** page. 
3. From that page, click **Log in to the Developer Dashboard**.
4. If prompted to log in, click **Sign up**.
5. Select **Business Account**, then click **Next**.
6. Provide the email address you want to associate with your PayPal account and create a password for your PayPal account. 
7. In the next form, fill out contact information details, then read the PayPal user agreement and Privacy statement. If you agree to the terms, click **Agree and Create Account**.  

> [!NOTE]
> The terms agreed to for the creation of a PayPal developer account are between the organization or individual creating the account and PayPal. Microsoft is in no way liable  and makes not warranty as to the terms specified the agreement. These instructions are for informational purposes only. 

8. Once you have agreed to the terms, specify your business type and click **Continue**.
9. Next navigate to the [PayPal Developer page](https://developer.paypal.com/developer/applications) and click **Log in to Dashboard**.
10. Log in using the credentials used when creating your PayPal account.
11. In the developer dashboard, select the **Default Application** in the list of RestAPI apps.
12. Note your the **Client ID**, and **Secret** for your Sandbox account. These will be used to set up the connector in Dynamics 365 Commerce.

> [!NOTE]
> To collect **Client ID** and **Secret** for a live environment, click the **Live** tab for the selected RestAPI app.

## Setup the connector in Dynamics 365

### Map the PayPal wallet payment method to a procesor payment method

> [!NOTE]
> Some of these steps leverage a new capabilities for supporting wallet payment methods. For more information on this feature, visit the docs article for [**Wallet support**](articles/commerce/wallets.md).

1. Navigate to **Retail and Commerce \> Channel Setup \> Payment methods \> Payment methods**.
2. Click **New**.
3. Specify a **Payment method ID**, **Payment method name** such as **Wallet**, and set the **Default function** to **Wallet**, then click **Save**.
4. Navigate to **Retail and Commerce \> Channel Setup \> Payment methods \> Card types**.
5. Click **New**.
6. Specify an **ID** such as **PayPal**, an **Electronic payment name** such as **PayPal**, set **Type** to **Wallet** and specify a name for the **Issuer** such as **PayPal**, then click **Save**.
7. Select the entry previously created and click **Processor mapping**.
8. In the **Processor payment method mapping** form, select the previously created **Paypal** card type, then in the middle column select the **Dynamics 365 Payment connetor for PayPal** and click **Add**. 

### Set up the PayPal connector in Payment services

Follow these steps to configure the PayPal payment connector in **Payment Services**.

1. Sign in to Headquarters, and go to **Accounts receivable \> Payments setup \> Payment services**.
2. On the Action Pane, select **New**, and then, on the **Setup** tab, enter the following information.

    | Field | Description | Sample value |
    |---|---|---|
    | Payment service | Enter the name of the payment service to configure. | PayPal |
    | Payment connector | Select the PayPal payment connector. | Dynamics 365 Payment Connector for PayPal |
    | Test mode | For the PayPal connector, in production and test environments you should set this field to **false**. | false |
    | Default processor for credit cards | This should be selt to **No** because the Call Center uses the default processor. | No |
    | Bypass payment processor for zero transactions | Specify whether this payment processor should be skipped for transactions that have a 0 (zero) amount. | Yes |

3. On the **Payment service account** tab, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for PayPal. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Merchant client ID | Enter the Sandbox **Client ID** collected from the PayPal developer dashboard under **Default application**  | Yes | Yes | *String* |
    | Merchant API key | Enter the Sandbox **Secret** collected from the PayPal developer dashboard under **Default application** | Yes | Yes | *String* |
    | Supported currencies | Enter the supported currencies, semicolon separated, to be supported for the PayPal connector. The default is **USD** | Yes | Yes, but can be edited | USD; CAD |
    | Supported tender types | Other payment connnectors may support multiple tender types, for PayPal, the only payment method will be **PayPal**. | Yes | Yes | PayPal |
    | Supported payment method variants | Other payment connnectors may return multiple payment method variants, for PayPal, the only variant will be **PayPal**. | Yes | Yes | PayPal |
    | Environment | This field is used to specify whether transactions should be sent to Sandbox or Live environments | Yes | Yes | *Sandbox* or *Live* |
    
> [!NOTE]
> When testing payments in a Sandbox environment, the **Environment** field should never be set to live and live environment **Merchant client ID** and **Merchant API key**s must never be used. Sandbox environments are for Sandbox testing only.

### Set up the PayPal connector for the online store

1. Sign in to Headquarters, and go to **Retail and Commerce \> Channels \> Online stores**.
2. Select the online store to add the Dynamics 365 Payment Connector for PayPal.
3. On the **Online store** page, on the **Payment accounts** FastTab, select **Add**.
4. In the **Connectors** field, select **Dynamics 365 Payment Connector for PayPal**.
5. Enter the following additional information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|:-:|:-:|---|
    | Assembly Name | Auto populated name of the assembly for the Dynamics 365 Payment Connector for PayPal. | Yes | Yes | *Binary name* |
    | Service account ID | Auto populated unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | *Guid* |
    | Merchant client ID | Enter the Sandbox **Client ID** collected from the PayPal developer dashboard under **Default application**  | Yes | Yes | *Guid* |
    | Merchant API key | Enter the Sandbox **Secret** collected from the PayPal developer dashboard under **Default application** | Yes | Yes | *Guid* |
    | Supported currencies | Enter the supported currencies, semicolon separated, to be supported for the PayPal connector. The default is **USD** | Yes | Yes, but can be edited | USD; CAD |
    | Supported tender types | Other payment connnectors may support multiple tender types, for PayPal, the only payment method will be **PayPal**. | Yes | Yes | PayPal |
    | Supported payment method variants | Other payment connnectors may return multiple payment method variants, for PayPal, the only variant will be **PayPal**. | Yes | Yes | PayPal |
    | Environment | This field is used to specify whether transactions should be sent to Sandbox or Live environments | Yes | Yes | *Sandbox* or *Live* |
    
> [!NOTE]
> When testing payments in a Sandbox environment, the **Environment** field should never be set to live and live environment **Merchant client ID** and **Merchant API key**s must never be used. Sandbox environments are for Sandbox testing only.

Once the above changes have been made in the back office environment, synchronize the changes using the **1070** distribution schedule.

### Configure PayPal for the Storefront checkout module

For details related to configuring Storefront to use PayPal in the checkout module, please visit the [Payment module](https://docs.microsoft.com/en-us/dynamics365/commerce/payment-module) docs article.  

## Entering a merchant relationship with PayPal

To create a **Live** merchant account with PayPal, visit the [PayPal Checkout page](https://www.paypal.com/merchantapps/appcenter/acceptpayments/checkout) for self-service or [connect with a sales representative](https://www.paypal.com/business/contact-sales) to discuss custom rates. 
 

## Additional resources

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Checkout module](https://docs.microsoft.com/dynamics365/commerce/add-checkout-module)
- [Payment module](https://docs.microsoft.com/en-us/dynamics365/commerce/payment-module)
