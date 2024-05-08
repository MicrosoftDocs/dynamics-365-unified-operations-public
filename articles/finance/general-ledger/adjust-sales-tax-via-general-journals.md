---
title: Adjust sales tax via general journals
description: Learn how to adjust sales tax by using general journals so that you can balance a tax account, record specific tax transactions, or correct discrepancies.
author: Kai-Cloud
ms.author: kailiang
ms.topic: article
ms.date: 08/08/2022
ms.custom:
ms.reviewer: kfend
audience: Application User
ms.search.region: 
ms.search.validFrom: 2022-08-03
ms.search.form: 
ms.dyn365.ops.version:
---

# Adjust sales tax via general journals

[!include[banner](../includes/banner.md)]

In general, sales tax transactions are generated only during invoice posting and settlement. In some cases, you might want to manually post a sales tax transaction that has a specified sales tax code and amount, so that you can balance a tax account, record a specific tax transaction, or correct a tax discrepancy that is caused by rounding or configuration issues.

1. Go to **General ledger** \> **Journals entries** \> **General journals**.
2. Create a record, and then select **Lines**.
3. In the **Account** field, enter the tax account number.
4. In the **Debit** or **Credit** field, enter the sales tax amount.
5. In the **Offset account** field, enter the offset account number.
6. On the **General** tab, in the **Sales tax code** field, select the sales tax code.

    > [!NOTE]
    > The sales tax group and item sales tax group are irrelevant to this process. Here, the sales tax code must be manually selected. Make sure that the tax account is maintained in the ledger posting group of the selected sales tax code.

7. Select **Post** to post the journal.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
