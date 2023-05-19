---
title: Payments FAQ
description: This article answers frequently ask questions about payment options in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 05/18/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Version 1611
ms.custom: 65801
ms.assetid: 99079d81-fde2-4432-8cee-82bbcc3bd57e

---

# Payments FAQ

[!include [banner](../../includes/banner.md)]

This article answers frequently ask questions about payment options in Microsoft Dynamics 365 Commerce.

### What payment scenarios are supported?

- Set up a merchant account.
- Process a call center order.
- Process an online order.
- Process a POS cash-and-carry transaction by using an accepting page.
- Process a POS cash-and-carry return by using an accepting page.
- Process a POS cash-and-carry return by using an accepting page.
- Process a POS customer order by using an accepting page.
- Process a POS cash-and-carry transaction by using Microsoft Dynamics Commerce Retail Hardware Station.
- Process a POS cash-and-carry return by using Hardware Station.
- Process a POS customer order by using Hardware Station.
- Buy online, pick up in store.
- Buy in call center, pick up in store.

### Which payment providers are supported and in what regions?

- Adyen is supported for card present and card not present transactions. For a list of supported regions, visit the [Dynamics 365 Payment Connector for Adyen overview page](/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3).
- PayPal is supported for online purchases. For a list of supported regions, visit the [Dynamics 365 Payment Connector for PayPal overview page](../paypal.md).
- Mastercard Simplify is no longer supported for new customers.

### What is the TestConnector, and how should it be used?

Commerce references a **TestConnector** in the payment connector setup pages for **Payment services**, **Online store payment accounts**, and **Hardware profile EFT service connectors**. The TestConnector mimics a payment gateway return without actually calling out to a gateway (it automatically sends its own approval signal). 

The TestConnector should only be used in test environments for the following limited point of sale (POS) scenarios:

- POS basic credit card test transaction
- POS basic unlinked test refund transaction

The TestConnector isn't supported for online store or call center channels, or for user acceptance testing (UAT) and production (prod) environments.

Many scenarios in Commerce payments require token usage and references that aren't supported by the TestConnector. Microsoft recommends using a payment gateway test account to test scenarios within your sandbox environment to validate test patterns. Using an actual gateway's test environment is the best means to ensure that all scenarios are working as expected during testing. 

### What is a payment connector and in what cases do I need to deploy and implement a payment connector?

Payment connectors are software components that can be set up which enable an application to process payments for transactions where the card is not present and transactions where the card is present.

Microsoft-provided connectors such as Adyen can be used, or custom connectors can be built by ISV partners. A connector is typically built to meet the business needs of a customer. Custom connectors are often created when there is a scenario that requires a new type of payment type (for example, linked refunds). Customers doing business in certain geographies may need new connectors if the out-of-box connectors do not support those regions.

### Are other payment connector providers supported?

Yes, but you must connect them using customization.

### What is the Service level agreement (SLA) for out-of-box payment connectors like Adyen?

For the Adyen connector, refer to the Adyen connector [overview page](/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3) if the issue is related to set up. For other setup or functional issues with the connector itself, create a support request with Microsoft. If the issue is originating from the device itself or Adyen's processing service, contact Adyen support at support-dynamics365@adyen.com.

### If a supported payment provider issues an update, will Microsoft automatically update the payment connector or do I need to work with the payment provider to get the updated payment connector?

If a payment connector update is issued by the payment connector provider, the updated version of the payment connector will be included in the next planned release of Dynamics 365 Commerce. However, the customer can also work directly with the payment connector provider to uptake it earlier.

### Does Dynamics 365 Commerce support "cash out" or "cash back" operations during the checkout process in point of sale (POS)?

No, cash back or cash out operations are not supported in POS during a transaction. However, customizations via extensibility can be achieved using cash return and payment operations that are similar to gift card "cash out" operations. 

## Related articles

- [Create an end-to-end payment integration for a payment terminal](end-to-end-payment-extension.md)
- [Deploy payment connectors](deploy-payment-connector.md)
- [Create Windows installers for payment connectors](create-windows-installer-payment-connector.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
