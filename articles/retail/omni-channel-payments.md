---
# required metadata

title: Omni-channel credit card payments overview
description: This topic provides an overview of omni-channel payments for Dynamics 365 for Retail.
author: rubendel
manager: AnnBe
ms.date: 05/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 8.1.3

---

# Omni-channel payments overview

[!include [banner](../includes/banner.md)]

This topic provides an overview of omni-channel payments in Microsoft Dynamics 365 for Retail. It includes a comprehensive list of supported features and functionality, setup, troubleshooting information, and descriptions of some common issues.

All scenarios described in this topic are supported out of the box with the Microsoft Dynamics 365 Payment Connector for Adyen or can be implemented for other payment connectors using the Payments SDK.

The following omni-channel payment scenarios are supported:

- Buy online, pick up in store.
- Buy in call center, pick up in store.
- Buy in Store A, pick up in store B.
- Buy in Store A, ship to customer.

## Key terms

> [!NOTE]
> The terms "token" and "reference" can be used interchangeably.

| Term | Description |
|---|---|
| Token | A string of data that is provided by payment processors to be used as a reference. Tokens can represent payment card numbers, payment authorizations and previous payment captures. Tokens are important because they help to keep sensitive data out of the point of sale system.   |
| Card token | A token that is provided by the payment processor for storage in the point of sale system. This card token can only be used by the merchant receiving the token and is generally harmless outside of the system. May also be referred to as 'Card reference'. Recurring card token |
| Auth(orization) token | When a point of sale system makes an authorization request to a payment processor, the payment processor will provide a unique ID back to the point of sale system as part of the response to that request. This authorization token, or authorization reference, can later be used when calling the processor to perform actions such as reversing or voiding the authorization. Most commonly the authorization token is used to capture funds when an order is fulfilled or a transaction is being finalized. |
| Capture token | When a payment is finalized, or captured, the processor provides a reference to that capture back to the point of sale. That capture can be referenced in subsequent operations such as refund requests. | 
| Card not present | Refers to payment transactions where a physical card is not present, such as E-Commerce or Call Center scenarios. In these scenarios the payment related information is entered manually either on an E-Commerce website, a Call Center flow, or on the point-of-sale or payment terminal. |
| Card present | Refers to payment transactions where a physical card is presented and used on a payment terminal connected to the Dynamics 365 Point of Sale. |

## Overview

In general, "omni-channel payments" describes the ability to create an order in one channel and fulfill it in another channel. The  key to omni-channel payment support is to preserve payment details with the rest of the order details and to utilize those payments when the order is recalled or processed in another channel. A classic example of this is "Buy online, pickup in store". In that scenario, the payment details are added when the order is created online and can be recalled at the point of sale to charge the customer's payment card at the time of pickup. 

All scenarios described here can be implemented using the standard Payments SDK provided with Microsoft Dynamics 365 for Retail. The [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3) provides an out of box implementation of each of the scenarios described. 


### Prerequisites

Each of the scenarios described in this document requires a payment connector that supports omni-channel payments. The out of box Adyen connector may also be used as it supports each of the scenarios enabled through the SDK. For more information about implementing payment connectors and the retail SDK in general visit the [Retail for IT pros and developers home page](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/dev-retail-home-page#payment-connectors).

#### Supported versions

Omni-channel payments capabilities described in this document were shipped as part of 8.1.3. 

#### Card present and card not present connectors

The retail payment SDK relies on two sets of payment APIs. The first, is called iPayment processor. This set of APIs is used to implement card not present payment connectors for use in call center and e-commerce. More information about the iPaymentProcessor interface can be found in this [whitepaper](http://download.microsoft.com/download/4/D/7/4D7C6B05-0C23-4C6C-BA13-AB62ED08AA61/The%20Guide%20to%20Implementing%20Payment%20Connector%20and%20Payment%20Device.docx) covering payments. 

The second set of APIs is called iNamedRequestHandler. This set of APIs is the supported method of implementing card present payment integrations that utilize a payment terminal. This set of APIs is documented in the [Create a payment integration for a payment terminal](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension) document. 

### Setup & Configuration

The following components and setup steps are required:

**E-commerce integration:** To support scenarios with an order originating in an online storefront, an integration to Microsoft Dynamics 365 for Retail is required. For more information related to the Retail e-commerce SDK, visit the [e-Commerce platform software development kit (SDK)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/ecommerce-platform-sdk) topic. In a demo environment, the sample storefront supports omni-channel payment scenarios. 

**Online payments configuration:** The online channel setup must include a payment connector that has been updated to support omni-channel payments, or the out of box payment connector can be used. To configure Adyen payments for online stores, visit the [Adyen payment connector topic](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce). 

In addition to the e-commerce setup steps provided in the link above, the Adyen connector settings must have the parameter "Allow saving payment information in e-commerce" set to 'True'. 

**Omni-channel payments configuration:** In the back office, navigate to Retail --> Headquarters setup --> Parameters --> Retail shared parameters. Select the "Omni-channel payments tab and set "Use omni-channel payments" to 'Yes'. 

**Payment services** The default payment connector in the "Payment services" form is used by the call center to process payments. To support scenarios such as "Buy in call center, pickup in store" this must be set up the Adyen payment connector or one that is compliant with omni-channel payment implementation requirements.

**EFT service** Payments through a payment terminal must be set up in the 'EFT service' fasttab on the hardware profile. The Adyen connector supports omni-channel payments scenarios out of box. Other payment connectors supporting the iNamedRequestHandler interface may also be used if they support omni-channel payments.

**Payment connector availability** When an order is recalled, the payment tender lines that are recalled with the order include the name of the payment connector that was used to create the authorizations associated with that order. Upon fulfillment, the payments SDK will attempt to use the same connector that was used to generate the original authorization, so a payment connector with the same merchant properties must be available for capture. 

**Card types**
For omni-channel scenarios to work properly, each channel needs to have same setup for tender types that can be used for omni-channel. This includes payment method IDs and card type IDs. For example, if tender type 'Cards' has ID '2' in the online store, it should have the same ID in the retail store setup. The same is true for card type IDs- if card number '12' is set to 'VISA' in the online store, the same should be set up for retail store. 

### Basic principle supporting omni-channel payments

Payment connectors and payment processors utilize references, or tokens, to reference interactions related to card payments. For example, when a payment authorization is requested, a reference to that authorization is provided so that authorization can referenced later when capturing funds upon fulfillment. This authorization is unique to the merchant, payment connector, and processor. 

If an order that was created online is being picked up in the store, the same payment details for that order must also be recalled and used. When those original details are provided as part of the request to capture a payment against the original authorization, the payment processor will understand the request and be able to capture the payment. 

To properly reference the online order, a card not present payment connector which supports the same processor must also be available. This allows the point of sale to have one processor for card present payments, but also have access to other payment connectors in order to fulfill orders created in different channels using different payment processors. 

## Supported scenarios

The following omni-channel payment scenarios are supported:

- Buy online, pick up in store
- Buy in call center, pick up in store
- Buy in Store A, pick up in store B
- Buy in Store A, ship to customer

Variations of the above scenarios are also supported. For example, an online order may have lines that ship to the customer and those that will be picked up in store. All order fulfillment options are supported via omni-channel payments. 

The steps for each of the scenarios below describe how to execute the scenario using demo data. 

### Buy online, pickup in store

Prerequisites: 
- Reference storefront with Adyen connector configured
- Omni-channel payments set to "True" in Retail shared parameters
- Houston point of register with Adyen payment connector configured

Steps:
1. In the reference storefront, create an order for pickup in store. Be sure to select the Houston store. 
2. Go through the checkout steps and pay using a test credit card number. Test credit card numbers can be found on the [Adyen test card numbers page](https://docs.adyen.com/development-resources/test-cards/test-card-numbers/#description).
3. In Dynamics for Retail, use the 'Synchronize orders' batch job and P-001 distribution schedule to create the orders in the back office.
4. In the point of sale, select the 'Orders to pickup' operation from the welcome screen to see orders for pickup in store. 
5. Select one or more lines from the order created in the reference storefront and click 'Pick up'
6. The order will then be retrieved from the back office. 
7. When the order line details are retrieved from the back office, and an omni-channel capable card payment is detected, the user will be informed that a payment method is available.
8. Select "Use available payment method" to complete the transaction using the card details entered in the reference storefront.
9. The order line(s) will then be loaded on the transaction screen with a balance of zero due. Click on the 'Payments' tab to observe the tender line that was pulled down from the online order. 
10. Select any payment method to complete the transaction. 

### Buy in call center, pick up in store

Steps:
1. Navigate to the "Customer service" form in Dynamics for Retail.
2. In the search bar, type Karen Berg, then click 'Search'. 
3. Select Karen Berg in the search results.
4. When Karen is loaded into the customer service form, click 'New sales order'.
5. In the new sales order form, first click 'Header' to view the order header. 
6. In the order header form, set the site to "Central" and the warehouse to "Houston".
7. In the deliver tab, set mode of delivery to "60" for customer pick up.
8. Select 'Lines', then add a line(s) to the order. 
9. Select 'Complete' to enter the order completion flow.
10. Scroll down to the payments area and click 'Add', then select a line of payment method type 'Cards'. 
11. Click the '+' symbol to add a card payment. 
12. Enter the details for a test credit card number found on the [Adyen test card numbers page](https://docs.adyen.com/development-resources/test-cards/test-card-numbers/#description) and then click 'OK'. 
*Note: If the card number entered is for a different card brand from the one selected when initiating the payment, the payment will still go through, but post to the accounts mapped to the card brand selected in step 10.* 
12. Click 'OK' again to close the order completion payments dialog.
13. Click 'Submit' on the sales order summary page.
14. In the point of sale, select the 'Orders to pickup' operation from the welcome screen to see orders for pickup in store. 
15. Select one or more lines from the order created in the reference storefront and click 'Pick up'
16. The order will then be retrieved from the back office. 
17. When the order line details are retrieved from the back office, and an omni-channel capable card payment is detected, the user will be informed that a payment method is available.
18. Select "Use available payment method" to complete the transaction using the card details entered in the reference storefront.
19. The order line(s) will then be loaded on the transaction screen with a balance of zero due. Click on the 'Payments' tab to observe the tender line that was pulled down from the online order. 
20. Select any payment method to complete the transaction. 

### Buy in Store A, pick up in store B

Steps:
1. Launch the point of sale for Houston.
2. Navigate to the transaction screen and in the number pad type "2001" to add Karen Berg to the transaction.
3. Add a line(s) to the transaction.
4. Click the 'Orders' button to see orders options.
5. Select 'Pick up all' select 'Customer order' when prompted.
6. In the search bar, type "Seattle", then select the Seattle store for pick up. 
7. Click 'OK' to accept today's date for the date of pickup.
9. Use 'Pay card' to initiate the payment.
10. Tender the card payment for the amount due for the deposit. 
11. Complete the deposit payment on the payment terminal. 
12. After the deposit is paid, select the option to use the same card for fulfillment and wait for the order to complete. 
13. Launch the point of sale for the Seattle store.
14. In the point of sale, select the 'Orders to pickup' operation from the welcome screen to see orders for pickup in store. 
15. Select one or more lines from the order created in the reference storefront and click 'Pick up'
16. The order will then be retrieved from the back office. 
17. When the order line details are retrieved from the back office, and an omni-channel capable card payment is detected, the user will be informed that a payment method is available.
18. Select "Use available payment method" to complete the transaction using the card details entered in the reference storefront.
19. The order line(s) will then be loaded on the transaction screen with a balance of zero due. Click on the 'Payments' tab to observe the tender line that was pulled down from the online order. 
20. Select any payment method to complete the transaction. 


### Buy in Store A, ship to customer

Steps:
1. Launch the point of sale for Houston.
2. Navigate to the transaction screen and in the number pad type "2001" to add Karen Berg to the transaction.
3. Add a line(s) to the transaction.
4. Click the 'Orders' button to see orders options.
5. Select 'Pick up all' select 'Customer order' when prompted.
6. In the search bar, type "Seattle", then select the Seattle store for pick up. 
7. Click 'OK' to accept today's date for the date of pickup.
9. Use 'Pay card' to initiate the payment.
10. Tender the card payment for the amount due for the deposit. 
11. Complete the deposit payment on the payment terminal. 
12. After the deposit is paid, select the option to use the same card for fulfillment and wait for the order to complete.
13. When the order is picked, packed and invoiced in the back office, the payment details provided at the point of sale will be used to capture the funds for the goods being shipped to the customer. 

## Scenario details

Aside from the above basic scenarios, several enhancements have been made to the payments SDK to support omni-channel payments. 

### Point of sale

#### Single swipe/dip for customer orders

Prior to the omni-channel payments feature, customer orders created at the point of sale that included deposits required the customer to swipe or dip their card twice. Once to pay the deposit and once to tokenize the card for fulfillment later. With omni-channel tokenization enabled, the customer only needs to swipe their card once to both pay the deposit and to authorize the amount due for goods to be fulfilled at a later time. At the time of fulfillment, the authorized funds are captured. Prior to omni-channel tokenization, only a recurring card token was created for later fulfillment. This meant that the funds for the pending fulfillment were not authorized and there was a greater chance of not being able to capture those funds later because they were not being held for that specific purchase.

*Note: Single swipe is not supported in 8.1.3. Customer orders in 8.1.3 use the same flow as experienced prior to omni-channel tokenization feature implementation. 

### Card cannot issue recurring card token

Some cards cannot be used for omni-channel payments because they do not support issuance of recurring card tokens. When an order is created at the point of sale and the deposit is paid using a card that does not support recurring card tokens, the point of sale user will experience the previous card tokenization flow. This means that if the customer wants to provide a payment to be used for subsequent order fulfillment, they will have to insert a second card. If the second card does not support recurring tokenization, the tokenization action will be declined and the cashier will be prompted to ask the customer to provide a different card. 

### Use a different card

If a customer comes to the store for order pickup, they have the option to use a different card. When the store associate is prompted to 'Use available payment method' upon order pickup, they can ask the customer if they want to use the same card. If the customer has lost the card made to create the order, the cashier can select 'Use a different payment method' to pay for the order with a different card. The next time the customer comes in to pick up more items for the same order, if the original card authorization is still valid, the cashier will again ask if the customer wants to use that card.

### Invalid authorization

If a card used to create an order is no longer valid, after products are selected for pickup, the payment capture request will fail. The POS payment connector will then try to create a new authorization and capture using the same card details. If the new authorization or capture fails, then the cashier will be informed that the payment could not be processed and they will need to get a new payment from the customer. 

### Multiple payments available

When an order is picked up with multiple tenders and multiple lines, the user will first be prompted to 'Use available payment method'. If there are multiple cards, upon selecting 'Use available payment method', existing card tender lines will be captured until the balance is met for the goods currently being picked up. The cashier will not be given the option to select a card to be used for the goods currently being picked up. 

## Related articles

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3)

