---
# required metadata

title: Print checks by using the Spanish layout
description: This topic provides information about how to print checks that follow the standards that are required in Spain.
author: neserovleo
manager: AnnBe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: BankChequeLayout, LedgerJournalTransVendPaym
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 274753
ms.search.region: Spain
# ms.search.industry: 
ms.author: v-lenest
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Print checks by using the Spanish layout

This topic provides information about how to print checks that follow the standards that are required in Spain.

To use the checks functionality together with the Spanish layout, you should consider the following settings:

-   To apply the correct grammar to the literal (text) amount, you must select the correct gender for the currency on the **Currencies** page. For example, select **Masculine** for euro (EUR) and **Feminine** for British pound (GBP).
-   For the method of payment, use the **Check** export file format.
-   For the bank account, use **Spanish check layout** in the **Check layout** section of the **Bank account** page (**Setup** &gt; **Layout** &gt; **Check**). Additionally, set the **Other currencies** field to **Yes**.

To generate the checks by using the Spanish layout, basic Payment journal (vendors) functionality is used. For more information, see [Vendor payment overview (task guide)](https://ax.help.dynamics.com/en/wiki/vendor-payment-overview/). After you run the Generate payments function and select all required parameters as described in this topic, the checks are generated. If the currency on the payment journal line differs from the currency of the bank account, you can still generate a check if the check layout is set up to use other currencies.

