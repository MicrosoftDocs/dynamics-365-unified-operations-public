---
# required metadata

title: Dynamics 365 Payment Connector for Adyen FAQ
description: This topic provides answers to frequently asked questions regarding the Microsoft Dynamics 365 Payment Connector for Adyen.
author: rassadi
ms.date: 09/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Dynamics 365 Payment Connector for Adyen FAQ

[!include [banner](../includes/banner.md)]

This topic provides answers to frequently asked questions regarding the Microsoft Dynamics 365 Payment Connector for Adyen. For an overview of the Dynamics 365 Payment Connector for Adyen, see [Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md). 

### Can I share a payment terminal with multiple hardware stations?

No. Payment terminals can only be used by a single hardware station or point of sale (POS) terminal. Attempting to connect multiple hardware stations to a single payment terminal will result in locking issues. If a payment terminal must be shared by multiple POS devices, an IIS hardware station must be deployed to manage the payment terminal. 

### Can I reuse my existing payment terminal with the Adyen connector?

No. Adyen payment terminals are injected with the Adyen software. Therefore, existing payment terminals that aren't preconfigured with Adyen can't be reused with the Dynamics 365 Payment Connector for Adyen.

### Do I need a static IP address for the Adyen payment terminal?

Yes. Modern POS requires a known IP address to communicate with the Adyen payment terminal. Although the IP address of the Adyen payment terminal can be changed in the client, attempts to keep up with changing IP addresses involve significant overhead and could cause business disruption.

### Can I use my merchant bank?

Yes. Adyen can work with any merchant bank.

### When I configure card type bin range mapping in Commerce for the Adyen Connector, how many digits can I use?

Adyen returns the first six digits of the card for matching. Six digits are the maximum for card type bin range mapping when the Dynamics 365 Payment Connector for Adyen is used.

### How do Commerce transaction events align with Adyen payment status codes?

The following tables show common payment events in Dynamics 365 Commerce and their corresponding payment status codes, as listed in the "Payments" section of the Adyen portal.

#### POS terminal

| Commerce event | Adyen payment status code |
|---|---|
| Initial transaction in progress | **AuthorisedPending** |
| Successful transaction | **Authorised** |
| Successful transaction in progress | **SentForSettle** |
| Successful transaction completed | **Settled** |
| Void | **Cancelled** (if authorized state only) or **Refunded** (if funds have been captured) |
| Cancel | Canceled items aren't expected to appear in the Adyen portal. |
| Linked refund | **SentForRefund** or **Refunded** |
| Unlinked refund | The original payment line remains in the final state (for example, **Authorized**). The new line shows **RefundPending** for the payment method that is used. |
| External gift card as payment method | **SettledExternally** |
| External gift card add funds | **RefundPending** |

#### Call center and online channels

| Commerce event | Adyen payment status code |
|---|---|
| Successful Transaction | **Authorised** |
| Authorisation | **Settled** |
| Void | **Cancelled** (if authorized state only) or **Refunded** (if funds have been captured) |
| Cancel | Canceled items aren't expected to appear in the Adyen portal. |
| Linked Refund | **SentForRefund** or **Refunded** (*Call center only*) |
| Unlinked Refund | The original payment line remains in the final state (for example, **Authorized**). The new line shows **RefundPending** for the payment method that is used. (*Call center only*) |
| External Gift Card as Payment Method | **SettledExternally** |
| External Gift Card Add Funds | **RefundPending** |

Call center and online stores will consider a payment successful even though Adyen might still be processing the payment originating service for the settled state.

For a complete list of Adyen payment status codes, see [Payments lifecycle](https://docs.adyen.com/account/payments-lifecycle).

### Can I cancel a refund action?

Adyen supports two types of refunds, referenced refunds and unreferenced refunds. Referenced refunds can not be canceled. For unreferenced refunds, an attempt to cancel is made but depends upon the payment issuer and potential delay set for the processing on Adyen's configurations. If forcing a local refund cancellation in Point-of-Sale upon encountering an error in the cancellation, Point-of-Sale will allow the ability to credit, but this may cause discrepencies between Dynamics reports and the Adyen reporting if the cancellation of the unlinked refund is not accepted on the payment gateway. For more information on Adyen's cancellation of unreferenced refunds, see their article [Cancel an unreferenced refund](https://docs.adyen.com/point-of-sale/refund-payment/cancel-unreferenced). 

## Next steps

For guidance on troubleshooting common issues related to the Dynamics 365 Payment Connector for Adyen, see [Troubleshoot Dynamics 365 Payment Connector for Adyen](adyen-connector-troubleshoot.md). 

## Additional resources

[Dynamics 365 Payment Connector for Adyen overview](adyen-connector.md)

[Set up Dynamics 365 Payment Connector for Adyen](adyen-connector-setup.md)

[Troubleshoot Dynamics 365 Payment Connector for Adyen](adyen-connector-troubleshoot.md)

[Payments FAQ](/dynamics365/unified-operations/retail/dev-itpro/payments-retail)

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
