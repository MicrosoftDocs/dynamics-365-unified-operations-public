---
# required metadata

title: Process unlinked refunds with the Dynamics 365 Commerce Adyen Connector
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

# Process unlinked refunds with the Dynamics 365 Commerce with Adyen Connector

[!include [banner](../includes/banner.md)]

This topic describes how unlinked refunds work using the Microsoft Dynamics 365 Payment Connector for Adyen, and reviews the ability to process a refund against a new payment method in point of sale (POS) or call center.

The Dynamics 365 Payment Connector for Adyen supports the ability to process refunds using a different payment method than was used for the original transaction. While it is recommended to use [linked refunds](linked-refunds.md) to process a refund against the originating payment method provided, there are scenarios where refunding to a different method is required. For example, the original card used for the original payment may now be expired, lost, or cancelled by the user. 

## Prerequisites

The following prerequisites must be completed before the Dynamics 365 Payment Connector for Adyen can process unlinked refunds:

- Set up [payment methods](../payment-methods.md).
- Set up [omni-channel payments](../omni-channel-payments.md).

## Additional configuration

The [Dynamics 365 Payment Connector for Adyen](adyen-connector.md) provides an out-of-box implementation for every supported refund scenario described below. Customers who aren't using the out-of-box implementation of the Dynamics 365 Payment Connector for Adyen must set up the connector that supports tokenization of credit cards.  

## Supported refund scenarios

Dynamics 365 Commerce supports refunds of transactions that were previously approved and confirmed. Refunds can consist of either a full refund or a partial refund of the transaction. Refunds cannot exceed the full amount of the original payment authorization. Unlinked refunds are only supported in POS and call center. 

## Enable unlinked refunds functionality

To enable unlinked refunds functionality in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**. 
1. On the **Omni-channel payments** tab, set the **Use omni-channel payments** option to **Yes**.

### Supported payment method variants

The following payment method variants support unlinked refunds out of the box:

- Cards
- Wallet

Not all payment method variants support unlinked refunds. The following table provides a list of common payment method support capability for linked and unlinked refunds.

|     Payment Method           |     Linked refund    |     Unlinked refund    |
|------------------------------|:--------------------------------:|:----------------------------------:|
|     amexcommercial           |     Yes                        |     Yes                          |
|     amexconsumer             |     Yes                        |     Yes                          |
|     amexcorporate            |     Yes                        |     Yes                          |
|     amexdebit                |     Yes                        |     Yes                          |
|     amexprepaid              |     Yes                        |     Yes                          |
|     amexprepaidreloadable    |     Yes                        |     Yes                          |
|     amexsmallbusiness        |     Yes                        |     Yes                          |
|     discover                 |     Yes                        |     Yes                          |
|     maestro                  |     Yes                        |     Yes                          |
|     maestrouk                |     Yes                        |     Yes                          |
|     mc                       |     Yes                        |     Yes                          |
|     mcalphabankbonus         |     Yes                        |     Yes                          |
|     mcprepaidanonymous       |     Yes                        |     Yes                          |
|     visa                     |     Yes                        |     Yes                          |
|     visaalphabankbonus       |     Yes                        |     Yes                          |
|     visacheckout             |     Yes                        |     Yes                          |
|     visadankort              |     Yes                        |     Yes                          |
|     visahipotecario          |     Yes                        |     Yes                          |
|     visasaraivacard          |     Yes                        |     Yes                          |
|     vpay                     |     Yes                        |     Yes                          |
|     givex                    |     **No**                         |     Yes                          |
|     svs                      |     **No**                         |     Yes                          |
|     cup                      |     Yes                        |     Yes                          |
|     diners                   |     Yes                        |     Yes                          |
|     interac                  |     **No**                         |     Yes                          |
|     jcb                      |     Yes                        |     Yes                          |
|     jcb_applepay             |     Yes                        |     Yes                          |
|     unionpay                 |     Yes                        |     Yes                          |

### Process an unlinked refund in POS

When a customer returns an item to a POS cashier with a valid receipt within the allowed period for returns, during processing for the return the **Return Payment** dialog box will include an option to **Choose a payment method** from the supported payment methods for refunds (cards, wallet).

### Process an unlinked refund in call center

When processing an unlinked refund in call center against an order, a call center employee choosing a different payment method from the originating method will be prompted to obtain an administrator override PIN in order to process the different payment method for the refund.

#### Set up an administrator override PIN for call center

To set up an administrator override PIN for call center in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Call center setup**, or search for "Override Permissions". 
1. Select the role for which you are allowing the unlinked refund processing permissions. 
1. On the **Returns** FastTab, set the **Allow alternate payment** option to **Yes**.

## Additional resources

[Dynamics 365 Payment Connector for Adyen](adyen-connector.md)

[Linked refunds of previously approved and confirmed transactions](linked-refunds.md)
