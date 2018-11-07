---
# required metadata

title: Dynamics 365 payment SDK privacy data notice
description: Dynamics 365 SDK privacy data notice
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

# Dynamics 365 payment SDK privacy data notice
This topic provides an overview of the data that is provided to payment connectors via the payments SDK for Microsoft Dyanmics 365. All data listed in this topic is available through the payments SDK to help facilitate payments. The data used to conduct payments through a payment connector is subject to the terms of the party supplying the payment connector and the parties providing the payment services. 
The data made available through the payment connector is may be used by the payment service provider in the United States or any other country in which it hosts services. 
In certain cases, Microsoft may share your contact information with the third party service provider to operate and troubleshoot the service or prevent misuse.

## Definition of "Customer data"
Any data that could be used- by itself or combined with other data- to identify a party who uses Microsoft services is considered to be "Customer data". For the purposes of this document, the "Customer" is most commonly a business conducting transasctions through he payment connector. Other customers could be the VARs amd ISVs who helps to set up, test and write connectors that make those transactions possible. Whenever that data is transmitted to a third party, Microsoft confirms that the other party has protections in place to ensure that data is being protected or, in cases where Microsoft may not control where that data is sent, provides notices to indicate customer data is leaving its protection boundary. 

### "Card Present" Customer data
When a payment terminal is implemented using the INamedRequestHandler, it is typically referred to as a "Card present" payment connector. The term card present is a way to describe such a payment connector due to the fact that is supports transactions where a physcical card is presented. In such an implementation, the following data is available through the payment SDK to facitlitate the transaction. That data may or may not be used by the payment connector. In such an implementation, the following data is available through the payment SDK to facitlitate the transaction. That data may or may not be used by the payment connector. 

| Datapoint | Description |  
| --- | --- | 
| DisplayRequest.DisplayOutput.OutputContent.OutputXHMTL	| The actual text being sent to the payment terminal to display |
| MessageHeader.POIID	 | Unique identifier of the Adyen payment terminal. |
| MessageHeader.SaleID	| Unique identifier of the Point of Sale. |
| PaymentRequest.PaymentTransaction.AmountsReq.Currency	| The currency to use when handling the payment. |
| PaymentRequest.PaymentTransaction.AmountsReq.RequestedAmount	| The amount to use when handling the payment. |
| PaymentRequest.SaleData.SaleToAcquirerData	| Sale information intended for the acquirer. |
| TransactionStatusRequest.MessageReference.SaleID	| Unique identifier of the Point of Sale. |
 
 ### "Card Not Present" Customer data
Payment connectors implemented for use in the back office, call center, or used in e-Commerce integrations are implemented using the IPaymentProcessor, are typically referred to as "Card not present" payment connectors. In this case, those connectors are described as "Card not present" because the card number has traditionally been manually entered or provided by some means other than a physical swipe or dip.  

| Datapoint | Description |  
| --- | --- |
| acquirerAccountCode	| The acquirer account code
| acquirerCode	| The acquirer code
| acquirerReference	| The acquirer reference
| additionalData.enhancedSchemeData.customerReference	| The customer reference
| additionalData.enhancedSchemeData.destinationCountryCode	| The destination country code
| additionalData.enhancedSchemeData.destinationPostalCode	| The destination postcode
| additionalData.enhancedSchemeData.destinationStateProvinceCode	| The destination state or province code
| additionalData.enhancedSchemeData.dutyAmount	| The duty amount
| additionalData.enhancedSchemeData.freightAmount	| The freight amount
| additionalData.enhancedSchemeData.itemDetailLine{line}.description	| The product description
| additionalData.enhancedSchemeData.itemDetailLine{line}.discountAmount	| The discount amount
| additionalData.enhancedSchemeData.itemDetailLine{line}.productCode	| The product code
| additionalData.enhancedSchemeData.itemDetailLine{line}.quantity	| The order line quantity
| additionalData.enhancedSchemeData.itemDetailLine{line}.totalAmount	| The total amount
| additionalData.enhancedSchemeData.itemDetailLine{line}.unitOfMeasure	| The order line unit of measure
| additionalData.enhancedSchemeData.itemDetailLine{line}.unitPrice	| The unit price
| additionalData.enhancedSchemeData.orderDate	| The order date
| additionalData.enhancedSchemeData.shipFromPostalCode	| The ship from postal code
| additionalData.enhancedSchemeData.totalTaxAmount | Total tax amount for an order
| amount.currency	| The currency of the transaction
| amount.value	| The amount to authorize (no decimal point)
| authCode	| The authorization code for the token
| authorisationMid	| The authorization mid
| avsResult	| The address verification result
| avsResultRaw	| The AVS result raw
| cardBin	| The first 6 digits of credit card
| cardHolderName	| The credit card holders name
| cardIssuingCountry	| The card issuing country
| cardPaymentMethod	| The card payment method
| cardSummary	| The last four digits of the credit card
| countryCode	| The current country code for the tokenization
| cvcResult	| The cvc result
| cvcResultRaw	| The cvc result raw
| expiryDate	| The expiry date for the card
| merchantAccount	| The Adyen merchants account assigned to customer
| modificationAmount.currency	| The currency of the transaction
| modificationAmount.value	| The amount to capture (no decimal point)
| originalReference	| The psp of the original authorization payment
| paymentMethod	| The payment method
| paymentMethodVariant	| The payment variant
| pspReference	| The Adyen psp reference number
| recurring.recurringDetailReference	| The detail reference for recurring payments (Token)
| selectedRecurringDetailReference	| The required recurring detail reference to make the payment against
| shopperLocale	| The shopper locale
| ua	| The amount to capture (no decimal point)
