---
# required metadata

title: Suspend and resume a transaction in the point of sale (POS)
description: This topic explains how users can suspend in-progress transactions and then resume them later or on a different register by using Dynamics 365 Commerce.
author: jblucher
ms.date: 11/27/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 261234
ms.assetid: 7cd68ecc-cc09-48ab-8cb8-48d5c304effa
ms.search.region: global
ms.search.industry: Retail
ms.author: jeffbl
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Suspend and resume a transaction in the point of sale (POS)

[!include [banner](includes/banner.md)]


Point of sale (POS) users can suspend in-progress transactions, and then resume them later or on a different register. Transactions are often suspended to quickly free up a register for a different task without losing any progress on the current transaction. For example, a store associate starts to process a customer's transaction on a mobile device but must complete it on a register that has a cash drawer. In this case, the store associate can suspend the transaction on the mobile device, and then recall and resume it on a register.

## Configure suspend and resume functionality

### POS operations

Two [POS operations](pos-operations.md) let the POS support suspend and resume scenarios. You can assign these operations to [button grids](pos-screen-layouts.md) on the transaction page or the welcome page.

- 503: Suspend transaction
- 504: Recall transaction

### Receipt template

The POS can be configured to generate a printed slip when a transaction is suspended. That slip can then be used to quickly identify and recall the transaction later.

To enable the POS to print a slip, you must add the **Suspended transaction** receipt format to the store's receipt profile. You can design the receipt format so that it includes or excludes specific details about the transaction. For example, the format can include a barcode to support scanning.

### Receipt numbering

As for other POS transaction types that generate a printed receipt, you can define a number sequence for suspended transactions in the **Receipt numbering** section of the store's functionality profile.

### Void when closing shift

You can use the **Void when closing shift** option to require that users either complete or void any suspended transactions before they close their shift. During the **Close shift** operation, the POS will prompt users to either view or void any outstanding suspended transactions.

## Suspend and resume a transaction

### Suspend a transaction

Users who have sufficient privileges, and who have a screen layout that includes the **Suspend transaction** operation, can suspend a transaction so that it can be recalled later or on a different register.

Transactions can be suspended only if they do **not** contain the following types of lines:

- Active payment lines
- Gift card lines (either to issue a gift card or to add to the gift card balance)

A suspended transaction doesn't affect sales information or inventory availability information for the store.

### Resume a suspended transaction

Suspended transactions can be recalled and resumed in the same store by any user who has sufficient privileges, and who also has a layout that includes the **Recall transaction** operation.

To quickly and easily recall a suspended transaction, scan the barcode on the printed slip while you're viewing the list of transactions from the **Recall transaction** operation.

### Considerations for offline mode

- Any transaction that is suspended while the POS is in online mode can't be resumed in offline mode, because the data isn't synced to the offline database.
- If you suspend a transaction while the POS is in offline mode, you can recall it in offline mode, provided that the POS wasn't switched back to online mode at any time since you suspended the transaction. When the POS is switched back to online mode, data about suspended transactions is moved to the online database and removed from the offline database. Therefore, the transactions can be resumed only in online mode. If you switch the POS back to offline mode, you won't be able to resume those suspended transaction, because they have already been removed from the offline database.

### Void a suspended transaction

You can void suspended transactions either by recalling the transaction and then performing the **Void transaction** operation, or by selecting the transaction in the **Recall transaction** list and selecting **Void** on the app bar. Alternatively, the store can be configured to prompt users to void suspended transactions when they close their shift.


[!INCLUDE[footer-include](../includes/footer-banner.md)]