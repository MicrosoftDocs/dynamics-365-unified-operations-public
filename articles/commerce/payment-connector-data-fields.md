---
# required metadata

title: Dynamics 365 payment data use
description: This topic provides an overview of the data that is managed by the payment connectors for Microsoft Dynamics 365.
author: BrianShook
ms.date: 12/03/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom: 2018-11-06
ms.dyn365.ops.version: AX 8.1.2

---

# Dynamics 365 payment data use

[!include [banner](includes/banner.md)]

This topic provides an overview of the data that is managed by the payment connectors for Microsoft Dynamics 365.

## Key terms

| Term | Description |
|---|---|
| Card present | The term *card present* describes the use of a payment connector to process transactions where a physical card is present, such as at a point of sale (POS) register. |
| Card not present | The term *card not present* describes the use of a payment connector to process transactions where a physical card isn't present, such as in call center or e-Commerce scenarios. |

## Overview

This topic provides specific details about the following areas with respect to data that is managed by the payment connectors:

- **[Data used in card-present scenarios](#data-used-in-card-present-scenarios)** – This section provides a list and descriptions of data fields that are passed to the payment connector for card-present scenarios.
- **[Data used in card-not-present scenarios](#data-used-in-card-not-present-scenarios)** – This section provides a list and descriptions of data fields that are passed to the payment connector for card-not-present scenarios.

## Data used in card-present scenarios

This section describes all data points that are sent to the payment connector for card-present scenarios. The payment connect might not use the data.

### Payment connector request-specific data

#### BeginTransactionPaymentTerminalDeviceRequest

| Field | Description |
|---|---|
| merchantInformation | The merchant information that is defined on the **POS hardware profile** page in the Finance and Operations client. |
| invoiceNumber | The unique invoice number that the POS generates to track the sales transaction. |

#### UpdateLineItemsPaymentTerminalDeviceRequest

| Field | Description |
|---|---|
| totalAmount | The total amount on the current sales transaction. |
| taxAmount | The tax amount on the current sales transaction. | 
| discountAmount | The discount amount on the current sales transaction. |
| subTotalAmount | The subtotal amount on the current sales transaction. |
| items | The list of product-specific details, such as product names, quantities, or units of measure. |

#### AuthorizePaymentTerminalDeviceRequest

| Field | Description |
|---|---|
| amount | The amount to authorize. |
| currency | The currency for the amount to authorize. |
| voiceAuthorization | The voice approval code that is sent from the POS if voice authorization is required. |

#### CapturePaymentTerminalDeviceRequest

| Field | Description |
|---|---|
| amount | The amount to capture. |
| currency | The currency for the amount to capture. |
| paymentPropertiesXml | The content of the **PaymentSdkData** object that is returned by the **AuthorizePaymentTerminalDeviceRequest** or **RefundPaymentTerminalDeviceRequest** request, and that is used to support stateful properties between the requests. For more details, see the [Payment SDK data](#payment-sdk-data) section later in this topic. |

#### VoidPaymentTerminalDeviceRequest

| Field | Description |
|---|---|
| amount | The amount of the payment to void. |
| currency | The currency for the payment to void. |
| paymentPropertiesXml | The content of the **PaymentSdkData** object that is returned by the **AuthorizePaymentTerminalDeviceRequest** or **RefundPaymentTerminalDeviceRequest** request, and that is used to support stateful properties between the requests. For more details, see the [Payment SDK data](#payment-sdk-data) section later in this topic. |

#### RefundPaymentTerminalDeviceRequest

| Field | Description |
|---|---|
| amount | The amount to refund. |
| currency | The currency for the amount to refund. |

#### ActivateGiftCardPaymentTerminalRequest

| Field | Description |
|---|---|
| amount | The initial amount to add to the gift card during activation. |
| currency | The currency for the initial amount to add to the gift card during activation. |

#### AddBalanceToGiftCardPaymentTerminalRequest

| Field | Description |
|---|---|
| amount | The amount to add to the gift card balance. |
| currency | The currency for the amount to add to the gift card balance. |

#### GetGiftCardBalancePaymentTerminalRequest

| Field | Description |
|---|---|
| currency | The currency to retrieve the gift card balance in. |

#### GetPrivateTenderPaymentTerminalDeviceRequest

| Field | Description |
|---|---|
| amount | The amount that is set on the POS. (Typically, this variable is used to show the amount on the payment terminal when the card number is retrieved.) |

### Shared data

#### Payment SDK data

| Field | Description |
|---|---|
| ApprovedAmount | The amount that was approved for the transaction. |
| AvailableBalance | The available balance on the card. |
| ApprovalCode | The approval code for the transaction. |
| ProviderTransactionId | The transaction identifier of the payment provider. |
| AuthorizationResult | The result of the authorization call. |
| ExternalReceipt | The external receipt data from the payment provider. |
| TerminalId | The unique identifier of the terminal that handled the payment. |
 
## Data used in card-not-present scenarios

This section describes data that is sent to the payment connector for card-not-present scenarios. The specific data that each connector processes varies, and a given connector might not use all the data that is provided.

### Payment connector method–specific data

#### Authorization

| Namespace | Field | Description |
|---|---|---|
| MerchantAccount | MerchantId | The merchant information that is defined on the **POS hardware profile** page in the Finance and Operations client. |
| PaymentCard | Last4Digits | The last four digits of the card that is used for the payment. | 
| PaymentCard | UniqueCardId | The unique randomized identifier of the card that is used for the payment. |
| PaymentCard | ExpirationYear | The expiration year of the card that is used for the payment. |
| PaymentCard | ExpirationMonth | The expiration month of the card that is used for the payment. |
| PaymentCard | StreetAddress | The street of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | City | The city of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | State | The state or province of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | PostalCode | The postal code of the billing address that is associated with the card that is used for the payment. |
| TransactionData | IndustryType | The type of channel where the payment occurred (for example, **Retail**, **Direct Marketing**, or **E-Commerce**). |
| TransactionData | AllowPartialAuthorization | A value that indicates whether partial authorization is supported. |
| TransactionData | Amount | The total amount of the transaction. |
| TransactionData | CurrencyCode | The currency code for the transaction. |
| TransactionData | TerminalId | The unique identifier of the terminal where the transaction occurred. |
| PurchaseLevelData | L2Data | The list of "Level 2" data. For more details, see the [L2 data](#l2-data) section later in this topic. |
| PurchaseLevelData | L3Data | The list of "Level 3" data. For more details, see the [L3 data](#l3-data) section later in this topic. |

#### Capture

| Namespace | Field | Description |
|---|---|---|
| MerchantAccount | MerchantId | The merchant information that is defined on the **POS hardware profile** page in the Finance and Operations client. |
| TransactionData | Amount | The total amount of the transaction. |
| TransactionData | CurrencyCode | The currency code for the transaction. |
| PurchaseLevelData | L2Data | The list of "Level 2" data. For more details, see the [L2 data](#l2-data) section later in this topic. |
| PurchaseLevelData | L3Data | The list of "Level 3" data. For more details, see the [L3 data](#l3-data) section later in this topic. |

#### Void

| Namespace | Field | Description |
|---|---|---|
| MerchantAccount | MerchantId | The merchant information that is defined on the **POS hardware profile** page in the Finance and Operations client. |
| TransactionData | Amount | The total amount of the transaction. |
| TransactionData | CurrencyCode | The currency code for the transaction. |

#### Refund

| Namespace | Field | Description |
|---|---|---|
| MerchantAccount | MerchantId | The merchant information that is defined on the **POS hardware profile** page in the Finance and Operations client. |
| PaymentCard | Last4Digits | The last four digits of the card that is used for the payment. | 
| PaymentCard | UniqueCardId | The unique randomized identifier of the card that is used for the payment. |
| PaymentCard | ExpirationYear | The expiration year of the card that is used for the payment. |
| PaymentCard | ExpirationMonth | The expiration month of the card that is used for the payment. |
| PaymentCard | StreetAddress | The street of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | City | The city of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | State | The state or province of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | PostalCode | The postal code of the billing address that is associated with the card that is used for the payment. |
| TransactionData | IndustryType | The type of channel where the payment occurred (for example, **Retail**, **Direct Marketing**, or **E-Commerce**). |
| TransactionData | AllowPartialAuthorization | A value that indicates whether partial authorization is supported. |
| TransactionData | Amount | The total amount of the transaction. |
| TransactionData | CurrencyCode | The currency code for the transaction. |
| TransactionData | TerminalId | The unique identifier of the terminal where the transaction occurred. |
| PurchaseLevelData | L2Data | The list of "Level 2" data. For more details, see the [L2 data](#l2-data) section later in this topic. |
| PurchaseLevelData | L3Data | The list of "Level 3" data. For more details, see the [L3 data](#l3-data) section later in this topic. |

#### GetPaymentAcceptPoint 

| Namespace | Field | Description |
|---|---|---|
| MerchantAccount | MerchantId | The merchant information that is defined on the **POS hardware profile** page in the Finance and Operations client. |
| PaymentCard | Name | The name of the cardholder. |
| PaymentCard | StreetAddress | The street of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | City | The city of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | State | The state or province of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | PostalCode | The postal code of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | Country | The country or region of the billing address that is associated with the card that is used for the payment. |
| PaymentCard | ShowSameAsShippingAddress | A value that identifies whether the billing address is the same as the shipping address. |
| TransactionData | IndustryType | The type of channel where the payment occurred (for example, **Retail**, **Direct Marketing**, or **E-Commerce**). |
| TransactionData | AllowPartialAuthorization | A value that indicates whether partial authorization is supported. |
| TransactionData | CurrencyCode | The currency code for the transaction. |
| TransactionData | TerminalId | The unique identifier of the terminal where the transaction occurred. |

### Shared data

#### L2 data

> [!NOTE]
> L2 data is sent to the connector only if this behavior is explicitly configured through the corresponding connector configuration in the Commerce client.

| Namespace | Field | Description |
|---|---|---|
| L2Data | OrderDateTime | The date and time when the order occurred. |
| L2Data | OrderNumber | The order number that is associated with the order. |
| L2Data | InvoiceDateTime | The date and time when the order was invoiced. |
| L2Data | InvoiceNumber | The invoice number for the order. |
| L2Data | OrderDescription | The description of the order. |
| L2Data | SummaryCommodityCode | The commodity code that is associated with the product. |
| L2Data | MerchantContact | The contact information for the merchant. |
| L2Data | MerchantTaxId | The unique tax identifier of the merchant. |
| L2Data | MerchantType | The unique merchant identifier that is maintained by the payment processor. |
| L2Data | PurchaserId | The unique identifier of the purchaser. |
| L2Data | PurchaserTaxId | The unique tax identifier of the purchaser. |
| L2Data | ShipToCity | The city of the shipping address. |
| L2Data | ShipToCounty	| The county of the shipping address. |
| L2Data | ShipToState\_ProvinceCode | The state or province code of the shipping address. |
| L2Data | ShipToPostalCode | The postal code of the shipping address. |
| L2Data | ShipToCountryCode | The country or region code of the shipping address. |
| L2Data | ShipFromCity | The city of the address that the order is shipped from. |
| L2Data | ShipFromCounty | The county of the address that the order is shipped from. |
| L2Data | ShipFromState\_ProvinceCode | The state or province code of the address that the order is shipped from. |
| L2Data | ShipFromPostalCode | The postal code of the address that the order is shipped from. |
| L2Data | ShipFromCountryCode | The country or region code of the address that the order is shipped from. |
| L2Data | DiscountAmount | The discount amount that is applied to the specific line item part of the order. |
| L2Data | MiscCharge | The miscellaneous charges that are applied to the specific line item part of the order. | 
| L2Data | DutyAmount | The duty amount that is applied to the specific line item part of the order. |
| L2Data | FreightAmount | The freight amount that is applied to the specific line item part of the order. |
| L2Data | HandlingCharge | The handling charge that is applied to the specific line item part of the order. |
| L2Data | IsTaxable | A value that identifies whether the specific line item part of the order is taxable. |
| L2Data | TotalTaxAmount | The total tax amount that is applied to the specific line item part of the order. |
| L2Data | TotalTaxRate | The total tax rate that is applied to the specific line item part of the order. |
| L2Data | MerchantName | The name of the merchant. |
| L2Data | MerchantCity | The city of the address of the merchant. |
| L2Data | MerchantState | The state or province of the address of the merchant. |
| L2Data | MerchantCounty | The county of the address of the merchant. |
| L2Data | MerchantCountryCode | The country or region code of the address of the merchant. |
| L2Data | MerchantZip | The postal code of the address of the merchant. |
| L2Data | TaxRate | The tax rate that is applied to the specific line item part of the order. |
| L2Data | TaxAmount | The tax amount that is applied to the specific line item part of the order. |
| L2Data | TaxDescription | The description of the taxes that are applied to the specific line item part of the order. | 
| L2Data | TaxTypeIdentifier | The type identifier of the taxes that are applied to the specific line item part of the order. |
| L2Data | RequesterName | The name of the requester. |
| L2Data | TotalAmount | The total amount of the specific line item part of the order. |
| L2Data | PurchaseCardType | The card type of the purchaser. |
| L2Data | AmexLegacyDescription1 | Legacy American Express description field 1. |
| L2Data | AmexLegacyDescription2 | Legacy American Express description field 2. |
| L2Data | AmexLegacyDescription3 | Legacy American Express description field 3. |
| L2Data | AmexLegacyDescription4 | Legacy American Express description field 4. |
| L2Data | TaxDetails\[\].TaxRate | The list of individual tax rates that are applied to the specific line item part of the order. |
| L2Data | TaxDetails\[\].TaxDescription | The list of individual descriptions of the taxes that are applied to the specific line item part of the order. |
| L2Data | TaxDetails\[\].TaxAmount | The list of individual tax amounts that are applied to the specific line item part of the order. |
| L2Data | TaxDetails\[\].TaxTypeIdentifier | The list of type identifiers of the taxes that are applied to the specific line item part of the order. |
| L2Data | MiscellaneousCharges\[\].ChargeType | The list of charge types that are applied to the specific line item part of the order. |
| L2Data | MiscellaneousCharges\[\].ChargeAmount | The list of charge amounts that are applied to the specific line item part of the order. |

#### L3 data

> [!NOTE]
> L3 data is sent to the connector only if this behavior is explicitly configured through the corresponding connector configuration in the Commerce client.

| Namespace | Field | Description |
|---|---|---|
| L3Data | SequenceNumber | The sequence number of the item for the order. |
| L3Data | CommodityCode | The commodity code that is associated with the product. |
| L3Data | ProductCode | The unique code of the product. | 
| L3Data | ProductName | The name of the product. |
| L3Data | ProductSKU | The stock keeping unit (SKU) of the product. |
| L3Data | Descriptor | The description of the product. |
| L3Data | UnitOfMeasure | The unit of measure of the product. |
| L3Data | UnitPrice | The unit price of the product. |
| L3Data | Discount | The discount that is applied to the product. |
| L3Data | DiscountRate | The discount rate that is applied to the product. |
| L3Data | Quantity | The quantity of the product. |
| L3Data | MiscCharge | The miscellaneous charge of the product. |
| L3Data | NetTotal | The net total amount of the product. |
| L3Data | TaxAmount | The tax amount of the product. |
| L3Data | TaxRate | The tax rate of the product. |
| L3Data | TotalAmount | The total amount of the product. |
| L3Data | CostCenter | The cost center of the product. |
| L3Data | FreightAmount | The freight amount of the product. |
| L3Data | HandlingAmount | The handling amount of the product. |
| L3Data | CarrierTrackingNumber | The carrier tracking number of the product that is being shipped. |
| L3Data | MerchantTaxID | The unique tax identifier of the merchant. |
| L3Data | MerchantCatalogNumber | The catalog number of the merchant. |
| L3Data | TaxCategoryApplied | The tax category that is applied to the product. |
| L3Data | PickupAddress | The street of the pickup address. |
| L3Data | PickupCity | The city of the pickup address. |
| L3Data | PickupState | The state or province of the pickup address. |
| L3Data | PickupCounty | The county of the pickup address. |
| L3Data | PickupZip | The postal code of the pickup address. |
| L3Data | PickupCountry | The country or region of the pickup address. |
| L3Data | PickupDateTime | The date and time of the pickup. |
| L3Data | PickupRecordNumber | The record number of the pickup. |
| L3Data | CarrierShipmentNumber | The shipment number of the carrier. |
| L3Data | UNSPSCCode | The United Nations Standard Products and Services Code (UNSPSC). |
| L2Data | TaxDetails\[\].TaxRate | The list of individual tax rates that are applied to the specific line item part of the order. |
| L2Data | TaxDetails\[\].TaxDescription | The list of individual descriptions of the taxes that are applied to the specific line item part of the order. |
| L2Data | TaxDetails\[\].TaxAmount | The list of individual tax amounts that are applied to the specific line item part of the order. |
| L3Data | TaxDetails\[\].TaxTypeIdentifier | The list of type identifiers of the taxes that are applied to the specific line item part of the order. |
| L3Data | MiscellaneousCharges\[\].ChargeType | The list of charge types that are applied to the specific line item part of the order. |
| L3Data | MiscellaneousCharges\[\].ChargeAmount | The list of charge amounts that are applied to the specific line item part of the order. |

## Related topics

- **[Create an end-to-end payment integration for a payment terminal](/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension)** – This topic describes how to create a custom payment connector.


[!INCLUDE[footer-include](../includes/footer-banner.md)]