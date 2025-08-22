---
title: Create a fixed asset lease and a return from lease transaction (Russia)
description: Learn how to create a fixed asset lease and a return from a leased asset in Russia with Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/22/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
---

# Create a fixed asset lease and a return from lease transaction (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to create a fixed asset lease and a return from a leased asset in Russia with Microsoft Dynamics 365 Finance.

You can register the lease of a fixed asset and the subsequent return of the leased asset. In this way, you can record the transactions for historical purposes.

## Lease a fixed asset

To lease a fixed asset, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
1. Select the fixed asset to lease, and then, on the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Lease** to open the **FA leased** page.
1. Create a new line.
1. In the **Date of lease** field, select the date when the fixed asset was leased out.
1. In the **Expected return date** field, select the planned return date.
1. In the **Leaseholder** field, enter the name of the lessee.
1. In the **Location** field, select the location of the leased fixed asset.
1. Close the page.
1. Go to **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
1. Create a new journal.
1. In the **Name** field, select a journal name.
1. In the **Description** field, view or modify the description of the journal.
1. Select **Lines** to open the **Journal voucher** page, so that you can create fixed asset transactions.
1. Select **New** to open the **Add to journal** dialog.
1. In the **Transaction date** field, select the date of the transaction. The date that you select must be the same as or later than the date that you selected in the **Date of lease** field on the **FA leased** page.
1. In the **Transaction type** field, select **Lease**.
1. In the **FA inventory number** field, select the number of the leased fixed asset.
1. In the **Value model** field, select a value model for the fixed asset.
1. In the **Reason code** field, select a reason code.
1. In the **Reason comment** field, view or modify the reason for leasing the fixed asset.
1. Select **OK**. The lines for the leased fixed asset appear in the journal.

    > [!NOTE]
    > To create transactions for several fixed assets, you can select **Group operations** \> **Lease** on the Action Pane of the **Journal voucher** page.

1. Select **Validate** \> **Validate** to validate the transaction.
1. Select **Post** \> **Post** to post the journal. Fixed asset and ledger transactions are created.

    On the **Fixed assets** page, the status of the fixed asset changes from **In operation** to **Lending**.

## Register the return of a leased fixed asset

You can register the return of a leased fixed asset in the same way that you registered the lease. Create a return-from-lease transaction on the **FA journal** page, and then verify the return date on the **FA on loan** and **Journal transactions** pages.

To register the return of a leased fixed asset, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
1. Select the leased fixed asset to return, and then, on the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Lease** to open the **FA leased** page.
1. Create a new line.
1. In the **Actual return date** field, view or modify the date, and then close the page.
1. Follow steps 9 through 21 in the [Lease a fixed asset](#lease-a-fixed-asset) procedure.

    > [!NOTE]
    > In the **Add to journal** dialog, you must select **Return from lease** in the **Transaction type** field to create a return-from-lease transaction.

1. Select **Validate** \> **Validate** to validate the transaction.
1. Select **Post** \> **Post** to post the journal. Fixed asset and ledger transactions are created.

    On the **Fixed assets** page, the status of the fixed asset changes from **Lending** to **In operation**.

> [!TIP]
> Lease and return-from-lease transactions are reversed in the same way as acquisition transactions.

## Reverse fixed asset lease and return lease from transactions

By default, when you reverse transactions, the reversal date is equal to the original transaction date. However, you can specify a different reversal date.

To reverse a fixed asset lease and return lease from transactions, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** > **Fixed assets**, and on the Action Pane, select **Value models**.
1. On the **FA value models** page, on the Action Pane, select **Transactions**.
1. On the **FA transactions** page, select and transaction and on the Action Pane, select **Reverse transaction**.
1. In the **Reverse transactions** dialog, change the transaction reversal date as needed and then select **OK**. A transaction to reverse the original transaction is created and added to the **FA transactions** page.
1. Select **Voucher**, and on the **Voucher transactions** page, view the transactions in the ledger.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
