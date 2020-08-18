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

## Overview

Microsoft Dynamics 365 Commerce now offers an out of box integration for PayPal Checkout. When the PayPal Connector is configured, the PayPal button is as a selectable payment method as part of online order checkout. When users select "PayPal" they are directed to complete their payment directly with PayPal and then returned to the web storefront for order completion.  

## Supported capabilities

The following capabilities are supported out of box by the PayPal Connector. 

### PayPal checkout 

The connector supports the use of the PayPal Checkout, or PayPal button, for e-commerce payments. This 

## Prerequisites for the PayPal connector

### Testing

To test the PayPal connector in a sandbox environment, you must create a PayPal development environment. To create a developmet environment, navigate to the [Get Started](https://developer.paypal.com/docs/platforms/get-started/) page provided as part of PayPal's development resources.

## Setup

Setup details will vary by payment connector. For setup details related to the out-of-box Adyen connector, see the [e-Commerce section](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce) of the Adyen connector topic. 

## Functional experience

When a customer is redirected for SCA, they will be presented with a challenge by their bank, typically within a new browser window or iFrame. After they have been authenticated, they will be redirected back to the checkout session. If the validation fails, they will not be allowed to continue with checkout. 

## Additional resources

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3)
- [Checkout module](https://docs.microsoft.com/dynamics365/commerce/add-checkout-module)
