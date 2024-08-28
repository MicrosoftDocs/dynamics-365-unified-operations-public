---
title: Strong Customer Authentication (SCA) using the Adyen connector
description: This article describes Strong Customer Authentication (SCA) in the storefront checkout.
author: BrianShook
ms.date: 07/30/2024
ms.topic: how-to
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-01-01
ms.custom: 
  - bap-template
---

# Strong Customer Authentication (SCA) using the Adyen connector


[!include [banner](../../finance/includes/banner.md)]

This article describes Strong Customer Authentication (SCA) support built into the Adyen connector.

## Key terms

| Term | Description |
|---|---|
| Redirect | The action of moving an online shopper's browsing session out of the context of the merchant's storefront. |
| SCA | Strong Customer Authentication. Part of the EU Payment Services Directive 2.0 (PSD2.0) that requires online shoppers to be authenticated outside of their online shopping experience when paying with an electronic payment method. |
| Issuing bank | The financial institution that issues a payment instrument to a customer. |

## Overview

PSD2.0 requires that SCA is supported during online shopping checkout so a customer can be authenticated by the bank that issued their payment method. The authentication commonly occurs when a shopper is going through the checkout for an online order and after they provide their payment details. Those details are evaluated, and based on criteria provided by PSD2.0, the customer may be redirected to their bank. After being redirected to their bank, the customer is required to provide some form of authentication to confirm that they're an authorized user for the payment instrument. If the user is confirmed to be the cardholder, they're redirected back to the storefront where the payment was submitted, after which checkout is allowed to proceed. If SCA fails, the process isn't allowed to continue for the transaction.

## Prerequisites for SCA support

Support for SCA is provided by the out-of-box [Dynamics 365 Payment Connector for Adyen](adyen-connector.md?tabs=8-1-3). The connector can be implemented by any third-party connector using the payments SDK.

## Setup

Setup details will vary by payment connector. For setup details related to the out-of-box Adyen connector, see [Configure additional information for the Adyen connector](adyen-connector-setup.md#configure-additional-information-for-the-connector). 

## Functional experience

When a customer is redirected for SCA, they're presented with a challenge by their bank, typically within a new browser window or iFrame element. After they're authenticated, they're redirected back to the checkout session. If the validation fails, they aren't allowed to continue with checkout. 

## Additional resources

- [Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 Payment Connector for Adyen](adyen-connector.md?tabs=8-1-3)
- [Checkout module](../add-checkout-module.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
