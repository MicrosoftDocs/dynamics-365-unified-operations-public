---
title: Revaluate fixed asset cost and depreciation (Russia)
description: Learn how to revaluate the cost and depreciation of fixed assets for Russia, including definitions for the indexing and direct recalculation methods.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/26/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Revaluate fixed asset cost and depreciation (Russia)

[!include [banner](../../includes/banner.md)]

An organization can independently change the cost of a fixed asset one time per year at the end of the reporting year (usually on 12.31). Revaluation of fixed assets can also be done because of a decision of the state. As a rule, revaluation of fixed assets cost is accompanied by a revaluation of depreciation. Two methods can be used to change the cost of fixed assets as a result of revaluation of fixed asset cost:

- **Indexing** – Indices are used. These indices are usually set by the state. In this case, the initial cost of the fixed asset and the amount of accrued depreciation are multiplied by the corresponding indices.
- **Direct recalculation (direct evaluation)** – Documented data about the market price of the fixed asset is used. At the same time, the amount of depreciation is subject to indexation by the conversion factor. The conversion factor is calculated as the ratio of the object's new cost to its old cost.

As a result of revaluation of fixed asset cost and depreciation, the following events occur:

- Ledger and fixed asset transactions are created. The fixed asset transactions that are created have transaction types of **Cost revaluation** and **Depreciation revaluation**.
- On the **Balance by FA** page, the **Cost revaluation** and **Depreciation revaluation** fields are filled in, and the value in the **Net book value** field is increased or decreased by the revaluation transaction amount.

To revaluate fixed asset cost and depreciation, follow these steps.

1. Select **Fixed assets (Russia)** \> **Journals** \> **Periodic journals** \> **FA revaluation** to open the **FA revaluation** page.
2. Select **New** to create a revaluation journal.
3. The **Revaluation period** and **State on** fields are automatically set to the current period and date. However, you can update these fields as you require. The **State on** field specifies the date that depreciation revaluation is calculated from.
4. In the **Fixed asset journal name** field, select a journal name. This journal name is used to create the Fixed asset journal when the revaluation journal is closed.
5. The **FA journal** field is automatically set, based on the number sequence setting, when the Fixed asset revaluation journal is closed.
6. Select **Lines**, and then, in the **Revaluation lines creation** dialog box, select the **RAP** value model. To set a filter to select fixed assets for revaluation, on the **Records to include** Fast Tab, select **Filter**. Then select **OK**.

    On the **FA revaluation lines** page, the system creates lines for fixed assets that have the selected value model.

    The **Balance cost** field is set to **Net book value**, and the **Replacement cost** field is set to the new fixed asset cost. The **Balance cost** value corresponds to the value in **Net book value** field on the **Balance by FA** page (**Fixed assets (Russia)** \> **Common** \> **Fixed assets**, select **Value models** on the **Fixed assets** page, and then select **Balance** on the **FA value models** page).

    > [!NOTE]
    > You can manually set the **Replacement cost** field. In this case, the system recalculates the factor. Alternatively, you can manually set the **Factor** field. In this case, the system recalculates the replacement cost.

7. You can add and remove lines as you require:

    - To add a line, select **New**. In the **Revaluation lines creation** dialog box, select the fixed asset inventory number and value model, and then select **OK**. If you don't specify the value model, the system creates lines for all value models that are set up in the fixed asset.
    - To remove a line, select it, and then select **Delete**

8. Follow one of these steps:

    - To revaluate fixed asset cost and depreciation by using the direct revaluation method, in the **Replacement cost** field, enter the market cost of fixed assets.
    - To revaluate fixed asset cost and depreciation for all fixed assets on the **FA revaluation lines** page by using the indexing method, select **Revaluation**. In the **Group revaluation** dialog box, select the value model that the revaluation should be calculated for, and enter the factor. To set a filter to select fixed assets for revaluation, on the **Records to include** Fast Tab, select **Filter**. Then select **OK**. The **Factor** and **Replacement cost** fields are filled in for all lines.

9. Close the **FA revaluation lines** page.
10. On the **FA revaluation** page, on the Action Pane, select **Close** to confirm the revaluation results.

    After the Fixed asset revaluation journal is closed and the Fixed asset journal is created, the Fixed asset journal number is filled in, and the **FA journal** button on the Action Pane becomes available.

11. Select **FA journal**, and then, on the **FA journal** page, select **Lines**. The **Voucher transaction** page shows revaluation transactions. You can correct these transactions as you require.
12. Select **Post** \> **Post** to post the journal.
13. Validate the balance in the value model (**Fixed asset (Russia)** \> **Fixed assets** \> **Value models** \> **Balance**). The values in the **Cost revaluation** and **Depreciation revaluation** fields are updated.


## Reverse fixed asset revaluation transactions

By default, when you reverse transactions, the reversal date is equal to the original transaction date. However, you can specify a different reversal date.
1. Go to **Fixed assets (Russia)** > **Fixed assets**, and on the Action Pane, select **Value models**.
2. On the **FA value models** page, on the Action Pane, select **Transactions**.
3. On the **FA transactions** page, select and transaction and on the Action Pane, select **Reverse transaction**.
4. In the **Reverse transactions** dialog box, change the transaction reversal date as needed and then select **OK**. A transaction to reverse the original transaction is created and added to the **FA transactions** page.
5. Select **Voucher**, and on the **Voucher transactions** page, view the transactions in the ledger.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
