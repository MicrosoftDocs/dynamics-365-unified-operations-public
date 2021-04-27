---
# required metadata

title: Acquiring fixed assets and putting them into operation (Russia)
description: This topic provides information about fixed asset acquisitions for Russia.
author: anasyash
ms.date: 09/25/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RAssetTable, LedgerJournalTable
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Acquiring fixed assets and putting them into operation (Russia)

[!include [banner](../includes/banner.md)]

The following depreciated property assets can be acquired and put into operation.

- Purchased assets
- Assets that are obtained as a deposit in charter capital
- Assets that are obtained under a gift agreement (that is, obtained without compensation)
- Assets that are obtained in exchange for other property
- Unaccounted fixed assets that are discovered during inventory
- Leased fixed assets and funds that are redeemed from a lessor

For scenarios that involve all these assets, a credit account is used. A credit account provides several options for creating correction transactions in the ledger. To specify an account, manually create a transaction in the Fixed asset journal. Alternatively, on the **Posting profiles** page (**Fixed assets (Russia) > Setup > Posting profiles)**, configure the posting profiles for transactions for various types of fixed assets.

The cost of an acquired fixed asset might differ from the purchase cost. For example, the cost might be increased by the addition of miscellaneous charges per acquisition, such as charges for testing and commissioning work.

Before you post a fixed asset acquisitions voucher, you must validate the depreciation parameters on the **Fixed asset value models** page (**Fixed assets (Russia)** > **Fixed assets** and on the Action Pane, select **Value models**). These parameters include the depreciation group, lifetime of FA group and the depreciation method.

The following updates occur when you post a **Putting into operation** transaction:

- A fixed asset model transaction of the **Putting into operation** type is created.
- Voucher transactions of the **Fixed assets (Russia)** transaction type and the **Fixed assets (Russia), debit** posting type are created.
- In the case of fixed asset assembly, inventory transactions that have an issue status of **Sold** are created.
- The fixed asset balance is changed for every value model on the **Balance by FA** dialog box (select **Fixed assets (Russia)** > **Fixed assets**, select **Value models** on the Action Pane, and then, on the **FA value models** page, on the Action Pane, select **Balance**).

You can put one fixed asset, a group of fixed assets, or all fixed assets that have a status of **Bought** or **Scheduled** into operation.

There are two ways to acquire fixed assets (that is, put them into operation):

- You can manually create a transaction for a single asset.
- A transaction can be automatically generated for one fixed asset, a fixed asset group, or all fixed assets that have a status of **Bought** or **Scheduled**.

## Acquire a fixed asset 

Follow these steps to create transactions for one fixed asset by using the Fixed asset journal.

1. Select **Fixed assets (Russia) > Journals > FA journal**.
2. Select **New** to create a fixed asset journal.
3. In the **Name** field, select a journal name. In the **Description** field, enter a description for the journal.
4. On the Action Pane, select **Lines** to open the **Journal voucher** page.
5. Select **New** to create a journal voucher.
6. In the **Add to journal** dialog box, in the **Transaction date** field, set the transaction date.
7. In the **Transaction type** field, select **Putting into operation**.
8. In the **FA inventory number** field, select the inventory number of the fixed asset.
9. In the **Depreciation bonus** and **Reason code** fields, select the depreciation bonus code and reason code, if these values are required.

    > [!NOTE]
    > You can't change the value of the **Value model** field in this dialog box, because **Putting into operation** transactions are created for all value models at the same time.

10. Select **OK**. The lines that have the **Putting into operation** transaction type for the value models, and that are registered in the fixed asset account, are created on the **Journal voucher** page.
11. On the Action Pane, select **Validate** > **Validate** to validate the transactions.
12. On the Action Pane, select **Post** > **Post** to post the transactions.

    Fixed asset and ledger transactions are created. The fixed asset status is updated to **In operation**.

    > [!NOTE] 
    > You can modify the text in the **Transaction text** field and the amount of the acquired fixed asset in the **Amount** field. By default, the **Amount** field is set to the suggested purchase price.

    The values of the **Offset account type** and **Offset account** fields are based on the posting profile setting. You can change these values as you require.

Follow these steps to create transactions for several fixed assets at the same time.

1. On the **Journal voucher** page (that is, on the Fixed asset journal lines), on the Action Pane, select **Group operations** \> **Putting into operation**.
2. In the **Putting into operation** dialog box, on the **Records to include** FastTab, select **Filter** to open the **Assets** dialog box, where you can specify the values for one fixed asset, a fixed asset list, or a group of fixed assets. When you've finished, select **OK**.
3. Enter values in the **Transaction date**, **Depreciation bonus**, and **Reason code** fields, if these values are required.
4. Select **OK**. The lines that have the **Putting into operation** transaction type for the value models, and that are registered in the fixed asset account, are created on the **Journal voucher** page.
5. On the Action Pane, select **Validate** \> **Validate** to validate the transactions.
6. On the Action Pane, select **Post** \> **Post** to post the transactions.

You can review posted transactions on the journal lines by selecting **Inquiries \> Transactions** on the Action Pane. From the **Value models** page, you can review posted transactions for each value model (select **Fixed assets (Russia) \> Fixed assets**, select **Value models** on the Action Pane, and then, on the **FA value models** page, on the Action Pane, select **Transactions**).

## Create standard printing forms
Follow these steps to create standard printing forms.

1. In the fixed asset record, on the Action Pane, select **Documents**, and then select one of the following printing forms:

    - Inventory card (\#FA-6)
    - Equipment acceptance statement (\#FA-14)

2. On the **FA transaction** page (select **Fixed assets (Russia) > Fixed assets**, select **Value models** on the Action Pane, and then, on the **FA value models** page, on the Action Pane, select **Transactions**), select a transaction of the **Putting into operation** type. On the Action Pane, select **Documents**, and then select one of the following pairs of printing forms:

    - **Acceptance report (\#FA-1)** and **Transference statement (\#FA-1)** – Acceptance of all fixed assets except buildings and encroachments.
    - **Acceptance report (\#FA-1a)** and **Transference statement (\#FA-1a)** – Acceptance of buildings and structures.

3. Select **New** to create the document record.
4. Select **Print** to create the document as a Microsoft Excel file.

You can review all document records that are created at **Fixed assets (Russia)** > **Inquiries > Documents**.

## Fixed asset assembly
You can assemble a fixed asset from the inventory items and then put the fixed asset into operation. When an assembled asset is put into operation, components are issued from inventory, based on their current cost.

1. Select **Fixed assets (Russia) > Fixed assets**, and then, on the Action Pane, select **Componentry** to open the **Componentry** page (you could not enter componentry if the fixed asset has not the **Bought** or **Scheduled** status).
2. In the upper pane, on the **Componentry** tab, select **Add**.
3. In the **Item** field, select an item that the fixed asset is assembled from.
4. In the **Quantity** field, enter the quantity of items that should be used to assemble the fixed asset.

    The **Transaction date** field is filled automatically and shows the date of fixed putting into operation (transaction posting).

5. On the **Inventory dimension** tab, specify the warehouse dimensions, configuration (if required), and so on, that are used to write off the item from inventory.

    If a fixed asset is built from items that are bought in one purchase, on the **Componentry** tab, select **From purchase**. Then, in the **Requisition** dialog box, select the purchase that includes items for assembly and then on the Action pane, select the **Append**. All items, included in the purchase, are added to the **Componentry** page.
7. Put the fixed asset into operation by using the Fixed asset journal (**Fixed asset (Russia)** > **Journals** > **FA journal**).

    > [!NOTE]
    > By default, the cost of acquiring the fixed asset is calculated as the cost price of all components. However, you can modify the cost amount as you require.

## Reverse acquisition transactions
By default, when you reverse transactions, the reversal date is equal to the original transaction date. However, you can specify a different reversal date. 

1. 'Select **Fixed assets (Russia) > Fixed assets**. On the Action Pane, select **Value models**. Then, on the **FA value models** page, on the Action Pane, select **Transactions** to open the **FA transactions** page'. 
2. Select a transaction, and then, on the Action Pane, select **Reverse transaction**. In the **Reverse transaction** dialog box, you can change the transaction reversal date as you require.
3. Select **OK**. A transaction to reverse the original transaction is created on the **FA transactions** page.
4. Select **Voucher** to open the **Voucher transactions** page, where you can view the transactions in the ledger.

When reverse transactions are posted for all value models, the status of the fixed asset is changed to **Scheduled** or **Bought**, depending on original status of the fixed asset.

When reverssing a transaction with the **Putting into operation** type for the fixed asset, which has components, the items are returned to inventory at the same cost price that they were issued from inventory at when the **Putting into operation** transaction was posted. The inventory transactions are marked and, after inventory closing, have the same cost price.

> [!NOTE]
> You can reverse **Putting into operation** transactions via the Fixed asset journal (**Fixed asset (Russia) \> Journals \> FA journal**).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]