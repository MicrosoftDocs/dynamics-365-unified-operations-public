---
title: Process customer order pickups in POS
description: Learn about the functionality for processing customer order pickups in Microsoft Dynamics 365 Commerce point of sale (POS).
author: hhainesms
ms.date: 11/18/2026
ms.topic: how-to
ms.author: shajain
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---

# Process customer order pickups in POS

[!INCLUDE [banner](includes/banner.md)]

This article explains the functionality for processing customer order pickups in Microsoft Dynamics 365 Commerce point of sale (POS).

When a [customer order](customer-orders-overview.md) is created for store pickup, a store user can use the point of sale (POS) application to start the pickup of inventory. POS runs the final payment capture as required. It also completes the inventory and financial posting for the quantities to be picked up.

If you're a store user, you can perform the pickup by using either the **Recall order** operation or the **Order fulfillment** operation in POS. To make the **Pick up** operation available, you must first follow one of these steps:

- To use the **Recall order** operation, search for and select the order to be picked up.
- To use the **Order fulfillment** operation, search for and select one or more order lines.

If the selected order or order lines aren't configured for pickup at that specific store, or if the order is already fully picked up, the **Pick up** operation is unavailable.

:::image type="content" source="media/pickupoperation.png" alt-text="Screenshot of the Pick up operation in POS." lightbox="media/pickupoperation.png":::

In Microsoft Dynamics 365 Commerce version 10.0.17 and later, turn on the **Improved user experience for pick up order processing in Point of Sale** feature through Feature management in Commerce headquarters. If this feature is turned off, users can't select pickup quantities. By default, the full quantity that was ordered for the line is the quantity to be picked up. This experience can be problematic, because users might forget to select some items for pickup when they perform the pickup through order fulfillment.

The **Improved user experience for pick up order processing in Point of Sale** feature gives users more control over the selection of products to be picked up and the quantity of those products to be picked up. Users don't have to select every line of the sales order on the order fulfillment page before they select **Pick up**. All the items that can be picked up are shown. Users can specify multiple lines for pickup even if only one product line is selected.

When the **Improve user experience for pick up order processing in Point of Sale** feature is turned on, and you select the **Pick up** operation, the **Pick up** dialog box appears. There, you can select the items and quantities to be picked up. By default, any ordered quantity that has inventory in a picked or packed state is considered eligible for pickup. By default, that quantity is set as the pickup quantity. You can change the quantity that was entered if the quantity isn't 0 (zero) and doesn't exceed the total open (that is, noninvoiced) quantity for the selected line.

:::image type="content" source="media/pickupselect.png" alt-text="Screenshot of the Pick up dialog box for selecting items and quantities." lightbox="media/pickupselect.png":::

After you select the quantities to be picked up and then select **Pick up**, the transaction page appears. If the [omni-channel payments](omni-channel-payments.md) feature is turned on, and there are preauthorized credit card payments on file, you must apply the payment.

On the transaction page, the system calculates the amounts that are due by calculating the total that's due for the selected pickup items and then subtracting any previously applied deposits or authorized credit card payments. You must process payment to complete the pickup transaction. If the [screen layout](pos-screen-layouts.md) of the transaction page is configured so that it includes the **Conclude transaction** operation, and no amount is due, you can complete the transaction without selecting a payment method. If the **Conclude transaction** operation isn't available, you can select the **$0.00 amount due** link in the **Totals** pane to conclude the transaction without having to select a payment method.

:::image type="content" source="media/pickupcart.png" alt-text="Screenshot of the transaction page for a customer order pickup transaction." lightbox="media/pickupcart.png":::

## Changing pickup lines or quantities

If you need to change the pickup quantity after selecting the items for pickup, select **Set quantity**. You can't set the pickup quantity to **0** (zero) or increase it to a value that exceeds the noninvoiced quantity that remains for the ordered line. To remove a pickup line from the transaction cart, select **Void transaction**. The current transaction stops, and the flow for the **Pick up** operation restarts.

If the **Improve user experience for pick up order processing in Point of Sale** feature is turned on, organizations can add a button for the **Change pickup lines** operation to the screen layout of the transaction page. After you create the pickup transaction cart in POS and select items, you can select **Change pickup lines** if you need to change the pickup items but don't want to void the whole transaction. In the **Change pickup lines** dialog box that appears, you can change the pickup items and quantities. The transaction cart is then updated to reflect your changes.

:::image type="content" source="media/pickupchange.png" alt-text="Screenshot of the Change pickup items dialog box." lightbox="media/pickupchange.png":::

## Streamline pickup order workflows in Store Commerce

Starting with Commerce release version 10.0.50, store admins can enable the enhanced customer order pickup experience in the Store Commerce application (also known as POS). Store associates can complete eligible pickups without opening checkout, collect multiple orders for the same customer in one pickup session, and add carry-out items when checkout is needed. The experience also supports capturing the pickup person's details and signature, and unpicking items that a customer hasn't collected.

### What changes in the pickup experience

| Before these improvements | After these improvements |
| ------------------------- | ------------------------ |
| Prepaid pickups require associates to open the transaction page and complete checkout, even when the amount due is $0. | **Quick pickup** completes eligible pickups without opening the transaction page. |
| Associates complete customer order pickups one order at a time. | Associates can complete eligible pickups from multiple orders for the same customer in one quick pickup session. |
| Associates can't add extra items to a pickup transaction. Customers need a separate transaction for those purchases. | Associates can add carry-out items during checkout-based pickup and collect one payment for the new items and any remaining pickup balance. |
| Pickup processes need a way to record who collected the goods. | Retailers can enable capture of the pickup person's details and signature. |
| Store associates need to reverse picking when a customer doesn't collect staged goods. | Associates can unpick eligible picked items from POS before following the applicable cancellation process. |

### Enable and configure the pickup experience

1. In Commerce headquarters, go to the feature management workspace, and enable the feature named **Enable modernized order fulfillment experience on POS**.
1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS profiles** > **Functionality profiles**.
1. Select the functionality profile assigned to the participating store.
1. Select **Edit**.
1. Configure the following settings for your pickup process.
1. Save the profile.
1. Run the **1070 - Channel configuration** job to distribute channel configuration changes.

| Setting | Configuration | Effect |
| ------- | ------------- | ------ |
| **Enable quick pickup** | Set to **Yes** to offer quick pickup for eligible customer orders. | Associates can complete eligible pickups without going to the checkout transaction page. |
| **Enable capturing pickup person details** | Set to **Yes** if your business needs to record the person who collects the goods. | Enables the pickup-person details and signature capture experience during quick pickup. The captured information applies to all orders included in the pickup session. |
| **Allow adding carry-out items during pickup** | Set to **Yes** to allow extra purchases during checkout-based pickup. | Associates can add carry-out products to the pickup transaction and collect a single payment. |

Enable the settings that support your store's process. For example, enable quick pickup to speed up prepaid collections, and enable carry-out additions so associates can handle extra purchases when using checkout-based pickup.

> [!NOTE]
> Pickup-person capture is configurable. Enabling this capability isn't the same as confirming that every field or a signature is mandatory. Confirm the capture requirements and supported signature input method in your deployed build.

If several stores share the profile, consider the impact on every store that uses it.

### Select the appropriate pickup flow

| Customer situation | Flow to use |
| ------------------ | ----------- |
| The order is fully paid or fully covered by an authorization, and no extra purchases need to be added to the pickup transaction. | Use **Quick pickup**. |
| The customer is permitted to pay on account and has sufficient available credit for the pickup balance. | Use **Quick pickup** to charge the applicable balance to the customer's account. |
| The customer has several eligible pickup orders. | Select the orders for that customer and use **Quick pickup**. |
| Payment must be collected and isn't covered by an existing authorization or an eligible customer account. | Use checkout-based pickup. |
| The customer wants to purchase extra products in the same transaction. | Use checkout-based pickup with **Allow adding carry-out items during pickup** enabled. |

Quick pickup skips the checkout page, not the payment or order completion. Completing a quick pickup invoices the selected lines and captures an applicable open payment authorization. For an eligible on-account customer, the applicable remaining balance is charged to the customer's account.

### Complete a quick pickup

1. In Store Commerce, open **Recall order** or **Order fulfillment**.
1. Find the customer's pickup order.
1. Select the eligible order or pickup lines.
1. Select **Quick pickup**.
1. In the pickup dialog, specify the quantities the customer is collecting. Use **Fulfill all** to select all eligible quantities, or scan items or enter quantities as appropriate.
1. If pickup-person capture is enabled, enter the pickup person's details and capture the signature as prompted.
1. Complete the pickup.

The pickup completes without opening the checkout transaction page.

### Add carry-out items during checkout-based pickup

Use checkout-based pickup when the customer wants to add products to the same transaction or needs to pay a remaining balance.

1. Open **Recall order** or **Order fulfillment**.
1. Find and select the pickup order or pickup lines.
1. Select **Pickup & checkout**.
1. Specify the items and quantities the customer is collecting.
1. On the transaction page, scan or add the extra products and select the **Carry out** mode of delivery for the newly added items.
1. Collect payment for any remaining pickup balance.
1. Complete the transaction.

> [!NOTE]
> You must enable **Allow adding carry-out items during pickup** in the store's functionality profile. Quick pickup doesn't open the transaction page for adding products.

### Capture the pickup person's details and signature

Enable **Enable capturing pickup person details** when your business needs a record of who collected an order. This record is useful when an employee or another authorized person collects goods on behalf of a business customer. This information is added as a note to the sales order.

During quick pickup, record the pickup person's details and capture the signature when prompted. For a multi-order pickup session, collect the information once; it is retained for all selected orders for audit purposes.

Follow your organization's identity-verification, privacy, and retention policies when collecting this information.

### Unpick items that aren't collected

Picking items means preparing them for collection. Completing customer pickup hands over the goods and completes the applicable order and payment processing. Use **Unpick** to reverse eligible picking when staged goods aren't collected. Don't use it to reverse a completed customer pickup.

1. In Store Commerce, open **Order fulfillment**.
1. Find the order with picked items that aren't collected.
1. Select the eligible picked lines from that order.
1. Select **Unpick** from the available fulfillment actions.
1. Confirm the items and quantities to unpick.
1. Complete the action.

Unpicking reverses picking so the goods can be returned to stock and the order can proceed through the applicable cancellation process. If the order must be canceled, perform that action separately.

### Limitations and considerations

- Multiple-order quick pickup is limited to one customer per pickup session.
- Quick pickup requires full payment coverage, a usable authorization, or an eligible on-account customer with sufficient available credit.
- The new items added during pickup are carry-out items, not items for later shipment or pickup.
- Unpicking doesn't automatically cancel an order and isn't a return or refund of goods already collected.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
