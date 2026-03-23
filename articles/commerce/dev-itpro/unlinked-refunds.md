---
title: Process unlinked refunds with the Dynamics 365 Commerce Payment Connector for Adyen
description: Learn how unlinked refunds work when the Microsoft Dynamics 365 Payment Connector for Adyen is used.
author: BrianShook
ms.date: 02/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-06-20
ms.custom: 
  - bap-template
---

# Process unlinked refunds with the Dynamics 365 Commerce Payment Connector for Adyen

[!include [banner](../includes/banner.md)]

This article describes how unlinked refunds work when the [Microsoft Dynamics 365 Payment Connector for Adyen](adyen-connector.md) is used. It also reviews the ability to process a refund against a new payment method in point of sale (POS) or call center.

The Dynamics 365 Payment Connector for Adyen supports the ability to process refunds by using a different payment method than was used for the original transaction. Although you should use [linked refunds](linked-refunds.md) to process a refund against the originating payment method that the customer provided, some scenarios require refunds to a different method. For example, the card that was used for the original payment might now be expired or lost, or the user might cancel it.

## Prerequisites

Before the Dynamics 365 Payment Connector for Adyen can process unlinked refunds, complete the following prerequisites:

- Set up [payment methods](../payment-methods.md).
- Set up [omni-channel payments](../omni-channel-payments.md).

## Additional configuration

The Dynamics 365 Payment Connector for Adyen provides an out-of-box implementation for every supported refund scenario that the next section describes. Customers who aren't using the out-of-box implementation of the Dynamics 365 Payment Connector for Adyen must set up the connector that supports tokenization of credit cards.

## Supported refund scenarios

Dynamics 365 Commerce supports refunds of transactions that were previously approved and confirmed. Refunds can consist of either a full refund or a partial refund of the transaction. Refunds can't exceed the full amount of the original payment authorization. POS and call center support unlinked refunds.

## Enable unlinked refunds functionality

To enable unlinked refunds functionality in Commerce headquarters, follow these steps:

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **Omni-channel payments** tab, set the **Use omni-channel payments** option to **Yes**.

### Supported payment method variants

The following payment method variants support unlinked refunds:

- Cards
- Wallet

Not all payment method variants support unlinked refunds. The following table provides a list of common payment methods and shows each method's support capability for linked and unlinked refunds.

| Payment method        | Linked refund | Unlinked refund |
|-----------------------|:-------------:|:---------------:|
| amexcommercial        | Yes           | Yes             |
| amexconsumer          | Yes           | Yes             |
| amexcorporate         | Yes           | Yes             |
| amexdebit             | Yes           | Yes             |
| amexprepaid           | Yes           | Yes             |
| amexprepaidreloadable | Yes           | Yes             |
| amexsmallbusiness     | Yes           | Yes             |
| discover              | Yes           | Yes             |
| maestro               | Yes           | Yes             |
| maestrouk             | Yes           | Yes             |
| mc                    | Yes           | Yes             |
| mcalphabankbonus      | Yes           | Yes             |
| mcprepaidanonymous    | Yes           | Yes             |
| visa                  | Yes           | Yes             |
| visaalphabankbonus    | Yes           | Yes             |
| visacheckout          | Yes           | Yes             |
| visadankort           | Yes           | Yes             |
| visahipotecario       | Yes           | Yes             |
| visasaraivacard       | Yes           | Yes             |
| vpay                  | Yes           | Yes             |
| givex                 | **No**        | Yes             |
| svs                   | **No**        | Yes             |
| cup                   | Yes           | Yes             |
| diners                | Yes           | Yes             |
| interac               | **No**        | Yes             |
| jcb                   | Yes           | Yes             |
| jcb_applepay          | Yes           | Yes             |
| unionpay              | Yes           | Yes             |

### Process an unlinked refund in POS

A customer returns an item to a POS cashier within the allowed period for returns and has a valid receipt. During processing for the return, the **Return Payment** dialog box includes a **Choose a payment method** option. The cashier can then select a payment method from the supported payment methods for refunds, such as cards and wallet options.

### Process an unlinked refund in call center

When a call center employee processes an unlinked refund against an order, they select a payment method that differs from the originating method. The employee is then prompted to enter an administrator override personal identification number (PIN). The PIN is required before the different payment method can be processed for the refund.

#### Set up an administrator override PIN for call center

To set up an administrator override PIN for call center in Commerce headquarters, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> Call center setup**, or search for "Override Permissions."
1. Select the role to grant unlinked refund processing permissions.
1. On the **Returns** FastTab, set the **Allow alternate payment** option to **Yes**.

## Additional resources

[Dynamics 365 Payment Connector for Adyen](adyen-connector.md)

[Linked refunds of previously approved and confirmed transactions](linked-refunds.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]