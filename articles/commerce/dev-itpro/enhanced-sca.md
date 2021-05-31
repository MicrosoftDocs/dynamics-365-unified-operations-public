---
# required metadata

title: Enhanced payments in Storefront Checkout
description: This topic provides an overview of enhanced Strong Customer Authentication support for Storefront checkout
author: rubendel
manager: annbe
ms.date: 4/29/2021
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
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 
ms.dyn365.ops.version: AX 7.0.1

---

# Enhanced payments in Storefront Checkout

[!include [banner](../includes/banner.md)]

This topic provides an overview of enhanced Strong Customer Authentication support in Storefront Checkout

## Key terms

| Term | Description |
|---|---|
| SCA | Strong Customer Authentication refers to a capability that allows a purchaser's identity to be verified by their bank when an online purchase is attempted. This is typically perfomred via a redirect from the checkout to a page hosted by the cardholder's bank where their identity is verified. Once validated, the purchaser is directed back to the storefront where the order proceeds through checkout. |
| Redirect | A web page used to verify that the person making the purchase is the cardholder associated with the card being used to make the purchase.
| Card token | An alias that is used to refer to a real card number. Card tokens allow a reference to an actual card to be saved while avoiding the security issues associated with saving real card numbers. | 

## Overview

Traditionally, the Storefront checkout process made two distinct calls to the payment processor. The first call was used to tokenize the card number entered in the payment processor's iFrame embedded in the checkout. During this first call, SCA was also enabled so, if needed, the cardholder could be authenticated with the card's issuing bank. The second call used the card token obtained from the first call to request the actual authorization response. 

This two-step method of acquiring payment authorizations was not ideal in all cases. First, not all payment processors support a zero amount authorization request, which was used in the first call to request the payment token. Second, because SCA was performed during the first call, the liability shift granted by SCA was only evident in the tokenization request- not on the actual authorization request. 

Aside from technical issues, it the traditional method also caused confusion for merchants when they were reviewing payment processing activity and seeing many zero amount requests. 

To address the above issues, payments in the Storefront checkout have been refactored to only require a single request. This single request perfomrs all necessary functions related to payment processing including:

- Obtaining a card token where supported in case the authorization becomes expired and a new authorization is required for fulfillment. 
- Support for SCA during the actual authorization request so liability shift is evident on the authoriation for the amount due.

## Key changes from the previous flow

### No "Review order" step

Once the payments flow is initiated, there is no step to review and submit the order. When payment details are entered, the user will only have the option to "Place order". If the payment method provided requires SCA, the users will be redirected to the bank's authentication page. Once authentication is completed, they will be redirected back to the checkout page and the order will be processed. 

The above flow is also applicable to payment method which redirect by default such as PayPal. Once payment details have been provided to PayPal, the redirect back to the checkout will initiate placement of the order. 

With the traditional flow, after the payment details had been entered in the iFrame there was a "Save and continue" button available which would add the tokenized payment to the checkout. In demo environments there may have also been a step to collect the shopper's email or have them agree to terms of use. With the new flow, the validation that was previously perfomed by the final "Save and continue" button is now included in the "Place order" button. So, the new flow saves a click for the customer and eliminates a page load for the checkout flow. 

## Payment connector support

The out of box payment connectors for Adyen and PayPal support the enhanced payment flows in checkout by default. One key thing to note is that only **V002** of the Adyen connector will truly support enhanced SCA. **V001** will still work when the checkout is configured for enhanced SCA, but behind the scenes that version of the connector will still make two calls. 

> [!NOTE]
> **V001** of the Adyen connector should no longer be used due to SCA requirements that went into enforcement in the EU on January 1, 2021. For information about configuring the Adyen connector to use **V002** visit the [Adyen connector docs page](adyen-connector?tabs=8-1-3#set-up-a-processor-for-new-credit-cards).

## Enabling enhanced payments in Storefront checkout

To enable this feature, open the Storefront Starter Kit, select the site you want to edit, expand **Site settings** and then click **Extensions**. Scroll down to **Cart and checkout**, then check the box next to **Enable single payment authorization checkout**. 

![Enabling](../media/rfac.png)

Once the change has been made, click **Save and publish**. 



## Additional resources

- [Payments FAQ](dev-itpro/payments-retail.md)
- [Dynamics 365 Payment Connector for PayPal](paypal.md)
- [Dynamics 365 Payment Connector for Adyen](adyen-connector.md)
- [Adyen redirect](adyen_redirect.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
