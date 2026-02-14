---
title: Omnichannel Commerce order payments
description: Learn about the omnichannel Commerce order payments feature in Microsoft Dynamics 365 Commerce.
author: ravimeda
ms.date: 02/12/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: raeda
ms.search.validFrom: 2019-01-01
ms.custom: 
  - bap-template
---

# Omnichannel Commerce order payments

[!include [banner](../includes/banner.md)]

This article describes the omnichannel Commerce order payments feature in Microsoft Dynamics 365 Commerce. This feature lets you edit e-commerce and point of sale (POS) order payments from Commerce headquarters.

Dynamics 365 Commerce consists of three main channels: POS, e-commerce, and call center. In Commerce version 10.0.12 and earlier, the management of payment lines for orders that you create in each channel isn't uniform. For example, when you create and edit orders in the call center, an order completion flow ensures that you specify payments for those orders before fulfillment. However, POS and e-commerce orders don't support call center order completion. To see the lack of uniformity, go to the **Customer service** page in Commerce headquarters, and notice which orders you can access the **Payments** page for by using the **Payments** button.

The following illustration shows an order that was created in the call center. Notice that the **Payments** button is available when the row for this order is selected. 

:::image type="content" source="../dev-itpro/media/COP_CC_PAY.png" alt-text="Screenshot of a call center order with the Payments button available.":::

The following illustration shows an order that was created at the POS. Notice that the **Payments** button is unavailable when the row for this order is selected.

:::image type="content" source="../dev-itpro/media/COP_NONCC_PAY.png" alt-text="Screenshot of a POS order with the Payments button unavailable.":::

In Commerce version 10.0.13 and later, you can access the **Payments** page for orders that you create in e-commerce and the POS. Additionally, when you turn on the omnichannel Commerce order payments feature, you can edit the orders by using the order completion function that was previously available only for call center orders.

When you enable this feature, use the **Sales order summary** dialog to edit payments for orders originating in POS and e-commerce.  

:::image type="content" source="../dev-itpro/media/COP_ORDERCOMPLETION.png" alt-text="Screenshot of the Sales order summary dialog with the Payments button available for a POS or e-commerce order.":::

## Key terms

| Term | Description |
|---|---|
| Commerce payment | A payment that is associated with a customer order that was generated at the POS or in the e-commerce storefront. |
| Order completion | The business logic in the call center that ensures that payments are collected before an order is submitted. Turn on this business logic by using the **Enable order completion** setting in the call center parameters. For more information, see [Enable order completion](../set-up-order-processing-options.md#enable-order-completion). 
| Call center order | An order that a call center user creates in Commerce headquarters. |
| Accounts receivable (AR) sales order | An order that a user who isn't a call center user creates through Accounts receivable in Commerce headquarters. You can't edit payments for AR sales orders through call center order completion. |

## Prerequisites

To turn on the omnichannel Commerce order payments feature, first turn on several other features and complete other configurations. Aside from being requirements for enabling **Omnichannel Commerce order payments**, turn on these features as a best practice because they address functional gaps that are related to orders. 

If any of the prerequisites are missing when you try to turn on the omnichannel Commerce order payments feature, you receive a message that states that you can't continue until the prerequisite features and configurations are in place.

:::image type="content" source="../dev-itpro/media/COP_PRE.png" alt-text="Screenshot of the message about prerequisite features and configurations.":::

> [!NOTE]
> When you enable the **Omnichannel Commerce order payments** feature, the call center **Enable order completion** button is hidden in headquarters on the **General** FastTab of your channel at **Retail and Commerce \> Channels \> Call Centers**.


### Prerequisite features

The following features are required for omnichannel Commerce order payments to work correctly.

| Feature name | Description |
|---|---|---|
| Unified payment posting journal defaults for Commerce | This feature changes the way that business logic creates customer payment and customer refund payment journals for orders that are created through the call center, POS, or e-commerce channel. |
| Omnichannel payments | This feature enables omnichannel payment scenarios, such as buy online, pick up in store. For more information, see [Omnichannel payments overview](../omni-channel-payments.md). |  
| Duplicate payment protection on invoicing | This feature enables duplicate payment protection for invoicing scenarios. Commerce payments functionality might affect customizations in invoicing scenarios. If your organization has invoicing customizations, make sure that they're refactored before you turn on Commerce payments functionality in production environments. | 
| Enable refunds over multiple captures | This functionality improves that capability to do multiple linked refunds against an order. |
| Enable manual void of expired credit card payment lines when authorizations are expired | This feature adds support for manual deletion of payment lines if they expire and the authorization can't be refreshed. |

> [!NOTE]
> If you plan to accept multiple payment methods for online orders in your online channel (for example, loyalty points and credit card payments), enable both the **Omnichannel Commerce order payments** feature (in headquarters at **System administration \> Workspace \> Feature management**) and the call center **Enable order completion** setting (on the **General** FastTab of your channel at **Retail and Commerce \> Channels \> Call Centers**). The **Enable order completion** setting is enabled by default and hidden if the **Omnichannel Commerce order payments** feature is enabled.

### Configure prerequisites

#### Map payment methods to operations

Map payment methods in all channels to corresponding operations so that Commerce headquarters supports the management of order payments. Map payment methods before you turn on the omnichannel Commerce order payments feature to avoid receiving warnings for each payment method that doesn't have an equivalent operation mapping.

The following illustration shows the mapping of a payment method to an operation in call center.

:::image type="content" source="../dev-itpro/media/COP_OPERATION.png" alt-text="Screenshot of a payment method mapped to an operation in the call center.":::

#### Configure a call center

To manage POS and e-commerce order payments through Commerce headquarters, configure at least one call center channel. For more information about how to create a call center channel, see [Set up a call center channel](../channel-setup-callcenter.md).

#### Set up users as call center users

Set up users who edit Commerce payments in Commerce headquarters as users of the call center channel. For more information about how to set up call center users, see [Set up a call center channel user](../channel-setup-callcenter.md#set-up-channel-users).

#### Turn on order completion for call centers

Turn on the order completion function for call centers. Order completion enforces business logic that makes sure that orders can be paid during fulfillment. For more information about order completion, see [Enable order completion](../set-up-order-processing-options.md#enable-order-completion).

## Turn on the omnichannel Commerce order payments feature

After you add the prerequisites that are described in the previous section, turn on the omnichannel Commerce order payments feature.

1. In the **Feature management** workspace, select the **All** tab to view the list of all features, and then search for **Omnichannel Commerce order payments**.

    :::image type="content" source="../dev-itpro/media/COP_ENABLE.png" alt-text="Screenshot of the Omnichannel Commerce order payments feature in the Feature management workspace.":::

1. Select the feature, and then select **Enable now**.

> [!IMPORTANT]
> The omnichannel Commerce order payments feature includes many changes to payments and order management workflows. Test these changes thoroughly before turning on this feature in a production environment.
> After you enable this feature, run the 1070 and 1110 scheduler jobs to synchronize changes to the channel database. 

To distinguish channel orders that the system creates while the omnichannel Commerce order payments feature is turned on from other orders, the system shows a **Payments type** field on the order header. For POS and e-commerce orders, this field is set to **Commerce**.

:::image type="content" source="../dev-itpro/media/COP_HEADERCOM.png" alt-text="Screenshot of an order where the Payments type field is set to Commerce.":::

For call center orders, the **Payments type** field is set to **Call Center**. For sales orders that are created in Accounts receivable, the field isn't shown.

## Fulfill orders after the omnichannel Commerce order payments feature is turned off

You must fulfill POS and e-commerce orders that are created while the omnichannel Commerce order payments feature is turned on. If you turn off the feature, you can't process the orders until you turn the feature back on.

## Manage orders that were created before the omnichannel Commerce order payments feature is turned on

You can process orders that were created before the omnichannel Commerce order payments feature is turned on. The editing experience for those orders doesn't change after the feature is turned on, and the orders don't change to accommodate omnichannel Commerce order payment workflows. Additionally, sales orders that non–call center users create in Accounts receivable continue to behave as they did before the feature was turned on.

## Key scenarios

When you turn on the omnichannel Commerce order payments feature, you can manage credit card payments for e-commerce and POS orders through order completion. For example, a customer places an online order and then calls the call center to request a change to the order. In this case, the order completion function enables you to adjust the payments on that order to support the new balance due.

You can edit the following properties on an order line before payment capture:

- Card type
- Card number
- Payment amount
- Percent amount

### Edit order payments

The following scenarios in call center order completion apply to order payments that you create at the POS or in the e-commerce storefront.

#### Uncaptured card payments

For any card payment line on an order that you didn't yet partially invoice, you can edit the following properties before payment capture:

- Card type
- Card number
- Payment amount
- Percent amount

After you edit the payments, the order submission process corrects any changes that are required for edited payment lines.

| Scenario | Description | Supported |
|---|---|---|
| Edit to specify a higher amount. | For card payments that you authorize but don't yet capture, you can increase the payment amount. When you increase the amount on a payment line, the system creates a new authorization for the new amount and voids the old authorization. | Yes |
| Edit to specify a lower amount. | For card payments that you authorize but don't yet capture, you can reduce the payment amount. When you reduce the amount on a payment line, the system creates a new authorization for the new amount and voids the old authorization. | Yes |
| Remove an old card, and add a new card. | Remove uncaptured card payment authorizations from orders and replace them by a payment on a different card. The system cancels the authorization for the first card, and obtains an authorization for the new card when you submit the order. | Yes |

#### Partially and fully captured card payments

| Scenario | Description | Supported |
|---|---|---|
| Edit a payment that was used to invoice part of the order. | When an order that has omnichannel Commerce payments is partially invoiced, the card payment amount for the existing card can be edited through call center order completion, down to the amount already captured. A new card can then be applied to cover the balance due for the order. | Yes |
| Edit fully captured card payment lines to specify a higher amount. | If a card payment is fully captured, but you increase the amount for that card payment through call center order completion, the system creates a new authorization for the card for the increased amount when you submit the order. | Yes |

### Remove order payments

| Scenario | Description | Supported |
|---|---|---|
| Authorized payments | Remove Omnichannel Commerce order card payments from an order through order completion, but only if they're not partially captured. | Yes |
| Prepayments | Prepayments can't be removed through order completion. Prepayments can't be removed from an order after they're applied. Payment vouchers are already associated with them. | No |
| Partially captured payments | If the payment is in a **Paid** state but isn't fully captured, it can't be removed. However, the payment amount can be reduced to the amount that was already posted. When this scenario happens, a request is sent to the payment provider to reduce the authorization amount to equal the new payment amount. | No |
| Fully captured credit card payments and prepayments | Fully captured credit card payments and prepayments can't be removed from the order. | No |

### Cancel order and sales lines

| Scenario | Description | Supported |
|---|---|---|
| Order cancellation for credit card payments that aren't captured | If an order is canceled, card payment authorizations that aren't captured are canceled. | Yes |
| Order cancellation for credit card payments that are captured but aren't invoiced | If an order is created at the POS, and a card payment is used to capture a deposit, the order is canceled before invoicing. The card payment is automatically refunded as part of order cancellation. | Yes |
| Order cancellation for orders that are partially shipped and invoiced | For orders that are partially shipped and invoiced, cancellation cancels the fulfillment of lines that aren't invoiced. Open credit card authorizations for the remaining balance on the order aren't automatically canceled. | Manual refund is required. |
| Order cancellation for orders that are invoiced but aren't shipped | If an order is fully invoiced, but some of the items aren't shipped, you can cancel the order. However, payments that are captured for that order aren't automatically refunded. Open authorizations for items that aren't invoiced aren't canceled but expire according to the authorization expiration policies of the bank that issued the card. | Manual refund is required. |
| Line cancellation for items that aren't fulfilled or invoiced | If an order line that isn't fulfilled or invoiced is canceled, the order completion process requires that payments are reduced to equal the new order total. |

### Refunds

| Scenario | Description | Supported |
|---|---|---|
| Linked refunds for POS and e-commerce orders | Return orders that are generated from orders that originate from the POS and e-commerce channels can issue linked refunds against the cards that were charged during invoicing. | Yes |
| Linked refunds for AR sales orders | Although the payments can't be edited through order completion, returns that are issued for AR sales orders can be subject to a linked refund to the original card that was charged during invoicing. | 
| Unlinked refunds | If the merchant's return policies and the payment processor allow this approach, unlinked refunds can be specified for return orders in cases where the order was originally paid in cash, for example, or in cases where the original card that was used for payment is no longer active. | Yes |
| Refunds to noncard prepayments | Return orders that were originally paid through noncard prepayments, such as cash or credit memo payments, aren't subject to linked refund. An appropriate payment method, such as **Check**, must be specified for the refund payment. Organizations that allow unlinked refunds can refund noncard prepayments to credit cards that weren't previously used for the order, if the payment processor allows this approach. | Yes |

### Credit notes

If a customer wants to return items or get reimbursement for items or services that you sold and received payment for, create and post a sales credit memo that specifies the requested change. To include the correct sales invoice information, you can create the sales credit memo directly from the posted sales invoice or you can create a new sales credit memo with copied invoice information.

- **Accounts receivable > All sales orders > Open an existing sales order > Sell > Credit note**
- **Accounts receivable > All sales orders > Create a new sales order > Sell > Credit note**

If you need more control of the sales return process, such as warehouse documents for the item handling or better overview when receiving items from multiple sales documents with one sales return, create sales return orders. A sales return order automatically issues the related sales credit memo and other return-related documents, such as a replacement sales order, if needed.

- **Accounts receivable > All return orders > Create a new return order**
- **Retail and Commerce > Customers > Customer service > Select the customer account > Select the invoiced order > Create a new return order**

> [!NOTE]
> A credit memo created from the existing sales order doesn't provide the option to invoice the order.

### Edit and remove orders that have prepayments

| Scenario | Description | Supported |
|---|---|---|
| Edit prepayment tender lines. | Payment vouchers are associated with prepayment tender lines. Therefore, prepayment tender lines can't be edited or removed. | No |

## Related changes

To support omnichannel Commerce order payments, changes to existing functionality were introduced in Commerce version 10.0.13.

### Consistent selection of payment journals when sales orders and refund payments are posted

In Commerce version 10.0.12 and earlier, payment journal assignment is inconsistent across channels. In Commerce version 10.0.13 and later, if you turn on the omnichannel Commerce order payments feature, all channels use the payment vouchers that you specify on the **Posting** tab of the **Commerce parameters** page.

:::image type="content" source="../dev-itpro/media/COP_VOUCH.png" alt-text="Screenshot of the payment voucher assignment on the Commerce parameters page.":::

### Check payment method

Orders that you create at the POS don't include a check number when they're created in Commerce headquarters. When you turn on the omnichannel Commerce order payments feature, **9999** is the check number for orders that you create at the POS and pay for by check.

The check number isn't required when **Check** is specified as the refund method of payment.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
