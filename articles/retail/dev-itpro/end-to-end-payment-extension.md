---
# required metadata

title: Create an end-to-end payment extension
description: 
author: 
manager: AnnBe
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2018-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Payment integration with payment terminal
This topic provides an overview of how to write a payment integration for the Dynamics 365 for Retail Modern POS (MPOS) for a payment terminal that can directly communicate with the payment gateway.

## Key Terms
| Term | Description |
| --- | --- |
| Payment Connector | Extension library written to integrate the Dynamics 365 for Retail Modern POS with a payment terminal. |

## Overview
The diagram below illustrates how a new payment connector that integrates with a payment terminal fits into the Dynamics 365 for Retail stack. Note, the diagram below assumes that a local Hardware Station is used to communicate with the payment terminal. However, the same patterns apply to the shared Hardware Station as well and the article below describes how a new payment connetors can be hooked up in each of the two scenarios.

![test](media/PAYMENTS/PAYMENT-TERMINAL/Overview.jpg)

This article describes in detail the following steps that are required to create an end-to-end payment integration for a payment terminal:
- **Write a payment connector**: The payment connector is the main integration point between the Dynamics 365 for Retail MPOS and the payment terminal. This section describes how to implement a new payment connector that can relay the various payment requests (e.g. authorize, refund, void) to the payment terminal. 
- **Write a payment processor**: The payment processor is used to define the merchant properties used as part of the payment integration. This section describes how to implement a new payment processor, including interfaces to implement and patterns to follow.
- **Configure the payment connector in the Hardware Station config**: This section describes how to configure the new payment connector to be loaded by the Hardware Station (local or shared).
- **Configure the payment connector on the AX Hardware Station profile page**: The Hardware Station profile page in the AX Client is where all payment related configuration properties are set for the end-to-end payment integration to work. This section describes how to configure the payment connector on the Hardware Station page.

## Write a payment connector
The instructions in this section can be found in the `PaymentDeviceSample` class in the Retail SDK.

### High level overview of payment flows 
The following diagram illustrates a high level overview of several payment flows (i.e. Begin Transaction, Update Cart Lines, Authorize, Void, Capture, End Transaction) across the Dynamics 365 for Retail MPOS, Hardware Station, and Payment Connector. 

### Implement payment connector

#### Implement the INamedRequestHandler interface
All MPOS payment related flows go through the hardware station through the request/response pattern, which is used as the extensibility pattern for other channel related components as well. The first step to writing a payment connector is to create a new class that implements the `INamedRequestHandler` interface.

``` csharp
public class PaymentDeviceSample : INamedRequestHandler
{
    private const string PaymentTerminalDevice = "MOCKPAYMENTTERMINAL";

    /// <summary>
    /// Gets the specify the name of the request handler.
    /// </summary>
    public string HandlerName
    {
	      get
        {
            return PaymentDeviceSample.PaymentTerminalDevice;
        }
    }
}
```

The `HandlerName` is used to configure the payment connector used on a given MPOS register through the AX Client UI (desccribed below).

#### Implement payment related request and response
In order to process payment related flows the payment connector has to define the `SupportedRequestTypes` that it can handle. This indicates to the MPOS and Hardware Station what type of requests (i.e. payment flows) this specific payment connector can handle. This becomes particularly important when several distinct connectors are implemented to handle different type of requests. Additionally, the `Execute` method has to be implemented to route each of the requests supported by the connector to a given method. The example below shows the complete list of `SupportedRequestTypes` and an example of a request (i.e. `Authorize`).

``` csharp
public class PaymentDeviceSample : INamedRequestHandler
{
    /// <summary>
    /// Gets the collection of supported request types by this handler.
    /// </summary>
    public IEnumerable<Type> SupportedRequestTypes
    {
        get
        {
            return new[]
            {
                typeof(OpenPaymentTerminalDeviceRequest),
                typeof(BeginTransactionPaymentTerminalDeviceRequest),
                typeof(UpdateLineItemsPaymentTerminalDeviceRequest),
                typeof(CancelOperationPaymentTerminalDeviceRequest),
                typeof(AuthorizePaymentTerminalDeviceRequest),
                typeof(CapturePaymentTerminalDeviceRequest),
                typeof(VoidPaymentTerminalDeviceRequest),
                typeof(RefundPaymentTerminalDeviceRequest),
                typeof(FetchTokenPaymentTerminalDeviceRequest),
                typeof(EndTransactionPaymentTerminalDeviceRequest),
                typeof(ClosePaymentTerminalDeviceRequest),
                typeof(ActivateGiftCardPaymentTerminalRequest),
                typeof(AddBalanceToGiftCardPaymentTerminalRequest),
                typeof(GetGiftCardBalancePaymentTerminalRequest),
                typeof(GetPrivateTenderPaymentTerminalDeviceRequest)
            };
        }
    }
    
        /// <summary>
    /// Executes the payment device simulator operation based on the incoming request type.
    /// </summary>
    /// <param name="request">The payment terminal device simulator request message.</param>
    /// <returns>Returns the payment terminal device simulator response.</returns>
    public Response Execute(Microsoft.Dynamics.Commerce.Runtime.Messages.Request request)
    {
        ThrowIf.Null(request, "request");

        Type requestType = request.GetType();

        if (requestType == typeof(AuthorizePaymentTerminalDeviceRequest))
        {
            return this.AuthorizePayment((AuthorizePaymentTerminalDeviceRequest)request);
        }
        else if (...)
        {
            ...
        }

        return new NullResponse();
    }

    /// <summary>
    /// Authorize payment.
    /// </summary>
    /// <param name="request">The authorize payment request.</param>
    /// <returns>The authorize payment response.</returns>
    public AuthorizePaymentTerminalDeviceResponse AuthorizePayment(AuthorizePaymentTerminalDeviceRequest request)
    {
        ThrowIf.Null(request, "request");

        PaymentInfo paymentInfo = Utilities.WaitAsyncTask(() => this.AuthorizePaymentAsync(request.Amount, request.Currency, request.VoiceAuthorization, request.IsManualEntry, request.ExtensionTransactionProperties));

        return new AuthorizePaymentTerminalDeviceResponse(paymentInfo);
    }
}
```

#### Full list of supported payment requests and responses
The list below describes each of the supported payment related requests and responses.

##### 
