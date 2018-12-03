---
# required metadata

title: Dynamics 365 Payment Data Use
description: Dynamics 365 Payment Data Use
author: rubendel
manager: AnnBe
ms.date: 11/06/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2018-11-06
ms.dyn365.ops.version: AX 8.1.2

---

# Dynamics 365 Payment Data Use
This topic provides an overview of the data that is managed by the payment connectors for Microsoft Dyanmics 365. 

## Key Terms
| Term | Description | 
| --- | --- |
| Card Present | The term card present describes the use of a payment connector processing transactions where a physical card is present, such as at a point of sale register. |
| Card Not Present | The term card not present describes the use of a payment connector processing transactions where a physical card is not present, such as call center or E-Commerce scenarios. |

## Overview
This topic provides specific details on the following areas with respect to data managed by the payment connectors:

- **[Data used in Card Present Scenarios](#Data-used-in-Card-Present-Scenarios)**: Provides a list of data fields and the corresponding descriptions that are passed to the payment connector for card present scenarios.
- **[Data used in Card Not Present Scenarios](#Data-used-in-Card-Not-Present-Scenarios)**: Provides a list of data fields and the corresponding descriptions that are passed to the payment connector for card not present scenarios.

## Data used in Card Present Scenarios
The following section describes all data points sent to the payment connector for card present scenarios. That data may or may not be used by the payment connector.

### Payment Connector Request Specific Data

#### BeginTransactionPaymentTerminalDeviceRequest

| Field | Description |
| --- | --- |
| merchantInformation | The merchant information that is defined on the POS hardware profile page in the Microsoft Dynamics 365 for Finance and Operations client. |
| invoiceNumber | The unique invoice number that the POS generates to track the sales transaction. |


#### UpdateLineItemsPaymentTerminalDeviceRequest

| Field | Description |
| --- | --- |
| totalAmount | The total amount on the current sales transaction. |
| taxAmount | The tax amount on the current sales transaction. | 
| discountAmount | The discount amount on the current sales transaction. |
| subTotalAmount | The subtotal amount on the current sales transaction. |
| items | The list of product specific details, such as product names, quantity, or unit of measure. |


#### AuthorizePaymentTerminalDeviceRequest

| Field | Description |
| --- | --- |
| amount | The amount to authorize. |
| currency | The currency for the amount to authorize. |
| voiceAuthorization | The voice approval code that is sent from the POS if voice authorization is required. |


#### CapturePaymentTerminalDeviceRequest

| Field | Description |
| --- | --- |
| amount | The amount to capture. |
| currency | The currency for the amount to capture. |
| paymentPropertiesXml | The content of the `PaymentSdkData` object that is returned by the `AuthorizePaymentTerminalDeviceRequest` or `RefundPaymentTerminalDeviceRequest` request, and that is used to support stateful properties between the requests. See the section on [Payment SDK Data](#Payment-SDK-Data) below for more details. |


#### VoidPaymentTerminalDeviceRequest

| Field | Description |
| --- | --- |
| amount | The amount for the payment to void. |
| currency | The currency for the payment to void. |
| paymentPropertiesXml | The content of the `PaymentSdkData` object that is returned by the `AuthorizePaymentTerminalDeviceRequest` or `RefundPaymentTerminalDeviceRequest` request, and that is used to support stateful properties between the requests. See the section on [Payment SDK Data](#Payment-SDK-Data) below for more details. |


#### RefundPaymentTerminalDeviceRequest

| Field | Description |
| --- | --- |
| amount | The amount to refund. |
| currency | The currency for the amount to refund. |


#### ActivateGiftCardPaymentTerminalRequest

| Field | Description |
| --- | --- |
| amount | The initial amount to add to the gift card during activation. |
| currency | The currency for the initial amount to add to the gift card during activation. |


#### AddBalanceToGiftCardPaymentTerminalRequest

| Field | Description |
| --- | --- |
| amount | The amount to add to the gift card. |
| currency | The currency for the amount to add to the gift card balance. |


#### GetGiftCardBalancePaymentTerminalRequest

| Field | Description |
| --- | --- |
| currency | The currency to retrieve the gift card balance in. |


#### GetPrivateTenderPaymentTerminalDeviceRequest

| Field | Description |
| --- | --- |
| amount | The amount that is set on the POS. (Typically, this variable is used to show the amount on the payment terminal when the card number is retrieved.) |

### Shared Data

#### Payment SDK Data

| Field | Description |
| --- | --- |
| ApprovedAmount | The amount that was approved for the transaction. |
| AvailableBalance | The available balance on the card. |
| ApprovalCode | The approval code for the transaction. |
| ProviderTransactionId | The transaction identifier of the payment provider. |
| AuthorizationResult | The result of the authorization call. |
| ExternalReceipt | The external receipt data from the payment provider. |
| TerminalId | The unique identifier of the terminal that handled the payment.	|
 
## Data used in Card Not Present Scenarios
The following section describes data sent to the payment connector for card not present scenarios. Each connector varies in the specific data it processes and may not use all of the data provided.

### Payment Connector Method Specific Data

#### Authorization

| Namespace | Field | Description |
| --- | --- | --- |
| MerchantAccount | MerchantId | The merchant information that is defined on the POS hardware profile page in the Microsoft Dynamics 365 for Finance and Operations client. |
| PaymentCard | Last4Digits | The last four digits of the card used for the payment. | 
| PaymentCard | UniqueCardId | Unique randomized identifier for the card used for the payment. |
| PaymentCard | ExpirationYear | Expiration year of the card used for the payment. |
| PaymentCard | ExpirationMonth | Expiration month of the card used for the payment. |
| PaymentCard | StreetAddress | Street of the billing address associated with the card used for the payment. |
| PaymentCard | City | City of the billing address associated with the card used for the payment .|
| PaymentCard | State | State of the billing address associated with the card used for the payment. |
| PaymentCard | PostalCode | Postal code of the billing address associated with the card used for the payment. |
| TransactionData | IndustryType | Type of channel the payment occurred in (i.e. "Retail", "Direct Marketing", "E-Commerce"). |
| TransactionData | AllowPartialAuthorization | Indicates whether partial authorization is supported. |
| TransactionData | Amount | The total amount of the transaction. |
| TransactionData | CurrencyCode | The currency code of the transaction. |
| TransactionData | TerminalId | The unique terminal identifier the transaction occurred on. |
| PurchaseLevelData | L2Data | List of "Level 2" data. See the section on [L2 Data](#L2-Data) below for additional details. |
| PurchaseLevelData | L3Data | List of "Level 3" data. See the section on [L3 Data](#L3-Data) below for additional details. |


#### Capture

| Namespace | Field | Description |
| --- | --- | --- |
| MerchantAccount | MerchantId | The merchant information that is defined on the POS hardware profile page in the Microsoft Dynamics 365 for Finance and Operations client. |
| TransactionData | Amount | The total amount of the transaction. |
| TransactionData | CurrencyCode | The currency code of the transaction. |
| PurchaseLevelData | L2Data | List of "Level 2" data. See the section on [L2 Data](#L2-Data) below for additional details. |
| PurchaseLevelData | L3Data | List of "Level 3" data. See the section on [L3 Data](#L3-Data) below for additional details. |


#### Void

| Namespace | Field | Description |
| --- | --- | --- |
| MerchantAccount | MerchantId | The merchant information that is defined on the POS hardware profile page in the Microsoft Dynamics 365 for Finance and Operations client. |
| TransactionData | Amount | The total amount of the transaction. |
| TransactionData | CurrencyCode | The currency code of the transaction. |

#### Refund

| Namespace | Field | Description |
| --- | --- | --- |
| MerchantAccount | MerchantId | The merchant information that is defined on the POS hardware profile page in the Microsoft Dynamics 365 for Finance and Operations client. |
| PaymentCard | Last4Digits | The last four digits of the card used for the payment. | 
| PaymentCard | UniqueCardId | Unique randomized identifier for the card used for the payment. |
| PaymentCard | ExpirationYear | Expiration year of the card used for the payment. |
| PaymentCard | ExpirationMonth | Expiration month of the card used for the payment. |
| PaymentCard | StreetAddress | Street of the billing address associated with the card used for the payment. |
| PaymentCard | City | City of the billing address associated with the card used for the payment .|
| PaymentCard | State | State of the billing address associated with the card used for the payment. |
| PaymentCard | PostalCode | Postal code of the billing address associated with the card used for the payment. |
| TransactionData | IndustryType | Type of channel the payment occurred in (i.e. "Retail", "Direct Marketing", "E-Commerce"). |
| TransactionData | AllowPartialAuthorization | Indicates whether partial authorization is supported. |
| TransactionData | Amount | The total amount of the transaction. |
| TransactionData | CurrencyCode | The currency code of the transaction. |
| TransactionData | TerminalId | The unique terminal identifier the transaction occurred on. |
| PurchaseLevelData | L2Data | List of "Level 2" data. See the section on [L2 Data](#L2-Data) below for additional details. |
| PurchaseLevelData | L3Data | List of "Level 3" data. See the section on [L3 Data](#L3-Data) below for additional details. |

#### GetPaymentAcceptPoint 

| Namespace | Field | Description |
| --- | --- | --- |
| MerchantAccount | MerchantId | The merchant information that is defined on the POS hardware profile page in the Microsoft Dynamics 365 for Finance and Operations client. |
| PaymentCard | Name | The name of the cardholder. |
| PaymentCard | StreetAddress | Street of the billing address associated with the card used for the payment. |
| PaymentCard | City | City of the billing address associated with the card used for the payment .|
| PaymentCard | State | State of the billing address associated with the card used for the payment. |
| PaymentCard | PostalCode | Postal code of the billing address associated with the card used for the payment. |
| PaymentCard | Country | Country of the billing address associated with the card used for the payment. |
| PaymentCard | ShowSameAsShippingAddress | Identifies whether the billing address is the same as the shipping address. |
| TransactionData | IndustryType | Type of channel the payment occurred in (i.e. "Retail", "Direct Marketing", "E-Commerce"). |
| TransactionData | AllowPartialAuthorization | Indicates whether partial authorization is supported. |
| TransactionData | CurrencyCode | The currency code of the transaction. |
| TransactionData | TerminalId | The unique terminal identifier the transaction occurred on. |


### Shared Data

#### L2 Data
> [!NOTE]
> L2 data is only sent to the connector if explicitly configured through the corresponding connector configuration in the Microsoft Dynamics 365 for Finance and Operations Client.

| Namespace | Field | Description |
| --- | --- | --- |
| L2Data | OrderDateTime | Date and time the order occurred. |
| L2Data | OrderNumber | Order number associated with the order. |
| L2Data | InvoiceDateTime | Date and time the order was invoiced. |
| L2Data | InvoiceNumber | Invoice number for the order. |
| L2Data | OrderDescription | Description of the order. |
| L2Data | SummaryCommodityCode | Commodity code associated with the product. |
| L2Data | MerchantContact | Contact information for the merchant. |
| L2Data | MerchantTaxId | Unique tax identifier for the merchant. |
| L2Data | MerchantType | Unique merchant identifier maintained by the payment processor. |
| L2Data | PurchaserId | Unique identifier of the pruchaser. |
| L2Data | PurchaserTaxId | Unique tax identifier of the purchaser. |
| L2Data | ShipToCity | City of the shipping address. |
| L2Data | ShipToCounty	| Country of the shipping address. |
| L2Data | ShipToState_ProvinceCode | Province of the shipping address. |
| L2Data | ShipToPostalCode | Postal code of the shipping address. |
| L2Data | ShipToCountryCode | Country code of the shipping address. |
| L2Data | ShipFromCity | City code of the address to ship from. |
| L2Data | ShipFromCounty | Country code of the address to ship from. |
| L2Data | ShipFromState_ProvinceCode | Province code of the address to ship from. |
| L2Data | ShipFromPostalCode | Postal code of the address to ship from. |
| L2Data | ShipFromCountryCode | Country code of the address to ship from. |
| L2Data | DiscountAmount | Discount amount applied to the specific line item part of the order. |
| L2Data | MiscCharge | Miscellaneous charges applied to the specific line item part of the order. | 
| L2Data | DutyAmount | Duty amount applied to the specific line item part of the order. |
| L2Data | FreightAmount | Freight amount applied to the specific line item part of the order. |
| L2Data | HandlingCharge | Handling charge applied to the specific line item part of the order. |
| L2Data | IsTaxable | Identifies whether the specific line item part of the order is taxable. |
| L2Data | TotalTaxAmount | Total tax amount applied to the specific line item part of the order. |
| L2Data | TotalTaxRate | Total tax rate applied to the specific line item part of the order. |
| L2Data | MerchantName | Name of the merchant. |
| L2Data | MerchantCity | City of the address of the merchant. |
| L2Data | MerchantState | State of the address of the merchant. |
| L2Data | MerchantCounty | Country of the address of the merchant. |
| L2Data | MerchantCountryCode | Country code of the address of the merchant. |
| L2Data | MerchantZip | Zip code of the address of the merchant. |
| L2Data | TaxRate | Tax rate applied to the specific line item part of the order. |
| L2Data | TaxAmount | Tax amount applied to the specific line item part of the order. |
| L2Data | TaxDescription | Description of the taxes applied to the specific line item part of the order. | 
| L2Data | TaxTypeIdentifier | Type identifier of the taxes applied to the specific line item part of the order. |
| L2Data | RequesterName | Name of the request. |
| L2Data | TotalAmount | Total amount of the specific line item part of the order. |
| L2Data | PurchaseCardType | The card type of the purchaser. |
| L2Data | AmexLegacyDescription1 | Legacy American Express description field 1. |
| L2Data | AmexLegacyDescription2 | Legacy American Express description field 2. |
| L2Data | AmexLegacyDescription3 | Legacy American Express description field 3. |
| L2Data | AmexLegacyDescription4 | Legacy American Express description field 4. |
| L2Data | TaxDetails[].TaxRate | List with individual tax rates applied to the specific line item part of the order. |
| L2Data | TaxDetails[].TaxDescription | List of individual tax rates applied to the specific line item part of the order. |
| L2Data | TaxDetails[].TaxAmount | List of individual descriptions of the taxes applied to the specific line item part of the order. |
| L2Data | TaxDetails[].TaxTypeIdentifier | List of type identifiers of the taxes applied to the specific line item part of the order. |
| L2Data | MiscellaneousCharges[].ChargeType | List of charge types applied to the specific line item part of the order. |
| L2Data | MiscellaneousCharges[].ChargeAmount | List of charge amounts applied to the specific line item part of the order. |

#### L3 Data
> [!NOTE]
> L3 data is only sent to the connector if explicitly configured through the corresponding connector configuration in the Microsoft Dynamics 365 for Finance and Operations Client.

| Namespace | Field | Description |
| --- | --- | --- |
| L3Data | SequenceNumber | Sequence number of the item for the order. |
| L3Data | CommodityCode | Commodity code associated with the product. |
| L3Data | ProductCode | Unique code of the product. | 
| L3Data | ProductName | Name of the product. |
| L3Data | ProductSKU | SKU of the product. |
| L3Data | Descriptor | Description of the product. |
| L3Data | UnitOfMeasure | Unit of measureof the product. |
| L3Data | UnitPrice | Unit price of the product. |
| L3Data | Discount | Discount applied to the product. |
| L3Data | DiscountRate | Discount rate applied to the product. |
| L3Data | Quantity | Quantity of the product. |
| L3Data | MiscCharge | Miscellaneous charge of the product. |
| L3Data | NetTotal | Net total amount of the product. |
| L3Data | TaxAmount | Tax amount of the product. |
| L3Data | TaxRate | Tax rate of the product. |
| L3Data | TotalAmount | Total amount of the product. |
| L3Data | CostCenter | Cost center of the product. |
| L3Data | FreightAmount | Freight amount of the product. |
| L3Data | HandlingAmount | Handling amount of the product. |
| L3Data | CarrierTrackingNumber | Carrier tracking number of the product being shipped. |
| L3Data | MerchantTaxID | Unique tax identifier of the merchant. |
| L3Data | MerchantCatalogNumber | Catalog number of the merchant. |
| L3Data | TaxCategoryApplied | Tax category applied to the product. |
| L3Data | PickupAddress | Street of the pickup address. |
| L3Data | PickupCity | City of the pickup address. |
| L3Data | PickupState | State of the pickup address. |
| L3Data | PickupCounty | Country of the pickup address. |
| L3Data | PickupZip | Zip code of the pickup address. |
| L3Data | PickupCountry | Country of the pickup address. |
| L3Data | PickupDateTime | Date and time of the pickup. |
| L3Data | PickupRecordNumber | Record number of the pickup. |
| L3Data | CarrierShipmentNumber | Shipment number of the carrier. |
| L3Data | UNSPSCCode | UNSPSC Code. |
| L3Data | TaxDetails[].TaxRate | List with individual tax rates applied to the specific line item part of the order. |
| L3Data | TaxDetails[].TaxDescription | List of individual tax rates applied to the specific line item part of the order. |
| L3Data | TaxDetails[].TaxAmount | List of individual descriptions of the taxes applied to the specific line item part of the order. |
| L3Data | TaxDetails[].TaxTypeIdentifier | List of type identifiers of the taxes applied to the specific line item part of the order. |
| L3Data | MiscellaneousCharges[].ChargeType | List of charge types applied to the specific line item part of the order. |
| L3Data | MiscellaneousCharges[].ChargeAmount | List of charge amounts applied to the specific line item part of the order. |



## Related Articles
- **[Create an end-to-end payment integration for a payment terminal](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension)**
  - Describes how to author a custom payment connector. 

