---
# required metadata

title: Omni-channel Commerce order payments
description: This topic describes the Omni-channel Commerce order payments feature.
author: rubendel
manager: Tonya.Fehr
ms.date: 05/13/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Omni-channel Commerce order payments

[!include [banner](../includes/banner.md)]

This topic describes the Omni-channel Commerce order payments feature that enables editing of e-Commerce and POS order payments from the back office.

## Availability

This feature is available starting with the 10.0.13 monthly update.

## Key terms

| Term | Description |
|---|---|
| Commerce payment | A payment associated with a customer order generated at the point of sale or in the e-commerce storefront after this feature has been enabled. |
| Order completion | Order completinn is the business logic in the Call Center that ensures payments have been collector before the order is submitted. The **Enable order completion** setting in call center parameters is used to enable this business logic in Call Center. For more details, visit the [Enable order completion](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-order-processing-options#enable-order-completion) section of the [Set up call center channels](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-order-processing-options) topic. 
| Call Center order | An order created in the back office by a Call Center user. |

## Overview

Dynamics 365 Commerce consists of 3 main channels: Point of Sale, e-Commerce, and Call Center. Until now, management of payment lines for orders created in those channels has not been uniform. For example, when creating and editing orders the Call Center there is an order completion flow that ensures payments are designated for those orders prior to fulfillment. Alternatively, POS and e-commerce orders have not supported Call Center order completion. The primary way to observe this lack of parity is by observing orders on the **Customer service** form in the back office and observing which orders have an active link to the **Payments** form. 

Order created in Call Center:

![Call center order with "Payments" link active](../dev-itpro/media/COP_CC_PAY.png)

Order created in the point of sale:

![POS order with disabled "Payments" link](../media/COP_NONCC_PAY.png)

This feature enables access to the payments form for orders created in e-commerce and the point of sale. In addition, with this feature enabled, those orders can be edited using the order completion function that was previously only available to Call Center orders.  

Order completion:

![POS or e-commerce order created with this feature enable has "Payments" link active](../media/COP_ORDERCOMPLETION.png)

## Prerequisite features

To enable Omni-Channel order payments, you first must enable several other features. These features should be enabled as a best practice because they address functional gaps related to orders. After OCOP has been enabled, some these features may be disabled, but that is discouraged because all testing for OCOP has been done with these features enabled.

| Feature name | Description | May be disabled later |
| --- | --- | --- |
| Omni-channel payments | Enables omni-channel payment scenarios such as buy online, pick up in store. For more information, visit the [Omni-channel payments overview](https://docs.microsoft.com/en-us/dynamics365/commerce/omni-channel-payments) topic. | No | 
| Unified payment posting journal defaults for Commerce | When this feature is enabled, business logic will be changed in regards to how customer payment and customer refund payment journals are created for orders created through Call Center, POS or e-Commerce channels. For more information, visit the [Unified payment posting journal defaults for Commerce](TBD) topic. | Yes |
| Duplicate payment protection on invoicing | This feature will enable duplicate payment protection for invoicing scenarios. It may affect customizations in invoicing scenarios. If your organization has customizations in this feature area, please ensure these customizations are refactored prior to enabling this option on production environments. | Yes |
| Enable refunds over multiple captures | This feature addresses an issue with performing multiple linked refunds against an order. | Yes |

## Prerequisite configurations

### Map payment methods to operations to payment methods

This feature requires that payment methods in all channels are mapped to a corresponding operation. This was not previously required, but is neccesary to support management of order payments in the back office. When the feature is enabled, warnings will be issued in the feature management for each payment method which does not have an equivalent operation mapping. Payment methods should be mapped to operations prior to enabling the feature to avoid receiving these errors at the time of feature enablement.

Example from call center:

![Operation mapped to payment method in call center](../media/COP_OPERATION.png)

### Call center is required

At least one Call Center channel must be configured in order to manage POS and e-commerce order payments through the back office. For more details on creating a call center, visit the [Set up a call center channel](https://docs.microsoft.com/en-us/dynamics365/commerce/channel-setup-callcenter#overview) article. 

### Users must be set up as call center users

Users who will be editing Commerce payments in the back office must be set up as call center channel users. For more details on setting up call center users, visit the [Set up a call center channel user](https://docs.microsoft.com/en-us/dynamics365/commerce/channel-setup-callcenter#set-up-channel-users) section of the call center article. 

### Enable order completion for call enters

Order completion must be enabled for Commerce payment editing function properly. For more information on order completeion, visit the [Enable order completion](https://docs.microsoft.com/en-us/dynamics365/commerce/set-up-order-processing-options#enable-order-completion) of the article explaining call center order processing options.

### Disable pay later

When customer orders are created at the point of sale, the store associate has the option to collect a card payment for fulfillment or they can select **Pay later** to skip collection of card details. When this feature is enabled, the option to **Pay later** shoudl be removed from the point of sale. To remove that option, search for **Functionality profiles**. In the **General** fasttab for the functionality profile, change the **Require payment for fulfillment** to **Card required**. These changes need to be synced to the channel data base to take effect at the point of sale. 

## Key scenarios

When this feature is enabled, e-commerce and POS order credit card payments can easily be managed through order completion. For example, if a customer places an online order, then calls into the Call Center to request a change to the order, the order completion function will allow for the payments on that order to be adjusted to support the new balance due.

Properties on order line that can be edited prior to payment capture:
- Card type
- Card number
- Payment amount
- Percent amount

For orders that were created in POS or the e-Commerce Storefront, the following scenarios in call center order completion apply: 

### Editing order payments

#### Uncaptured card payments

| Scenario | Description | Supported |
| --- | --- | --- |
| **Editing to specify a higher amount** | For card payments which have been authorized, but not yet captured, the payment amount may be increased. When this is done, a new authorization will be created for the new amount and the old authorization will be voided. | Yes |
| **Editing to specify a lower amount** | Card payments which have been authorized, but not yet captured, may be reduced. When a payment line amount is reduced, the previous authorization is cancelled and a new authorization is created for the lower amount. | Yes |
| **Removing an old card and adding a new one** | Uncaptured card payment authorizations may be removed from orders and be replaced by a payment on a different card. When this is done, the authorization for the first card is cancelled and an authorization for the new card will be obtained when the order is submitted. | Yes |

#### Editing partially and fully captured card payments

| Scenario | Description | Supported |
| --- | --- | --- |
| **Editing a payment that has already been used to invoice part of the order** | When an order with Commerce payments has already been partially invoiced, the card payment amount for the existing card may be edited through call center order completion down to the amount that has already been captured. A new card may then be applied to cover the balance due for the order.  | Yes |
| **Editing amount when the car payment is fully captured** | If a card payment has already been fully captured, but the amount for that card payment is increased through call center order completion, upon submittal a new authorization for the card will be created for the amount that the payment was increased. | Yes |

### Removing order payments

| Scenario | Description | Supported |
| --- | --- | --- |
| **Authorized payments** | Commerce order card payments may be removed through order completion only if they have not been partially captured. | Yes |
| **Prepayments** | Prepayments may not be removed through order completion. Prepayments have payment vouchers already associated with them and may not be removed from an order once they have been applied. | No |
| **Partially captured payments** | If the payment is in a 'Paid' state, but has not been fully captured, then the payment cannot be removed. However, the payment amount can be reduced to the already posted amount and the uncaptured amount will be voided from the authorization. | No | 
| **Fully captured credit card payments and prepayments** | Cannot be removed from the order. | Yes |

### Order and sales line cancellation

**Order cancellation for credit card payments that have not been captured**
Voided

**Order cancellation for credit card payments that have been captured**
Refunded

**Line cancellation**
If an order is modified to cancel an order line, then order completion must be used to complete the process. During order cancellation, the payment amount should be reduced to reflect the new order total. 

### Linked refund 

Return orders for non-Call Center orders generated in the back office can execute linked refunds against the credit card used to pay for the original order.

### Unlinked refund

Return orders can be refunded to a credit card other than the one used to pay for the original order. 

### Orders with prepayments

Prepayments already have payment vouchers associated with them.That meass



## Related articles

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
