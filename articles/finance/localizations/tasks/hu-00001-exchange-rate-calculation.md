--- 
# required metadata 
 
title: HU-00001 Exchange rate calculation
description: This task walks you through running an average exchange rate calculation. 
author: v-oloski
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalTable, LedgerJournalTransDaily   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Hungary
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# HU-00001 Exchange rate calculation

[!include [banner](../../includes/banner.md)]

This task walks you through running an average exchange rate calculation. 

You can calculate the exchange rates for journal lines. For cash and bank transactions, you can use either the daily exchange rate or an average exchange rate. For petty cash and bank journal lines, the calculation of the average exchange rate uses the summarized amounts of the accounting currency and the foreign currency before the specified transaction date.

This task was created using the demo data company DEMF with the country/region of legal entity primary address updated to be Hungary. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

1. Go to General ledger > Journal entries > General journals.
2. Click New.
3. In the Name field, enter or select a value.
4. Click Lines.
5. In the Account type field, select 'Customer'.
6. In the Account field, specify the desired values.
7. In the Debit field, enter any amount.
8. In the Offset account type field, select 'Bank'.
9. In the Offset account field, specify the desired values.
10. In the Currency field, enter or select a value.
    * You may use value 'USD'.  
11. Click Functions.
12. Click Exchange rate calculation.
13. In the From date field, enter a date.
    * Select a transaction date to specify a period. Ledger transactions are included in the calculation of the average exchange rate if the transaction dates are on or after the date that you enter in this field, and before the transaction date of the journal line. If you leave this field blank, the calculation includes all ledger transactions for which the transaction dates are before the transaction date of the journal line.  
14. Expand the Records to include section.
    * Use 'Records to include tab' to set up selection criteria for the lines to include in the exchange rate calculation. If you do not set up selection criteria in the Filter form, the calculation method that you selected is used for all lines in the current journal.  
15. Click OK.

