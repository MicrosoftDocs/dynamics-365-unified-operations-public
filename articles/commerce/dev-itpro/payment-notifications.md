---
title: Enable critical payment notifications using the Dynamics 365 Payment Connector for Adyen (preview)
description: Learn how to receive critical payment notifications in Microsoft Dynamics 365 Commerce headquarters using the Dynamics 365 Payment Connector for Adyen.
author: shajain
ms.date: 11/24/2025
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2025-11-15
---

# Enable critical payment notifications using the Dynamics 365 Payment Connector for Adyen (preview)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article explains how to receive critical payment notifications in Microsoft Dynamics 365 Commerce headquarters using the Dynamics 365 Payment Connector for Adyen.

Merchants can use the asynchronous payment notification framework to receive crucial and actionable notifications from Adyen, which are then displayed in Commerce headquarters. This functionality provides the operations team with the necessary visibility to take timely actions based on the notifications received.
 
## Prerequisites

### Minimum required version

The minimum required version of Commerce headquarters to use the payment notification service is Commerce version 10.0.46.

### Link your Commerce environment to a Dataverse environment

The payment notification service uses Microsoft Dataverse. To receive payment notifications, you must link your Commerce environment to a corresponding Dataverse environment.

Learn more in [Connect finance and operations apps with a new Microsoft Dataverse instance](../../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv.md) and [Connect finance and operations apps with an existing Microsoft Dataverse instance](../../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv.md).
 
### Required role to complete the setup

Some of the setup steps require a Commerce headquarters user who is either an administrator or has the Commerce Payment Administrator role assigned to them in Microsoft Power platform.

## Setup

The following setup steps are the same as the steps required to enable pay by link functionality. If you already enabled the pay by link feature, you can skip the steps in [Enable the features required for receiving the payment notifications](payment-notifications.md#enable-the-features-required-for-receiving-payment-notifications) and [Create a webhook to receive payment notifications from Adyen](payment-notifications.md#create-a-webhook-to-receive-payment-notifications-from-adyen) since they're already completed.

Learn more in [Enable pay by link in POS by using the Dynamics 365 Payment Connector for Adyen](pay-by-link-overview.md).

### Enable the features required for receiving payment notifications

To enable payment notifications functionality for pay by link, you must enable the following features in the Commerce headquarters **Feature management** workspace:
- **Enhanced wallet support and payment improvements**
    - Learn more in [Wallet payment support](wallets.md).
- **Enable unified payments experience in POS**
    - Learn more in [Check out faster with optimized payment flows](faster-checkout-pos.md).
- **Enable Payments Notification**
 
### Create a webhook to receive payment notifications from Adyen

To create a webhook to receive payment notifications from Adyen, complete the steps in [Create a webhook to receive payment notifications from Adyen](pay-by-link-overview.md#create-a-webhook-to-receive-payment-notifications-from-adyen) before **Test the connection to the payment notification service**.
 
After you complete the steps, Commerce can receive authorization notifications from Adyen. However, to receive nonauthorization type notifications such as failure to capture or refund payments, in headquarters you must go to the **Commerce shared parameters** \> **Payment notifications** form and enable the **Persist payment processor notifications** configuration. 
 
To select which notifications should be sent to Commerce, go to the Adyen customer portal and open the webhook you created. Under the **Events** section where you previously only selected **Authorization**, select the business-critical events that are actionable for your business. Learn more about the various event notifications that Adyen can send in [Webhooks](https://docs.adyen.com/api-explorer/Webhooks/latest/overview).

> [!IMPORTANT]
> You should only select business-critical events because notifications volume can grow quickly and consume critical storage space in headquarters. Microsoft recommends that you start by selecting three to four events such as **Capture**, **Capture_failed**, **Refund**, and **Refund_failed**.
 
After you select the events, save the changes and test the webhook from the Adyen customer portal by selecting the events one at a time. This method ensures that the Commerce notifications service receives the events. However, not all of the selected events are sent to headquarters, because some events are acknowledged and ignored. This prevents overloading headquarters and the Commerce notifications service. 

The following table lists which events can be saved to headquarters, and which events are ignored. 
  	
| Webhook name                                      | Saved to headquarters?                                                   |
|---------------------------------------------------|-------------------------------------------------------------------------|
| AUTHORISATION                                     | No. Only the authorizations related to pay by link functionality are saved.            |
| AUTHORISATION_ADJUSTMENT                          | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| AUTORESCUE                                        | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| CANCEL_AUTORESCUE                                 | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| CANCEL_OR_REFUND                                  | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| CANCELLATION                                      | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| CAPTURE                                           | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| ORDER_CLOSED                                      | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| ORDER_OPENED                                      | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| POSTPONED_REFUND                                  | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| RECURRING_CONTRACT                                | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| REFUND                                            | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| REFUND_WITH_DATA                                  | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| REFUNDED_REVERSED                                 | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| VOID_PENDING_REFUND                               | Partially. Only saved to headquarters when the **Success** property value for the event is **False**.      |
| CAPTURE_FAILED                                    | Yes                                                                     |
| CHARGEBACK                                        | Yes                                                                     |
| CHARGEBACK_REVERSED                               | Yes                                                                     |
| DIRECT_DEBIT_NOTICE_OF_CHANGE_NOTIFICATION        | Yes                                                                     |
| EXPIRE                                            | Yes                                                                     |
| ISSUER_COMMENTS                                   | Yes                                                                     |
| ISSUER_RESPONSE_TIMEFRAME_EXPIRED                 | Yes                                                                     |
| MANUAL_REVIEW_ACCEPT                              | Yes                                                                     |
| MANUAL_REVIEW_REJECT                              | Yes                                                                     |
| NOTIFICATION_OF_CHARGEBACK                        | Yes                                                                     |
| NOTIFICATION_OF_FRAUD                             | Yes                                                                     |
| OFFER_CLOSED                                      | Yes                                                                     |
| PREARBITRATION_LOST                               | Yes                                                                     |
| PREARBITRATION_OPEN                               | Yes                                                                     |
| PREARBITRATION_WON                                | Yes                                                                     |
| REFUND_FAILED                                     | Yes                                                                     |
| REPORT_AVAILABLE                                  | Yes                                                                     |
| REQUEST_FOR_INFORMATION                           | Yes                                                                     |
| SECOND_CHARGEBACK                                 | Yes                                                                     |
| TECHNICAL_CANCEL                                  | Yes                                                                     |

The following examples from the table can help you understand the expected behavior. 
 
- **AUTHORIZATION**: If you select this event in the Adyen customer portal, Adyen sends both successful and failed authorizations information as events, irrespective of where these events are generated (for example, payment terminal or e-commerce). This selection can result in thousands of event notifications every minute, but these notifications aren't actionable because the failures are visible to the sales associate using POS, or the customer using the e-commerce site. The Commerce system ignores all authorizations except those authorizations related to the pay by link functionality that originates from one of the Commerce channels.
- **CAPTURE**: If you select this event in the Adyen customer portal, Adyen sends both successful and failed capture event notifications, irrespective of where these events are generated. This selection can result in a large number of notifications, but success events aren't actionable and are ignored. However, for any capture that fails, Adyen sends the capture event with the **Success** property set to **False**. These failures are actionable because the product is sold, but the payment can't be captured. The operations team can then investigate the capture failure and manually recover the payment.
- **CAPTURE_FAILURE**: This event is different from the **CAPTURE** event notification with the **Success** property set to **False**. In rare cases, it's possible that Adyen sends the **CAPTURE** event notification with the **Success** property set to **True**, but the payment capture still fails due to rejection by the card scheme. Such events, if configured from the Adyen portal, are always saved in headquarters because they're actionable and are generated in low volume. Learn more in [Capture request failed due to scheme rejection](https://docs.adyen.com/api-explorer/Webhooks/1/post/CAPTURE_FAILED).

## View notifications in headquarters

To view event notifications saved to headquarters, go to **Retail and Commerce** \> **Inquiries and reports** \> **Payment notifications** and look under **Payment process notifications**.

## Purge old payment notifications

To ensure that old notifications are deleted to save the storage and keep the notifications form actionable, you can either manually delete notifications from the **Payment process notifications** form, or automatically delete notifications by running the **Purge payment provider notifications data** batch job. This batch job allows you to specify the number of days before which notifications are deleted.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
