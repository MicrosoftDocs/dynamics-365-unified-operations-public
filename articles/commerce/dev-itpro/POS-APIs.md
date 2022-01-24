---
# required metadata

title: Point of sale (POS) APIs
description: This topic contains a list of available POS APIs and how to access them.
author: mugunthanm 
ms.date: 11/03/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2018-10-29
ms.dyn365.ops.version: AX 8.0, AX 8.1

---
# Point of sale (POS) APIs
[!include [banner](../includes/banner.md)]

Retail POS APIs help you to easily build extensions or new features to the POS app. For example, if you are extending the Retail POS application to add new features in which to want to get product details, change prices, or add items to a cart. you can consume APIs that will do the work for you. To do this, you need to call the APIs to do the work. The POS API simplifies the extension pattern and provides continuous support to build the extensions.

Extension patterns have been unified across commerce runtime (CRT), POS, and Hardware station (HWS) by following the request/response pattern. All the POS APIs are exposed as request/response like CRT and HWS. 

POS APIs are categorized into three different scenarios:

- **Consume** – Consume public APIs in your extension.

- **Extend** – Override public APIs to do some additional logic.

- **Create** – Create new APIs using the exposed POS interface, which can be used across extensions.

Many APIs can be consumed in extensions. For example, if you want to change the price of the item based on an external web service call, you can call PriceOverrideOperationRequest to change the price of the item. Within the consume, the APIs are sub categorized by module like cart, peripherals, store operations, etc.

> [!NOTE]
> A list of the all of the APIs is available in **Pos.Api.d.ts**, which is part of the Retail SDK (...Retail SDK\POS\Extensions\Pos.Api.d.ts). Extensions must consume only the exposed request and response from the POS.Api.d.ts and no modification is allowed to Pos.Api.d.ts. Extensions should not consume or update any POS APIs, properties, methods, or handlers directly from POS commerce or sessions objects. 

## How to consume APIs in your extension

Use the following steps to consume Retail APIs in your extensions.

1.  Import the API in your extension file.

    For example, if you want to consume the save attribute on cart API in your extension, then you need to add the following import statements.

    The pattern is import { api name } from "PosApi/Consume/Module name";
 
    ```typescript
    import { SaveAttributesOnCartClientRequest, SaveAttributesOnCartClientResponse } from "PosApi/Consume/Cart";
    ```

2.  Import the client entities and proxy entities if necessary.

    ```typescript
    import { ClientEntities } from "PosApi/Entities";

    import { ProxyEntities } from "PosApi/Entities";
    ```
3.  Declare the API variable and execute it using the POS runtime, which you can access the runtime by using: this.context.runtime.executeAsync("api name")

    ```typescript
    executeAsync<TResponse extends Response>(request: Request<TResponse>): Promise<Client.Entities.ICancelableDataResult<TResponse>>;
    ```
    
    For example, if you want to execute the tender removal, use SaveAttributesOnCartClientRequest api, and refer to the following steps.
 
    ```typescript
    let attributeValue: ProxyEntities.AttributeTextValue = new ProxyEntities.AttributeTextValueClass();

     attributeValue.Name = PreEndTransactionTrigger.B2B_CART_ATTRIBUTE_NAME;

     attributeValue.TextValue = "Yes";

     let attributeValues: ProxyEntities.AttributeValueBase[] = [attributeValue];

     let saveAttributesOnCartRequest: SaveAttributesOnCartClientRequest<SaveAttributesOnCartClientResponse> =

    new SaveAttributesOnCartClientRequest(attributeValues);

    result = this.context.runtime.executeAsync(saveAttributesOnCartRequest);
    ```

### Samples showing how to access APIs

**Get Current cart**
```typescript
// Gets the current cart.

 let currentCart: ProxyEntities.Cart;

 return this.context.runtime.executeAsync<GetCurrentCartClientResponse>(new GetCurrentCartClientRequest())

 .then((getCurrentCartClientResponse: ClientEntities.ICancelableDataResult<GetCurrentCartClientResponse>):

 Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>> => {

currentCart = getCurrentCartClientResponse.data.result;

```

**Get Current customer added to cart**
```typescript
 // Gets the current customer.

 let result: Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>>;

 if (!ObjectExtensions.isNullOrUndefined(currentCart) && !ObjectExtensions.isNullOrUndefined(currentCart.CustomerId)) {

 let getCurrentCustomerClientRequest: GetCustomerClientRequest<GetCustomerClientResponse> =

 new GetCustomerClientRequest(currentCart.CustomerId);

 result = this.context.runtime.executeAsync<GetCustomerClientResponse>(getCurrentCustomerClientRequest);

 } else {

 result = Promise.resolve({ canceled: true, data: new GetCustomerClientResponse(null) });

}
```

**Force void transaction**
```typescript
 // Force void tarnsaction.
 let forceVoidTransactionRequest: VoidTransactionOperationRequest<VoidTransactionOperationResponse> =

 new VoidTransactionOperationRequest<VoidTransactionOperationResponse>(false, this.context.logger.getNewCorrelationId());

 this.context.runtime.executeAsync(forceVoidTransactionRequest).then((value: ICancelableDataResult<VoidTransactionOperationResponse>) => {

 this.currentCart(JSON.stringify(value.data.cart));

 }).catch((err: any) => {

 this.currentCart(JSON.stringify(err));

 });
```

### Cart

The following table lists APIs exposed to perform cart-related functionality.

| POS API                                   | Description                            | Release                  |
|-------------------------------------------|----------------------------------------|--------------------------|
| AddPreprocessedTenderLineToCartClientRequest    | Adds the pre-processed tender line to the cart.   | 10.0.14  |
| AddTenderLineToCartClientRequest                | Adds the tender line to the cart.  | 10.0.14  |
| ConcludeTransactionClientRequest                | Concludes the transaction.    | 10.0.14  |
| GetCurrentCartClientRequest                     | Gets the current cart.   | 10.0.14  |
| GetKeyedInPriceClientRequest                    |  Gets the keyed in price.                                      | 10.0.14  |
| GetPickupDateClientRequest                      |  Gets the pickup date.                                      | 10.0.14  |
| GetReasonCodeLinesClientRequest                 |  Gets the reason code.                                      | 10.0.14  |
| GetReceiptEmailAddressClientRequest             |  Gets the receipt email address.                                     | 10.0.14  |
| GetShippingDateClientRequest                    |  Gets the shipping date.                                      | 10.0.14  |
| RefreshCartClientRequest                        |  Refresh the current cart with the cart data from the server.                                      | 10.0.14  |
| ResumeSuspendedCartClientRequest                | Resumes the suspended transaction based on the ID passed.                                       | 10.0.14  |
| SaveAttributesOnCartClientRequest               | Saves the attributes on the cart.                                       | 10.0.14  |
| SaveAttributesOnCartLinesClientRequest          | Saves the attributes on the cart line.                                       | 10.0.14  |
| SaveExtensionPropertiesOnCartClientRequest      | Saves the extension properties on the cart.                                        | 10.0.14  |
| SaveExtensionPropertiesOnCartLinesClientRequest | Saves the extension properties on the cart line.                                       | 10.0.14  |
| SaveReasonCodeLinesOnCartClientRequest          | Saves the reason code lines on the cart.                                       | 10.0.14  |
| SaveReasonCodeLinesOnCartLinesClientRequest     |  Saves the reason code lines on the cart line.                                      | 10.0.14  |
| SelectSalesLinesForPickUpClientRequest          |  Select the sales lines for pickup.                                      | 10.0.14  |
| SetCartAttributesClientRequest                  |   Sets the cart attribute.                                     | 10.0.14  |
| ShowChangeDueClientRequest                      |  Shows the change due dialog.                                      | 10.0.14  |
| AddAffiliationOperationRequest                  |  Adds affiliation to the cart.                                      | 10.0.14  |
| AddItemToCartOperationRequest                   |  Add items to the cart.                                      | 10.0.14  |
| CalculateTotalOperationRequest                  |  Calculate the total for the cart.                                      | 10.0.14  |
| ChangeCartLineUnitOfMeasureOperationRequest     |  Changes the cart line unit of measure.                                      | 10.0.14  |
| CreateCustomerOrderOperationRequest             |   Creates the customer order.                                     | 10.0.14  |
| CreateCustomerQuoteOperationRequest             |   Creates the customer quote.                                     | 10.0.14  |
| CustomerAccountDepositOperationRequest          |                                        | 10.0.14  |
| DepositOverrideOperationRequest                 |  Overrides the deposit amount.                                      | 10.0.14  |
| EditCustomerOrderOperationRequest               |   Edit the customer order.                                     | 10.0.14  |
| LineDiscountAmountOperationRequest              |  Add line discount amount to the cart line.                                      | 10.0.14  |
| LineDiscountPercentOperationRequest             |  Add line discount percent to the cart line.                                      | 10.0.14  |
| OverrideLineTaxFromListOperationRequest         |  Override the cart line tax from the list.                                      | 10.0.14  |
| OverrideLineTaxOperationRequest                 |   Override the cart line tax.                                     | 10.0.14  |
| OverrideTransactionTaxOperationRequest          |    Override the transaction tax.                                       | 10.0.14  |
| PickupAllOperationRequest                       |   Picks up the order.                                     | 10.0.14  |
| PriceOverrideOperationRequest                   | Override the price for the cart line.                                       | 10.0.14  |
| SetCartLineCommentOperationRequest              |  Sets the cart line comment.                                      | 10.0.14  |
| SetCartLineQuantityOperationRequest             |   Sets the cart line quantity.                                     | 10.0.14  |
| SetCustomerOnCartOperationRequest               |   Sets the customer on the cart.                                     | 10.0.14  |
| SetTransactionCommentOperationRequest           |   Sets the transaction comment.                                     | 10.0.14  |
| SuspendCurrentCartOperationRequest              | Suspends the current transaction.                                       | 10.0.14  |
| TotalDiscountAmountOperationRequest             |   Add total discount amount to the transaction.                                     | 10.0.14  |
| TotalDiscountPercentOperationRequest            |  Add total discount percent to the transaction.                                         | 10.0.14  |
| VoidCartLineOperationRequest                    |  Voids the cart line.                                      | 10.0.14  |
| VoidTenderLineOperationRequest                  | Voids the tender line.                                       | 10.0.14  |
| VoidTransactionOperationRequest                 |  Voids the transaction.                                      | 10.0.14  |
| CreateEmptyCartServiceRequest                   |  Creates empty cart.                                      | 10.0.14  |
| GetTaxOverridesServiceRequest                   |  Gets the tax override list.                                      | 10.0.14  |
| UpdateTenderLineSignatureServiceRequest         |  Updates the tender line signature data.                                      | 10.0.14  |
| CarryoutSelectedProductsOperationRequest |   Marks the selected line as carry out.                                            | 10.0.14  |
| AddCouponsOperationRequest |    Add coupon to the transaction.                                                         | 10.0.14  |
| CreateNonSalesTransactionServiceRequest | Create non sales transaction cart.                                               | 10.0.14  |
| ReturnTransactionOperationRequest |  Returns the transaction.                                                    | 10.0.14  |
| AddLoyaltyCardToCartOperationRequest | Adds loyalty card to the transaction.                                                  | 10.0.14  |
| ReturnCartLineOperationRequest |   Returns the cart line.                                                      | 10.0.14  |
| ReturnItemOperationRequest |  Returns the item.                                                           | 10.0.14  |
| AddExpenseAccountLineToCartOperationRequest | Add expense account line to the cart.                                           | 10.0.14  |
| ShipAllCartLinesOperationRequest |   Ships all the cart lines.                                                    | 10.0.14  |
| ShipSelectedCartLinesOperationRequest |    Ships the selected cart line.                                              | 10.0.14  |
|PickupSelectedOperationRequest | Marks the included lines for pickup                      |  10.0.16 |


### Payments

The following table lists APIs exposed to perform payment-related functionality.

| POS API                                   | Description                            | Release                  |
|-------------------------------------------|----------------------------------------|--------------------------|
| GetGiftCardByIdServiceRequest             | Gets the gift card ID.     |   10.0.12   |
| GetPaymentCardTypeByBinRangeClientRequest | Get the card type bin range.  |  10.0.12     |
| GetSignatureClientRequest                 | Shows the signature capture dialog in POS or sends the message to the signature capture device based on the configuration. | 10.0.15 |

### Peripherals

The following table lists APIs exposed to perform peripheral-related functionality.

| POS API                                                |
|--------------------------------------------------------|
| CardPaymentAuthorizePaymentRequest                     |
| CardPaymentBeginTransactionRequest                     |
| CardPaymentCapturePaymentRequest                       |
| CardPaymentEndTransactionRequest                       |
| CardPaymentEnquireGiftCardBalancePeripheralRequest     |
| CardPaymentExecuteTaskRequest                          |
| CardPaymentRefundPaymentRequest                        |
| CardPaymentVoidPaymentRequest                          |
| CardPaymentAuthorizeCardTokenPeripheralRequest                          |
| CashDrawerIsOpenRequest                                |
| HardwareStationDeviceActionRequest                     |
| HardwareStationStatusRequest                           |
| LineDisplayDisplayLinesRequest                         |
| PaymentTerminalAuthorizePaymentActivityRequest         |
| PaymentTerminalAuthorizePaymentRequest                 |
| PaymentTerminalBeginTransactionRequest                 |
| PaymentTerminalCancelOperationRequest                  |
| PaymentTerminalCapturePaymentRequest                   |
| PaymentTerminalEndTransactionRequest                   |
| PaymentTerminalEnquireGiftCardBalancePeripheralRequest |
| PaymentTerminalExecuteTaskRequest                      |
| PaymentTerminalRefundPaymentActivityRequest            |
| PaymentTerminalRefundPaymentRequest                    |
| PaymentTerminalUpdateLinesRequest                      |
| PaymentTerminalVoidPaymentRequest                      |
| PaymentTerminalFetchTokenPeripheralRequest             |
| PrinterPrintRequest                                    |
| ScaleReadRequest                                       |

### ScanResults

The following table lists APIs exposed to perform scan results-related functionality.

| POS API                    |
|----------------------------|
| GetScanResultClientRequest |

### Customer

The following table lists APIs exposed to perform customer-related functionality.

| POS API                  |
|--------------------------|
| GetCustomerClientRequest |
|CreateCustomerServiceRequest |
|UpdateCustomerServiceRequest |
|SelectCustomerClientRequest |


### Authentication

The following table lists APIs exposed to perform authentication-related functionality.

| POS API                |
|------------------------|
| LogOffOperationRequest |
| LockRegisterOperationRequest |

### DataService

The following table lists APIs exposed to perform data service-related functionality.

| POS API            |
|--------------------|
| DataServiceRequest |

### Device

The following table lists APIs exposed to perform device-related functionality.

| POS API                               |
|---------------------------------------|
| GetDeviceConfigurationClientRequest   |
| GetExtensionProfileClientRequest      |
| GetHardwareProfileClientRequest       |
| GetAuthenticationTokenClientRequest   |
| GetConnectionStatusClientRequest      |
| GetActiveHardwareStationClientRequest |
| GetApplicationVersionClientRequest    |
| GetChannelConfigurationClientRequest  |

### Diagnostics 

The following table lists APIs exposed to perform diagnostics-related functionality.

| POS API                     |
|-----------------------------|
| GetSessionInfoClientRequest |

### Dialog

The following table lists APIs exposed to perform dialog-related functionality.

| POS API                                  |
|------------------------------------------|
| ShowMessageDialogClientRequest           |
| IAlphanumericInputDialogResult           |
| ShowAlphanumericInputDialogClientRequest |
| ShowNumericInputDialogClientRequest      |
| ShowListInputDialogClientRequest         |
| ShowTextInputDialogClientRequest         |

### Employee

The following table lists APIs exposed to perform employee-related functionality.

| POS API                                   | Description                            | Release                  |
|-------------------------------------------|----------------------------------------|--------------------------|
| GetLoggedOnEmployeeClientRequest |  Gets the current logged in POS employee details.      | 10.0.14      |
| SelectStoreEmployeeClientRequest | Gets the current store employee list for selection. | 10.0.16 |

### Formatters

The following table lists APIs exposed to perform formatter-related functionality.

| POS API                             |
|-------------------------------------|
| IBooleanFormatter                   |
| ICurrencyFormatter                  |
| IDateFormatter                      |
| ITransactionTypeFormatter           |
| IPurchaseTransferOrderTypeFormatter |

### OrgUnits

The following table lists APIs exposed to perform org units-related functionality.

| POS API                              |
|--------------------------------------|
| GetOrgUnitConfigurationClientRequest |
| GetOrgUnitTenderTypesClientRequest   |
| InventoryLookupOperationRequest      |

### Products

The following table lists APIs exposed to perform products-related functionality.

| POS API                                    |
|--------------------------------------------|
| GetProductsByIdsClientRequest              |
| GetCurrentProductCatalogStoreClientRequest |
| SelectProductVariantClientRequest          |
| GetSerialNumberClientRequest               |
| GetRefinerValuesByTextServiceRequest       |
| SelectProductClientRequest |
| SelectProductVariantClientRequest |
| GetActivePricesServiceRequest |

### Categories

The following table lists APIs exposed to perform categories-related functionality.

| POS API                                    |
|--------------------------------------------|
| GetCategoriesServiceRequest              |


### SalesOrders

The following table lists APIs exposed to perform sales orders-related functionality.

| POS API                                          |
|--------------------------------------------------|
| GetReceiptsClientRequest                         |
| RegisterPrintReceiptCopyEventRequest             |
| GetSalesOrderDetailsByTransactionIdClientRequest |
| GetGiftReceiptsClientRequest                     |
| RegisterPrintReceiptCopyEventRequest             |
| MarkAsPickedServiceRequest                       |
| PrintPackingSlipClientRequest                    |
| PickUpCustomerOrderLinesClientRequest            |


### Shifts

The following table lists APIs exposed to perform shifts-related functionality.

| POS API                    |
|----------------------------|
| CloseShiftOperationRequest |
| CloseShiftOperationRequest |

### StockCountJournals

The following table lists APIs exposed to perform stock count journals-related functionality.

| POS API                                |
|----------------------------------------|
| SyncAllStockCountJournalsClientRequest |

### StoreOperations

The following table lists APIs exposed to perform store operations-related functionality.

| POS API                                   | Description                            | Release                  |
|-------------------------------------------|----------------------------------------|--------------------------|
| DeclareStartingAmountClientRequest              | Declare start amount using this request. | 10.0.14        |
| GetSalesOrdersWithNoFiscalTransactionsRequest   | Gets sales order with no fiscal transaction request.  |   10.0.14        |
| RegisterCustomAuditEventClientRequest           | Register custom audit event request.   |  10.0.14        |
| GetOfflinePendingTransactionCountClientRequest  | Gets the offline pending transaction count.  | 10.0.14        |
| SaveFiscalTransactionClientRequest              | Save fiscal transaction request.   |   10.0.14        |
| SafeDropOperationRequest                        | Safe drop operation request.  |  10.0.14        |
| TenderDeclarationOperationRequest               | Tender declaration operation request.      |   10.0.14        |
| TenderRemovalOperationRequest                   | Tender removal operation request.  |  10.0.14        |
| CreateBankDropTransactionClientRequest          | Bank drop transaction request.    | 10.0.14        |
| CreateFloatEntryTransactionClientRequest        | Float entry transaction request. |  10.0.14        |
| CreateStartingAmountTransactionClientRequest    | Create start amount transaction request.       |   10.0.14        |
| CreateTenderDeclarationTransactionClientRequest | Create tender declaration transaction request.     |   10.0.14        |
| CreateTenderRemovalTransactionClientRequest     | Remove tender declaration transaction request.       |  10.0.14        |
| GetDenominationTotalsClientRequest              | Gets the denomination total request.        | 10.0.14        |
| SelectZipCodeInfoClientRequest                  | Selects the Zip code information request.    | 10.0.14        |
| CreateSafeDropTransactionClientRequest          | Create safe drop transaction request.                                       |  10.0.14        |
| GetTenderDetailsClientRequest                   | Gets the tender details.    | 10.0.14        |
| LoyaltyCardPointsBalanceOperationRequest        | Gets the loyalty card balance.  | 10.0.14        |
| GetCommissionSalesGroupsServiceRequest          | Gets the commission sales group.  |  10.0.14        |
| GetCurrenciesServiceRequest                     | Gets the store currencies. | 10.0.14        |
| GetSrsReportDataSetServiceRequest               | Gets the Srs report data.  |  10.0.14        |
| SearchCommissionSalesGroupsServiceRequest       |  Search commission sales groups request.   | 10.0.14        |
| IssueLoyaltyCardOperationRequest                |  Issues loyalty card.  |  10.0.14        |
| GetPickingAndReceivingOrdersClientRequest       |  Gets the picking and receiving orders list.  |    10.0.14        |
| BankDropOperationRequest                 |  Bank drop request.   |        10.0.14        |
| DeclareStartAmountOperationRequest        |   Declare start amount request.       |          10.0.14        |
| GetAllDiscountsServiceRequest        | Gets the discount applicable for the current cart.  | 10.0.16 |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]