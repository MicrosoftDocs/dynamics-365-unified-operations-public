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
| Processor payment method | A new property payment card property in the payments SDK. When this property is added to supported payment methods within a connector, those payment methods can be mapped to cards or wallets configured in the Dynamics 365 back office and avoid the traditional BIN range mapping. 

## Overview

Unlike traditional credit and debit cards, wallet payment authorization responses to not include BIN ranges. Traditionally, BIN ranges have been used to match payment authorization responses to predefined card types with BIN ranges. This feature adds support for **Processor payment methods** and mapping of those variants to card types set up in the back office.

**Processor payment method** is a new property for the payments SDK that can be applied to payment methods supported for a particular payment connector. When an authorization response is received that includes the processor payment method, a lookup will be performed to determine if that processor payment method has been mapped to a card or wallet type. If a mapping is found, that payment will be mapped to the matching card or wallet type. If a match cannot be found, a BIN lookup will be performed following the traditional bin range settings for Commerce. 

Because wallet payments don't include BIN range, if a payment connector supports wallet payments, such as PayPal, the payment connector should be updated to the latest payments SDK and the processor payment method property should be populated at least for all supported wallet payments. 

Processor payment method mappings are also useful for traditional debit and credit card payments. Mapping processor payment methods to cards is much more straight forward than BIN range mapping and less prone to errors because it is easy to ensure all possible payment methods supported by a connector are mapped to a card or wallet type. 

## Wallet payment method support and processor payment methods

This feature introduces support for a new payment method and card type called **Wallet**. The primary characteristic of a wallet payment is that it does not have a BIN range, but wallet payment methods may also not return expiration dates and some properties that have traditionally been considered mandatory. Wallet payment methods must be mapped to processor payment methods as an alternative to the traditional BIN range mapping. 

### Adding support of processor payment methods

To support processor payment methods, payment connectors need to populate the PaymentMethodVariant property in PaymentCardProperties. If the payments SDK in use does not include this property, it should be updated. 

### Processor payment method mapping

This feature adds a new form called **Processor payment method mapping** which can be used to map processor payment methods to configured card or wallet types. This form is accessed via a new link in the **Card types** form.

![Procesor payment mapping link](../media/Payments/ProcPmtMap.png)

When this form is launched, it queries available payment connectors to collect a set or payment methods with the PaymentMethodVariant field populated. It then checks to determine if those payment methods have an existing mapping to a card or wallet. Payment methods that do not have a mapping are listed in the center column of the form. 

![Unmapped processor payment method](../media/Payments/Unmapped.png)

To map a processor payment method to a card or wallet, first select the card or wallet, then select the processor payment method and click **Add**. This will move the processor payment method to the **Mapped** column and the next time a matching payment authorization is received, it will be mapped to the chosen card or wallet.

![Mapped processor payment method](../media/Payments/Mapped.png)

### When not to use processor payment method mapping

In certain cases, processor payment method mapping may not be granular enough for reporting needs. For example, some retailers differentiate different external gift cards from the same provider by their BIN range. In cases such as that, the gift cards should not be mapped using the above form. Instead, they should continue to use traditional BIN range mapping. 

## Support for unidentified card types

In certain cases, a payment connector may return a card that does not have a BIN range or processor payment method mapping. When that happens, the payment is authorized by the payment terminal, but is then reversed when the point of sale cannot map the authorization response to a specific card type. To address this issue, a capability is provided to specify map unknown authorization responses to a default card type. 

![Default for unmapped cards](../media/Payments/DefaultUnMapped.png)

This ensures that the payment is never authorized by the terminal and then reversed by the POS, thus avoiding confusion for customers and store associates. When this setting is used, the default card for unknown authorizations should be checked periodically to ensure that wanted card types are not accidentally being mapped to the default for unknown card types. If a card type is truly unwanted for processing, it should be disabled at the processor level. 

## Additional resources

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 Payment Connector for PayPal](paypal.md)
