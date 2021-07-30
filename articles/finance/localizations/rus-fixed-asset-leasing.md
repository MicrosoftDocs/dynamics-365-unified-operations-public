---
# required metadata

title: Create a fixed asset lease and a return from lease transaction (Russia)
description: This topic explains how to the lease of a fixed asset and the subsequent return of the leased asset in Microsoft Dynamics 365 Finance in Russia.
author: ShylaThompson
ms.date: 07/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Create a fixed asset lease and a return from lease transaction (Russia)

[!include [banner](../includes/banner.md)]

You can register the lease of a fixed asset and the subsequent return of the leased asset. In this way, you can record the transactions for historical purposes.

## Lease a fixed asset

1. Go to **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
2. Select the fixed asset to lease, and then, on the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Lease** to open the **FA leased** page.
3. Create a new line.
4. In the **Date of lease** field, select the date when the fixed asset was leased out.
5. In the **Expected return date** field, select the planned return date.
6. In the **Leaseholder** field, enter the name of the lessee.
7. In the **Location** field, select the location of the leased fixed asset.
8. Close the page.
9. Go to **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
10. Create a new journal.
11. In the **Name** field, select a journal name.
12. In the **Description** field, view or modify the description of the journal.
13. Select **Lines** to open the **Journal voucher** page, so that you can create fixed asset transactions.
14. Select **New** to open the **Add to journal** dialog box.
15. In the **Transaction date** field, select the date of the transaction. The date that you select must be the same as or later than the date that you selected in the **Date of lease** field on the **FA leased** page.
16. In the **Transaction type** field, select **Lease**.
17. In the **FA inventory number** field, select the number of the leased fixed asset.
18. In the **Value model** field, select a value model for the fixed asset.
19. In the **Reason code** field, select a reason code.
20. In the **Reason comment** field, view or modify the reason for leasing the fixed asset.
21. Select **OK**. The lines for the leased fixed asset appear in the journal.

    > [!NOTE]
    > To create transactions for several fixed assets, you can select **Group operations** \> **Lease** on the Action Pane of the **Journal voucher** page.

22. Select **Validate** \> **Validate** to validate the transaction.
23. Select **Post** \> **Post** to post the journal. Fixed asset and ledger transactions are created.

    On the **Fixed assets** page, the status of the fixed asset changes from **In operation** to **Lending**.

## Register the return of a leased fixed asset

You can register the return of a leased fixed asset in the same way that you registered the lease. Create a return-from-lease transaction on the **FA journal** page, and then verify the return date on the **FA on loan** and **Journal transactions** pages.

1. Go to **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
2. Select the leased fixed asset to return, and then, on the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Lease** to open the **FA leased** page.
3. Create a new line.
4. In the **Actual return date** field, view or modify the date, and then close the page.
5. Follow steps 9 through 21 in the [Lease a fixed asset](#lease-a-fixed-asset) procedure.

    > [!NOTE]
    > In the **Add to journal** dialog box, you must select **Return from lease** in the **Transaction type** field to create a return-from-lease transaction.

6. Select **Validate** \> **Validate** to validate the transaction.
7. Select **Post** \> **Post** to post the journal. Fixed asset and ledger transactions are created.

    On the **Fixed assets** page, the status of the fixed asset changes from **Lending** to **In operation**.

> [!TIP]
> Lease and return-from-lease transactions are reversed in the same way as acquisition transactions.

## Reverse fixed asset lease and return lease from transactions
By default, when you reverse transactions, the reversal date is equal to the original transaction date. However, you can specify a different reversal date.

1. Go to **Fixed assets (Russia)** > **Fixed assets**, and on the Action Pane, select **Value models**.
2. On the **FA value models** page, on the Action Pane, select **Transactions**.
3. On the **FA transactions** page, select and transaction and on the Action Pane, select **Reverse transaction**.
4. In the **Reverse transactions** dialog box, change the transaction reversal date as needed and then select **OK**. A transaction to reverse the original transaction is created and added to the **FA transactions** page.
5. Select **Voucher**, and on the **Voucher transactions** page, view the transactions in the ledger.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
