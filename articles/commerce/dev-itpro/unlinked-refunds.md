---
# required metadata

title: Unlinked refunds using the Dynamics 365 Commerce Adyen Connector
description: This topic describes how unlinked refunds work using the Microsoft Dynamics 365 Payment Connector for Adyen.
author: BrianShook
ms.date: 09/29/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: BrShoo
ms.search.validFrom: 2017-06-20
---

# Unlinked refunds using the Dynamics 365 Commerce with Adyen Connector

[!include [banner](../includes/banner.md)]

This topic describes how unlinked refunds work using the Microsoft Dynamics 365 Payment Connector for Adyen. This article reviews the ability to process the refund against a new payment method in POS or Call Center.

The Dynamics 365 Payment Connector for Adyen supports the ability to process refunds using a different payment method than was used for the original transaction. While it is recommended to use [linked refunds](linked-refunds.md) to process a refund against the originating payment method provided, there are scenarios where refunding to a different method is required. For example, the original card used for the original payment may now be expired, lost, or cancelled by the user. 

## Prerequisites

[Payment Method Setup](https://docs.microsoft.com/en-us/dynamics365/commerce/payment-methods)

[Omni-channel payments setup](https://docs.microsoft.com/en-us/dynamics365/commerce/omni-channel-payments)

## Additional configuration

Customers who aren't using the out-of-box implementation of the Dynamics 365 Payment Connector for Adyen must set up the connector that supports tokenization of credit cards. All the scenarios that are described in this topic can be implemented by using the standard payments software development kit (SDK) that is provided with Commerce. The [Dynamics 365 Payment Connector for Adyen](adyen-connector.md) provides an out-of-box implementation of every scenario that is described here.

## Supported refund scenarios

Dynamics 365 Commerce supports refunds of a transaction that was previously approved and confirmed. Refunds can be either a full refund or a partial refund of the transaction. Refunds cannot exceed the full amount of the original authorization which occurred. Unlinked refunds are only supported in POS and Call Center.

## Enable unlinked refunds functionality

To enable unlinked refunds functionality in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. 
1. On the **Omni-channel payments** tab, set the **Use omni-channel payments** option to **Yes**.

### Supported payment method variants

The following payment method variants support unlinked refunds out of the box:

- Cards
- Wallet

Not all payment method variants support unlinked refunds. Review the Adyen payment method variant specific documentation for further confirmation.

### Process an unlinked refund in POS

When a customer brings in an item for return and provides a receipt within the allowed period for returns, as the cashier processes the payment for the return the **Return Payment** dialog box will include an option to **Choose a payment method**. Here the option to choose a supported payment method for refunds (Card, Wallet)

### Process an unlinked refund in Call Center

When processing an unlinked refund in call center against an order, a call center employee choosing a different payment method from the originating method will be prompted to get an administrator override in order to process the different payment method for the refund.

### Set up administrator override PIN for call center

To set up an administrator override PIN for call center in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Call center setup** or search for "Override Permissions". 
1. Select the Role for which you are allowing the unlinked refund processing permissions, and 
1. On the **Returns** FastTab, set the **Allow alternate payment** option to **Yes**.

## Additional resources

[Dynamics 365 Payment Connector for Adyen](adyen-connector.md)

[Linked refunds of previously approved and confirmed transactions](linked-refunds.md)
