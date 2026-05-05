---
title: Reversing fixed asset transactions for India
description: Learn about reversing a fixed asset transaction for India in Microsoft Dynamics 365 Finance, including examples and a step-by-step process.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.date: 05/01/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: India
ms.search.validFrom: 2017-12-31
ms.search.form:
ms.dyn365.ops.version: 7.3
---

# Reversing fixed asset transactions for India

[!include [banner](../../includes/banner.md)]

You can reverse a fixed asset transaction, reverse taxes for the transaction, and update general ledger accounts. The **Books** > **Balances** page for the selected asset displays information about the updates to an asset.

You can reverse fixed asset acquisitions or acquisition adjustment transactions along with the tax that you calculated. You should also reverse the posted tax along with the fixed asset transaction reversal.

As a prerequisite, select the **Companies Act depreciation** and **Income tax Act depreciation** check boxes in the **Fixed assets parameters** page.

1. In **Fixed assets**, select a fixed asset. Select **Books**.
1. Select the book with a tax layer in the **Book** field.
1. Select **Transactions** to open the **Fixed asset transactions** page.
1. Select the transaction that is posted for the acquisition to activate the reverse transaction.
1. Select **Reverse transaction** to open the **Transaction reversal** page.
1. Enter the **Reversal posting date**.
1. Select **OK** to reverse the transactions.

## Example 1

This example shows how to post the **Fixed assets journal** with an acquisition transaction for a selected fixed asset.

1. In **Fixed assets**, select a fixed asset.
1. Select **Books**. Select the book and select **Balances**.
1. The page displays details that are specific to the selected fixed asset, including the posted acquisition transaction.
1. Close the **Balances** page and select **Transactions**.
1. Select a previously posted acquisition transaction and select **Reverse transaction**.
1. Return to the **Balances** page and ensure that the balance of the acquisition transaction is decreased by the amount of the reversed transaction.

## Example 2

In this example, the transaction list for a fixed asset group shows all reversed transactions. You can trace and reverse the acquisition transaction that you reversed in Example 1.

1. In **Fixed assets**, select a fixed asset.
1. Select **Books**. Select **Transactions**, and then select **Reversed tracing**.
1. In the list of reversed transactions, select a previously reversed acquisition transaction, and then select **Reverse transaction**.
1. The previously posted acquisition transaction is restored with a voucher number that's specific to the reversal transaction.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
