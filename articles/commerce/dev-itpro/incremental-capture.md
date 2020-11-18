---
# required metadata

title: Incremental capture for back-office invoicing
description: This topic describes enhancements that have been made to the payments software development kit (SDK) to support incremental capture as part of order invoicing.
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
# ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Incremental capture for back-office invoicing

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes how the payments software development kit (SDK) supports incremental capture as part of order invoicing. In incremental capture, payment processing supports fulfillment of an order that has multiple invoices. Specifically, as invoices are processed against the order, payment capture requests reference the original payment authorization instead of getting a new payment authorization when previous payment captures have caused the balance due to change.

## Overview

Many merchants fulfill orders in multiple shipments. In Microsoft Dynamics 365 Commerce version 10.0.12 and earlier, the out-of-box process for handling credit card payments for orders that are fulfilled over multiple shipments is to capture payments as those shipments are invoiced and then get a new payment authorization for the balance due for the remaining items that must be shipped. This process ensures that payment capture can be consistently supported across payment processors. However, it also has some downsides. Specifically, when an authorization is partially captured, and then a new authorization is created for the balance due, the old authorization and new authorization might overlap. In this case, open authorizations that exceed the order total might appear against customer payment cards. Therefore, authorizations might exceed open balances that are available for credit cards, or card issuers might block cards from being processed because of suspicion of fraud.

To address these issues, the payments SDK in Commerce version 10.0.13 and later includes incremental capture support for back-office payment captures. Therefore, if a processor supports incremental capture, payment connectors can be updated to capture against a single authorization multiple times over the course of order fulfillment. The following illustration shows the difference between the different payment capture frameworks when multiple captures are done against a single authorization.

![Current payment capture framework vs. incremental capture](../dev-itpro/media/INC_DIFF.png)

In Commerce version 10.0.13, incremental capture is supported as part of back-office invoicing (that is, any invoicing that occurs as part of order fulfillment in the back office). In a later release, support for incremental capture from the point of sale (POS) will be added to the out-of-box Adyen payment connector.

## Turn on incremental capture for back-office invoicing

In the **Feature management** workspace, select the **All** filter to show all available features, and then search for **Extensibility to support incremental credit card capture**. Select the feature, and then select **Enable now**.

## Uptake incremental capture for back-office invoicing

To uptake support for incremental capture as part of back-office invoicing, you must upgrade to the payments SDK that is provided in Commerce version 10.0.13.

## IPaymentReferenceProvider

This version of the payment SDK adds the **IPaymentReferenceProvider** interface. This interface supports using a **PaymentTrackingID** value for each request and response. The **PaymentTrackingID** value can be used to track payment requests. It also ensures that, between back-office invoicing requests and the processor, duplicate requests can be caught before they are re-sent. In this way, it helps prevent duplicate payments.

Here is a sample implementation from the SampleConnector.cs file in the payments SDK.

```xml
#region ITrackingSupport
/// <summary>
/// Get the payment provider reference to safeguard against duplicate requests.
/// </summary>
/// <param name="command">The payment operation that will use the tracking ID.</param>
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

The following sample from the AuthorizeRequest.cs file in the payments SDK uses a **PaymentTrackingID** value.

```xml
authorizeRequest.PaymentTrackingId = PaymentUtilities.GetPropertyStringValue(
    hashtable,
    GenericNamespace.TransactionData,
    TransactionDataProperties.PaymentTrackingId);
```

## Support for multiple captures

If a payment processor supports multiple captures, the **SupportsMultipleCaptures** property for authorization responses from the connector should be set to **True**. If the property is set to **False**, or if it isn't provided, the authorization won't be eligible for incremental capture. In this case, if there is a new balance due after invoicing, a new authorization will be obtained. 

Here is a sample from the AuthorizationResponseProperties.cs file in the payments SDK.

```xml
/// <summary>
/// Gets the SupportsMultipleCaptures property.
/// </summary>
public static string SupportsMultipleCaptures
{
    get { return "SupportsMultipleCaptures"; }
}
```

As back-office invoicing processes captures against authorizations that are enabled for multiple capture, the total captured amount is tracked. Capture requests continue to reference the original authorization until it's fully captured.

Authorizations that are expired according to Accounts receivable parameters aren't eligible for incremental capture. 

The **SupportsMultipleCaptures** property isn't global. It's specific to the authorization. An environment might have both connectors that support incremental capture and connectors that don't support it.
