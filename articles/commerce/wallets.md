---
# required metadata

title: Dynamics 365 Payment Connector for PayPal
description: Wallet payment method support
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

# Wallet payment support

[!include [banner](../includes/banner.md)]

This topic provides an overview of wallet payment support for Microsoft Dynamics 365 Commerce.  

## Key terms

| Term | Description |
|---|---|
| Wallet | A payment type which does not include traditional payment characteristics, such as the BIN range that is used to differentiate among credit and debit card types. |
| Processor payment method | A new property payment card property in the payments SDK. When this property is added to supported payment methods within a connnector, those payment methods can be maped to cards or wallets configured in the Dynamics 365 back office and avoid the traditional BIN range mapping. 

## Overview

Unlike traditional credit and debit cards, wallet payment authorization responses to not include BIN ranges. Traditionally, BIN ranges have been used to match payment authorization responses to predefined card types with BIN ranges. This feature adds support for **Processor payment methods** and mapping of those variants to card types set up in the back office.

**Processor payment method** is a new property for the payments SDK that can be applied to payment methods supported for a particular payment connector. When an authorization response is received that includes the processor payment method, a lookup will be performed to determine if that procesor payment method has been mapped to a card or wallet type. If a mapping is found, that payment will be mapped to the matching card or wallet type. If a match cannot be found, a BIN lookup will be performed following the traditional bin range settings for Commerce. 

Because wallet payments don't include BIN range, if a payment connector supports wallet payments, such as PayPal, the payment connector should be updated to the latest payments SDK and the processor payment method property should be populated at least for all supported wallet payments. 

Processor payment method mappings are also useful for traditional debit and credit card payments. Mapping processor payment methods to cards is much more straight forward than BIN range mapping and less prone to errors because it is easy to ensure all possible payment methods supported by a connector are mapped to a card or wallet type. 

## Wallet payment method support and processor payment methods

This feature introduces support for a new payment method and card type called **Wallet**. The primary characteristic of a wallet payment is that it does not have a BIN range, but wallet payment methods may also not return expiration dates and some properties that have traditionally been considered mandatory. Wallet payment methods must be mapped to processor payment methods as an alternative to the traditional BIN range mapping. 

### Adding support of processor payment methods

To support processor payment methods, payment connectors need to populate the PaymentMethodVariant property in PaymentCardProperties. If the payments SDK in use does not include this property, it should be updated. 

### Processor payment method mapping

This feature adds a new form called **Processor payment method mapping** which can be used to map processor payment methods to configured card or wallet types. When this form is launched, it queries available payment connectors to collect a set or payment methods with the PaymentMethodVariant field populated. It then checks to determin if those payment methods have an existing mapping to a card or wallet. Payment methods that do not have a mapping are listed in the center column of the form. 




## Mapping cards and wallets to processor payment methods



## Availability

The Microsoft Dynamics 365 Payment Connector for PayPal is not available in China. For other locales where Dynamics 365 Commerce is available, there are currently no restrictions. 

## Functional overview

The following capabilities are supported out of box by the PayPal Connector. 

### PayPal Checkout in Storefront 

The connector supports the use of the PayPal Checkout, or PayPal button, for e-commerce payments. When the connector is configured for the web Storefront, at the time of checkout customers will be presented with the option to pay using the PayPal button. When the customer selects the PayPal button, they will be redirected to a PayPal Checkout mini browser window where they will be authenticated by PayPal and be able to select their method of payment. Upon succesful authentication and selection of a payment method, the customer will be redirected back to the storefront with the PayPal payment loaded into the checkout form. Once the order is placed, the PayPal payment will be included as a payment line on the order and it will by synchronized to the Commerce back office.

For more information on PayPal Checkout, please visit the [PayPal Checkout page](https://www.paypal.com/merchantapps/appcenter/acceptpayments/checkout) hosted by PayPal. 

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
12. Note your **Sandbox account**, **Client ID**, and **Secret**. These will be used to set up the connector in Dynamics 365 Commerce.

## Setup the connector in Dynamics 365

> [!NOTE]
> Some of these steps leverage a new capability called **Processor payment methods**. For more information on this feature, visit the docs article for [**Processor payment methods**](


1. Navigate to 



Setup details will vary by payment connector. For setup details related to the out-of-box Adyen connector, see the [e-Commerce section](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce) of the Adyen connector topic. 

## Functional experience

When a customer is redirected for SCA, they will be presented with a challenge by their bank, typically within a new browser window or iFrame. After they have been authenticated, they will be redirected back to the checkout session. If the validation fails, they will not be allowed to continue with checkout. 

## Additional resources

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3)
- [Checkout module](https://docs.microsoft.com/dynamics365/commerce/add-checkout-module)
