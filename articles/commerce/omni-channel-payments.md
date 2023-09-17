---
# required metadata

title: Omni-channel payments overview
description: This article provides an overview of omni-channel payments in Dynamics 365 Commerce.
author: BrianShook
ms.date: 02/03/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: ["141393"]
ms.collection: get-started
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 8.1.3

---

# Omni-channel payments overview

[!include [banner](../includes/banner.md)]

This article provides an overview of omni-channel payments in Dynamics 365 Commerce. It includes a comprehensive list of supported scenarios, information about functionality, setup, and troubleshooting, and descriptions of some typical issues.

## Key terms

| Term | Description |
|---|---|
| Token | A string of data that a payment processor provides as a reference. Tokens can represent payment card numbers, payment authorizations, and previous payment captures. Tokens are important because they help keep sensitive data out of the point of sale (POS) system. They're sometimes also referred to as *references*. |
| Card token | A token that a payment processor provides for storage in the POS system. A card token can be used only by the merchant who receives it. Card tokens are sometimes also referred to as *card references*. |
| Authorization (auth) token | A unique ID that a payment process provides as part of the response that it sends to a POS system after the POS system makes an authorization request. An authorization token can be used later if the processor is called to perform actions such as reversing or voiding the authorization. However, it's most often used to capture funds when an order is fulfilled or a transaction is finalized. Authorization tokens are sometimes also referred to as *authorization references*. |
| Capture token | A reference that a payment processor provides to a POS system when a payment is finalized or captured. The capture token can then be used to reference the payment capture in subsequent operations, such as refund requests. | 
| Card not present | A term that refers to payment transactions where a physical card isn't presented. For example, these transactions can occur in e-commerce or call center scenarios. For these transactions, the payment-related information is manually entered on an e-commerce website, in a call center flow, or on the POS or payment terminal. |
| Card present | A term that refers to payment transactions where a physical card is presented and used on a payment terminal that is connected to the Microsoft Dynamics 365 POS system. |

## Overview

In general, the term *omni-channel payments* describes the ability to create an order in one channel and fulfill it in another channel. The key to omni-channel payment support is preserving payment details together with the rest of the order details, and then using those payment details when the order is recalled or processed in another channel. A classic example is the "Buy online, pick up in store" scenario. In this scenario, the payment details are added when the order is created online. They're then recalled at the POS to charge the customer's payment card at the time of pickup. 

All the scenarios that are described in this article can be implemented by using the standard Payments software development kit (SDK) that is provided with Commerce. The [Dynamics 365 Payment Connector for Adyen](/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3) provides an out-of-box implementation of every scenario that is described here. 

### Prerequisites

Every scenario that is described in this article requires a payment connector that supports omni-channel payments. The out-of-box Adyen connector can also be used, because it supports the scenarios that are made available through the Payments SDK. For more information about how to implement payment connectors, and about the Retail SDK in general, visit the [Retail for IT pros and developers home page](/dynamics365/unified-operations/retail/dev-itpro/dev-retail-home-page#payment-connectors).

#### Supported versions

The omni-channel payment capabilities that are described in this article were released as part of Microsoft Dynamics 365 for Retail version 8.1.3. 

#### "Card present" and "card not present" connectors

The Payments SDK relies on two sets of application programming interfaces (APIs) for payments. The first set of APIs is named **iPaymentProcessor**. It's used to implement "card not present" payment connectors that can be used in call centers and with the Microsoft Dynamics e-Commerce platform. For more information about the **iPaymentProcessor** interface, see the [Implement a payment connector and a payment device](https://download.microsoft.com/download/e/2/7/e2735c65-1e66-4b8d-8a3c-e6ef3a319137/The%20Guide%20to%20Implementing%20Payment%20Connector%20and%20Payment%20Device_update.pdf) white paper, which covers payments. 

The second set of APIs is named **iNamedRequestHandler**. It supports the implementation of "card present" payment integrations that use a payment terminal. For more information about the **iNamedRequestHandler** interface, see [Create a payment integration for a payment terminal](/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension). 

### Setup and configuration

The following components and setup steps are required:

- **eCommerce integration:** An integration with Commerce is required to support scenarios where an order originates in an online storefront. For more information about the Retail e-Commerce SDK, see [e-Commerce platform software development kit (SDK)](/dynamics365/unified-operations/retail/dev-itpro/ecommerce-platform-sdk). In a demo environment, the reference storefront supports omni-channel payment scenarios. 
- **Online payments configuration:** The setup of the online channel must include a payment connector that has been updated to support omni-channel payments. Alternatively, the out-of-box payment connector can be used. For information about how to configure the Adyen payment connector for online stores, see [Adyen payment connector](/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce). In addition to the eCommerce setup steps that are described in that article, the **Allow saving payment information in e-commerce** parameter must be set to **True** in the settings for the Adyen connector. 
- **Omni-channel payments configuration:** In the back office, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. Then, on the **Omni-channel payments** tab, set the **Use omni-channel payments** option to **Yes**. In Commerce versions 10.0.12 and later, this setting is in the **Feature Management** workspace. Select the **Omni-channel payments** feature and click **Enable now**. 
- **Payment services:** The call center uses the default payment connector on the **Payment services** page to process payments. To support scenarios such as "Buy in call center, pick up in store," this default payment connector must be the Adyen payment connector or a payment connector that meets the implementation requirements for omni-channel payments.
- **EFT service:** Payments through a payment terminal must be set up on the **EFT service** FastTab of the hardware profile. The Adyen connector supports omni-channel payments scenarios out of the box. Other payment connectors that support the **iNamedRequestHandler** interface can also be used if they support omni-channel payments.
- **Payment connector availability:** When an order is recalled, the payment tender lines that are recalled together with the order include the name of the payment connector that was used to create the authorizations that are associated with that order. When the order is fulfilled, the Payments SDK tries to use the same connector that was used to create the original authorization. Therefore, a payment connector that has the same merchant properties must be available for capture. 
- **Card types:** For omni-channel scenarios to work properly, each channel must have the same setup for tender types that can be used for omni-channel. This setup includes payment method IDs and card type IDs. For example, if the **Cards** tender type has an ID of **2** in the online store setup, it should have the same ID in the retail store setup. The same requirement applies to card type IDs. If card number **12** is set to **VISA** in the online store, the same ID should be set up for the retail store. 
- The Store Commerce app for Windows, Android, or iOS with built-in Hardware Station.
    -or-
- Store Commerce for web with connected shared Hardware Station. 

### Basic principle supporting omni-channel payments

Payment connectors and payment processors use tokens, or references, to reference interactions that are related to card payments. For example, when a payment authorization is requested, a reference to that authorization is provided. Therefore, the authorization can be referenced later, when funds are captured at the time of fulfillment. This authorization is unique to the merchant, payment connector, and processor. 

If an order that was created online is being picked up in the store, the same payment details for that order must be recalled and used. When the original details are provided as part of the request to capture a payment against the original authorization, the payment processor will be able to handle the request and capture the payment. 

To correctly reference the online order, a "card not present" payment connector that supports the same processor must also be available. In this way, the POS system can have one processor for "card present" payments, but it can also have access to other payment connectors so that it can fulfill orders that are created in other channels by using different payment processors. 

## Supported scenarios

The following omni-channel payment scenarios are supported:

- Buy online, pick up in store
- Buy in call center, pick up in store
- Buy in store A, pick up in store B
- Buy in store A, ship to customer

    > [!NOTE]
    > Payments made in the call center that map to the "Normal" payment function must be marked as **Prepay** = **Yes** to be reflected in the amount due when recalling the order in the POS. Non-prepay payments of type "Normal" are not recognized when the order is recalled in POS. 

Variations of these scenarios are also supported. For example, an online order might include both lines that will be shipped to the customer and lines that will be picked up in a store. All order fulfillment options are supported via omni-channel payments. 

The following sections describe the steps for each scenario and show how to run the scenario by using demo data. 

### Buy online, pick up in store

Before you start, make sure that the following prerequisites are in place:

- You have a reference storefront where the Adyen connector is configured.
- The **Omni-channel payments** option on the **Commerce shared parameters** page is set to **True**. In later versions this setting is moved to the **Feature Management** workspace where you can select the **Omni-channel payments** feature and click **Enable now**. 
- The Adyen payment connector is configured for the Houston POS register.
- The Store Commerce app for Windows, Android, or iOS with built-in Hardware Station.
    -or-
- Store Commerce for web with connected shared Hardware Station.

Follow these steps to run the scenario.

1. In the reference storefront, create an order for in-store pickup. Be sure to select the **Houston** store. 
2. Go through the checkout steps, and pay by using a test credit card number. You can find test credit card numbers on the [Adyen test card numbers page](https://docs.adyen.com/development-resources/test-cards/test-card-numbers/#description).
3. In Commerce, use the **Synchronize orders** batch job and the **P-001** distribution schedule to create the orders in the back office.
4. In the POS, on the welcome page, select the **Orders to pickup** operation to see the orders for in-store pickup. 
5. Select one or more lines from the order that was created in the reference storefront, and then select **Pick up**.

    The order is retrieved from the back office. 

6. When the order line details are retrieved from the back office, and a card payment that can be used for omni-channel is detected, you're informed that a payment method is available.
7. Select **Use available payment method** to complete the transaction by using the card details that were entered in the reference storefront.

    The order lines are loaded on the transaction page, and the balance due is 0 (zero). 

8. Select the **Payments** tab to view the tender line that was pulled from the online order. 
9. Select any payment method to complete the transaction. 

### Buy in call center, pick up in store

1. In Commerce, on the **Customer service** page, enter **Karen Berg** in the search bar, and then select **Search**. 
3. Select **Karen Berg** in the search results.
4. After Karen is loaded onto the **Customer service** page, select **New sales order**.
5. On the new sales order page, select **Header** to view the order header. 
6. On the **Order header** page, set the site to **Central** and the warehouse to **Houston**.
7. On the **Deliver** tab, set the **Mode of delivery** field to **60** for customer pickup.
8. Select **Lines**, and then add one or more lines to the order. 
9. Select **Complete** to enter the order completion flow.
10. Scroll down to the payments section, select **Add**, and then select a line where the payment method type is set to **Cards**. 
11. Select the plus sign (**+**) to add a card payment. 
12. Enter the details for a test credit card number that you found on the [Adyen test card numbers page](https://docs.adyen.com/development-resources/test-cards/test-card-numbers/#description), and then select **OK**.

    > [!NOTE]
    > If the card brand for the card number that you entered differs from the brand that was selected when the payment was initiated, the payment will still go through. However, it will be posted to the accounts that are mapped to the card brand that you selected in step 10.

12. Select **OK** again to close the **Order completion payments** dialog box.
13. On the **Sales order summary** page, select **Submit**.
14. In the POS, on the welcome page, select the **Orders to pickup** operation to see the orders for in-store pickup. 
15. Select one or more lines from the order that was created in the reference storefront, and then select **Pick up**.

    The order is retrieved from the back office. 

16. When the order line details are retrieved from the back office, and a card payment that can be used for omni-channel is detected, you're informed that a payment method is available.
17. Select **Use available payment method** to complete the transaction by using the card details that were entered in the reference storefront.

    The order lines are loaded on the transaction page, and the balance due is 0 (zero).

18. Select the **Payments** tab to view the tender line that was pulled from the online order. 
19. Select any payment method to complete the transaction. 

### Buy in store A, pick up in store B

1. Start the POS for the Houston store.
2. On the **Transaction** page, add Karen Berg to the transaction by using the number pad to enter **2001**.
3. Add one or more lines to the transaction.
4. Select **Orders** to see the order options.
5. Select **Pick up all**, and then, when you're prompted, select **Customer order**.
6. In the search bar, enter **Seattle**, and then select the **Seattle** store for pickup. 
7. Select **OK** to accept the current date as the date of pickup.
9. Select **Pay card** to initiate the payment.
10. Tender the card payment for the amount that is due for the deposit.
11. Complete the deposit payment on the payment terminal. 
12. After the deposit is paid, select the option to use the same card for fulfillment, and wait for the order to be completed. If 100% of the deposit is paid (from step 10 above), the funds are captured immediately against the card and an authorization token won't be available at invoicing because the funds have already been captured and tracked as paid.
13. Start the POS for the Seattle store.
14. In the POS, on the welcome page, select the **Orders to pickup** operation to see the orders for in-store pickup. 
15. Select one or more lines from the order that was created in the reference storefront, and then select **Pick up**.

    The order is retrieved from the back office. 

16. When the order line details are retrieved from the back office, and a card payment that can be used for omni-channel is detected, you're informed that a payment method is available.
17. Select **Use available payment method** to complete the transaction by using the card details that were entered in the reference storefront.

    The order lines are loaded on the transaction page, and the balance due is 0 (zero).

18. Select the **Payments** tab to view the tender line that was pulled from the online order. 
19. Select any payment method to complete the transaction. 

### Buy in store A, ship to customer

1. Start the POS for the Houston store.
2. On the **Transaction** page, add Karen Berg to the transaction by using the number pad to enter **2001**.
3. Add one or more lines to the transaction.
4. Select **Orders** to see the order options.
5. Select **Ship all**, and then, when you're prompted, select **Customer order**.
6. In the shipping method page, select **Standard overnight**, and then select **OK** to accept today's date as the shipping date. 
7. Select **OK** to accept the current date as the date of pickup.
8. Select **Pay card** to initiate the payment.
9. Tender the card payment for the amount that is due for the deposit. 
10. Complete the deposit payment on the payment terminal. 
11. After the deposit is paid, select the option to use the same card for fulfillment, and wait for the order to be completed. If 100% of the deposit is paid (from step 9 above), the funds are captured immediately against the card and an authorization token won't be available at invoicing because the funds have already been captured and tracked as paid.

When the order is picked, packed, and invoiced in the back office, the payment details that are provided at the POS will be used to capture the funds for the goods that are being shipped to the customer. 

## Scenario details

In addition to the basic scenarios that were just described, several enhancements have been made to the Payments SDK to support omni-channel payments. 

### POS

#### Single swipe/dip for customer orders

Before the omni-channel payments feature was implemented, when customer orders that included deposits were created at the POS, customers were required to swipe (or dip) their card two times: one time to pay the deposit and one time to tokenize the card for subsequent order fulfillment. When the omni-channel tokenization feature is turned on, customers must swipe their card only one time to both pay the deposit and authorize the amount that is due for goods that will be fulfilled later. At the time of fulfillment, the authorized funds are captured. Before the omni-channel tokenization feature was implemented, only a recurring card token was created for subsequent order fulfillment. Therefore, the funds for the pending fulfillment weren't authorized, and because those funds weren't being held for that specific purchase, it was less likely that they could be captured later.

> [!NOTE]
> Single swipe isn't supported in Retail version 8.1.3. Customer orders in version 8.1.3 use the same flow that was used before the omni-channel tokenization feature was implemented. 

### Cards that can't issue recurring card tokens

Some cards can't be used for omni-channel payments, because they don't support issuing recurring card tokens. When an order is created at the POS, if the deposit is paid by using a card that doesn't support recurring card tokens, the previous card tokenization flow is used. Therefore, a customer who wants to provide a payment that will be used for subsequent order fulfillment must present a second card. If the second card doesn't support recurring card tokens, the tokenization action will be declined, and the cashier will be prompted to ask the customer to provide a different card. 

### Using a different card

A customer who comes to the store for order pickup has the option to use a different card. When the cashier receives the **Use available payment method** prompt at the time of order pickup, the cashier can ask whether the customer wants to use the same card. If the customer has lost the card that was used to create the order and wants to pay for the order by using a different card, the cashier can select **Use a different payment method**. If the customer comes back later to pick up more items for the same order, if the original card authorization is still valid, the cashier can again ask whether the customer wants to use that card.

### Invalid authorizations

If the card that was used to create an order is no longer valid, when products are selected for pickup, the payment capture request will fail. The POS payment connector will then try to create a new authorization and capture by using the same card details. If the new authorization or capture fails, the cashier will be informed that the payment couldn't be processed. The cashier must then get a new payment from the customer. 

### Multiple available payments

When an order that has multiple tenders and multiple lines is picked up, the cashier first receives the **Use available payment method** prompt. If there are multiple cards, when the cashier selects **Use available payment method**, existing card tender lines will be captured until the balance is met for the goods that are currently being picked up. The cashier won't have the option to select the card that should be used for the goods that are being picked up. 

## Related articles

- [Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 Payment Connector for Adyen](/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3)
- [Configure BOPIS in a Dynamics 365 Commerce evaluation environment](./cpe-bopis.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
