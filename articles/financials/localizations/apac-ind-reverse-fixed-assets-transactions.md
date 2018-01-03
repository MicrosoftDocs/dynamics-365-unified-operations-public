---
# required metadata

title: Reversing fixed asset transactions for India
description:  This topic walks you through reversing a fixed asset transaction for India in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: AdamTrukawka
manager: AnnBe
ms.date: 01/03/2017
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
ms.search.region: India
# ms.search.industry:
ms.author: atrukawk
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Reversing fixed asset transactions

[!include[banner](../includes/banner.md)]

You can reverse a fixed asset transaction, reverse taxes for the transaction, and update general ledger accounts. Information about the all updates to an asset are displayed in the **Books** > **Balances** form for the selected asset.

You can reverse fixed asset acquisitions or acquisition adjustment transactions with tax calculated. The posted tax should also be reversed along with the fixed asset transaction reversal.

The **Companies Act depreciation** and the **Income tax Act depreciation** check boxes must be selected in the **Fixed assets parameters** form.

1. **Fixed assets** > Select a fixed asset line, and click **Books**.

2. Select the book with a tax layer in the **Book** field.

3. Click **Transactions** to open the **Fixed asset transactions** page.

4. Select the transaction posted for acquisition to activate the **Reverse transaction**.

5. Click **Reverse transaction** to open the **Transaction reversal** page.

6. Enter the **Reversal posting date**.

7. Click **OK** to reverse the transactions.

## Example 1

Post Fixed assets journal with acquisition transaction for selected fixed asset. Navigate to **Fixed assets** > Select the fixed asset and click **Books** > Select book and click **Balances**. The form displays details specific to selected fixed asset including posted acquisition transaction.

Close **Balances** form and click **Transactions**. Navigate to recently posted acquisition transaction. Select previously posted acquisition transaction and click **Reverse transaction**. Navigate back to **Balances** and ensure balance of acquisition transaction has been decreased by amount of reversed transaction.

## Example 2

All reversed transactions are displayed in the transaction list for a fixed asset group. The acquisition transaction that was reversed in earlier example can be traced and also reversed. 

Navigate to **Fixed assets** > Select the fixed asset and click **Books** > Select **Transactions** > Select **Reversed tracing**. Form list all reversed transactions select previously reversed acquisition transaction and click **Reverse transaction**. Notice previously acquisition transaction has been restored with voucher number specific to reversal transactions.
