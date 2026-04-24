---
title: Suspend and resume a transaction in the point of sale (POS)
description: Learn how users can suspend in-progress transactions and then resume them later or on a different register using Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: anvenkat
ms.search.validFrom: 2016-11-30
ms.assetid: 7cd68ecc-cc09-48ab-8cb8-48d5c304effa
ms.custom: 
  - bap-template
---

# Suspend and resume a transaction in the point of sale (POS)

[!include [banner](includes/banner.md)]

This article explains how users can suspend in-progress transactions and then resume them later or on a different register by using Microsoft Dynamics 365 Commerce.

Point of sale (POS) users can suspend in-progress transactions, and then resume them later or on a different register. Users often suspend transactions to quickly free up a register for a different task without losing any progress on the current transaction. For example, a store associate starts to process a customer's transaction on a mobile device but must complete it on a register that has a cash drawer. In this case, the store associate can suspend the transaction on the mobile device, and then recall and resume it on a register.

## Configure suspend and resume functionality

### POS operations

Two [POS operations](pos-operations.md) let the POS support suspend and resume scenarios. Assign these operations to [button grids](pos-screen-layouts.md) on the transaction page or the welcome page.

- 503: Suspend transaction
- 504: Recall transaction

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

Users can suspend transactions only if they don't contain the following types of lines:

- Active payment lines
- Gift card lines (either to issue a gift card or to add to the gift card balance)

A suspended transaction doesn't affect sales information or inventory availability information for the store.

### Resume a suspended transaction

Users with sufficient privileges and a layout that includes the **Recall transaction** operation can recall and resume suspended transactions in the same store.

To quickly and easily recall a suspended transaction, scan the barcode on the printed slip while you're viewing the list of transactions from the **Recall transaction** operation.

### Considerations for offline mode

- You can't resume any transaction in offline mode that you suspended while the POS was in online mode, because the data isn't synced to the offline database.
- If you suspend a transaction while the POS is in offline mode, you can recall it in offline mode if the POS wasn't switched back to online mode at any time since you suspended the transaction. When the POS is switched back to online mode, data about suspended transactions is moved to the online database and removed from the offline database. Therefore, the transactions can be resumed only in online mode. If you switch the POS back to offline mode, you can't resume those suspended transactions, because they're already removed from the offline database.

### Void a suspended transaction

You can void suspended transactions either by recalling the transaction and then performing the **Void transaction** operation, or by selecting the transaction in the **Recall transaction** list and selecting **Void** on the app bar. Alternatively, you can configure the store to prompt users to void suspended transactions when they close their shift.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
