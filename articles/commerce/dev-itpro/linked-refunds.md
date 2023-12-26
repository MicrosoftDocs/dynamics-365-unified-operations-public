---
title: Linked refunds of previously approved and confirmed transactions
description: This article describes how to enable and use Linked refunds.
author: josaw1
ms.date: 05/18/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2019-03-28
ms.dyn365.ops.version: Retail 10.0.1 update
ms.custom: 
ms.search.industry: Retail
---

# Linked refunds of previously approved and confirmed transactions

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/preview-banner.md)]

Returns are an important operation for retailers. The ability to accept returns for sales and refund payments to customers gives retailers a way to service the needs of customers and to help resolve their issues.

This article provides information about how to configure and use linked refunds. A linked refund is a refund of a transaction that was previously approved and confirmed. The refund can be either a full refund or a partial refund of the transaction, and it can't exceed the full amount of the original authorization. The functionality for linked refunds is available in Microsoft Dynamics 365 Retail version 10.0.1.

In Microsoft Dynamics 365 Retail version 10.0 and earlier, retailers can process refunds to cards, but cashiers must manually specify these refunds. Cashiers can process refunds to the original mode of payment only if the customer provides that mode of payment. Therefore, by providing new card details, customers can use the return process to move balances from one card to another and therefore do unauthorized card balance transfers.

By using linked refunds, retailers can greatly reduce risk by making sure that refunds are processed only to the card that was authorized during the original transaction. To help prevent unauthorized card balance transfers, the system can prompt cashiers to use the confirmed and approved card token to process refunds. By using the original mode of payment for refunds, retailers can help reduce their card authorization costs.

## Prerequisites

[Payment method setup](../payment-methods.md) 

[Omni-channel payments setup](../omni-channel-payments.md)

### Additional setup

Customers who aren't using the out-of-box implementation of the Adyen Connector must set up the connector that supports tokenization of credit cards. All the scenarios that are described in this article can be implemented by using the standard Payments software development kit (SDK) that is provided with Commerce. The [Dynamics 365 Payment Connector for Adyen](adyen-connector.md?tabs=8-1-3) provides an out-of-box implementation of every scenario that is described here.

## Turn on the linked refunds functionality

The linked refunds functionality works with the omni-channel payments functionality that is available in Microsoft Dynamics 365 Retail 8.1.3 and later.

To turn on the linked refunds functionality in headquarters, go to **System administration \> Workspaces \> Feature management** and enable the **Omni-channel payments** feature.

> [!NOTE]
> In versions prior to Commerce version 10.0.11, omnichannel payments are enabled in headquarters at **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. On the **Omni-channel payments** tab, set the **Use omni-channel payments** option to **Yes**.

When you turn on the omni-channel payments functionality, you change the business process flow for calculating shipping charges and other charges, and for adding those charges to point of sale (POS) sales. Therefore, make sure that you test and train your employees before you turn on this functionality.

When the omni-channel payments functionality is turned on, the card payment tokens that are used in one channel (for example, a call center or the Store Commerce app) will be available in all channels that are set up for the retailer. For POS applications, the linked refunds functionality will also be turned on. For call center, Store Commerce app, and e-commerce applications, customers can still manually enter card numbers for payment.

### Supported flows

Cashiers can process a refund to the card that was used during the original transaction, even if the card isn't presented for the return. Supported flows include the following:

- Linked refunds for cash-and-carry transactions that use credit or debit cards.
- Linked refunds for customer orders that use credit or debit cards.
- Linked refunds when the **Unified return processing experience in POS** feature is enabled, but only if a single invoice is being returned at a time. 
 
### Unsupported flows

- Linked refunds for transactions that use gift cards.
- Linked refunds for transactions that use loyalty cards.
- Linked refunds for exchange orders.
- Multiple return orders in the same transaction.
- Returns without a receipt or customer account details.
- Linked refunds when the **Unified return processing experience in POS** feature is enabled, and multiple invoices are being grouped at once for the return

## Enable refunds over multiple captures

This feature enables multiple linked refunds against the same customer order.
1.	Go to the **Feature management** workspace and search for **Enable refunds over multiple captures**.
2.	Select **Enable refunds over multiple orders** and then click **Enable**.


## Use case examples

This section presents examples of use cases to help you understand the configuration and use of linked refunds and payment authorizations in the context of a customer order or a return where a receipt is presented. These examples show the behavior of the application when the **Omni-channel payments** parameter has been turned on.

### Customer account–based or receipt-based return that has a single card authorization

A customer comes to return an item that was purchased by using a single credit card. The customer provides a receipt, and the return is being made within the allowed period for returns. When the cashier scans the receipt, the item for return is processed. When the cashier processes the payment refund by selecting the button for any payment method, the existing credit card authorization is shown.

![Single card authorization.](media/LinkedRefundsSingleAuthorization.jpg)

When the cashier selects the credit card authorization, the payment refund is processed, and the **Transaction end** screen appears. If a receipt printing is configured, the cashier is prompted to print a receipt.

### Customer account–based or receipt-based return that has multiple card authorizations

A customer comes to return an item that was purchased by using multiple credit cards. When the cashier scans the receipt, the item for return is processed. When the cashier processes the payment refund by selecting the button for any payment method, all the existing credit card authorizations are shown.

![Multiple card authorizations.](media/LinkedRefundsMultipleAuthorization.jpg)

When the cashier selects a credit card authorization, the payment refund is processed. If more must be refunded, the current transaction screen shows the remaining amount. When the cashier processes the payment refund for this amount, the remaining credit card authorizations are shown. This process continues until there is no remaining amount that must be refunded.

After the full amount is successfully refunded, the cashier can complete the transaction, and a receipt can be printed as configured.

## Related articles

- [Payments FAQ](payments-retail.md)
- [Dynamics 365 Payment Connector for Adyen](adyen-connector.md?tabs=8-1-3)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
