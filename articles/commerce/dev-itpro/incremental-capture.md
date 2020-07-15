---
# required metadata

title: Support for incremental capture for back office invoicing
description: This topic describes payments SDK enhancements to support incremental capture as part of order invoicing
author: rubendel
manager: Tonya.Fehr
ms.date: 7/14/2020
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

This topic describes payments SDK enhancements to support incremental capture as part of order invoicing.

## Availability

This feature is available starting with the 10.0.13 monthly update.

## Key terms

| Term | Description |
|---|---|
| Incremental capture | Incremental capture indicates payment processing support for fulfilling an order with multiple invoices. Specifically, as invoices are processed against that order payment capture requests reference the original payment authorization, as opposed to getting a new payment authorization when the balance due changes because of previous payment captures. |

## Overview

Many merchants fulfill orders not in a single shipment, but in multiple shipments. The current out of box for dealing with credit card payments for orders that are fulfilled over multiple shipments is to capture payments as those shipments are invoiced, then get a new payment authorization for balance due for remaining items to be shipped. This method is used to ensure that payment capture can be consistently supported across payment processors. This method also comes with some downsides. Specifically, when an authorization is partially captured, then a new authorization is created for the balance due, the old authorization and new authorization may overlap. When this occurs, customers may see open authorizations against their payment cards which exceed the order total. The result is that authorizations may exceed open balances available for credit cards or card issuers may block cards from being processed due to suspicion of fraud. 

To address these issues, incremental capture support is being added to the payments SDK for back office payment captures. This means that, if a processor supports incremental capture, payment connectors can be updated to capture against a single authorization multiple times over the course of order fulfillment. The following diagram illustrates the difference between the currently supported payment capture framework and the newly supported incremental capture framework with mulitple captures against a single authorization. 

![Current payment capture framework vs. Incremental capture](../dev-itpro/media/INC_DIFF.png)

The first part of adding support for incremental capture is to add support for incremental capture as part of back office invoicing, meaning any invoicing happening as part of order fulfillment in the back office. In a future release, incremental capture support will also be added to the out of box Adyen payment connector as captures that occur from the point of sale. 

## Enable the incremental capture for back office invoicing feature

In the back office, search for **Feature management**. In the feature management workspace, click the **All** filter to list all available features, then search for **Extensibility to support incremental credit card capture**. Select the feature and click **Enable now**. 

## Uptake incremental capture for back office invoicing

To uptake support for incremental capture as part of back office invoicing, you will also need to upgrade to the payments SDK provided as part of 10.0.13. 

This version of the payment SDK adds the IPaymentReferenceProvider interface. The IPaymentReferenceProvider interface is an optional interface that supports using a PaymentTrackingID to each request and response. The PaymentTrackingID can be used to track payment requests and ensure that, between back office invoicing requests and the processor, duplicate requests can be caught before they are resent, thus reducing duplicate payments. 

    ``` xml
namespace Microsoft.Dynamics.Retail.PaymentSDK.Portable
{
    using Microsoft.Dynamics.Retail.PaymentSDK.Portable.Constants;
    /// <summary>
    /// IPaymentReferenceProvider interface.
    /// </summary>
    public interface IPaymentReferenceProvider
    {
        /// <summary>
        /// Get the payment providers reference to safe guard against duplicate requests.
        /// </summary>
        /// <param name="command">The payment opertion that will uses the tracking id.</param>
        /// <param name="amount">The payment transaction amount.</param>
        /// <returns>Returns the PaymentTransactionReferenceData.</returns>
        /// <remarks>List of supported commands can be seen in the constants defined in <see cref="Microsoft.Dynamics.Retail.PaymentSDK.Portable.Constants.SupportedCorrelationCommands"/></remarks>
        PaymentTransactionReferenceData GetPaymentReferenceData(string command, decimal amount);
    }
}
    ```

