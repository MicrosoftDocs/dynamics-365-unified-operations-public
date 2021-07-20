---
# required metadata

title: Cash management improvements
description: This topic describes the cash management improvements in POS for Dynamics 365 Commerce.
author: anpurush
ms.date: 05/21/2019
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
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-05-21
ms.dyn365.ops.version: 

---

# Cash management improvements

[!include [banner](includes/banner.md)]


Cash management is a key function for retailers in physical stores. Retailers want their stores to have systems that can help them provide complete traceability and accountability of cash and its movement across the different registers and cashiers in a store. They must be able to reconcile any differences and determine accountability.


Microsoft Dynamics 365 Commerce has cash management capabilities in its point of sale (POS) application. However, in versions of Retail that are earlier than version 10.0.3, cash management functionality isn't robust enough to provide complete traceability of cash movements in stores. Although retailers can reconcile the cash for a store, they can't precisely determine accountability in the event of a cash discrepancy.


In Retail version 10.0.3 and later, retailers will gain traceability for cash handling. As part of this traceability, retailers will be able to define safes, make two-sided cash transactions, and reconcile cash management transactions.

## Set up traceability and define safes

To set up the new cash management functionality, follow these steps to configure the functionality profile for stores.

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**, and select a functionality profile that is linked to the stores where you want to make the improvements for cash management available.
2. On the **Functions** FastTab of the functionality profile, under **Advanced cash management**, set the **Enable cash traceability** option to **Yes**.
3. To set up safes, go to **Retail and Commerce \> Channels \> Stores \> All stores**, and select a store.
4. On the **Stores** page, on the Action Pane, on the **Set up** tab, in the **Set up** group, select **Safes**. By using this option, you can define and maintain multiple safes for a store.
4. Before the functionality can be used, you must run the **1070 Channel configuration** distribution schedule job to sync these configurations to the channel database.

## Additional cash management changes

In Retail version 10.0.3 and later, the following capabilities that are related to cash transactions are also provided:

- A user who is prompted to "declare start amount" must enter the source of cash. The user can search for the available safes that are defined in the store and select the safe that the cash is being taken out of so that it can be put into the register.
- A user who does a "tender removal" operation is prompted to select, in a list of open "float entry" transactions, the transaction that the operation is being done against. If the corresponding float entry doesn't exist in the system, the user can create a non-linked tender removal transaction.
- A "float entry" operation prompts a user to select, in a list of open "tender removal" transactions, the transaction that the float entry operation is being done against. If the corresponding tender removal doesn't exist in the system, the user can create a non-linked float entry transaction.
- A user who makes a "safe drop" is prompted to select the safe where the cash is being dropped.
- For safes that are defined in a store, users can manage operations such as declaring the start amount, doing a float entry, doing a tender removal, and making a bank drop.
- For users who have the appropriate user privileges, "manage shifts" operations show the cash balances of active, suspended, and blind closed shifts.
- To reconcile the cash transactions within a shift or across shifts, select the shift to reconcile, and then select **Reconcile**. The view that is opened shows the list of reconciled and unreconciled transactions on separate tabs. From this view, users can either select unreconciled transactions and reconcile them, or select previously reconciled transactions and unreconcile them.
- During reconciliation, if the selected transaction doesn't balance, the user must enter a description of the reason for the unbalanced reconciliation. Users can select a single transaction and reconcile it with the relevant reason description as they require.
- Users can continue to reconcile and unreconcile transactions until the shift is closed. After a shift is closed, the transactions can't be unreconciled.
- When a user chooses to close a shift, Commerce validates that there are no unreconciled cash management transactions in the shift. Users can't close a shift if there are unreconciled transactions.


[!INCLUDE[footer-include](../includes/footer-banner.md)]