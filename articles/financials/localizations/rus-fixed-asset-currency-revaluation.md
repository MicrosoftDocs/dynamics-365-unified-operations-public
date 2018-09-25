---
# required metadata

title: Fixed asset currency revaluation
description: This topic provides information about fixed asset currency revaluation for Russia.
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

Foreign representatives have the right to keep an account of the fixed assets that are entered and acquired in their currency, together with a recalculation in Russian rubles for Russian tax accounting purposes. If a fixed asset is entered in a foreign currency, the accounting currency is specified in the asset record. Cost figures for all transactions are specified in both the accounting currency and the original company currency (rubles), at the exchange rate that applied on the transaction date. When the currency exchange rate is changed, a revaluation of the ruble value for the asset is calculated in correspondence with the profit and loss accounts.

Individual or group currency revaluation transactions can be calculated for the value of objects of depreciated property. When group transactions are ended, records for the currency revaluation and depreciation that were calculated at the rate that applied on the date when the transactions were created are updated. When individual transactions are ended, the currency revaluation and depreciation must be calculated separately in two different transactions.

The following changes occur when currency is revaluated (depreciated):

- Corresponding transactions are created in the ledger.
- The **Currency cost revaluate** fields on the **Balance** page are updated.
- The depreciated cost of the fixed asset is updated.

## Revalue the currency of fixed assets

1. Select **Fixed assets (Russia) \> Journals \> FA journal**.
2. Select **New**. In the **Description** field, enter a short description of the journal.
3. Select **Lines** to open the **Journal voucher** page, where you can enter fixed asset transactions.
4. Select **New** to open the **Add to journal** dialog box.
5. In the **Transaction type** field, select **Currency cost revaluation**, and then, in the **FA inventory number**, select the fixed asset. Select **OK**.

    > [!NOTE]
    > Journal lines are created only if the exchange rate for the fixed asset differs from the exchange rate that applied on the date when the fixed asset was put into operation.

6. Verify the information in the **Debit**, **Date**, and **Currency** fields. Change the cost revaluation amount and transaction date if different values are required.
7. Select **Post \> Post**. The fixed asset and ledger transactions are created, and the value in the **Currency cost revaluate** field on the **Balance by FA** page is updated. The currency revaluation of depreciation is also updated.

## Reverse revaluation transactions

Revaluation transactions are reversed in the same way as acquisition transactions (putting into operation transactions). Two transactions are created: a cost revaluation transaction and a depreciation revaluation transaction.
