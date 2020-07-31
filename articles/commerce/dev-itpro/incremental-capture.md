---
# required metadata

title: Incremental capture for back office invoicing
description: This topic describes payments SDK enhancements to support incremental capture as part of order invoicing.
author: rubendel
manager: annbe
ms.date: 7/31/2020
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

# Support for incremental capture for back office invoicing

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes how the payments SDK supports incremental capture as part of order invoicing. Incremental capture indicates payment processing support for fulfilling an order with multiple invoices. Specifically, as invoices are processed against the order, payment capture requests reference the original payment authorization as opposed to getting a new payment authorization when the balance due changes because of previous payment captures. 

## Overview

Many merchants fulfill orders in multiple shipments. In Commerce versions 10.0.12 and earlier, the out-of box process for dealing with credit card payments for orders that are fulfilled over multiple shipments is to capture payments as those shipments are invoiced, then get a new payment authorization for balance due for remaining items to be shipped. This method is used to ensure that payment capture can be consistently supported across payment processors. The method also comes with some downsides. Specifically, when an authorization is partially captured, and then a new authorization is created for the balance due, the old authorization and new authorization may overlap. When this occurs, customers may see open authorizations against their payment cards which exceed the order total. The result is that authorizations may exceed open balances available for credit cards, or card issuers may block cards from being processed due to suspicion of fraud. 

To address these issues, in Commerce versions 10.0.13 and later, the payments SDK includes incremental capture support for back office payment captures. That way, if a processor supports incremental capture, payment connectors can be updated to capture against a single authorization multiple times over the course of order fulfillment. The following diagram illustrates the difference between the different payment capture frameworks with mulitple captures against a single authorization. 

![Current payment capture framework vs. Incremental capture](../dev-itpro/media/INC_DIFF.png)

In Commerce version 10.0.13, support is provided for incremental capture as part of back office invoicing (any invoicing that occurs as part of order fulfillment in the back office). In a later release, support for incremental capture will be added to the out-of-box Adyen payment connector as captures that occur from the point of sale (POS). 

## Enable incremental capture for back office invoicing

In the **Feature management** workspace, select the **All** filter to list all available features, then search for **Extensibility to support incremental credit card capture**. Select the feature and then select **Enable now**. 

## Uptake incremental capture for back office invoicing

To uptake support for incremental capture as part of back office invoicing, you also must upgrade to the payments SDK provided in Commerce version 10.0.13. 

## IPaymentReferenceProvider

This version of the payment SDK also adds the IPaymentReferenceProvider interface. The IPaymentReferenceProvider interface is an interface that supports using a PaymentTrackingID to each request and response. The PaymentTrackingID can be used to track payment requests and ensure that, between back office invoicing requests and the processor, duplicate requests can be caught before they are resent, thus reducing duplicate payments. 

Sample implementation from the payments SDK SampleConnector.cs:

   ``` xml
            #region ITrackingSupport
            /// <summary>
            /// Get the payment providers reference to safe guard against duplicate requests.
            /// </summary>
            /// <param name="command">The payment opertion that will uses the tracking id.</param>
            /// <param name="amount">The payment transaction amount.</param>
            /// <returns>Returns the PaymentTransactionReferenceData.</returns>
            /// <remarks>List of supported commands can be seen in the constants defined in <see cref="Microsoft.Dynamics.Retail.PaymentSDK.Portable.Constants.SupportedCorrelationCommands"/></remarks>
            public PaymentTransactionReferenceData GetPaymentReferenceData(string command, decimal amount)
            {
                PaymentTransactionReferenceData paymentTransactionReferenceData = new PaymentTransactionReferenceData();
                paymentTransactionReferenceData.Amount = amount;
                paymentTransactionReferenceData.Command = command;
                paymentTransactionReferenceData.IdFromConnector = Guid.NewGuid().ToString();
                paymentTransactionReferenceData.InitiatedDate = DateTime.UtcNow;
                return paymentTransactionReferenceData;
            }
            #endregion
   ```

Sample of AuthorizeRequest.cs in the payments SDK using PaymentTrackingID:

   ``` xml
                authorizeRequest.PaymentTrackingId = PaymentUtilities.GetPropertyStringValue(
                    hashtable,
                    GenericNamespace.TransactionData,
                    TransactionDataProperties.PaymentTrackingId);
   ``` 

## Support for mulitple captures

If a payment processor supports mutiple captures, authorization responses from the connector should have the SupportsMultipleCaptures property set to **True**. If the property is set to **False** or not provided, the authorization won't be eligible for incremental capture, and if there's a new balance due after invoicing, a new authorization will be obtained. 

Sample from AuthorizationResponseProperties.cs from the payments:

   ``` xml
     /// <summary>
            /// Gets the SupportsMultipleCaptures property.
            /// </summary>
            public static string SupportsMultipleCaptures
            {
                get { return "SupportsMultipleCaptures"; }
            }
   ``` 

As the back office invoicing processes captures against authorizations that are enabled for multiple capture, the total captured amount is tracked. Capture requests continue to reference the original authorization until it is fully captured.

Authorizations that are expired according to Accounts Receivable parameters aren't eligible for incremental capture. 

The "supports multiple captures" property isn't global, but per authorization. An environment may have connectors that support incremental capture and those that don't.  

