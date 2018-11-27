---
# required metadata

title: Suspend and resume transactions in the point of sale (POS)
description: Users can suspend an in-progress transaction and resume it at a later time or on a different register.
author: jblucher
manager: AnnBe
ms.date: 10/30/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 261234
ms.assetid: 7cd68ecc-cc09-48ab-8cb8-48d5c304effa
ms.search.region: global
ms.search.industry: Retail
ms.author: jeffbl
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Suspend and resume transactions in the point of sale (POS)

POS users can suspend an in-progress transaction and resume it at a later time or on a different register.  This is typically done to quickly free up a register for a different task, without losing any progress on the current transaction.  For example, a store associate begins processing a customer's transaction on a mobile device, but needs to complete it on register with a cash drawer.  The user would suspend the transaction on their register so it could be recalled and resumed on a different register.

## Configurating supsend/resume

### POS Operations
Suspend and resume scenarios are enabled in POS by using two [POS operations](pos-operations.md), which can be assigned to [button grids](pos-screen-layouts.md) on the transaction screen or welcome screen.

- 503: Suspend transaction
- 504: Recall transaction

### Receipt template
The POS can be confiugred to generate a printed slip when a transaction is suspended.  This can be used to quickly identify and recall the transaction at a later time.  

To enable this, you must add the **Suspended transaction** receipt format to the store's **Receipt profile**.  The format itself can be designed to include or exclude details about the transaction, including a barcode to enable scanning.

### Receipt numbering
As with other POS transaction types that generates a printed receipt, the number sequence can be defined in the **Receipt numbering** section of the store's **Functionality profile**. 

### Void when closing shift
When enabled this option will require that users either complete or void any suspended transactions before closing their shift. During the close shift operation, the POS will prompt the user to either view or void any outstanding suspended transactions. 

## Using suspend/resume in POS

### Suspending transactions
Users with suffiencent privileges and with a screen layout containing the **Suspended transaction** operation can suspend a transaction to be recalled at a later time or from a different register.  

Transactions can only be suspended if they do not contain:
- Active payment lines
- Gift card lines (issue or add to)

A suspended transaction does not impact sales or inventory availability information for the store.

### Resuming suspended transactions
Suspendeded transactions can be recalled and resumed within the same store, by any user with suffiencient privileges and with a layout containing the **Recall transaction** operation.

Suspeneded transactions can quickly and easily be recalled by scanning the barcode on the printed slip while viewing the list of transactions from the **Recall transaction** operation.

#### Offline mode considerations #### 

- Any transaction which is suspended in online-mode cannot be resumed in offline-mode as the data is not synced to the offline database.
- If the user suspended a transaction while in offline-mode they can recall those transactions in offline mode as long as POS is not switched back to online from the time the transaction was suspended. Once switched back to online the suspended transaction data is moved to the online database and is removed from the offline database. Therefore, these transactions can only be resumed in online mode. If the user switches back to offline they won't be able to resume those suspended transaction as they are already removed from the offline database.

### Voiding suspended transactions
Suspended transactions can be voided either by recalling the transaction and then performing the **Void transaction** operation or by selecting the transaction from the **Recall transaction** list and choosing Void from the app bar.  Alternatively, the store can be configured to prompt users to void suspeneded transactions when closing their shift. 
