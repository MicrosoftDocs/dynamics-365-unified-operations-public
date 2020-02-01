---
# required metadata

title: Point of sale (POS) APIs
description: This topic contains a list of available POS APIs and how to access them.
author: mugunthanm 
manager: AnnBe
ms.date: 11/19/2019
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
ms.search.validFrom: 2018-29-10
ms.dyn365.ops.version: AX 8.0, AX 8.1

---
# Point of sale (POS) APIs
[!include [banner](../includes/banner.md)]

Retail POS APIs help you to easily build extensions or new features to the POS app. For example, if you are extending the Retail POS application to add new features in which to want to get product details, change prices, or add items to a cart. you can consume APIs that will do the work for you. To do this, you need to simply call the APIs to do the work. The POS API simplifies the extension pattern and provides continuous support to build the extensions.

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
 
    ```Typescript
    import { SaveAttributesOnCartClientRequest, SaveAttributesOnCartClientResponse } from "PosApi/Consume/Cart";
    ```

2.  Import the client entities and proxy entities if required.

    ```Typescript
    import { ClientEntities } from "PosApi/Entities";

    import { ProxyEntities } from "PosApi/Entities";
    ```
3.  Declare the API variable and execute it using the POS runtime, which you can access the runtime by using: this.context.runtime.executeAsync("api name")

    ```Typescript
    executeAsync<TResponse extends Response>(request: Request<TResponse>): Promise<Client.Entities.ICancelableDataResult<TResponse>>;
    ```
    
    For example, if you want to execute the tender removal, use SaveAttributesOnCartClientRequest api, and refer to the following steps.
 
    ```Typescript
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
```
// Gets the current cart.

 let currentCart: ProxyEntities.Cart;

 return this.context.runtime.executeAsync<GetCurrentCartClientResponse>(new GetCurrentCartClientRequest())

 .then((getCurrentCartClientResponse: ClientEntities.ICancelableDataResult<GetCurrentCartClientResponse>):

 Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>> => {

currentCart = getCurrentCartClientResponse.data.result;

```
**Get Current customer added to cart**
```
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
```
 // Force void tarnsaction.
```Typescript
 let forceVoidTransactionRequest: VoidTransactionOperationRequest<VoidTransactionOperationResponse> =

 new VoidTransactionOperationRequest<VoidTransactionOperationResponse>(false, this.context.logger.getNewCorrelationId());

 this.context.runtime.executeAsync(forceVoidTransactionRequest).then((value: ICancelableDataResult<VoidTransactionOperationResponse>) => {

 this.currentCart(JSON.stringify(value.data.cart));

 }).catch((err: any) => {

 this.currentCart(JSON.stringify(err));

 });
```

### Cart

The following is a list of APIs exposed to perform cart-related functionality.

| POS API                                         |
|-------------------------------------------------|
| AddPreprocessedTenderLineToCartClientRequest    |
| AddTenderLineToCartClientRequest                |
| ConcludeTransactionClientRequest                |
| GetCurrentCartClientRequest                     |
| GetCurrentCartClientResponse                    |
| GetKeyedInPriceClientRequest                    |
| GetPickupDateClientRequest                      |
| GetReasonCodeLinesClientRequest                 |
| GetReceiptEmailAddressClientRequest             |
| GetShippingDateClientRequest                    |
| RefreshCartClientRequest                        |
| ResumeSuspendedCartClientRequest                |
| SaveAttributesOnCartClientRequest               |
| SaveAttributesOnCartLinesClientRequest          |
| SaveExtensionPropertiesOnCartClientRequest      |
| SaveExtensionPropertiesOnCartLinesClientRequest |
| SaveReasonCodeLinesOnCartClientRequest          |
| SaveReasonCodeLinesOnCartLinesClientRequest     |
| SelectSalesLinesForPickUpClientRequest          |
| SetCartAttributesClientRequest                  |
| ShowChangeDueClientRequest                      |
| AddAffiliationOperationRequest                  |
| AddItemToCartOperationRequest                   |
| CalculateTotalOperationRequest                  |
| ChangeCartLineUnitOfMeasureOperationRequest     |
| CreateCustomerOrderOperationRequest             |
| CreateCustomerQuoteOperationRequest             |
| CustomerAccountDepositOperationRequest          |
| DepositOverrideOperationRequest                 |
| EditCustomerOrderOperationRequest               |
| LineDiscountAmountOperationRequest              |
| LineDiscountPercentOperationRequest             |
| OverrideLineTaxFromListOperationRequest         |
| OverrideLineTaxOperationRequest                 |
| OverrideTransactionTaxOperationRequest          |
| PickupAllOperationRequest                       |
| PriceOverrideOperationRequest                   |
| SetCartLineCommentOperationRequest              |
| SetCartLineQuantityOperationRequest             |
| SetCustomerOnCartOperationRequest               |
| SetTransactionCommentOperationRequest           |
| SuspendCurrentCartOperationRequest              |
| TotalDiscountAmountOperationRequest             |
| TotalDiscountPercentOperationRequest            |
| VoidCartLineOperationRequest                    |
| VoidTenderLineOperationRequest                  |
| VoidTransactionOperationRequest                 |
| CreateEmptyCartServiceRequest                   |
| GetTaxOverridesServiceRequest                   |
| UpdateTenderLineSignatureServiceRequest         |
| CarryoutSelectedProductsOperationRequest |
| AddCouponsOperationRequest |
| CreateNonSalesTransactionServiceRequest |
| ReturnTransactionOperationRequest |
| AddLoyaltyCardToCartOperationRequest |
| ReturnCartLineOperationRequest |
| ReturnItemOperationRequest |


### Payments

The following is a list of APIs exposed to perform payment-related functionality.

| POS API                                   |
|-------------------------------------------|
| GetGiftCardByIdServiceRequest             |
| GetPaymentCardTypeByBinRangeClientRequest |

### Peripherals

The following is a list of APIs exposed to perform peripheral-related functionality.

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
| PrinterPrintRequest                                    |
| ScaleReadRequest                                       |

### ScanResults

The following is a list of APIs exposed to perform scan results-related functionality.

| POS API                    |
|----------------------------|
| GetScanResultClientRequest |

### Customer

The following is a list of APIs exposed to perform customer-related functionality.

| POS API                  |
|--------------------------|
| GetCustomerClientRequest |
|CreateCustomerServiceRequest |
|UpdateCustomerServiceRequest |
|SelectCustomerClientRequest |


### Authentication

The following is a list of APIs exposed to perform authentication-related functionality.

| POS API                |
|------------------------|
| LogOffOperationRequest |

### DataService

The following is a list of APIs exposed to perform data service-related functionality.

| POS API            |
|--------------------|
| DataServiceRequest |

### Device

The following is a list of APIs exposed to perform device-related functionality.

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

The following is a list of APIs exposed to perform diagnostics-related functionality.

| POS API                     |
|-----------------------------|
| GetSessionInfoClientRequest |

### Dialog

The following is a list of APIs exposed to perform dialog-related functionality.

| POS API                                  |
|------------------------------------------|
| ShowMessageDialogClientRequest           |
| IAlphanumericInputDialogResult           |
| ShowAlphanumericInputDialogClientRequest |
| ShowNumericInputDialogClientRequest      |
| ShowListInputDialogClientRequest         |
| ShowTextInputDialogClientRequest         |

### Employee

The following is a list of APIs exposed to perform employee-related functionality.

| POS API                          |
|----------------------------------|
| GetLoggedOnEmployeeClientRequest |

### Formatters

The following is a list of APIs exposed to perform formatter-related functionality.

| POS API                             |
|-------------------------------------|
| IBooleanFormatter                   |
| ICurrencyFormatter                  |
| IDateFormatter                      |
| ITransactionTypeFormatter           |
| IPurchaseTransferOrderTypeFormatter |

### OrgUnits

The following is a list of APIs exposed to perform org units-related functionality.

| POS API                              |
|--------------------------------------|
| GetOrgUnitConfigurationClientRequest |
| GetOrgUnitTenderTypesClientRequest   |
| InventoryLookupOperationRequest      |

### Products

The following is a list of APIs exposed to perform products-related functionality.

| POS API                                    |
|--------------------------------------------|
| GetProductsByIdsClientRequest              |
| GetCurrentProductCatalogStoreClientRequest |
| SelectProductVariantClientRequest          |
| GetSerialNumberClientRequest               |
| GetRefinerValuesByTextServiceRequest       |
| SelectProductClientRequest |

### SalesOrders

The following is a list of APIs exposed to perform sales orders-related functionality.

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

The following is a list of APIs exposed to perform shifts-related functionality.

| POS API                    |
|----------------------------|
| CloseShiftOperationRequest |
| CloseShiftOperationRequest |

### StockCountJournals

The following is a list of APIs exposed to perform stock count journals-related functionality.

| POS API                                |
|----------------------------------------|
| SyncAllStockCountJournalsClientRequest |

### StoreOperations

The following is a list of APIs exposed to perform store operations-related functionality.

| POS API                                         |
|-------------------------------------------------|
| DeclareStartingAmountClientRequest              |
| GetSalesOrdersWithNoFiscalTransactionsRequest   |
| RegisterCustomAuditEventClientRequest           |
| GetOfflinePendingTransactionCountClientRequest  |
| SaveFiscalTransactionClientRequest              |
| SafeDropOperationRequest                        |
| TenderDeclarationOperationRequest               |
| TenderRemovalOperationRequest                   |
| CreateBankDropTransactionClientRequest          |
| CreateFloatEntryTransactionClientRequest        |
| CreateStartingAmountTransactionClientRequest    |
| CreateTenderDeclarationTransactionClientRequest |
| CreateTenderRemovalTransactionClientRequest     |
| GetDenominationTotalsClientRequest              |
| SelectZipCodeInfoClientRequest                  |
| CreateSafeDropTransactionClientRequest          |
| GetTenderDetailsClientRequest                   |
| LoyaltyCardPointsBalanceOperationRequest        |
| GetCommissionSalesGroupsServiceRequest          |
| GetCurrenciesServiceRequest                     |
| GetSrsReportDataSetServiceRequest               |
| SearchCommissionSalesGroupsServiceRequest       |
| IssueLoyaltyCardOperationRequest                |
| GetPickingAndReceivingOrdersClientRequest       |


