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
This topic describes how to write a payment integration for the Dynamics 365 for Retail Modern and Cloud POS (POS) for a payment terminal that can directly communicate with the payment gateway.

## Key Terms
| Term | Description |
| --- | --- |
| Payment Connector | Extension library written to integrate the POS with a payment terminal. |
| Payment Processor | Extension library written to retrieve merchant propeties used by the payment connector. |

## Overview
The diagram below provides a high level overview of the payment terminal integration through the POS. Note, the diagram assumes that a local Hardware Station is used to communicate with the payment terminal but the same patterns apply to the shared Hardware Station as well.

![Payment Connector Integration Overview](media/PAYMENTS/PAYMENT-TERMINAL/Overview.jpg)

This article describes the following steps that are required to create an end-to-end payment integration for a payment terminal:
- **Write a payment connector**: The payment connector is the main integration point between the POS and the payment terminal. This section describes how to implement and configure a new payment connector that can relay payment requests (e.g. authorize, refund, void) to the payment terminal. 
- **Write a payment processor**: The payment processor is used to define the merchant properties used as part of the payment integration. This section describes how to implement a new payment processor, including interfaces to implement and patterns to follow.

## Write a payment connector
This section describes how to write a new payment connector.

### Understanding the payment flows
The following diagram illustrates a high level overview of several payment flows (i.e. Begin Transaction, Update Cart Lines, Authorize, Capture, End Transaction) across the POS, Hardware Station, and payment connector.

![Payment Flow Overview](media/PAYMENTS/PAYMENT-TERMINAL/PaymentFlow.jpg)

### Implement a payment connector
The section below describes how to implement a new payment connector. The examples shown below can be found in the `PaymentDeviceSample` class located under `SampleExtensions\HardwareStation\Extension.PaymentSample` folder in the Retail SDK.

#### Implement the INamedRequestHandler interface
All POS payment related flows are handled through request/response patterns in the Hardware Station. The first step in writing a new payment connector is to create a class that implements the `INamedRequestHandler` interface defined in the `Microsoft.Dynamics.Commerce.Runtime.Framework` library.

``` csharp
namespace Contoso.Commerce.HardwareStation.PaymentSample 
{ 
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
}
```

The `HandlerName` is used to configure the payment connector used on a given POS register through the AX client (desccribed below).

#### Implement supported payment requests
In order to process payment related flows the payment connector has to define the `SupportedRequestTypes` that it can handle. Additionally, the `Execute` method has to be implemented to route each of the requests supported by the connector to a given method. The example below shows the complete list of `SupportedRequestTypes` and an example of a specific request (i.e. `Authorize`).

``` csharp
namespace Contoso.Commerce.HardwareStation.PaymentSample 
{ 
    /// <summary>
    /// <c>Simulator</c> manager payment device class.
    /// </summary>
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
}
```

#### Full list of supported requests
The list below descibes all supported requests types that a payment connector can implement.

| Request Class | Payment Flow Description |
| --- | --- |
| **OpenPaymentTerminalDeviceRequest** | Called before a sales transaction is initiated to establish a connection to the payment terminal. | 
| **BeginTransactionPaymentTerminalDeviceRequest** | Called when a new sales transaction is initiated to handle any initialization on the payment terminal (e.g. initializing transaction screen). | 
| **UpdateLineItemsPaymentTerminalDeviceRequest** | Called when line items on the cart are updated. | 
| **AuthorizePaymentTerminalDeviceRequest** | Called when a payment is initiated on the POS payment view. | 
| **CancelOperationPaymentTerminalDeviceRequest** | Called when a user hits the "cancel" button on the payment view dialog after the payment is initiated but before the payment is completed on the payment terminal. | 
| **CapturePaymentTerminalDeviceRequest** | Called for each payment line when the entire amount on the cart is paid and before the sales transaction is concluded. | 
| **VoidPaymentTerminalDeviceRequest** | Called when a payment line is voided on the cart. | 
| **RefundPaymentTerminalDeviceRequest** | Called when a refund is issued. | 
| **FetchTokenPaymentTerminalDeviceRequest** | Called to fetch a payment token to support deferred payments for customer orders. | 
| **EndTransactionPaymentTerminalDeviceRequest** | Called when the sales transaction is concluded and all payments have been captured. | 
| **ClosePaymentTerminalDeviceRequest** | Called after the sales transaction is concluded to close the connection to the payment terminal. | 
| **ActivateGiftCardPaymentTerminalRequest** | Called when an external gift card is being activated through the POS. | 
| **AddBalanceToGiftCardPaymentTerminalRequest** | Called when a balance is being added to an external gift card. | 
| **GetGiftCardBalancePaymentTerminalRequest** | Called to when the balance on the gift card is being retrieved. | 
| **GetPrivateTenderPaymentTerminalDeviceRequest** | TODO | 
| **ExecuteTaskPaymentTerminalDeviceRequest** | Extension request that can be invoked from the POS through customizations to enable additional payment related flows. | 

##### OpenPaymentTerminalDeviceRequest
###### Signature
``` csharp
public OpenPaymentTerminalDeviceRequest(string token, string deviceName, SettingsInfo terminalSettings, PeripheralConfiguration deviceConfig, ExtensionTransaction extensionTransactionProperties);
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| deviceName | Name of the device as defined in the AX client POS hardware profile form . |
| terminalSettings | Set of payment terminal specific configuration properties defined in the AX client, such as signature capture minimum amount, debit cash back limit, etc. |
| deviceConfig | Set of payment terminal specific configuration properties in the form of name value pairs, such as the IP address and port in case of network devices. |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### BeginTransactionPaymentTerminalDeviceRequest
###### Signature
``` csharp
public BeginTransactionPaymentTerminalDeviceRequest(string token, string paymentConnectorName, string merchantInformation, string invoiceNumber, bool isTestMode, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| paymentConnectorName | The name of the payment connctor used as part of the payment flow. This is used in case you plan to integrat with payment flows leveraging the IPaymentProcessor. | 
| merchantInformation | The merchant information defined in the AX client POS hardware profile form. |
| invoiceNumber | Unique invoice number generated by the POS to track the sales transaction. |
| isTestMode | Indicates whether the payment connector is being used in testing mode. |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### UpdateLineItemsPaymentTerminalDeviceRequest
###### Signature
``` csharp
public UpdateLineItemsPaymentTerminalDeviceRequest(string token, string totalAmount, string taxAmount, string discountAmount, string subTotalAmount, IEnumerable<ItemInfo> items, ExtensionTransaction extensionTransactionProperties = null)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| totalAmount | The total amount on the current sales transaction. | 
| taxAmount | The tax amount on the current sales transaction. |
| discountAmount | The discount amount on the current sales transaction |
| subTotalAmount | The sub total amount on the current sales transaction |
| items | List of line item to display. |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### AuthorizePaymentTerminalDeviceRequest
###### Signature
``` charp
public AuthorizePaymentTerminalDeviceRequest(string token, string paymentConnectorName, decimal amount, string currency, TenderInfo tenderInfo, string voiceAuthorization, bool isManualEntry, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| paymentConnectorName | The name of the payment connctor used as part of the payment flow. This is used in case there is an integration with payment flows leveraging the IPaymentProcessor. | 
| amount | The amount to authorize. |
| currency | The currency for the amount to authorize. |
| tenderInfo | TODO |
| voiceAuthorization | TODO |
| isManualEntry | Defines whether the card number was entered manually. |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

###### Response
The `AuthorizePaymentCardPaymentResponse` response object has to be returned when handling the `AuthorizePaymentTerminalDeviceRequest` request. The response must contain an instance of the `PaymentInfo` object with the following required properties:

| Property | Description |
| --- | --- |
| ApprovedAmount | The amount approved for the transaction. |
| CardNumberMasked | The masked credit card number which must at least contain the first digit of the credit card to support bin range lookup in POS (most devices return first 6 digits and last 4 digits). |
| CardType | The type of card used for the payment (e.g. Credit or Debit) using the `Microsoft.Dynamics.Commerce.HardwareStation.CardPayment.CardType` entity. |
| CashbackAmount | The cashback amount defined on the payment terminal (for debit transactions). |
| Errors | List of errors occurred during the authorize call. |
| IsApproved | Flag indicating whether the payment was approved. |
| PaymentSdkData | The response data used to support cross channel payment operations. |

The `PaymentSdkData` has to contain the following data.

| Namespace | Name | Description | Sample value |
| --- | --- | --- | --- |
| Connector | ConnectorName | The name of the `IPaymentProcessor` used for the transactions as described in the **Write a payment processor** section below. |
| AuthorizationResponse | Properties | The list of authorization responses. | *See list below*. |

The `Properties` field above must contain the following fields.

| Namespace | Name | Description | Sample value |
| --- | --- | --- | --- |
| AuthorizationResponse | ApprovedAmount | The amount approved for the transaction. | 28.08m |
| AuthorizationResponse | AvailableBalance | The available balance on the card. | 100.00m |
| AuthorizationResponse | ApprovalCode | The apprival code for the transaction. | Z123456 |
| AuthorizationResponse | ProviderTransactionId | The transaction identifier of the payment provider. | 123456789 |
| AuthorizationResponse | AuthorizationResult | The result of the authorization call. | `AuthorizationResult.Success.ToString()` |
| AuthorizationResponse | ExternalReceipt | The external receipt data from the payment provider. | `<ReceiptData>...</ReceiptData>` |
| AuthorizationResponse | TerminalId | The unique identifier of the terminal that handled the payment. | 000001 |

The example below illustrates how to construct the `PaymentSdkData` object.

``` csharp
List<PaymentProperty> paymentSdkProperties = new List<PaymentProperty>();
paymentSdkProperties.Add(new PaymentProperty(GenericNamespace.Connector, ConnectorProperties.ConnectorName, "TestConnector");

List<PaymentProperty> paymentSdkAuthorizationProperties = new List<PaymentProperty>();
paymentSdkAuthorizationProperties.Add(new PaymentProperty(GenericNamespace.AuthorizationResponse, AuthorizationResponseProperties.ApprovedAmount, 28.08m);
paymentSdkAuthorizationProperties.Add(new PaymentProperty(GenericNamespace.AuthorizationResponse, AuthorizationResponseProperties.AvailableBalane, 100.00);
paymentSdkAuthorizationProperties.Add(new PaymentProperty(GenericNamespace.AuthorizationResponse, AuthorizationResponseProperties.ApprovalCode, "Z123456");
paymentSdkAuthorizationProperties.Add(new PaymentProperty(GenericNamespace.AuthorizationResponse, AuthorizationResponseProperties.ProviderTrasactionId, "123456789");
paymentSdkAuthorizationProperties.Add(new PaymentProperty(GenericNamespace.AuthorizationResponse, AuthorizationResponseProperties.AuthorizationResult, AuthorizationResult.Success.ToString());
paymentSdkAuthorizationProperties.Add(new PaymentProperty(GenericNamespace.AuthorizationResponse, TransactionDataProperties.TerminalId, "000001");

paymentSdkProperties.Add(new PaymentProperty(GenericNamespace.AuthorizationResponse, AuthorizationResponseProperties.Properties, paymentSdkAuthorizationProperties.ToArray()));

string paymentSdkData = PaymentProperty.ConvertPropertyArrayToXML(paymentSdkProperties.ToArray());
```

##### CancelOperationPaymentTerminalDeviceRequest
###### Signature
``` charp
public CancelOperationPaymentTerminalDeviceRequest(string token)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |

##### CapturePaymentTerminalDeviceRequest
###### Signature
``` charp
public CapturePaymentTerminalDeviceRequest(string token, decimal amount, string currency, string paymentPropertiesXml, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| amount | The amount to capture. |
| currency | The currency for the amount to capture. |
| paymentPropertiesXml | TODO |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### VoidPaymentTerminalDeviceRequest
###### Signature
``` charp
public VoidPaymentTerminalDeviceRequest(string token, string paymentConnectorName, decimal amount, string currency, TenderInfo tenderInfo, string paymentPropertiesXml, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| paymentConnectorName | The name of the payment connctor used as part of the payment flow. This is used in case there is an integration with payment flows leveraging the IPaymentProcessor. | 
| amount | The amount for the payment to void. |
| currency | The currency for the payment to void. |
| tenderInfo | TODO |
| paymentPropertiesXml | TODO |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### RefundPaymentTerminalDeviceRequest
###### Signature
``` charp
public RefundPaymentTerminalDeviceRequest(string token, string paymentConnectorName, TenderInfo tenderInfo, decimal amount, string currency, bool isManualEntry, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| paymentConnectorName | The name of the payment connctor used as part of the payment flow. This is used in case there is an integration with payment flows leveraging the IPaymentProcessor. | 
| tenderInfo | TODO |
| amount | The amount to refund. |
| currency | The currency for the amount to refund. |
| isManualEntry | Defines whether the card number was entered manually. |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### FetchTokenPaymentTerminalDeviceRequest
###### Signature
``` charp
public FetchTokenPaymentTerminalDeviceRequest(string token, bool isManualEntry, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| isManualEntry | Defines whether the card number was entered manually. |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### EndTransactionPaymentTerminalDeviceRequest
##### Signature
``` charp
public EndTransactionPaymentTerminalDeviceRequest(string token, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### ClosePaymentTerminalDeviceRequest
###### Signature
``` charp
public ClosePaymentTerminalDeviceRequest(string token, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### ActivateGiftCardPaymentTerminalRequest
###### Signature
``` charp
public ActivateGiftCardPaymentTerminalRequest(string token, string paymentConnectorName, decimal amount, string currencyCode, TenderInfo tenderInfo, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| paymentConnectorName | The name of the payment connctor used as part of the payment flow. This is used in case there is an integration with payment flows leveraging the IPaymentProcessor. | 
| amount | The initial amount to add to the gift card during activation. |
| currency | The currency for the initial amount to be added to the gift card during activation. |
| tenderInfo | TODO |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### AddBalanceToGiftCardPaymentTerminalRequest
###### Signature
``` charp
public AddBalanceToGiftCardPaymentTerminalRequest(string token, string paymentConnectorName, decimal amount, string currencyCode, TenderInfo tenderInfo, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| paymentConnectorName | The name of the payment connctor used as part of the payment flow. This is used in case there is an integration with payment flows leveraging the IPaymentProcessor. | 
| amount | The amount to add to the gift card. |
| currency | The currency in which to add the gift card balance. |
| tenderInfo | TODO |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### GetGiftCardBalancePaymentTerminalRequest
###### Signature
``` charp
public GetGiftCardBalancePaymentTerminalRequest(string token, string paymentConnectorName, string currencyCode, TenderInfo tenderInfo, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| paymentConnectorName | The name of the payment connctor used as part of the payment flow. This is used in case there is an integration with payment flows leveraging the IPaymentProcessor. |  
| currency | The currency in which to retrieve the gift card balance on. |
| tenderInfo | TODO |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### GetPrivateTenderPaymentTerminalDeviceRequest
###### Signature
``` charp
public GetPrivateTenderPaymentTerminalDeviceRequest(string token, decimal amount, bool declined, bool isSwipe, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| amount | TODO | 
| declined | TODO |
| isSwipe | TODO |
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

##### ExecuteTaskPaymentTerminalDeviceRequest
###### Signature
``` charp
public ExecuteTaskPaymentTerminalDeviceRequest(string token, string task, ExtensionTransaction extensionTransactionProperties)
```

###### Variables
| Variable | Description |
| --- | --- |
| token | Unique token value generated when the payment terminal is initially locked for the transaction. |
| task | Unique identifier for the task being executed. | 
| extensionTransactionProperties | Set of extension configuration properties in the form of name value pairs. |

#### State in the payment connector
The payment connector can be either hosted as part of the `dllhost.exe` process when hosted through the in-proc Hardware Station inside the POS or as a `w3wp.exe` process when hosted in the IIS based Hardware Station. In either scenario there are circumstances under which each of these processes can be terminated or crash in between or in the middle of payment flows. As a result, it is recommended that payment connectors do not have state dependencies and can recover if terminated at any point in time during the payment flow related requests described above.

### Configure the payment connector in the Hardware Station config
In order to ensure that the payment connector is loaded by the Hardware Station the corresonding assembly reference has to be set on the `HardwareStation.Extension.config` found in the `Assets` folder in the Retail SDK.

``` xml
<?xml version="1.0" encoding="utf-8"?>
<hardwareStationExtension>
  <composition>
    <!-- 
        Register your own assemblies or types here. The the following example registers NewPeripheralDevice 
        (and all its request handlers). Any other services are not being overridden:

        <add source="type" 
             value="Contoso.Commerce.HardwareStation.NewPeripheralDevice, Contoso.Commerce.HardwareStation.NewPeripheralDevice" />
        <add source="assembly" 
             value="Contoso.Commerce.HardwareStation.NewPeripheralDevice” />
    -->
    <add source="assembly" value="Contoso.Commerce.HardwareStation.PaymentSample" />
  </composition>
</hardwareStationExtension>
```

### Configure the payment connector on the AX client POS hardware profile form
In order to determine the right payment connector to load on the POS the value of the `PaymentTerminalDevice` property has to be set on the `Device` field in the `PIN Pad` section on the AX client POS hardware profile form as shown below.

![Configure payment connector on the AX client POS hardware profile form](media/PAYMENTS/PAYMENT-TERMINAL/SamplePaymentDeviceConfigurInAx.jpg)

## Write a payment processor
Payment processes are usually used only if a direct connection to a payment gateway is established as it is most commonly the case in card-not-present sales transactions or more involved card-present scenarios. Additionally, the payment processor is also used to process the merchant properties configured through the `POS hardware profile` form in the AX client. 

> [!NOTE]
> The payment processor is required today even if all payment requests are handled directly through the payment terminal and no merchant properties need to be set through the POS. 
    
### Understanding the merchant properties flows
The sections below describe how the merchant properties are set on the AX client POS hardware profile page and how they are passed to the payment connector during payment flows on the POS.

#### Set merchant properties in AX client POS hardware profile form
The diagram below illustrates how the merchant properties are set through the AX client POS hardware profile form. In order to enable the merchant properties to be set the `IPaymentProcessor` interface defined in the `Microsoft.Dynamics.Retail.PaymentSDK` library has to be implemented. The two required interface methods are `GetMerchantAccountPropertyMetadata` and `ValidateMerchantAccount`. 

![Setting Merchant Properties in AX client POS hardware profile form](media/PAYMENTS/PAYMENT-TERMINAL/MerchantPropertiesAXFlow.jpg)

#### Set merchant properties on payment connector during POS sales transaction
The diagram below illustrates how the merchant properties are retrieved from the AX DB through the Retail Server and passed to the payment connector during the `BeginTransactionPaymentTerminalDeviceRequest`.

![Setting Merchant Properties on payment connector during POS payment flows](media/PAYMENTS/PAYMENT-TERMINAL/MerchantPropertiesPOSFlow.jpg)

### Implement the IPaymentProcessor interface
In order to handle merchant properties related payment flows the `IPaymentProcessor` interface defiend in the `Microsoft.Dynamics.Retail.PaymentSDK` library has to be implemented. The example below shows how to implement the two required interface methods `GetMerchantAccountPropertyMetadata` and `ValidateMerchantAccount`. Other interface methods can be left blak (e.g. return `FeatureNotSupportedException`).

``` charp
/// <summary>
/// SampleConnector class (Portable Class Library version).
/// </summary>
public class SampleConnector : IPaymentProcessor
{
     /// <summary>
     /// GetMerchantAccountPropertyMetadata returns the merchant account properties need by the payment provider.
     /// </summary>
     /// <param name="request">Request object.</param>
     /// <returns>
     /// Response object.
     /// </returns>
     public Response GetMerchantAccountPropertyMetadata(Request request)
     {
         string methodName = "GetMerchantAccountPropertyMetadata";

         // Check null request
         List<PaymentError> errors = new List<PaymentError>();
         if (request == null)
         {
             errors.Add(new PaymentError(ErrorCode.InvalidRequest, "Request is null."));
             return PaymentUtilities.CreateAndLogResponseForReturn(methodName, this.Name, Platform, locale: null, properties: null, errors: errors);
         }

         // Prepare response
         List<PaymentProperty> properties = new List<PaymentProperty>();
         PaymentProperty property;
         property = new PaymentProperty(
             GenericNamespace.MerchantAccount,
             MerchantAccountProperties.AssemblyName,
             this.GetAssemblyName());
         property.SetMetadata("Assembly Name:", "The assembly name of the test provider", false, true, 0);
         properties.Add(property);
		 
         Response response = new Response();
         response.Locale = request.Locale;
         response.Properties = properties.ToArray();
         if (errors.Count > 0)
         {
             response.Errors = errors.ToArray();
         }

         PaymentUtilities.LogResponseBeforeReturn(methodName, this.Name, Platform, response);
         return response;
     }

     /// <summary>
     /// ValidateMerchantAccount the passed merchant account properties with the payment provider.
     /// </summary>
     /// <param name="request">Request object to validate.</param>
     /// <returns>
     /// Response object.
     /// </returns>
     public Response ValidateMerchantAccount(Request request)
     {
         string methodName = "ValidateMerchantAccount";

         // Convert request
         ValidateMerchantAccountRequest validateRequest = null;
         try
         {
             validateRequest = ValidateMerchantAccountRequest.ConvertFrom(request);
         }
         catch (SampleException ex)
         {
             return PaymentUtilities.CreateAndLogResponseForReturn(methodName, this.Name, Platform, locale: request == null ? null : request.Locale, properties: null, errors: ex.Errors);
         }

         // Validate merchant account
         List<PaymentError> errors = new List<PaymentError>();
         ValidateMerchantProperties(validateRequest, errors);
         if (errors.Count > 0)
         {
             return PaymentUtilities.CreateAndLogResponseForReturn(methodName, this.Name, Platform, validateRequest.Locale, errors);
         }

         // Create response
         var validateResponse = new ValidateMerchantAccountResponse(validateRequest.Locale, validateRequest.ServiceAccountId, this.Name);

         // Convert response and return
         Response response = ValidateMerchantAccountResponse.ConvertTo(validateResponse);
         PaymentUtilities.LogResponseBeforeReturn(methodName, this.Name, Platform, response);
         return response;
     }
}
```

#### Required merchant property fields
The following table illustrates the required merchant property fields that have to be set as part of the `GetMerchantAccountPropertyMetadata` method.

| Namespace | Name | Sample value |
| --- | --- | --- |
| MerchantAccount | PortableAssemblyName | Contoso.Microsoft.PaymentsSample |
| MerchantAccount | ServiceAccountId | f35989c8-e571-4de1-862a-996c82a2e6b6 |
| MerchantAccount | SupportedCurrencies | AUD;BRL;CAD;CHF;CNY;CZK;DKK;EUR;GBP;HKD;HUF;INR;JPY;KPW;KRW;MXN;NOK;NZD;PLN;SEK;SGD;TWD;USD;ZAR |
| MerchantAccount | SupportedTenderTypes | Visa;MasterCard;Amex;Discover;Debit |
