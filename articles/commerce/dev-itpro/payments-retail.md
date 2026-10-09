---
title: Payments FAQ
description: This article answers frequently ask questions about payment options in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 10/09/2026
ms.topic: faq
ms.reviewer: mirao
ms.search.region: Global
ms.author: mirao
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Version 1611
ms.assetid: 99079d81-fde2-4432-8cee-82bbcc3bd57

---

# Payments FAQ

[!INCLUDE [banner](../../includes/banner.md)]

This article answers frequently ask questions about payment options in Microsoft Dynamics 365 Commerce.

## What payment scenarios are supported?

- Set up a merchant account.
- Process a call center order.
- Process an online order.
- Process a POS cash-and-carry transaction by using an accepting page.
- Process a POS cash-and-carry return by using an accepting page.
- Process a POS cash-and-carry return by using an accepting page.
- Process a POS customer order by using an accepting page.
- Process a POS cash-and-carry transaction by using Microsoft Dynamics Commerce Retail Hardware Station.
- Process a POS cash-and-carry return by using Hardware Station.
- Process a POS customer order by using Hardware Station.
- Buy online, pick up in store.
- Buy in call center, pick up in store.

## Which payment providers are supported and in what regions?

- Adyen is supported for card present and card not present transactions. For a list of supported regions, visit the [Dynamics 365 Payment Connector for Adyen overview page](/dynamics365/unified-operations/retail/dev-itpro/adyen-connector?tabs=8-1-3).
- PayPal is supported for online purchases. For a list of supported regions, visit the [Dynamics 365 Payment Connector for PayPal overview page](../paypal.md).
- Mastercard Simplify is no longer supported for new customers.

## What is the TestConnector, and how should I use it?

Commerce references a **TestConnector** in the payment connector setup pages for **Payment services**, **Online store payment accounts**, and **Hardware profile EFT service connectors**. The TestConnector simulates payment gateway responses without actually sending the payment to a gateway. It can return approvals, declines, partial approvals, and errors based on predefined test inputs.

Use the TestConnector only in test environments for the following limited point of sale (POS) scenarios:

- POS basic credit card test transaction
- POS basic unlinked test refund transaction

The TestConnector isn't supported for online store or call center channels, or for user acceptance testing (UAT) and production environments.

Many scenarios in Commerce payments require token usage and references that the TestConnector doesn't support. To test scenarios and validate test patterns, use a payment gateway test account within your sandbox environment. Using an actual gateway's test environment is the best way to ensure that all scenarios work as expected during testing.

### Which amounts trigger simulated responses in the TestConnector?

The TestConnector uses predefined payment amounts to simulate the responses listed in the following sections. Amounts are in the transaction's currency and use a period as the decimal separator.

#### Authorization

For credit-card authorization, the requested amount determines the simulated response.

| Requested amount | Simulated response |
| ---------------- | ------------------ |
| `1.12` | `Declined` with result `Failure`. |
| `1.14` | `Declined` with result `None`. |
| `1.16` | `Declined` with result `Referral`. |
| `1.18` | `Partial Approval` for `1.13` if the request allows partial authorization. Otherwise, `Declined`. |
| `1.20` | `Declined` with result `ImmediateCaptureFailed`. |
| `1.22` | `Approved`. The response also returns an available balance of `10.00` when the amount's text matches `1.22`. |
| `1.24` | `Timed out` with result `Failure`. |
| `4.18` | `Partial Approval` for `4.12` if the request allows partial authorization. Otherwise, `Declined`. |

#### Capture

| Requested capture amount | Simulated response |
| ------------------------ | ------------------ |
| `2.12` | `Declined` with result `Failure`. |
| `2.14` | `Capture queued for batch` with result `Success`. |
| `2.16` | `Unknown error has occurred` with result `None`. |
| `2.18` | `Declined` with result `Failure`. |
| `2.20` | `Invalid voice authorization code` with result `Failure`. |
| `2.22` | `Multiple captures are not supported` with result `Failure`. |
| `2.24` | `Capture timed out` with result `Failure`. |

#### Refund

| Requested refund amount | Simulated response |
| ----------------------- | ------------------ |
| `3.12` | `Declined` with result `Failure`. |
| `3.14` | `Approved` with result `Success`. |
| `3.16` | `Unknown error has occurred` with result `None`. |
| `3.18` | `Timed out` with result `Failure`. |
| `3.20` | `Refund is not supported` with result `Failure`. |

#### Void

For void, the original approved authorization amount determines the simulated response.

| Original approved authorization amount | Simulated response |
| -------------------------------------- | ------------------ |
| `2.18` or `4.12` | `Declined` with result `Failure`. |
| `4.14` | `Unknown error has occurred` with result `None`. |
| `4.16` | `Authorization is already voided` with result `Failure`. |
| `4.20` | `Void timed out` with result `Failure`. |

## What is a payment connector and when do I need to deploy and implement one?

Payment connectors are software components that you set up to enable an application to process payments for transactions where the card isn't present and transactions where the card is present.

You can use Microsoft-provided connectors such as Adyen, or ISV partners can build custom connectors. You typically build a connector to meet the business needs of a customer. Create custom connectors when you need a new type of payment type, such as linked refunds. If you're doing business in certain geographies, you might need new connectors if the default connectors don't support those regions.

## Are other payment connector providers supported?

Yes, but you must connect them by using customization.

## What is the service level agreement (SLA) for default payment connectors like Adyen?

If the issue relates to Adyen connector setup, see [Dynamics 365 Payment Connector for Adyen overview](/dynamics365/unified-operations/retail/dev-itpro/adyen-connector).

For other setup or functional issues associated with the Dynamics 365 Payment Connector, create a Microsoft Support request.

If the issue originates from the device itself or Adyen's processing service, use the following email template to start the support process with the Adyen team. To expedite troubleshooting, ensure that the email contains all the required details.

| Field | Value |
| ----- | ----- |
| To | `support@adyen.com` |
| Cc | |
| Subject line | Microsoft Dynamics Support Request |
| Body | <p>Hi Support,</p><p>Please provide support for the following issue:</p><ul><li>Merchant account</li><li>Environment (Test/Prod)</li><li>Channel (POS/call center/Commerce e-commerce)</li><li>Payment Service Provider (PSP) reference number, if the issue involved a specific transaction. (You can find the PSP reference number on the receipt, in the Adyen Customer Area, or on the transactions menu on the POS terminal.)</li><li>Screenshot or photo of the error message, if applicable.</li><li>Event Viewer logs (in .txt format)</li><li>Description of the issue and troubleshooting steps that you tried.</li></ul> |

## If a supported payment provider issues an update, does Microsoft automatically update the payment connector or do I need to work with the payment provider to get the updated payment connector?

If the payment connector provider issues a payment connector update, Microsoft includes the updated version of the payment connector in the next planned release of Dynamics 365 Commerce. However, you can also work directly with the payment connector provider to uptake it earlier.

## Does Dynamics 365 Commerce support "cash out" or "cash back" operations during the checkout process in point of sale (POS)?

No, POS doesn't support cash-back or cash-out operations during a transaction. However, you can customize the system through extensibility by using cash return and payment operations that are similar to gift card cash-out operations.

## Related information

- [Create an end-to-end payment integration for a payment terminal](end-to-end-payment-extension.md)
- [Deploy payment connectors](deploy-payment-connector.md)
- [Create Windows installers for payment connectors](create-windows-installer-payment-connector.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
