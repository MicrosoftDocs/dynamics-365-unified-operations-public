---
title: Print checks by using the Spanish layout
description: Learn about how to print checks that follow the standards that are required in Spain with a process for using the checks' functionality with the Spanish layout.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/26/2024
ms.reviewer: johnmichalak
ms.search.region: Spain
ms.search.validFrom: 2016-11-30
ms.search.form: BankChequeLayout, LedgerJournalTransVendPaym
ms.dyn365.ops.version: Version 1611
---

# Print checks by using the Spanish layout

[!include [banner](../../includes/banner.md)]

This article provides information about how to print checks that follow the standards that are required in Spain.

To use the checks functionality together with the Spanish layout, you should consider the following settings:

-   To apply the correct grammar to the literal (text) amount, you must select the correct gender for the currency on the **Currencies** page. For example, select **Masculine** for euro (EUR) and **Feminine** for British pound (GBP).
-   For the method of payment, use the **Check** export file format.
-   For the bank account, use **Spanish check layout** in the **Check layout** section of the **Bank account** page (**Setup** &gt; **Layout** &gt; **Check**). Additionally, set the **Other currencies** field to **Yes**.

To generate the checks by using the Spanish layout, basic Payment journal (vendors) functionality is used. For more information, see [Vendor payment overview](../../cash-bank-management/tasks/vendor-payment-overview.md). After you run the Generate payments function and select all required parameters as described in this article, the checks are generated. If the currency on the payment journal line differs from the currency of the bank account, you can still generate a check if the check layout is set up to use other currencies.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
