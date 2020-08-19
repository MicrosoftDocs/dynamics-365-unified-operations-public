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

This topic provides an overview of the Microsoft Dynamics 365 Payment Connector for PayPal(PayPal Connector). It includes a comprehensive list of supported features and functionality, a guide to setting up and configuring the connector, troubleshooting information, and descriptions of some common issues.

## Key terms

| Term | Description |
|---|---|
| PayPal Checkout | Also known as the PayPal "button", PayPal Checkout describes customer experience and integration supported by the PayPal Connector. |
| Wallet | A payment type which does not include traditional payment characteristics, such as the BIN range that is used to differentiate among credit and debit card types. |

## Overview

Microsoft Dynamics 365 Commerce now offers an out of box integration for PayPal Checkout. When the PayPal Connector is configured, the PayPal button is as a selectable payment method as part of online order checkout. When users select "PayPal" they are directed to complete their payment directly with PayPal and then returned to the web storefront for order completion.  

The PayPal connector is implemented using the same payments SDK that is leveraged for credit card payments. To better support PayPal payments, support for non-credit card payments has also been enhanced with the addition of support for "Wallet" payment types. Specifically, PayPal payments do not return a BIN range. To support PayPal and other wallet payments, a new mapping has been introduced for payments that do not include BIN range. This new mapping can also be used to augment existing BIN range mapping for credit card payment methods. For more details, visit Processor payment method documentation. 

## Availability

The Microsoft Dynamics 365 Payment Connector for PayPal is not available in China. For other locales where Dynamics 365 Commerce is available, there are currently no restrictions. 

## Supported capabilities

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

## Prerequisites for the PayPal connector

### Testing

To test the PayPal connector in a sandbox environment, you must create a PayPal sandbox environment. To create a sandbox environment:
1. Navigate to the [**Test and go live**](https://developer.paypal.com/docs/business/test-and-go-live/) page provided as part of PayPal's development resources. 
2. Click [**Get Started**](https://developer.paypal.com/docs/platforms/get-started/) link on the **Test and go live** page should be used to create sandbox environment crentials. 
3. From that page, click **Log in to the Developer Dashboard**.
4. If propted to log in, click **Sign up**.
5. Select **Business Account**, then click **Next**.
6. Provide the email address you want to associate with your PayPal account and create a password for your PayPal account. 
7. In the next form, fill out contact information details, then read the PayPal user agreement and Privacy statement. If you agree to the terms, click **Agree and Create Account**.  

> [!NOTE]
> The terms agreed to for the creation of a PayPal developer account are between the organization or individual creating the account and PayPal. Microsoft is in no way liable  and makes not warranty as to the terms specified the agreement. These instructions are for informational purposes only. 

8. Once you have agreed to the terms, specify your business type and click **Continue**.
9. Next navigate to the [PayPal Devloper](https://developer.paypal.com/developer/applications) and click **Log in to Dashboard**.
10. Log in using the credentials used when creating your PayPal account.
11. In the developer dashboard, select the **Default Application** in the list of RestAPI apps.
12. Note your **Sandbox account**, **Client ID**, and **Secret**.

Specify: Merchant Client ID = Client ID
Merchant API key = Secret 
Environment = Live or Sandbox

## Setup

Setup details will vary by payment connector. For setup details related to the out-of-box Adyen connector, see the [e-Commerce section](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce) of the Adyen connector topic. 

## Functional experience

When a customer is redirected for SCA, they will be presented with a challenge by their bank, typically within a new browser window or iFrame. After they have been authenticated, they will be redirected back to the checkout session. If the validation fails, they will not be allowed to continue with checkout. 

## Additional resources

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3)
- [Checkout module](https://docs.microsoft.com/dynamics365/commerce/add-checkout-module)
