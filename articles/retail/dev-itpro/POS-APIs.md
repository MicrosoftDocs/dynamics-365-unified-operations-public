---
# required metadata

title: POS API
description: This topic describes the list of POS APIs available and how to access them.
author: mugunthanm 
manager: AnnBe
ms.date: 10/29/2018
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
ms.search.validFrom: 2018-29-10
ms.dyn365.ops.version: AX 8.0, AX 8.1

---
# Retail POS API

Retail POS API helps you to build extensions or new features to the POS app easily. Ex: If you are extending Retail POS application to add new feature in which to want to get product details or change price or add item to cart in many such scenarios you can consume our APIs which will do the work for you, simply call our APIs to do the work. The POS API simplifies the extension pattern and provide continuous support to build the extensions.

We unified our extension patterns across commerce runtime (CRT), POS and Hardware station (HWS) by following the request/response pattern. All the POS APIs are exposed as request/response like CRT and HWS. This topic is applicable for Dynamics 365 for Finance and Operations or Dynamics 365 for Retail with the latest hotfix. 

**The POS APIs are categorized into three different scenarios:**

1.  **Consume** – Consume our public APIs in your extension.

2.  **Extend** – Override our public APIs to do some additional logic.

3.  **Create** – Create your new APIs using the POS interface exposed which can be used across your extensions.

**Consume:**

We exposed lot of APIs to be consumed in extensions. Ex: You have scenario where want to change the price of the item based on an external web service call, in that case you can call our PriceOverrideOperationRequest API to change the price of the item. Within the consume, the APIs are sub categorized by module like Crat, peripherals, store operations etc.

**Note:** You can get all the API list from the **Pos.Api.d.ts** which is part of the Retail SDK (…Retail SDK\POS\Extensions\Pos.Api.d.ts)

**How to consume our APIs in your extension:**

If you want to consume our APIs in your extension, then follow the below steps:

1.  Import the API in your extension file:

    Ex: If you want to consume our save attribute on cart API in your extension then you need to add the below import statements:

 The pattern is import { api name } from "PosApi/Consume/Module name";
```Typescript
 import { SaveAttributesOnCartClientRequest, SaveAttributesOnCartClientResponse } from "PosApi/Consume/Cart";
```

2.  Import the client entities and proxy entities if required:

```Typescript
    import { ClientEntities } from "PosApi/Entities";

    import { ProxyEntities } from "PosApi/Entities";
```
3.  Declare the API variable and execute it using the pos runtime, you can access the runtime by using: this.context.runtime.executeAsync("api name")

```Typescript
    executeAsync<TResponse extends Response>(request: Request<TResponse>): Promise<Client.Entities.ICancelableDataResult<TResponse>>;
```

 Ex: If you want to execute the tender removal, SaveAttributesOnCartClientRequest api, follow the below steps:
```Typescript
let attributeValue: ProxyEntities.AttributeTextValue = new ProxyEntities.AttributeTextValueClass();

 attributeValue.Name = PreEndTransactionTrigger.B2B_CART_ATTRIBUTE_NAME;

 attributeValue.TextValue = "Yes";

 let attributeValues: ProxyEntities.AttributeValueBase[] = [attributeValue];

 let saveAttributesOnCartRequest: SaveAttributesOnCartClientRequest<SaveAttributesOnCartClientResponse> =

new SaveAttributesOnCartClientRequest(attributeValues);

result = this.context.runtime.executeAsync(saveAttributesOnCartRequest);

**More samples on how to access our APIs:**

**Get Current cart:**

// Gets the current cart.

 let currentCart: ProxyEntities.Cart;

 return this.context.runtime.executeAsync<GetCurrentCartClientResponse>(new GetCurrentCartClientRequest())

 .then((getCurrentCartClientResponse: ClientEntities.ICancelableDataResult<GetCurrentCartClientResponse>):

 Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>> => {

currentCart = getCurrentCartClientResponse.data.result;

**Get Current customer added to cart:**

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
**Force void transaction:**

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
Below is the list of APIs currently exposed by module, we will be adding more APIs to simplify the development experience.

**Cart:**

Below is the list of APIs exposed to perform cart related functionality:

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

**Payments:**

Below is the list of APIs exposed to perform peripheral related functionality:

| POS API                                   |
|-------------------------------------------|
| GetGiftCardByIdServiceRequest             |
| GetPaymentCardTypeByBinRangeClientRequest |

**Peripherals:**

Below is the list of APIs exposed to perform peripheral related functionality:

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

**ScanResults:**

Below is the list of APIs exposed to perform scan results related functionality:

| POS API                    |
|----------------------------|
| GetScanResultClientRequest |

**Customer:**

Below is the list of APIs exposed to perform Customer related functionality:

| POS API                  |
|--------------------------|
| GetCustomerClientRequest |
|CreateCustomerServiceRequest |
|UpdateCustomerServiceRequest |


**Authentication:**

Below is the list of APIs exposed to perform authentication related functionality:

| POS API                |
|------------------------|
| LogOffOperationRequest |

**DataService:**

Below is the list of APIs exposed to perform data service related functionality:

| POS API            |
|--------------------|
| DataServiceRequest |

**Device:**

Below is the list of APIs exposed to perform Device related functionality:

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

**Diagnostics:**

Below is the list of APIs exposed to perform Diagnostics related functionality:

| POS API                     |
|-----------------------------|
| GetSessionInfoClientRequest |

**Dialogs:**

Below is the list of APIs exposed to perform dialogs related functionality:

| POS API                                  |
|------------------------------------------|
| ShowMessageDialogClientRequest           |
| IAlphanumericInputDialogResult           |
| ShowAlphanumericInputDialogClientRequest |
| ShowNumericInputDialogClientRequest      |
| ShowListInputDialogClientRequest         |
| ShowTextInputDialogClientRequest         |

**Employees:**

Below is the list of APIs exposed to perform employees related functionality:

| POS API                          |
|----------------------------------|
| GetLoggedOnEmployeeClientRequest |

**Formatters:**

Below is the list of APIs exposed to perform formatters related functionality:

| POS API                             |
|-------------------------------------|
| IBooleanFormatter                   |
| ICurrencyFormatter                  |
| IDateFormatter                      |
| ITransactionTypeFormatter           |
| IPurchaseTransferOrderTypeFormatter |

**OrgUnits:**

Below is the list of APIs exposed to perform Org units related functionality:

| POS API                              |
|--------------------------------------|
| GetOrgUnitConfigurationClientRequest |
| GetOrgUnitTenderTypesClientRequest   |
| InventoryLookupOperationRequest      |

**Products:**

Below is the list of APIs exposed to perform products related functionality:

| POS API                                    |
|--------------------------------------------|
| GetProductsByIdsClientRequest              |
| GetCurrentProductCatalogStoreClientRequest |
| SelectProductVariantClientRequest          |
| GetSerialNumberClientRequest               |
| GetRefinerValuesByTextServiceRequest       |

**SalesOrders:**

Below is the list of APIs exposed to perform sales orders related functionality:

| POS API                                          |
|--------------------------------------------------|
| GetReceiptsClientRequest                         |
| RegisterPrintReceiptCopyEventRequest             |
| GetSalesOrderDetailsByTransactionIdClientRequest |
| GetGiftReceiptsClientRequest                     |
| RegisterPrintReceiptCopyEventRequest             |
| MarkAsPickedServiceRequest                       |
| PrintPackingSlipClientRequest                    |

**Shifts:**

Below is the list of APIs exposed to perform Shifts related functionality:

| POS API                    |
|----------------------------|
| CloseShiftOperationRequest |
| CloseShiftOperationRequest |

**StockCountJournals:**

Below is the list of APIs exposed to perform stock count journals related functionality:

| POS API                                |
|----------------------------------------|
| SyncAllStockCountJournalsClientRequest |

**StoreOperations:**

Below is the list of APIs exposed to perform store operations related functionality:

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
