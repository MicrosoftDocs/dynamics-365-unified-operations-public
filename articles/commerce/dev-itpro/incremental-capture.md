---
# required metadata

title: Incremental payment capture  
description: This topic describes support for capturing multiple credit card payments with a single authorization
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
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Incremental capture for order invoicing

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes out of box support for incremental capture as part of order invoicing. When incremental capture is enabled, orders that are fulfilled over time with multiple invoices will reference the original authorization for multiple invoices and captured payments. This is opposed to legacy support for fulfilling orders with multile invoices, which causes a new authorization to be obtained every time a portion of the order is fulfilled and the balance due changes.

Incremental capture is supported out of box with the Dynamics 365 Payment Connector for Adyen when orders are fulfilled from the POS and back office. Enabling incremental capture for the Adyen connector is described in this topic.

This topic also describes how incremental capture can be added to third party payment connectors using the payments software development kit (SDK).

## Overview

Many merchants fulfill orders in multiple shipments. By default, the out-of-box process for handling credit card payments for orders that are fulfilled over multiple shipments is to capture payments as those shipments are invoiced and then get a new payment authorization for the balance due for the remaining items that must be shipped. This process ensures that payment capture can be consistently supported across payment processors. However, it also has some downsides. Specifically, when an authorization is partially captured, and then a new authorization is created for the balance due, the old authorization and new authorization might overlap. In this case, open authorizations that exceed the order total might appear against customer payment cards. Consequently, authorizations might exceed open balances that are available for credit cards, or card issuers might block cards from being processed because of suspicion of fraud.

To address these issues, incremental capture support has been introduced for the Adyen connector and payments SDK. If a processor supports incremental capture, payment connectors can be updated to capture against a single authorization multiple times over the course of order fulfillment. The following illustration shows the difference between the different payment capture frameworks when multiple captures are done against a single authorization.

![Current payment capture framework vs. incremental capture](../dev-itpro/media/INC_DIFF.png)

Incremental capture support for back-office invoicing(that is, any invoicing that occurs as part of order fulfillment in the back office) was first added to the payments SDK in Commerce version 10.0.13. In 10.0.18, incremental capture support through the SDK has been extended to channels outside of the back office. For the Storefront, Modern POS, and Call Center this means that authorizations created for new orders can be marked as **SupportsMultipleCaptures**. When those orders are later invoiced in the back-office or Modern POS, payments can be captured and the original authorization will be retained and referenced when payments are captured for subsequent invoices. 

## Enabling on incremental capture

### Prerequisite features

The following features are must be enabled prior to enabling incremental capture. 

| Feature name | Description |
|---|---|---|
| Unified payment posting journal defaults for Commerce | This feature changes the way that business logic creates customer payment and customer refund payment journals for orders that are created through the call center, POS, or e-commerce channel. |
| Omni-channel payments | This feature enables omni-channel payment scenarios, such as buy online, pick up in store. For more information, see [Omni-channel payments overview](https://docs.microsoft.com/dynamics365/commerce/omni-channel-payments). |  
| Duplicate payment protection on invoicing | This feature enables duplicate payment protection for invoicing scenarios. Commerce payments functionality might affect customizations in invoicing scenarios. If your organization has invoicing customizations, make sure that they are refactored before you turn on Commerce payments functionality in production environments. | 
| Enable refunds over multiple captures | This functionality improves that capability to do multiple linked refunds against an order. |
| Enable manual void of expired credit card payment lines when authorizations are expired | This feature adds support for manual deletion of payment lines if they expire and the authorization cannot be refreshed. |
| Omni-channel Commerce order payments. | This feature rationalizes payments across channels and enables editing of payments for Storefront and point of sale orders within the Call Center. Previously listed features are prerequisites for this feature, so it should be enabled last. For more information about this feature visit the (Omni-channel Commerce order payments)[https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/commerce-payments] docs article. |

### Enable **Extensiblity to support incremental credit card capture

In the **Feature management** workspace, select the **All** filter to show all available features, and then search for **Extensibility to support incremental credit card capture**. Select the feature, and then select **Enable now**. This feature was originally introduced for incremental capture for back-office invoicing through the payments SDK and has been augmented to also enable incremental capture support through the Adyen connector and all channels.  

## Enabling incremental capture for the Adyen connector

Aside from enabling the feature **Extensibility to support incremental credit card capture**, the property **Enable Request Protection** must also be set to **True** in the Adyen connector merchant properties for every channel where the connector is used. If this field is set to **False** or left blank, incremental capture will not be enabled for the Adyen connector. When this property is set to **True** a tracking ID is added to requests to the payment provider to prevent duplicate requests. Tracking ID support for thrid party payment connectors is explained in a later section of this topic.

Some payment methods do not support incremental capture. Those payment methods can be configured in the **Non incremental capture payment methods** field of the Adyen connector merchant properties. The values set in this field should match the **Payment Method Varian/Card type** string used by Adyen to identify card types in authorization responses. Those strings can be found in Adyen on the **PaymentMethodVariant** wiki page of Adyen's developer resources page. If there are mulitple card types that should be exempt from incremental capture, they should be separated by semicolons. 

One example of payment method variants that does not support incremental capture- at the time of the publication of this article- is Interac. In the Adyen documentation, the string listed for this PMV in authorization responses is *"interac"*. If payment services are being configured for a Canadian merchant that accepts Interac, this payment method variant should be added to the list of **Non incremental capture payment methods**.  

Merchants enabling incremental capture for the Adyen connector should also contact Adyen to ensure that the **Incremental capture** flag is enabled for their merchant account. If this flag is not enabled at the merchant account level, the capture logic at the time of invoicing will fall back to legacy supported flows. 

## Uptake incremental capture for 3rd party payment connectors

To uptake support for incremental capture as part of back-office invoicing for 3rd party payment connectors, and to support incremental capture across all channels, you must upgrade to the payments SDK that is provided in Commerce version 10.0.18.

### IPaymentReferenceProvider

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

### Support for multiple captures

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

## Using incremental capture

The user experience for incremental capture is no different from the user experience when incremental capture is not enabled. The key difference is that when incremental capture is enabled, if the original authorization is still valid, a new authorization will not be obtained after an order is partially invoiced. Instead, the existing authorization will be retained and used for subsequent payment captures. 

For users investigating payment issues in the back office or in their processor's portal, incremental capture orders will appear as having a single authorization with multiple payment captures mapped to it. As opposed to legacy flows where authorizations and captures would have a 1:1 ratio. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
