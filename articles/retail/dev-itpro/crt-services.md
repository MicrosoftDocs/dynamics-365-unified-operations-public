---
# required metadata

title: Commerce Runtime services
description: This topic describes the Commerce runtime service (CRT), which is a collection of portable .NET libraries that contain the core business logic for the retail channel and pricing functionalities.
author: mugunthanm 
manager: AnnBe
ms.date: 05/23/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2018-18-05
ms.dyn365.ops.version: AX 8.0, Retail July 2017 update

---
# Commerce Runtime services

[!include [banner](../../includes/banner.md)]

Commerce runtime (CRT) is a collection of portable .NET libraries that contain the core business logic for the retail channel and pricing functionalities, if you want to add or modify any business logic then you should customize CRT. The Retail POS call the CRT to perform any business logic, CRT process the request and then sends the response back to POS. POS is like a thin client, all the business logic should be done in CRT.

Each CRT service contains one or more Request/Response, CRT service is a group of request and response. Anything you do in POS it sends Request to Retail server (RS) and RS call CRT, CRT process the request and sends the response back.

In this topic we see some important request/response which you may customize for your business scenario.

There are three main layers in CRT:

1.  Services

2.  Workflow and Messages

3.  Data Access

Other core components which is required for CRT to function are runtime, authentication, data access managers and avoid any customization on these layers because all business logic customization can be done in services, data access or at workflow level.

## Overall flow

CRT Service Request < > Zero or more workflow Request < > Zero or more Data Access Request

**Example** Create sales order service request will call multiple workflow and data access request to perform the request.

## CRT Services

Each CRT service contains one or more Request/Response. Ex: **Customer service** in CRT contains all the customer related and each one is executed in different flow.

### Default CRT Services

There are many services in the commerce runtime that support the functionality of retail channel and store operations. You can add your own services or extend the existing services. The following table describes some of the services that you might customize for different business service.

For more information about each service, see the CRT request response document in Retail SDK (…\RetailSDK\Code\Documents\CommerceRuntimeMessages.chm).

| Service               | Description                                                                                                                                                                                                                                                                                                                                                     |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AddressService             | Verifies addresses and gets location information like cities, counties, or states.                                                                                                                                                                                                                                                                                   |
| BarcodeService             | Process the barcode scanned based on Mask, barcode types and calculate quantity and price from barcode.                                                                                                                                                                                                                                                              |
| CartService                | Gets the cart from the transaction and sales transaction service from the transaction tables.                                                                                                                                                                                                                                                                                                                                                                                                                       
| ChargeService              | This service implements logic for calculating auto-charges, price charges and shipping charges for transactions.                                                                                                                                                                                                                                                     |
| CouponService              | Validate and updates coupon related request.                                                                                                                                                                                                                                                                                                                         |
| CurrencyService            | Converts currencies based on exchange rates.                                                                                                                                                                                                                                                                                                                         |
| CustomerService            | Maintains customer information and like Save, purchase history, get customer, customer balance.                                                                                                                                                                                                                                                                      |
| EmployeeService            | Gets employee related information and employee by store.                                                                                                                                                                                                                                                                                                             |
| FormattingService          | This service implements logic for format number, currency and date                                                                                                                                                                                                                                                                                                   |
| GiftCardService            | Provides information about internal gift card related activities like issue, get balance, add.                                                                                                                                                                                                                                                                       |
| LoyaltyService             | Implements a program that rewards repeat customers.                                                                                                                                                                                                                                                                                                                  |
| NotificationService        | Maintains the POS notification service.                                                                                                                                                                                                                                                                                                                              |
| PaymentService             | You can connect your online store to a payment service to provide credit card authorization and utilize pre-configured payment processing. You can also extend the payment service to add additional third party payment processors.                                                                                                                                 |
| ProductService             | Get product and variant related information.                                                                                                                                                                                                                                                                                                                         |
| ProductsService            | Get products and variants related information.                                                                                                                                                                                                                                                                                                                       |
| PricingService             | Obtains the price of an item in real time. The price is adjusted based on the base price and any applicable discounts. Discounts can be customized for each retailer.                                                                                                                                                                                                |
| ProductAvailabilityService | Calculates the quantities of products that are available to sell.                                                                                                                                                                                                                                                                                                    |
| ReasonCodeService          | Calculates and gets the required reason code for POS operations or any workflow.                                                                                                                                                                                                                                                                                     |
| ReceiptService             | Gets and formats the receipt details.                                                                                                                                                                                                                                                                                                                                |
| RoundingService            | Rounds the tender amount based on the tender type and store.                                                                                                                                                                                                                                                                                                         |
| SalesOrderService          | Creates a sales order based on a customer shopping cart.                                                                                                                                                                                                                                                                                                             |
| SearchProductsService      | Search product based on the input text.   |
| ShippingService            | Calculates shipping costs and determine shipping options for the current order.     |
| StockCountService          | Create, commit and sync stock journals.                                             |
| StoreOperationService      | Maintains store related operation service like Save and Drop, Tender declaration and Search journal.                                                                                                                                                                                                                                                                 |
| TaxService                 | Calculates the sales tax for the current order. You can use sales tax information from Microsoft Dynamics AX or from a third party sales tax service.                                                                                                                                                                                                                |
| TotalingService            | Calculates the totals on the sales transactions and sales lines.                                                                                                                                                                                                                                                                                                     |

For extension scenarios you can override any of the request inside the service class. Ex: If you want to change the customer search flow then you will extend the CustomersSearchServiceRequest from the CustomerService.

Note: You will not customize the Service class you will extend the request/response within the service class, service class by itself doesn’t have any logic it just routes the call to the right request.

## Sample service class implementation

```C#
public class MyService : IRequestHandler

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

typeof(MyRequest),

typeof(MyRequest1),

typeof(MyRequest2),

};

}

}

/// <summary>

/// Entry point to my service. Takes a service request and returns the result

/// of the request execution.

/// </summary>

/// <param name="request">The my service request to execute.</param>

/// <returns>Result of executing request, or null object for void operations.</returns>

public Response Execute(Request request)

{

if (request == null)

{

throw new ArgumentNullException("request");

}

Type requestType = request.GetType();

Response response;

if (requestType == typeof(MyRequest))

{

response = MyRequestCustomMethod((MyRequest)request);

}

else if (requestType == typeof(MyRequest1))

{

response = MyRequest1CustomMethod ((MyRequest1)request);

}

else if (requestType == typeof(MyRequest2))

{

response = MyRequest2CustomMethod ((MyRequest2)request);

}

else

{

throw new NotSupportedException(string.Format(CultureInfo.InvariantCulture, "Request '{0}' is not supported.", request.GetType().ToString()));

}

return response;

}

private static MyResponse MyRequestCustomMethod (MyRequest request)

{

return myresponse;

}

}
```

## Extension pattern for CRT

1.  Create a new service class and implement one or more request/response – Follow this approach if you want to create new feature.

2.  Override the core request/response - If you want to modify the standard workflow or business logic.

3.  Add pre or post trigger for any request/response – If you want to add additional business logic or add some custom fields etc.

Note: It doesn’t matter whether you create a data request, workflow request or service request everything in CRT is request and response. It’s up to you write whatever logic within the request/response. As said earlier the request are classified into different types for logical reasons but from the framework perspective everything is same.

**All our request/response will have the below three classes implemented:**

1.  **Request class** – POS/RS/E-commerce/CRT workflow class the request to perform something.

2.  **Response class** – Returns the response based on the request to the caller.

3.  **Handler class** – Contains the core logic for the request. Within the handler class you can call other request, do custom logic etc.

### Request class

```C#
public class MyRequest : Request

{

/// <summary>

/// Initializes a new instance of the <see cref="MyRequest"/> class.

/// </summary>

public MyRequest ()

{

}

// other properties

}

**Response class:**

public sealed class MyResponse : Response

{

/// <summary>

/// Initializes a new instance of the <see cref=" MyResponse"/> class.

/// </summary>

public MyResponse ()

{

}

}

**Handler class:**

public sealed class MyRequestHandler : SingleRequestHandler< MyRequest, MyResponse >

{

/// <summary>

/// Saves (updating if it exists and creating a new one if it does not) the shopping cart on the request.

/// </summary>

/// <param name="request">The request.</param>

/// <returns><see cref=" MyResponse "/> object containing the cart with updated item quantities.</returns>

protected override MyResponse Process(MyRequest request)

{

//logic class.

}

}
```

### AddressService

Address service supports the below request/response for different extension scenarios:

| Request                            | Purpose                                           |
|------------------------------------|---------------------------------------------------|
| GetCountryRegionsServiceRequest    | Gets the list of country and region supported.    |
| GetStateProvincesServiceRequest    | Gets the list of state supported for the country. |
| GetCitiesServiceRequest            | Gets the list of cities supported for the state.  |
| GetDistrictServiceRequest          | Gets the list of districts supported.             |
| GetZipCodesServiceRequest          | Gets the list of zip codes supported.             |
| GetFromZipPostalCodeServiceRequest | Gets the list of postal codes supported.          |
| GetAddressFormattingServiceRequest | Gets the address format for the specific country. |

### BarcodeService

| Request                                  | Purpose                                                                    |
|------------------------------------------|----------------------------------------------------------------------------|
| ProcessMaskSegmentsServiceRequest        | Process the barcode based on the barcode mask configuration                |
| GetBarcodeTypeServiceRequest             | Gets the types of barcode supported.                                       |
| CalculateQuantityFromPriceServiceRequest | Calculates the price and quantity based on the barcode scanned or entered. |

### CartService

| Request                                                     | Purpose                                                                                     |
|-------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| GetSalesTransactionsServiceRequest                          | Gets the sales transaction from the retail headquarters.                                    |
| GetCartServiceRequest                                       | Gets the cart from the sales transaction table using the cart id.                           |
| CalculateSalesTransactionServiceRequest                     | Calculates the various sales transaction totals depending on the specified calculation mode |
| CalculateEstimatedShippingAuthorizationAmountServiceRequest | The request to calculate estimated shipping authorization amount on the transaction         |
| ConvertSalesTransactionToCartServiceRequest                 | Convert the sales transaction to cart based on transaction id passed.                       |

### CouponService

| Request                               | Purpose                                                                                          |
|---------------------------------------|--------------------------------------------------------------------------------------------------|
| UpdateCouponCodesOnCartServiceRequest | Updated the coupon codes status in the retail headquarters based on the coupons used in the cart |
| ValidateCouponCodesServiceRequest     | This request validated the coupon code entered in the transactions.                              |
| UpdateCouponUsageServiceRequest       | The service request to update coupon usage for the transaction                                   |

### CustomerService

| Request                                      | Purpose                                                                      |
|----------------------------------------------|------------------------------------------------------------------------------|
| SaveCustomerServiceRequest                   | This request is called when you do save customer from POS.                   |
| GetCustomersServiceRequest                   | This request is used to get the selected customer details.                   |
| CustomersSearchServiceRequest                | This request is executed when you search customer from POS                   |
| GetCustomerGroupsServiceRequest              | This request is used to get the customer group details.                      |
| InitiateLinkToExistingCustomerServiceRequest | Internal request for backward compatibility                                  |
| FinalizeLinkToExistingCustomerServiceRequest | Internal request for backward compatibility                                  |
| UnlinkFromExistingCustomerServiceRequest     | Internal request for backward compatibility                                  |
| GetCustomerBalanceServiceRequest             | Get the customer on Account balance                                          |
| GetOrderHistoryServiceRequest                | Gets the customer order history.                                             |
| GetPurchaseHistoryServiceRequest             | Gets the customer recent purchase history                                    |
| CustomerSearchByFieldsServiceRequest         | This request is executed when you search by customer by fields (hint search) |
| GetCustomerSearchFieldsServiceRequest        | This request gets the list of customer search fields (hint fields).          |

### PricingService

| Request                                   | Purpose                                                                                           |
|-------------------------------------------|---------------------------------------------------------------------------------------------------|
| CalculatePricesServiceRequest             | Calculates the price for each item added to the cart and in search screen.                        |
| CalculateDiscountsServiceRequest          | Calculates the discount for each item added to the cart.                                          |
| GetIndependentPriceDiscountServiceRequest | Calculates the price for each item in price check screen and other non-transaction related flows. |
| ValidateDiscountsServiceRequest           | Validates the discount entered based on the employee.                                             |
| GetAllPeriodicDiscountsServiceRequest     | Gets all the periodic discounts configured.                                                       |
| GetDiscountCodesServiceRequest            | Gets all the discount codes configured.                                                           |

### ProductService

| Request                     | Purpose                                                                                                                                       |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ProductSearchServiceRequest | Gets the product list based on the search text from POS. (This is legacy request, use the new SearchProductsServiceRequest for customization) |
| GetProductServiceRequest    | Gets the product based on the product id.                                                                                                     |
| GetProductRefinersRequest   | Retrieves the product refiner values                                                                                                          |

### ProductsService

| Request                          | Purpose                                                        |
|----------------------------------|----------------------------------------------------------------|
| GetProductsServiceRequest        | Gets the products based on the products ids provided.          |
| GetVariantProductsServiceRequest | The request to get specific variations of master type products |

### ReasonCodeService

| Request                                                             | Purpose                                                                                        |
|---------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| GetReasonCodesServiceRequest                                        | Gets the required reason code for workflow or POS operation.                                   |
| CalculateRequiredReasonCodesServiceRequest                          | Calculates the required reason code for the POS operation or workflow.                         |
| CalculateCartRequiredReasonCodesServiceRequest                      | Calculates the required reason code for the cart workflow.                                     |
| CalculateDropAndDeclareTransactionRequiredReasonCodesServiceRequest | Calculates the required reason code for the drop and tender declaration transaction.           |
| CalculateNonSalesTransactionRequiredReasonCodesServiceRequest       | Calculates the required reason code for the non-sales transaction like tender declaration etc. |
| GetReturnOrderReasonCodesServiceRequest                             | Gets the required reason code for the return transaction.                                      |
| ValidateReasonCodeLineForUpdateServiceRequest                       | Validates the reason code lines added during the save cart request.                            |

### ReceiptService

| Request                               | Purpose                                                                                            |
|---------------------------------------|----------------------------------------------------------------------------------------------------|
| GetReceiptServiceRequest              | Gets the receipt type and generate the receipt data based on the receipt type.                     |
| GetCustomReceiptFieldServiceRequest   | Override this request and add custom logic for your custom fields added in the receipt.            |
| GetEmailReceiptServiceRequest         | The service request to get the formatted receipts that will be used for print and email scenarios. |
| PopulateTaxSummaryIndiaServiceRequest | The request to populate tax summary for India transaction                                          |

### SearchProductsService

| Request                      | Purpose                                                          |
|------------------------------|------------------------------------------------------------------|
| SearchProductsServiceRequest | This requested is executed when you search for product from POS. |

### TaxService

| Request                      | Purpose                                                                                                                                                                               |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CalculateTaxServiceRequest   | The request to calculate taxes on the transaction                                                                                                                                     |
| AssignTaxCodesServiceRequest | The request to assign tax codes on the transaction's taxable items prior the tax calculation. The default tax calculation handler of CalculateTaxServiceRequest is using this message |
| PopulateTaxRatesRequest      | The request to populate tax rates for recalled transaction. There is no tax percentage information persisted for tax lines. This message handler restores it                          |

## Workflow layer

On top of the services layer is the workflow layer. A workflow is a collection of services and business logic that together define business processes. For example, when a customer adds an item to the cart, you could use workflow to get the price, perform validation, check inventory quantity, calculate shipping, calculate tax, and calculate discounts. You can customize the existing workflows, or you can create new workflows. You can even use a workflow to connect to a third-party system as part of your business processes.

Just like services, workflow uses the request and response pattern. The request object inherits from the base commerce runtime [Request](https://technet.microsoft.com/en-us/library/microsoft.dynamics.commerce.runtime.messages.request.aspx) class. The response object inherits from the base commerce runtime [Response](https://technet.microsoft.com/en-us/library/microsoft.dynamics.commerce.runtime.messages.response.aspx) class. A workflow also has a request handler class that extends the [WorkflowRequestHandler<TRequest, TResponse>](https://technet.microsoft.com/en-us/library/jj764791.aspx) class. To create a workflow, you create a request class and a response class, and then create a request handler class that contains the business logic for your workflow.

Ex: When you create a cash & carry transaction or customer order we perform lot of different steps or workflow before creating the order. One of the workflow steps in the order process is to Save Cart. Save cart request workflow is the one responsible for saving any changes done to the cart from POS. Ex: When you add item to cart, change quantity etc. anything you do in POS will call the SaveCart to save the changes to the POS and DB.

The Save cart workflow process will have the below three classes implemented:

### Request class

```C#
public class SaveCartRequest : Request

{

/// <summary>

/// Initializes a new instance of the <see cref="SaveCartRequest"/> class.

/// </summary>

public SaveCartRequest()

{

}

// other properties

}

**Response class:**

public sealed class SaveCartResponse : Response

{

/// <summary>

/// Initializes a new instance of the <see cref="SaveCartResponse"/> class.

/// </summary>

public SaveCartResponse()

{

}

}

**Handler class:**

public sealed class SaveCartRequestHandler : SingleRequestHandler<SaveCartRequest, SaveCartResponse>

{

/// <summary>

/// Saves (updating if it exists and creating a new one if it does not) the shopping cart on the request.

/// </summary>

/// <param name="request">The request.</param>

/// <returns><see cref="SaveCartResponse"/> object containing the cart with updated item quantities.</returns>

protected override SaveCartResponse Process(SaveCartRequest request)

{

//logic class.

}

}
```
All our workflow classes will follow the same pattern.

### Default Workflows and Handlers

Below is the list of default workflow request which been called one more service based on the operation you perform in POS. You can customize any of these workflows according to your business scenario:

| Request                           | Handler                                 | Purpose                                                                                        |
|-----------------------------------|-----------------------------------------|------------------------------------------------------------------------------------------------|
| AddOrderInvoiceToCartRequest      | AddOrderInvoiceToCartRequestHandler     | Request to add invoice to cart as a cart line                                                  |
| AddOrRemoveDiscountCodesRequest   | AddOrRemoveDiscountCodesRequestHandler  | Request for adding or removing discount codes from cart                                        |
| CancelOrderRequest                | CancelOrderRequestHandler               | Triggered when you do a cancel order from POS.                                                 |
| CopyCartRequest                   | CopyCartRequestHandler                  | Creates an identical shopping cart with the specified cart type                                |
| GetAddressRequest                 | GetAddressRequestHandler                | Gets the address from the list.                                                                |
| GetCardPaymentAcceptPointRequest  | GetCardPaymentAcceptPointRequestHandler | Request for getting the accepting point of card payment                                        |
| GetCartRequest                    | GetCartRequestHandler                   | Request to get the shopping cart based on cart search criteria                                 |
| GetDiscountCodesRequest           | GetDiscountCodesRequestHandler          | Request for getting discount codes                                                             |
| GetOrdersRequest                  | GetOrdersRequestHandler                 | Request for getting sales orders                                                               |
| GetPromotionsRequest              | GetPromotionsRequestHandler             | Gets the shopping cart with promotions lines for the cart and for the cart items               |
| GetScanResultRequest              | GetScanResultRequestHandler             | Gets the entity details based on the scanned or keyed in details.                              |
| GetSupportedCardTypesRequest      | GetSupportedCardTypesRequestHandler     | Retrieves the supported cart types for the specified currency                                  |
| IssueOrAddToGiftCardRequest       | IssueOrAddToGiftCardRequestHandler      | Request to issue or add balance gift to card                                                   |
| PickAndPackOrderRequest           | PickAndPackOrderRequestHandler          | Represents a request for picking list creation and packing slip creation for a customer order. |
| PickupAtStoreRequest              | PickupAtStoreRequestHandler             | Represents a pick up at store request                                                          |
| RecalculateOrderRequest           | RecalculateOrderRequestHandler          | Represents a recalculate order workflow request                                                |
| RecallCustomerOrderRequest        | RecallCustomerOrderRequestHandler       | Request for getting sales orders and converting into a cart                                    |
| RecallSalesInvoiceRequest         | RecallSalesInvoiceRequestHandler        | Request for getting invoices                                                                   |
| ResumeCartRequest                 | ResumeCartRequestHandler                | Represents a request to resume suspended cart                                                  |
| SaveCartLinesRequest              | SaveCartLinesRequestHandler             | Represents the request for create, update, delete or void operations on the cart line          |
| SaveCartRequest                   | SaveCartRequestHandler                  | Triggered when you do any changes in POS which affects the cart.                               |
| SaveCustomerOrderRequest          | SaveCustomerOrderRequestHandler         | Initiates a save customer order request given the cart identifier and payment card information |
| SaveReasonCodeLineRequest         | SaveReasonCodeLineRequestHandler        | Request for add or update reason code line                                                     |
| SaveTenderLineRequest             | SaveTenderLineRequestHandler            | Adds/Removes/Updates a tender line for the given shopping cart                                 |
| SaveVoidTransactionRequest        | SaveVoidTransactionRequestHandler       | Request for voiding a transction.                                                              |
| SubmitSalesTransactionRequest     | SubmitOrderRequestHandler               | Initiates a submit sales transaction request given the cart identifier.                        |
| SuspendCartRequest                | SuspendCartRequestHandler               | Represents a request to suspend cart.                                                          |
| TransferCartRequest               | TransferCartRequestHandler              | Transfers the given shopping cart                                                              |
| UpdateCommissionSalesGroupRequest | UpdateCommissionSalesGroupHandler       | Encapsulates request for updating the sales rep on the cart or the cart line.                  |
| UploadOrderRequest                | UploadOrderRequestHandler               | Request for uploading sales order                                                              |
| ValidateCartForCheckoutRequest    | ValidateCartForCheckoutRequestHandler   | Validate cart for checkout request                                                             |

