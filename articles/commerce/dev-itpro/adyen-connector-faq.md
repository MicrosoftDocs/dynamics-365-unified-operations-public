---
title: Dynamics 365 Payment Connector for Adyen FAQ
description: This article provides answers to frequently asked questions regarding the Microsoft Dynamics 365 Payment Connector for Adyen.
author: Reza-Assadi
ms.date: 02/11/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2019-01-01
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.custom: 
  - bap-template
---

# Dynamics 365 Payment Connector for Adyen FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the Microsoft Dynamics 365 Payment Connector for Adyen. For an overview of the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md).

### Can I share a payment terminal with multiple hardware stations?

No. A single hardware station or point of sale (POS) terminal can use a payment terminal. If you try to connect multiple hardware stations to one payment terminal, you run into locking problems. If multiple POS devices need to share a payment terminal, you must deploy a Microsoft Internet Information Services (IIS) hardware station to manage the payment terminal.

### Can I reuse my existing payment terminal with the Adyen connector?

No. Adyen injects its software into its payment terminals. Therefore, you can't use existing payment terminals that don't come preconfigured with Adyen with the Dynamics 365 Payment Connector for Adyen.

### Do I need a static IP address for the Adyen payment terminal?

Yes. The Store Commerce app needs a known IP address to communicate with the Adyen payment terminal. Although you can change the IP address of the Adyen payment terminal in the client, keeping up with changing IP addresses involves significant overhead and could cause business disruption.

### Can I use my merchant bank?

Yes. Adyen works with any merchant bank.

### When I configure card type bin range mapping in Commerce for the Adyen Connector, how many digits can I use?

Adyen returns the first six digits of the card for matching. Six digits are the maximum for card type bin range mapping when you use the Dynamics 365 Payment Connector for Adyen.

### How do Commerce transaction events align with Adyen payment status codes?

The following tables show common payment events in Dynamics 365 Commerce and their corresponding payment status codes, as listed in the "Payments" section of the Adyen portal.

#### POS terminal

| Commerce event | Adyen payment status code |
|---|---|
| Initial transaction in progress | **AuthorizedPending** |
| Successful transaction | **Authorized** |
| Successful transaction in progress | **SentForSettle** |
| Successful transaction completed | **Settled** |
| Void | **Canceled** (if authorized state only) or **Refunded** (if funds are captured) |
| Cancel | Canceled items don't appear in the Adyen portal. |
| Linked refund | **SentForRefund** or **Refunded** |
| Unlinked refund | The original payment line stays in the final state (for example, **Authorized**). The new line shows **RefundPending** for the payment method that is used. |
| External gift card as payment method | **SettledExternally** |
| External gift card add funds | **RefundPending** |

#### Call center and online channels

| Commerce event | Adyen payment status code |
|---|---|
| Successful Transaction | **Authorized** |
| Authorisation | **Settled** |
| Void | **Canceled** (if authorized state only) or **Refunded** (if funds are captured) |
| Cancel | Canceled items don't appear in the Adyen portal. |
| Linked Refund | **SentForRefund** or **Refunded** (*Call center only*) |
| Unlinked Refund | The original payment line stays in the final state (for example, **Authorized**). The new line shows **RefundPending** for the payment method that is used. (*Call center only*) |
| External Gift Card as Payment Method | **SettledExternally** |
| External Gift Card Add Funds | **RefundPending** |

Call center and online stores consider a payment successful even though Adyen might still be processing the payment originating service for the settled state.

For a complete list of Adyen payment status codes, see [Payments lifecycle](https://docs.adyen.com/account/payments-lifecycle).

### Can I cancel a refund action?

Adyen supports two types of refunds: referenced and unreferenced. You can't cancel referenced refunds. For unreferenced refunds, the system tries to cancel the refund, but successful cancellation depends on the payment issuer and the potential delay that Adyen configures for processing. If an error occurs when you force a local refund cancellation in POS, POS allows for a credit. However, if the cancellation of the unlinked refund isn't accepted on the payment gateway, discrepancies might occur between Dynamics 365 reports and Adyen reporting. For more information about Adyen's cancellation of unreferenced refunds, see [Cancel an unreferenced refund](https://docs.adyen.com/point-of-sale/basic-tapi-integration/refund-payment/cancel-unreferenced/).

### Is 3D Secure (3DS) authentication supported in Commerce call center iFrame payment windows?

No, the payment window used in the Commerce call center payment forms (configured via the connector on the **Payment Services** page in headquarters) doesn't support 3DS authentication flows. Customer authentications that require passwords or Strong Customer Authentication (SCA) are only supported in the online channel where customers directly enter their sensitive and protective data.

## Next steps

For guidance on troubleshooting common issues related to the Dynamics 365 Payment Connector for Adyen, see [Troubleshoot Dynamics 365 Payment Connector for Adyen](adyen-connector-troubleshoot.md).

## Additional resources

[Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md)

[Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md)

[Troubleshoot Dynamics 365 Payment Connector for Adyen](adyen-connector-troubleshoot.md)

[Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
