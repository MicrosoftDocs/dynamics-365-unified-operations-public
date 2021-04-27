---
# required metadata

title: Reversing fixed asset transactions for India
description:  This topic walks you through reversing a fixed asset transaction for India in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.date: 01/03/2017
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
ms.search.region: India
# ms.search.industry:
ms.author: atrukawk
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Reversing fixed asset transactions for India

[!include [banner](../includes/banner.md)]

You can reverse a fixed asset transaction, reverse taxes for the transaction, and update general ledger accounts. Information about the updates to an asset are displayed in the **Books** > **Balances** page for the selected asset.

You can reverse fixed asset acquisitions or acquisition adjustment transactions with the tax that is calculated. The posted tax should also be reversed along with the fixed asset transaction reversal.

As a prerequisite, the **Companies Act depreciation** and **Income tax Act depreciation** check boxes must be selected in the **Fixed assets parameters** page.

1. In **Fixed assets**, select a fixed asset. Click **Books**.

2. Select the book with a tax layer in the **Book** field.

3. Click **Transactions** to open the **Fixed asset transactions** page.

4. Select the transaction that is posted for the acquisition to activate the reverse transaction.

5. Click **Reverse transaction** to open the **Transaction reversal** page.

6. Enter the **Reversal posting date**.

7. Click **OK** to reverse the transactions.

## Example 1

This example shows how to post the **Fixed assets journal** with an acquisition transaction for a selected fixed asset. 

In **Fixed assets**, select a fixed asset. Click **Books**. Select the book and click **Balances**. The page displays details that are specific to the selected fixed asset including posted acquisition transaction.

Close the **Balances** page and click **Transactions**. Select a previously posted acquisition transaction and click **Reverse transaction**. Return to the **Balances** page and ensure that the balance of the acquisition transaction has been decreased by the amount of the reversed transaction.

## Example 2

In this example, all reversed transactions are displayed in the transaction list for a fixed asset group. The acquisition transaction that was reversed in Example 1 can be traced and reversed. 

In **Fixed assets**, select a fixed asset. Click **Books**. Select **Transactions** and then select **Reversed tracing**. In the list of reversed transactions, select a previously reversed acquisition transaction and click **Reverse transaction**. Notice how the previously posted acquisition transaction has been restored with a voucher number that is specific to the reversal transaction.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]