---
# required metadata

title: Fixed asset currency revaluation
description: 
author: Anasyash
manager: AnnBe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: Anasyash
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Fixed asset currency revaluation

[!include [banner](../includes/banner.md)]

Foreign representatives have the right to keep an account of the fixed assets entered and acquired in their currency, but with a recalculation in rubles for Russian tax accounting. If the fixed asset is stated in a foreign currency, the accounting currency is specified in the asset record. Cost figures for all transactions are specified both in the accounting currency and in the original company currency (rubles) at the exchange rate on the transaction date. When changing the currency exchange rate, a revaluation of the ruble value for the asset is calculated in correspondence with the profit and loss accounts.

Individual or group currency revaluation transactions can be calculated for the value of objects of depreciated property. When concluding group transactions, records of the currency revaluation and depreciation calculated at the rate applicable on the date of creating the transaction are updated. When concluding individual transactions, the currency revaluation and depreciation must be calculated separately in two different transactions.

The following changes take place when currency is revaluated (depreciated):

-	Corresponding transactions are created in the ledger
-	The Currency cost revaluate fields are updated in the Balance form.
-	The depreciated cost of the fixed asset is updated.

## Revalue currency of fixed assets

1.	Click **Fixed Assets (Russia) > Journals > Fixed assets journal**.
2.	Press **New** button. Enter a short description of the journal in the Description field. 
3.	Click the **Lines** button to open the **Journal voucher** form to enter fixed asset transactions.
4.	Press **New** button to open the **Add to journal** form. 
5.	Select the **Currency cost revaluation** transaction type and FA inventory number. Click OK.
The lines in the journal are created only if the currency exchange rate for the fixed asset was changed in comparing with exchange rate on the date of putting the fixed asset into operation.
6.	Verify the information in the Debit, Date, and Currency fields. if nessary, change the cost revaluation amount and transaction date.
7.	Click **Post > Post** button. The fixed asset and ledger transactions are created and the value of the Currency cost revaluate field is updated in the **Balance by FA** form. 
 The currency revaluation of depreciation is also updated.

## Reverse revaluation transactions

Revaluation transactions are reversed in the same way as acquisition (putting into operation) transactions are reversed, and two transactions, cost revaluation and depreciation revaluation, are created. 
