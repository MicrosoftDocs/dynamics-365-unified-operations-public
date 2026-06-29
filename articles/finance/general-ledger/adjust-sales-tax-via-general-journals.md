---
title: Adjust sales tax through general journals
description: Learn how to adjust sales tax by using general journals so that you can balance a tax account, record specific tax transactions, or correct discrepancies.
author: Kai-Cloud
ms.author: kailiang
ms.topic: how-to
ms.date: 06/24/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: 
ms.search.validFrom: 2022-08-03
ms.search.form: 
ms.dyn365.ops.version:
---

# Adjust sales tax through general journals

[!include[banner](../includes/banner.md)]

Typically, you generate sales tax transactions during invoice posting and settlement. In some cases, you might want to manually post a sales tax transaction that has a specified sales tax code and amount. You can use this approach to balance a tax account, record a specific tax transaction, or correct a tax discrepancy caused by rounding or configuration issues.

1. Go to **General ledger** > **Journals entries** > **General journals**.
1. Create a record, and then select **Lines**.
1. In the **Account** field, enter the tax account number.
1. In the **Debit** or **Credit** field, enter the sales tax amount.
1. In the **Offset account** field, enter the offset account number.
1. On the **General** tab, in the **Sales tax code** field, select the sales tax code.

    > [!NOTE]
    > The sales tax group and item sales tax group don't apply to this process. You must manually select the sales tax code. Make sure that the tax account is maintained in the ledger posting group of the selected sales tax code.

1. Select **Post** to post the journal.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
