---
# required metadata

title: Cash management improvements
description: This topic describes the cash management improvements in POS for Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 5/21/2019
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
[!include [banner](../includes/preview-banner.md)]

Cash management is a key function for retailers in a physical store. Retailers want to have systems in the store that can help them provide complete traceability and accountability of cash and its movement across the different registers and cashiers in the store. They need capability to reconcile any differences and pinpoint accountability.

Dynamics 365 for Retail has cash management capabilities in its point of sale (POS) application. However, in versions of Retail earlier than version 10.0.3, cash management functionality is not robust enough to provide complete traceability of cash movement in the stores. Retailers can reconcile the cash for a store, but they aren't able to pinpoint the accountability in the case of a cash discrepancy. 

Beginning with Retail version 10.0.3, retailers will gain cash handling traceability, including the capability to define safes, make two-sided cash transactions, and reconcile cash management transactions.

## Set up tracability and declare safes

You can set up the new cash management functionality by configuring the functionality profile for stores using the following steps.

1. Go to **Retail > Channel setup > POS setup > POS profiles > Functionality profiles** and choose a profile linked to the stores where you want to enable the cash management improvements.

1. On the **Functions** tab of the functionality profile for the store, under the **Functions** group, under **Advanced cash management**, set the **Enable cash traceability** parameter to **Yes**. 

1. To set up safes, go to **Retail > Channels > Retail stores > All retail stores** and select a store. On the **Setup** fastab for the store, under **Set up**, click **Safes**. Using this option, multiple **Safes** can be defined and maintained for a store.

4) The **1070 Channel configuration** distribution schedule job must be run for these configurations to be synchronized to the channel database before the functionality can be used.

## Additional cash management changes

In Retail version 10.0.3 and higher, the following capabilities relating to cash transactions are also provided. 

- When a user is prompted to "declare start amount", the user is required to enter the source of cash. The user can search for the available defined safe in the store and select the safe from which the cash is being taken out to put into the register.

- When a user executes a "tender removal" action, the user is prompted to choose from a list of open "float entry" transactions against which the tender removal operation is being performed. If the corresponding float entry doesn't exist in the system, the user can create a non-linked tender removal transaction

- A "float entry" operation prompts a user to choose from a list of open "tender removal" transactions against which the float entry operation is being performed. If the corresponding tender removal doesn't exist in the system, the user can create a non-linked float entry transaction.

- When a user makes a "safe drop", the user is prompted to choose the safe where the cash is being dropped.

- For safes that are defined in a store, users can manage operations such as declaring start amount, float entry, tender removal, and bank drop. 

- With the appropriate user privileges, "manage shifts" operations show the user cash balances of active, suspended, and blind closed shifts.

- To reconcile the cash transactions within a shift or across shifts, select the shift to reconcile, then click **Reconcile**. This opens a view where the user can see the list of reconciled and unreconciled transactions in separate tabs. From this view, users can choose to either select unreconciled transactions and reconcile them, or choose already reconciled transactions and unreconcile them.

- During reconciliation, if the selected transaction doesn't balance, the user must enter a reason description for the unbalanced reconciliation. Users can select a single transaction and reconcile it with the relevant reason description if necessary.

- Users can continue to reconcile and unreconcile transactions until the shift is closed. After a shift is closed, the transactions cannot be unreconciled.

- When a user chooses to close a shift, Retail will validate that there are no unreconciled cash management transactions in the shift. A user will not be able to close a shift if there are unreconciled transactions.
