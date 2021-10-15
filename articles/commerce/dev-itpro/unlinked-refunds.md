---
# required metadata

title: Process unlinked refunds with the Dynamics 365 Commerce Payment Connector for Adyen
description: This topic describes how unlinked refunds work when the Microsoft Dynamics 365 Payment Connector for Adyen is used.
author: BrianShook
ms.date: 10/07/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: BrShoo
ms.search.validFrom: 2017-06-20
---

# Process unlinked refunds with the Dynamics 365 Commerce Payment Connector for Adyen

[!include [banner](../includes/banner.md)]

This topic describes how unlinked refunds work when the [Microsoft Dynamics 365 Payment Connector for Adyen](adyen-connector.md) is used. It also reviews the ability to process a refund against a new payment method in point of sale (POS) or call center.

The Dynamics 365 Payment Connector for Adyen supports the ability to process refunds by using a different payment method than was used for the original transaction. Although we recommend that you use [linked refunds](linked-refunds.md) to process a refund against the originating payment method that was provided, refunds to a different method are required in some scenarios. For example, the card that was used for the original payment might now be expired or lost, or it might have been canceled by the user.

## Prerequisites

The following prerequisites must be completed before the Dynamics 365 Payment Connector for Adyen can process unlinked refunds:

- Set up [payment methods](../payment-methods.md).
- Set up [omni-channel payments](../omni-channel-payments.md).

## Additional configuration

The Dynamics 365 Payment Connector for Adyen provides an out-of-box implementation for every supported refund scenario that is described in the next section. Customers who aren't using the out-of-box implementation of the Dynamics 365 Payment Connector for Adyen must set up the connector that supports tokenization of credit cards.

## Supported refund scenarios

Dynamics 365 Commerce supports refunds of transactions that were previously approved and confirmed. Refunds can consist of either a full refund or a partial refund of the transaction. Refunds can't exceed the full amount of the original payment authorization. Unlinked refunds are supported only in POS and call center.

## Enable unlinked refunds functionality

To enable unlinked refunds functionality in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **Omni-channel payments** tab, set the **Use omni-channel payments** option to **Yes**.

### Supported payment method variants

The following payment method variants support unlinked refunds out of the box:

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

A customer returns an item to a POS cashier within the allowed period for returns and has a valid receipt. During processing for the return, the **Return Payment** dialog box includes a **Choose a payment method** option. The cashier can then select a payment method among the supported payment methods for refunds (cards and wallet).

### Process an unlinked refund in call center

When an unlinked refund is processed against an order in call center, a call center employee selects a payment method that differs from the originating method. The employee is then prompted to obtain an administrator override personal identification number (PIN). The PIN is required before the different payment method can be processed for the refund.

#### Set up an administrator override PIN for call center

To set up an administrator override PIN for call center in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Call center setup**, or search for "Override Permissions."
1. Select the role to allow the unlinked refund processing permissions for.
1. On the **Returns** FastTab, set the **Allow alternate payment** option to **Yes**.

## Additional resources

[Dynamics 365 Payment Connector for Adyen](adyen-connector.md)

[Linked refunds of previously approved and confirmed transactions](linked-refunds.md)
