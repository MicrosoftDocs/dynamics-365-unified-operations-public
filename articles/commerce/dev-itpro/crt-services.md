---
# required metadata

title: Commerce runtime (CRT) services
description: This topic describes the Commerce runtime (CRT) services, which are a collection of portable .NET libraries that contain the core business logic for the commerce channel and pricing functionality.
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
ms.reviewer: rhaertle
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
# Commerce runtime (CRT) services

[!include [banner](../../includes/banner.md)]

Commerce runtime (CRT) is a collection of portable .NET libraries that contain the core business logic for the commerce channel and pricing functionality. To add or modify any business logic, you should customize CRT. Retail Modern POS or Cloud POS calls CRT to request that it perform business logic. CRT processes the request and then sends the response back to point of sale. POS is like a thin client, all the business logic should be done in CRT.

A CRT service is a group of requests/responses. Any time that you do something in POS, POS sends a request to Commerce Scale Unit, and Commerce Scale Unit calls CRT. CRT processes the request and sends back the response.

This topic shows some important requests/responses that you can customize for your business scenario.

There are three main layers in CRT:

- Services
- Workflow
- Data Access

All CRT customization for business logic can be done in Services, Workflow or Data Access layers, other core layers that are required for CRT to work are runtime, authentication, and data access managers and you should avoid any customization on these layers.

## Overall flow
The overall flow looks like this:

CRT service request \< \> Zero or more workflow requests \< \> Zero or more data access requests

For example, multiple workflow and data access requests are called to perform the **Create sales order** service request.

## CRT services

Each CRT service contains one or more requests/responses. For example, the Customer service in CRT contains all the customer-related requests/responses. Each request/response is run in a different flow.

### Default CRT services

Many services in CRT support the functionality of the channel and store operations. You can add your own services or extend the existing services. The following table describes some of the services that you might customize for various business services.

For more information about each service, see the CRT request/response document in the Retail software development kit (SDK), at …\\RetailSDK\\Code\\Documents\\CommerceRuntimeMessages.chm.

| Service                    | Description |
|----------------------------|-------------|
| AddressService             | This service verifies addresses and gets location information, such as cities, counties, or states. |
| BarcodeService             | This service processes the barcode that was scanned, based on the mask and barcode types, and calculates the quantity and price from the barcode. |
| CartService                | This service gets the cart from the transaction and sales transaction service from the transaction tables. |
| ChargeService              | This service implements logic that calculates automatic charges, price charges, and shipping charges for transactions. |
| CouponService              | This service validates and updates coupon-related requests. |
| CurrencyService            | This service converts currencies, based on exchange rates. |
| CustomerService            | This service contains customer related operations such as Save cusotomer, purchase history, get customer and customer balance. |
| EmployeeService            | This service gets employee-related information and employees by store. |
| FormattingService          | This service implements logic for the format of numbers, currencies, and dates. |
| GiftCardService            | This service provides information about internal activities that are related to gift cards, such as issuing the gift card, getting the balance, and adding value. |
| LoyaltyService             | This service implements a program that rewards repeat customers. |
| NotificationService        | This service maintains the POS notification service. |
| PaymentService             | This service lets you connect your online store to a payment service to provide credit card authorization and use preconfigured payment processing. You can also extend the payment service to add additional third-party payment processors. |
| ProductService             | This service gets product-related and variant-related information. |
| ProductsService            | This service gets information that is related to products and variants. |
| PricingService             | This service gets the price of an item in real time. The price is adjusted, based on the base price and any applicable discounts. Discounts can be customized for each retailer. |
| ProductAvailabilityService | This service calculates the quantities of products that are available to sell. |
| ReasonCodeService          | This service calculates and gets the required reason code for POS operations or any workflow. |
| ReceiptService             | This service gets and formats the receipt details. |
| RoundingService            | This service rounds the tender amount, based on the tender type and store. |
| SalesOrderService          | This service creates a sales order, based on a customer shopping cart. |
| SearchProductsService      | This service searches products, based on the input text. |
| ShippingService            | This service calculates shipping costs and determines shipping options for the current order. |
| StockCountService          | This service creates, commits, and synchronizes stock journals. |
| StoreOperationService      | This service maintains store-related operation services, such as Save and Drop, Tender declaration, and Search journal. |
| TaxService                 | This service calculates the sales tax for the current order. You can use sales tax information provided, or from a third-party sales tax service. |
| TotalingService            | This service calculates the totals on the sales transactions and sales lines. |

For extension scenarios, you can override any of the requests in the service class. For example, to change the customer search flow, extend the **CustomersSearchServiceRequest** request from the **CustomerService** service.

> [!NOTE]
> You don't customize the service class. Instead, you extend the request/response in the service class. By itself, the service class doesn't have any logic. It just routes the call to the correct request.

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


## How to execute the base handler in extension

### NotHandledResponse()

If the overridden logic executes the base handler for some scenarios, this can achieved by returning **NotHandledResponse().** If the NotHandledResponse is returned, the CRT framework will use the extension that is requesting to execute the base or out of band logic, so the CRT framework will execute the out of band handler.

**NotHandledResponse** can be used in scenarios where the extension executes the base handler logic. For example, if the overridden request executes the base handler logic then it can return the NotHandledResponse for the base handler to execute. Or if the extension executes custom logic and base logic, then the extension code can return NotHandledResponse after executing the custom logic.

```C#
  private Response GetCustomReceiptFieldForSalesTransactionReceipts(GetLocalizationCustomReceiptFieldServiceRequest request)
        {
            ThrowIf.Null(request.SalesOrder, nameof(request.SalesOrder));

            string receiptFieldName = request.CustomReceiptField;
            string receiptFieldValue = string.Empty;

            if (request.SalesOrder.TaxCalculationType == TaxCalculationType.GTE)
            {
                switch (receiptFieldName)
                {
                    case "Sample":
                        receiptFieldValue = this.GetGstRegistrationNumber(request);
                        break;
                    default:
                        return new NotHandledResponse();
                }
            }
            else
            {
                return new NotHandledResponse();
            }

            int receiptFieldLength = request.ReceiptItemInfo == null ? 0 : request.ReceiptItemInfo.Length;
            var returnValue = ReceiptStringUtils.WrapString(receiptFieldValue, receiptFieldLength);

            return new GetCustomReceiptFieldServiceResponse(returnValue);
        }

```

## How to execute extension request for a channel type

If an extension request needs to be executed only for a certain channel type, such as execute the request for online channel not for the Retail channel (physical store), then before executing the request, check the channel type and execute the custom logic executed or execute the base logic by calling the NotHandledResponse().

```C#
if (requestContext.GetChannel().OrgUnitType == RetailChannelType.RetailStore)
{
    // run your extension code here.
}
else
{
    return new NotHandledResponse();
}
```

## Extension pattern for CRT

- **Create a new service class, and implement one or more requests/responses** – Use this approach to create a new feature.
- **Override the core request/response** – Use this approach to modify the standard workflow or business logic.
- **Add a pre-trigger or post-trigger for any request/response** – Use this approach to add business logic or add custom fields, and so on.

> [!NOTE]
> It doesn't matter whether you create a data access request, a workflow request, or a service request. Everything in CRT is a request/response. You write the logic that is required in the request/response. Although the requests are classified into different types for logical reasons, everything is the same from the framework perspective.

The following three classes will be implemented in all our requests/responses:

- **Request class** – This class is POS/Retail server/E-commerce/CRT workflow class that is the request to do something.
- **Response class** – This class returns the response, based on the request to the caller.
- **Handler class** – This class contains the core logic for the request. In the handler class, you can call other requests, do custom logic, and so on.

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
```

### Response class

```C#
public sealed class MyResponse : Response
{
    /// <summary>
    /// Initializes a new instance of the <see cref=" MyResponse"/> class.
    /// </summary>

    public MyResponse ()
    {
    }
}
```

### Handler class

```C#
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

The Address service supports the following requests/responses for various extension scenarios.

| Request                            | Purpose                                                                                         |
|------------------------------------|-------------------------------------------------------------------------------------------------|
| GetCountryRegionsServiceRequest    | This request gets the list of countries and regions that are supported.                         |
| GetStateProvincesServiceRequest    | This request gets the list of states or provinces that are supported for the country or region. |
| GetCitiesServiceRequest            | This request gets the list of cities that are supported for the state or region.                |
| GetDistrictServiceRequest          | This request gets the list of districts that are supported.                                     |
| GetZipCodesServiceRequest          | This request gets the list of ZIP Codes that are supported.                                     |
| GetFromZipPostalCodeServiceRequest | This request gets the list of postal codes supported.                                           |
| GetAddressFormattingServiceRequest | This request gets the address format for the specified country or region.                       |

### BarcodeService

| Request                                  | Purpose                                                                                          |
|------------------------------------------|--------------------------------------------------------------------------------------------------|
| ProcessMaskSegmentsServiceRequest        | This request processes the barcode, based on the barcode mask configuration.                     |
| GetBarcodeTypeServiceRequest             | This request gets the types of barcodes that are supported.                                      |
| CalculateQuantityFromPriceServiceRequest | This request calculates the price and quantity, based on the barcode that is scanned or entered. |

### CartService

| Request                                                     | Purpose                                                                                                    |
|-------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| GetSalesTransactionsServiceRequest                          | This request gets the sales transaction from Headquarters.                                          |
| GetCartServiceRequest                                       | This request gets the cart from the sales transaction table by using the cart ID.                          |
| CalculateSalesTransactionServiceRequest                     | This request calculates the various sales transaction totals, based on the specified calculation mode.     |
| CalculateEstimatedShippingAuthorizationAmountServiceRequest | This request calculates the estimated shipping authorization amount on the transaction.                    |
| ConvertSalesTransactionToCartServiceRequest                 | This request converts the sales transaction to a cart transaction, based on transaction ID that is passed. |

### CouponService

| Request                               | Purpose                                                                                                              |
|---------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| UpdateCouponCodesOnCartServiceRequest | This request updates the coupon codes status in Headquarters, based on the coupons that are used in the cart. |
| ValidateCouponCodesServiceRequest     | This request validates the coupon code that is entered in the transactions.                                          |
| UpdateCouponUsageServiceRequest       | This request updates coupon usage for the transaction.                                                               |

### CustomerService

| Request                                      | Purpose                                                                  |
|----------------------------------------------|--------------------------------------------------------------------------|
| SaveCustomerServiceRequest                   | This request is called when you save a customer from the POS.            |
| GetCustomersServiceRequest                   | This request gets the selected customer details.                         |
| CustomersSearchServiceRequest                | This request is run when you search for a customer from the POS.         |
| GetCustomerGroupsServiceRequest              | This request gets the customer group details.                            |
| InitiateLinkToExistingCustomerServiceRequest | This request is an internal request for backward compatibility.          |
| FinalizeLinkToExistingCustomerServiceRequest | This request is an internal request for backward compatibility.          |
| UnlinkFromExistingCustomerServiceRequest     | This request is an internal request for backward compatibility.          |
| GetCustomerBalanceServiceRequest             | This request gets the balance of the customer's account.                 |
| GetOrderHistoryServiceRequest                | This request gets the customer's order history.                          |
| GetPurchaseHistoryServiceRequest             | This request gets the history of the customer's recent purchases.        |
| CustomerSearchByFieldsServiceRequest         | This request is run when you search customer by using fields such as name, phone number etc. (hint search). |
| GetCustomerSearchFieldsServiceRequest        | This request gets the list of customer search fields (hint fields).      |

### PricingService

| Request                                   | Purpose                                                                                                               |
|-------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| CalculatePricesServiceRequest             | This request calculates the price for each item that is added to the cart and on the search screen.                   |
| CalculateDiscountsServiceRequest          | This request calculates the discount for each item that is added to the cart.                                         |
| GetIndependentPriceDiscountServiceRequest | This request calculates the price for each item on the price check screen and in other non-transaction-related flows. |
| ValidateDiscountsServiceRequest           | This request validates the discount that is entered, based on the employee.                                           |
| GetAllPeriodicDiscountsServiceRequest     | This request gets all the periodic discounts that are configured.                                                     |
| GetDiscountCodesServiceRequest            | This request gets all the discount codes that are configured.                                                         |

### ProductService

| Request                     | Purpose                                                                                                                                                                               |
|-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ProductSearchServiceRequest | This request gets the product list, based on the search text from the POS. (This is an old request. For customization, use the new **SearchProductsServiceRequest** request instead.) |
| GetProductServiceRequest    | This request gets the product, based on the product ID.                                                                                                                               |
| GetProductRefinersRequest   | This request retrieves the product refiner values.                                                                                                                                    |

### ProductsService

| Request                          | Purpose                                                                      |
|----------------------------------|------------------------------------------------------------------------------|
| GetProductsServiceRequest        | This request gets the products, based on the products IDs that are provided. |
| GetVariantProductsServiceRequest | This request gets specific variations of master type products.               |

### ReasonCodeService

| Request                                                             | Purpose                                                                                                     |
|---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| GetReasonCodesServiceRequest                                        | This request gets the required reason code for the workflow or POS operation.                               |
| CalculateRequiredReasonCodesServiceRequest                          | This request calculates the required reason code for the workflow or POS operation.                         |
| CalculateCartRequiredReasonCodesServiceRequest                      | This request calculates the required reason code for the cart workflow.                                     |
| CalculateDropAndDeclareTransactionRequiredReasonCodesServiceRequest | This request calculates the required reason code for the drop and tender declaration transaction.           |
| CalculateNonSalesTransactionRequiredReasonCodesServiceRequest       | This request calculates the required reason code for the non-sales transaction, such as tender declaration. |
| GetReturnOrderReasonCodesServiceRequest                             | This request gets the required reason code for the return transaction.                                      |
| ValidateReasonCodeLineForUpdateServiceRequest                       | This request validates the reason code lines that are added during the save cart request.                   |

### ReceiptService

| Request                               | Purpose                                                                                           |
|---------------------------------------|---------------------------------------------------------------------------------------------------|
| GetReceiptServiceRequest              | This request gets the receipt type and generates the receipt data, based on the receipt type.     |
| GetCustomReceiptFieldServiceRequest   | Override this request, and add custom logic for your custom fields that are added in the receipt. |
| GetEmailReceiptServiceRequest         | This request gets the formatted receipts that will be used for print and email scenarios.         |
| PopulateTaxSummaryIndiaServiceRequest | This request populates the tax summary for India transaction.                                     |

### SearchProductsService

| Request                      | Purpose                                                         |
|------------------------------|-----------------------------------------------------------------|
| SearchProductsServiceRequest | This request is run when you search for a product from the POS. |

### TaxService

| Request                      | Purpose                                                                                                                                                                                            |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CalculateTaxServiceRequest   | This request calculates taxes on the transaction.                                                                                                                                                  |
| AssignTaxCodesServiceRequest | This request assigns tax codes on the transaction's taxable items before the tax calculation. The default tax calculation handler of the **CalculateTaxServiceRequest** request uses this message. |
| PopulateTaxRatesRequest      | This request populates tax rates for the recalled transaction. No tax percentage information is persisted for tax lines. This message handler restores the information.                            |

## Workflow layer

On top of the Services layer is the Workflow layer. A workflow is a collection of services and business logic that together define business processes. For example, when a customer adds an item to the cart, you can use a workflow to get the price, do validation, check the inventory quantity, calculate shipping, calculate tax, and calculate discounts. You can customize the existing workflows, or you can create new workflows. You can even use a workflow to connect to a third-party system as part of your business processes.

Just like services, workflows use the request/response pattern. The request object inherited from the base CRT [Request](https://technet.microsoft.com/library/microsoft.dynamics.commerce.runtime.messages.request.aspx) class. The response object inherited from the base CRT [Response](https://technet.microsoft.com/library/microsoft.dynamics.commerce.runtime.messages.response.aspx) class. A workflow also has a request handler class that extends the [WorkflowRequestHandler<TRequest, TResponse>](https://technet.microsoft.com/library/jj764791.aspx) class. To create a workflow, you create a request class and a response class, and you then create a request handler class that contains the business logic for the workflow.

For example, when you create a cash-and-carry transaction or a customer order, many different steps or workflows are completed before the order is created. One of the workflow steps in the order process is the Save cart request. The Save cart request workflow is responsible for saving any changes that are made to the cart from the POS. For example, when you add an item to the cart, change the quantity, and so on, anything that you do in the POS will cause a call to the SaveCart to save the changes to the POS and database.

The following three classes will be implemented in the Save cart request workflow.

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
```

### Response class

```C#
public sealed class SaveCartResponse : Response
{
    /// <summary>
    /// Initializes a new instance of the <see cref="SaveCartResponse"/> class.
    /// </summary>

    public SaveCartResponse()
    {
    }
}
```

### Handler class

```C#
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

All your workflow classes will follow the same pattern.

### Default workflows and handlers

The following table lists the default workflow requests and response. CRT services call the workflows request and response based on the operation you perform in POS. You can customize any of these workflows request and response according to your business scenario. 

| Request                           | Handler                                 | Purpose                                                                                                                    |
|-----------------------------------|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| AddOrderInvoiceToCartRequest      | AddOrderInvoiceToCartRequestHandler     | This request adds the invoice to the cart as a cart line.                                                                  |
| AddOrRemoveDiscountCodesRequest   | AddOrRemoveDiscountCodesRequestHandler  | This request adds discount codes to the cart or removes them from the cart.                                                |
| CancelOrderRequest                | CancelOrderRequestHandler               | This request is triggered when you cancel an order from the POS.                                                           |
| CopyCartRequest                   | CopyCartRequestHandler                  | This request creates an identical shopping cart that has the specified cart type.                                          |
| GetAddressRequest                 | GetAddressRequestHandler                | This request gets the address from the list.                                                                               |
| GetCardPaymentAcceptPointRequest  | GetCardPaymentAcceptPointRequestHandler | This request shows the accepting page for card payment.                                                                     |
| GetCartRequest                    | GetCartRequestHandler                   | This request gets the shopping cart, based on the cart search criteria.                                                    |
| GetDiscountCodesRequest           | GetDiscountCodesRequestHandler          | This request gets the discount codes.                                                                                      |
| GetOrdersRequest                  | GetOrdersRequestHandler                 | This request gets sales orders.                                                                                            |
| GetPromotionsRequest              | GetPromotionsRequestHandler             | This request gets the shopping cart together with promotion lines for the cart and the cart items.                         |
| GetScanResultRequest              | GetScanResultRequestHandler             | This request gets the entity details, based on the details that are scanned or typed.                                      |
| GetSupportedCardTypesRequest      | GetSupportedCardTypesRequestHandler     | This request retrieves the cart types that are supported for the specified currency.                                       |
| IssueOrAddToGiftCardRequest       | IssueOrAddToGiftCardRequestHandler      | This request issues a gift card or adds to a gift card's balance.                                                          |
| PickAndPackOrderRequest           | PickAndPackOrderRequestHandler          | This request represents a request for picking list creation and packing slip creation for a customer order.                |
| PickupAtStoreRequest              | PickupAtStoreRequestHandler             | This request represents a request for pick-up at the store.                                                                |
| RecalculateOrderRequest           | RecalculateOrderRequestHandler          | This request represents a request for the recalculate order workflow.                                                      |
| RecallCustomerOrderRequest        | RecallCustomerOrderRequestHandler       | This request gets sales orders and converts them into a cart.                                                              |
| RecallSalesInvoiceRequest         | RecallSalesInvoiceRequestHandler        | This request gets invoices.                                                                                                |
| ResumeCartRequest                 | ResumeCartRequestHandler                | This request represents a request to resume a cart that was suspended.                                                     |
| SaveCartLinesRequest              | SaveCartLinesRequestHandler             | This request represents a request for create, update, delete, or void operations on the cart line.                         |
| SaveCartRequest                   | SaveCartRequestHandler                  | This request is triggered when you make any changes in that POS that affect the cart.                                      |
| SaveCustomerOrderRequest          | SaveCustomerOrderRequestHandler         | This request initiates a request to save the customer order, based on the specified cart identifier and payment card information. |
| SaveReasonCodeLineRequest         | SaveReasonCodeLineRequestHandler        | This request adds or updates a reason code on the cart line.                                                                           |
| SaveTenderLineRequest             | SaveTenderLineRequestHandler            | This request adds, removes, or updates a tender line for the given shopping cart.                                          |
| SaveVoidTransactionRequest        | SaveVoidTransactionRequestHandler       | This request voids a transaction.                                                                                          |
| SubmitSalesTransactionRequest     | SubmitOrderRequestHandler               | This request initiates a request to submit the sales transaction, based on the specified cart identifier.                         |
| SuspendCartRequest                | SuspendCartRequestHandler               | This request represents a request to suspend the cart.                                                                     |
| TransferCartRequest               | TransferCartRequestHandler              | This request transfers the specified shopping cart.                                                                        |
| UpdateCommissionSalesGroupRequest | UpdateCommissionSalesGroupHandler       | This request encapsulates a request for updating the sales representative on the cart or the cart line.                    |
| UploadOrderRequest                | UploadOrderRequestHandler               | This request uploads the sales order.                                                                                      |
| ValidateCartForCheckoutRequest    | ValidateCartForCheckoutRequestHandler   | This request validates the cart for checkout.                                                                              |
