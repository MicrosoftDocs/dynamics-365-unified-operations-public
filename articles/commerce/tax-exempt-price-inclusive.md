---
# required metadata

title: Enhancements to calculation of tax exemption
description: This topic describes enhancements to tax exempt calculations in the point of sale and Call Center. 
author: rubendel
manager: Tonya.Fehr
ms.date: 06/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
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

# Enhancements to calculation of tax exemption


[!include [banner](../includes/banner.md)]

This topic describes enhancements to tax exempt calculations in the point of sale and Call Center.

## Key terms

| Term | Description |
|---|---|
| B2B | An abbreviation for "Business to business" used to indicate sales between businesses, as opposed to sales between a retailer and an individual. 
| VAT | Value-added tax which is included in the price of a product. 

## Overview

This topice describes capabilities that have been added to support more robust tax calculation scenarios for cases where customers are tax exempt. 

**Calculate customer tax exempt** was added in 10.0.7 and introduced a new store-level setting to support using store based(non-customer based) tax calculations while also taking into account tax exemptions for specific customer. This scenario is important for retailers who may perform a mix of retail and B2B transactions in the point of sale and need to be able to have business customer exemptions handled in the point of sale automatically. 

**Calculate price inclusive tax exempt** will be added in 10.0.13 and introduces a new store-level setting to support tax inclusive scenarios which include customers for whom the prices should be reduced because their status makes them exempt from paying VAT. For that scenario, the default tax at the point of sale may be overridden to indicate the customer's exempt status with prices subsequently being reduced by the amount of tax that would normally be included. 


## Calculate customer tax exempt

Certain retail verticals, a primary example being liquor stores, sell goods to individuals and other businesses in cash and carry transactions. In many cases, however, transactions involving those different customer segments have different requirements for taxation purchases. When a liquor store sells goods to certain businesses, sales taxes associated with the items being sold may be exempt fof those particular businesses. In all other cases, normal sales tax should apply. 

To support this scenario, a property called **Calculate customer tax exempt** has been added to the settings for the retail store. Then this setting is enabled, typical store-based tax calculations are used. If a named customer is added to the transaction, the point of sale will check the taxes applicable to that customer. If the customer's tax settings have a tax code which is marked as "Exempt", but that tax is applicable for the transasction, that tax will be treated as "Exempt" for the transaction and will not be added to the transaction. 

This setting is applicable for stores in which the price does not include tax and the exemption calculation is also applicable if the **Use destination based tax** setting for the store is also set to "Yes".

### Calculate customer tax exempt setup

Steps provided are specific to testing this capability in demo data scenarios. Setup steps for other data sets will be similar. 

1. Navigate to **Retail and Commerce** > **Channels** > **Stores** > **All stores**.
2. Select the **San Francisco** and view its details by clicking on the **Retail Channel Id** for the store.
3. Clieck **Edit** and 



The List PI capability requires the following elements:

- An e-commerce integration with Microsoft Dynamics 365 Commerce
- A payment connector that is compatible with the List PI capability
- A payment processor that maps unique customer IDs to the payment instruments that the customers want that payment processor to save

For more information about how to implement payment connectors and the software development kit (SDK) in general, visit the [Commerce for IT pros and developers home page](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/dev-retail-home-page#payment-connectors).

## Setup

The List PI capability requires the following components and setup steps:

- **E-commerce integration** – An online storefront integration with Commerce is required. For more information about the e-Commerce SDK, see [e-Commerce platform software development kit (SDK)](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/ecommerce-platform-sdk).
- **Online payments configuration** – The Dynamics 365 Payment Connector for Adyen supports List PI out of the box. For information about how to configure payments for online stores, see [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce). 

    In addition to completing the ecommerce setup steps that are described in that topic, you must set the **Allow saving payment information in e-commerce** option in the Payment accounts fasttab of the **Online store** form to **Yes**. 

- **Omni-channel payments configuration** – In the back office, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. Then, on the **Omni-channel payments** tab, set the **Use omni-channel payments** option to **Yes**. 

## Functional experience

### Guest checkout

When e-commerce visitors choose to check out as guests, customer records aren't created during checkout, and the customers can't save payment instruments for their next visit. 

### Named user checkout

When named users (signed-in customers) go to the payment step of the checkout process, they will experience the List PI capability. The first time that a named user checks out, a **Save for my next payment** check box appears in the section where credit card information is entered. 

![Save for my next payment option](../media/Payments/Save_PI.png)

If this check box is selected, when a new credit card is submitted for payment, the named user's unique customer ID is sent to the payment processor, and the credit card is securely saved and mapped to the that unique customer ID. 

If the same customer signs in during future visits to the storefront, he or she will be able to select the same credit card for payment at checkout. 

![Previously saved payment instrument](../media/Payments/Saved_PI.jpg)

### Order fulfillment and processing

E-Commerce orders where the customer applied a tender line by using the List PI capability work in the same way as orders that were created without using a saved card payment. From the standpoint of order processing and fulfillment, the two types of payment are indistinguishable. 

## Details of eCommerce payment card tokenization

### Standard flow

In e-Commerce integrations, the payment card is typically entered as part of the checkout process and is saved together with the order before finalization. The card details are entered directly on a payment acceptance page that a payment processor provides. After card details are entered and the customer moves on to the next step of the checkout process, the processor creates a token that is used later in the order creation process. 

When the customer finalizes the online order, the payment card token is sent to the payment processor as part of an authorization request. If the payment authorization request is successful, the payment processor replies by sending an authorization token. This authorization token is saved together with the customer's order and is referenced when that order is fulfilled from the back office. 

### List PI flow

The main difference between the standard flow and the List PI flow is that the customer doesn't have to enter the full credit card number. Instead, the customer just has to select a previously saved credit card and provide the Card Verification Value (CVV number). If the customer provides the correct CVV number and moves on to the next step of the checkout process, the payment processor provides a payment card token that will be included in the authorization request. 

## Related articles

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
