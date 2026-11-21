---
title: Suspend and resume a transaction in the point of sale (POS)
description: Learn how users can suspend or pin in-progress transactions, and then resume them later or on a different register using Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 11/21/2026
ms.topic: how-to
ms.author: anvenkat
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.assetid: 7cd68ecc-cc09-48ab-8cb8-48d5c304effa
ms.custom: 
  - bap-template
ai-usage: ai-assisted
---

# Suspend and resume a transaction in the point of sale (POS)

[!INCLUDE [banner](includes/banner.md)]

This article explains how to suspend and resume transactions in Microsoft Dynamics 365 Commerce point of sale (POS), and how to pin suspended transactions for quick access.

Store associates can suspend an in-progress transaction to free up a register without losing their progress. For example, an associate can suspend a transaction on a mobile device and then resume it on a register that has a cash drawer. For transactions that associates expect to return to frequently, pinning them provides quick access from a list in POS. Associates can pause one customer's transaction, serve another customer, and then quickly return to the pinned transaction. This capability helps associates manage interruptions and reduces the time spent finding transactions to resume.

## Configure suspend and resume functionality

### POS operations

Two [POS operations](pos-operations.md) let the POS support suspend and resume scenarios. Assign these operations to [button grids](pos-screen-layouts.md) on the transaction page or the welcome page.

- 503: Suspend transaction
- 504: Recall transaction

### Configure pin and resume functionality

Enable transaction pinning so that store associates can quickly access suspended transactions from a pinned transaction list in POS.

1. In Commerce headquarters, open **Feature management**.
1. Enable the **Pin and Resume Suspended Transactions** feature.
1. Open the **Button grid designer** for the button grid used by your POS layout.
1. Configure the **Suspend transaction** button to use the standard suspend behavior, pin the transaction, or prompt the associate to choose between suspending and pinning.
1. Configure the **Resume transaction** button to use the standard resume behavior, resume a pinned transaction, or prompt the associate to choose between the two options.
1. Save the button grid changes.

Select the button behavior that best supports your store's workflow. For example, use a prompt when associates need both standard suspension and pinning from the same button.

> [!NOTE]
> The available choices in POS depend on how the administrator configures the buttons. The procedures in this article describe a layout that prompts associates to select an action.

### Receipt template

You can configure the POS to generate a printed slip when a transaction is suspended. Use that slip to quickly identify and recall the transaction.

To enable the POS to print a slip, add the **Suspended transaction** receipt format to the store's receipt profile. You can design the receipt format so that it includes or excludes specific details about the transaction. For example, the format can include a barcode to support scanning.

### Receipt numbering

As with other POS transaction types that generate a printed receipt, define a number sequence for suspended transactions in the **Receipt numbering** section of the store's functionality profile.

### Void when closing shift

Use the **Void when closing shift** option to require that users either complete or void any suspended transactions before they close their shift. During the **Close shift** operation, the POS prompts users to either view or void any outstanding suspended transactions.

## Suspend and resume a transaction

### Suspend a transaction

Users who have sufficient privileges and a screen layout that includes the **Suspend transaction** operation can suspend a transaction so that they can recall it later or on a different register.

Users can suspend or pin transactions only if they don't contain the following types of lines:

- Active payment lines
- Gift card lines (either to issue a gift card or to add to the gift card balance)

> [!NOTE]
>
> You can suspend a transaction before you accept any payment for it. After you accept a payment, the transaction contains an active payment line and you can't suspend it. For example, a customer adds three items to the cart and pays part of the total in cash or by card. The standard suspend workflow doesn't support suspending that partially paid transaction, recalling it later, and then adding more items.
>
> If you use pay-by-link with the Dynamics 365 Payment Connector for Adyen for cash and carry transactions, a separate flow lets cashiers (who have the required permissions) suspend a transaction by selecting **Cancel payment link** and then **Suspend payment link**. This flow is available only when the pay-by-link prerequisites are met, including the minimum component versions, the required features, and payment notifications through a Commerce environment that's linked to Dataverse. After you recall the transaction, check the payment status before you add a payment line or void the transaction. When you void a suspended transaction, unused payment links expire automatically, but used payment links remain unchanged. For more information, see the [Payment experience](dev-itpro/pay-by-link-overview.md#payment-experience-when-using-pay-by-link-for-cash-and-carry-transactions) and [Suspended transactions](dev-itpro/pay-by-link-overview.md#suspended-transactions) sections of [Enable pay by link in POS by using the Dynamics 365 Payment Connector for Adyen](dev-itpro/pay-by-link-overview.md).
>
> The pay-by-link flow isn't a general way to suspend partially paid transactions or transactions that have active payment lines. To request support for other suspension scenarios, submit feedback at [Dynamics 365 Application Ideas](https://ideas.dynamics.com).

A suspended transaction doesn't affect sales information or inventory availability information for the store.

### Resume a suspended transaction

Users with sufficient privileges and a layout that includes the **Recall transaction** operation can recall and resume suspended transactions in the same store.

To quickly and easily recall a suspended transaction, scan the barcode on the printed slip while you're viewing the list of transactions from the **Recall transaction** operation.

### Pin a transaction

Pin a transaction when you want to pause it and keep it readily accessible in POS. For example, if a customer leaves the checkout to find another item, you can pin their transaction and serve the next customer.

1. On the transaction page, select **Suspend transaction**.
1. When prompted to select between suspending and pinning, select **Pin transaction**.

The transaction is suspended and appears in the pinned transaction list. You can start another transaction and return to the pinned transaction when you're ready.

:::image type="content" source="media/suspend-or-pin-transaction.png" alt-text="Screenshot displaying a dialog to suspend or pin a transaction." lightbox="media/suspend-or-pin-transaction.png":::

If the button is configured to pin transactions directly, selecting it pins the transaction without prompting you to choose an action.

### Resume a pinned transaction

Use the pinned transaction list to quickly return to a transaction that you previously pinned.

1. Select **Resume transaction**.
1. If prompted, choose the option **Recall pinned transaction** to resume a pinned transaction. You can recall pinned transactions by using the left panel where the pinned suspended transactions are displayed.
1. Select the transaction that you want to resume from the pinned transaction list.

The selected transaction becomes the active transaction. Continue processing it as usual.

:::image type="content" source="media/pinned-transaction.png" alt-text="Screenshot of POS showing multiple pinned transactions available to resume." lightbox="media/pinned-transaction.png":::

If the button is configured to resume pinned transactions directly, selecting it opens the pinned transaction list without prompting you to choose between standard and pinned transactions.

> [!NOTE]
> The pinned transaction list is local to the POS where the transaction was pinned. Don't rely on that list to find pinned transactions on another register. Use the existing suspend and resume workflow when you need to move a transaction between registers.

Pinning helps you switch between transactions, but only one transaction is active at a time.

### Considerations for offline mode

- You can't resume any transaction in offline mode that you suspended while the POS was in online mode, because the data isn't synced to the offline database.
- If you suspend a transaction while the POS is in offline mode, you can recall it in offline mode if the POS wasn't switched back to online mode at any time since you suspended the transaction. When the POS is switched back to online mode, data about suspended transactions is moved to the online database and removed from the offline database. Therefore, the transactions can be resumed only in online mode. If you switch the POS back to offline mode, you can't resume those suspended transactions, because they're already removed from the offline database.

### Void a suspended transaction

You can void suspended transactions either by recalling the transaction and then performing the **Void transaction** operation, or by selecting the transaction in the **Recall transaction** list and selecting **Void** on the app bar. Alternatively, you can configure the store to prompt users to void suspended transactions when they close their shift.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
