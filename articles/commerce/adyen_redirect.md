---
# required metadata

title: Strong Customer Authentication (SCA) using the Adyen connector
description: This topic describes Strong Customer Authentication (SCA) in the storefront checkout.
author: rubendel
manager: annbe
ms.date: 05/17/2020
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

# Strong Customer Authentication (SCA) using the Adyen connector


[!include [banner](../includes/banner.md)]

This topic describes Strong Customer Authentication (SCA) support built into the Adyen connector.

## Key terms

| Term | Description |
|---|---|
| Redirect | The action of moving an online shopper's browsing session out of the context of the merchant's storefront. |
| SCA | Stront Customer Authentication. Part of the EU Payment Services Directive 2.0 (PSD2.0) which requires that online shoppers are authenticated outside of their online shopping experience when paying with an electronic payment method. |
| Issuing bank | The financial institution which issues a payment instrument to a customer. |

## Overview

PSD2.0 requires that SCA is supported during online shopping checkout so a customer can be authenticated by the bank that issued their payment method. This commonly occurs when a shopper is going through the checkout for an online order and after they have provided their payment details. Those details are evaluated, and based on a criteria provided by PSD2.0, the customer may be redirected to their bank. Upon being redirected to their bank, the customer is required to provide some form of authentication to confirm that they are an authorized user for the payment instrument submitted for payment during checkout. If the user is confirmed to be the cardholder, they are then redirected back to the storefront where the payment was previously submitted and checkout is allowed to proceed. If SCA fails, they will not be allowed to proceed with the transaction.

## Prerequisites for SCA support

Support for SCA is provided by the out-of-box [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3) and may be implemented by any third-party connector using the payments SDK.

## Setup

Setup details will vary by payment connector. For setup details related to the out-of-box Adyen connector, visit the [e-Commerce section](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce) of the Adyen connector topic. 

## Functional experience

When a customer is redirected for SCA, they will be presented with a challege by their bank, typically within a new browser window or iFrame. Once they have been authenticated, they will be redirected back to the checkout session. If the validation fails, they will not be allowed to continue with checkout. 

## Related articles

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3)
- [Checkout module](https://docs.microsoft.com/en-us/dynamics365/commerce/add-checkout-module)
