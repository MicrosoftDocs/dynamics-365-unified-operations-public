---
# required metadata

title: Fixed asset currency revaluation
description: This topic provides information about fixed asset currency revaluation for Russia.
author: Anasyash
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTable
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
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

Foreign representatives have the right to keep an account of the fixed assets in the foreign currency. Fixed asset accounting (for example, business accounting and tax accounting) can be executed in different currencies. If a fixed asset value model is entered in a foreign currency, the accounting currency is specified in the asset record. Fixed asset transaction amounts are specified in both the accounting currency and the original company currency (rubles) at the exchange rate that applied on the transaction date. When the currency exchange rate is changed, a revaluation is calculated and profit or loss exchange rate adjustment transactions are created both for fixed asset module and ledger transactions.

Individual or group currency revaluation transactions can be calculated for the value of objects of depreciated property. When group transactions are ended, records for the currency revaluation and depreciation that were calculated at the rate that applied on the date when the transactions were created are updated. When individual transactions are ended, the currency revaluation and depreciation must be calculated separately in two different transactions.

The following changes occur when currency is revaluated (depreciated):

- Corresponding transactions are created in the ledger.
- The **Currency cost revaluate** fields in the **Balance by FA** dialog box are updated.
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
7. Select **Post \> Post**. The fixed asset and ledger transactions are created, and the value in the **Currency cost revaluate** field in the **Balance by FA** dialog box is updated. The currency revaluation of depreciation is also updated.

## Reverse revaluation transactions

Revaluation transactions are reversed in the same way as acquisition transactions (putting into operation transactions). Two transactions are created: a cost revaluation transaction and a depreciation revaluation transaction.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]