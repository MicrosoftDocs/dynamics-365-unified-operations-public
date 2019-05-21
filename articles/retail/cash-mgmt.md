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

Cash management is a key function for retailers in a physical store. Retailers want to have systems in the store that can help them provide complete traceability and accountability of cash and its movement across the different registers and cashiers in the store. They need capability to reconcile any differences and pinpoint accountability.

Dynamics 365 for Retail has cash management capabilities in its point of sale (POS) application. However, functionality around the same is not rounded enough to provide complete traceability of the cash movement in the stores. With the current set of capability, Retailers can reconcile the cash for a store. However, they are not able to pinpoint the accountability in the case of cash discrepancy due to not so strong traceability feature around Cash management. Due to this, Retailers do not have enough data to recover the losses in a situation of cash discrepancy by fixing accountability where required.

This feature will provide for a fully rounded and robust capability around cash management that will provide retailers the required traceability from a cash handling standpoint including the capability to define **Safe** entities, make two sided cash transactions and reconcile the cash management transactions.

**Setup**

The improvements around the Cash management functions can be leveraged by configuring the functionality profile for stores as per the below steps:

1) Navigate to **Retail \&gt; Channel setup \&gt; POS setup \&gt; POS profiles \&gt; Functionality profiles** and choose a profile linked to the stores where you want to enable the cash management improvements

2) In the **Functions** tab of the Functionality profiles, under the fast tab **Functions,** group **Advanced cash management,** a new parameter called **&quot;Enable cash traceability&quot;** is introduced. Turning this parameter on will light-up the cash management improvements in the stores to which the functionality profile is associated to

3) Navigate to **Retail \&gt; Channels \&gt; Retail stores \&gt; All retail stores** and select a store for which you want to define the **Safes.** The **Safes** for a store can be maintained using the **Safes** button on the **Setup group** of the **Setup tab** n the Retail stores. Using this option, multiple **Safes** can be defined and maintained for a store.

4) The **1070 Channel configuration** distribution schedule job must be run for these configurations to be synchronized to the Channel database before the feature can be used

**Details**

The cash management improvements will provide the following functionality around the different cash transactions that happens in a retail store

1) The &quot;Declare start amount&quot; operation will mandate a user to enter the source of cash and the user can look up the available **Safe** entity in the store and select the **Safe** from where the cash is being taken out to put into the register

2) The **Tender removal** operation will prompt the user to choose from a list of open **Float entry** transactions against which the tender removal operation is being performed. If the corresponding **Float entry** does not exist in the system, the user will be allowed to create a non-linked **Tender removal** transaction

3) The **Float entry** operation will prompt the user to choose from a list of open **Tender removal** transactions against which the **Float entry** operation is being performed. If the corresponding **Tender removal** does not exist in the system, the user will be allowed to create a non-linked **Float entry** transaction

4) The **Safe drop** operation will mandate a user to choose the **Safe** to which the cash is being dropped to

5) A new operation called as **Manage Safe** is introduced in the application using which users can manage the **Safe&#39;s** in the store and perform cash management transactions for the **Safe** like **Declare start amount** , **Float entry** , **Tender removal** &amp; **Bank drop**

6) With proper user privileges, the **Manage shifts** operations will show the user cash balances of active, suspended and blind closed shifts

7) Users can reconcile the cash transactions within a shift or across shifts using the **Reconcile** button in the **Manage shifts** operation after selecting the **Shifts** to reconcile. This will take the user to a view where the user can see the list of reconciled and un-reconciled transactions in separate tabs. From this view, users can choose to either select multiple un-reconciled transactions and reconcile them or choose an already reconciled transactions and un-reconcile them.

8) During reconciliation, if the selected transactions to reconcile does not balance, the system will force the user to enter a reason description for the unbalanced reconciliation. Users can even select a single transaction and reconcile them with the relevant reason description.

9) Users can continue to perform the reconciliation / un-reconciliation of transactions till the Shift is closed. After a Shift is closed, the transactions cannot be un-reconciled.

10)The **Close shift** operation will validate that there are no un-reconciled cash management transactions in the shift. Users will not be able to **Close shift** if there are un-reconciled transactions in the shift
