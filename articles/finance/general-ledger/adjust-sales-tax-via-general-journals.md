---
# required metadata

title: Adjust sales tax via general journals
description: Use this article to adjust sales tax by using general journals.
author: kailiang
ms.date: 08/05/2022
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
ms.search.region: 
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2022-08-03
ms.dyn365.ops.version:

---

# Adjust sales tax via general journals

[!include[banner](../includes/banner.md)]

In general, sales tax transactions are only generated during invoice posting and settlement. In some cases, you might want to manually post a sales tax transaction with a specified sales tax code and amount so that you can balance a tax account, record a specific tax transaction, or correct the tax discrepancy due to rounding or configuration issues.

1. Go to **General ledger** > **Journals entries** > **General journals**.
2. Create a record and then select **Lines**.
3. In the **Account** field, enter the tax account number.
4. In the **Debit** or **Credit** field, enter the sales tax amount.
5. In the **Offset account** field, enter the offset account number.
6. On the **General** tab, in the **Sales tax code** field, select the sales tax code.
    
    > [!NOTE]
    > **Sales tax group** and **Item sales tax group** are irrelevant to this process. Here, the **Sales tax code** must be selected manually. Make sure the tax account is maintained in the **Ledger posting group** of the selected sales tax code. 

7. Select **Post** to post the journal.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
