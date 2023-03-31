--- 
# required metadata 
 
title: Set up value models
description: This procedure shows you to how create a new fixed asset book and associate it with a fixed asset group. 
author: moaamer
ms.date: 12/03/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetBookTable, AssetGroupBookSetup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up value models

[!include [banner](../../includes/banner.md)]
[!include [preview banner](../../includes/preview-banner.md)]

This procedure shows you to how create a new fixed asset book and associate it with a fixed asset group.

## Create a book
1. Go to **Fixed assets \> Setup \> Books**.
2. Select **New**.
3. In the **Book** field, enter a value.
4. In the **Description** field, enter a value.
5. Set the **Calculate depreciation** option to **Yes**.

    If the **Calculate depreciation** is option is set to **Yes**, the associated asset book will be included in depreciation proposals. If it's set to **No**, the asset book won't automatically be depreciated.

6. In the **Depreciation profile** field, enter or select a value.

    * An alternative depreciation profile is also known as a switchover method of depreciation. The depreciation proposal will switch to this profile when the alternative profile calculates a depreciation amount that is equal to or greater than the default depreciation profile.
    * The Extraordinary depreciation profile is used for additional depreciation of an asset in unusual circumstances. For example, you might use this to record depreciation that results from a natural disaster.
    * If you select **Create depreciation adjustments with basis adjustments**, depreciation adjustments will automatically be created when the value of the asset is updated. Otherwise, the updated asset value will affect only future depreciation calculations.

7. Set the **Create depreciation adjustments with basis adjustments** option to **Yes**.

    * By default, fixed asset book transactions are posted to the general ledger. However, you can disable posting to the general ledger for the book by setting the **Post to general ledger** option to **No**. Books that aren't posted to the general ledger are typically used for tax reporting. This option gives you more flexibility to delete historical transactions for the asset book, because the transactions haven't been committed to the general ledger.
    * By default, the **Posting layer** field is set to the **Current layer** if the book is posted to the general ledger and **None** if the book isn't posted to the general ledger. Update the value of the **Posting layer** field if transactions for this book should be posted to a different layer.

8. Calculate positive depreciation.

    * By default, the **Calculate positive depreciation** option is set to **No**. This setting indicates that depreciation will credit the selected asset book. In addition, the **Allow net book value higher than acquisition price** and **Allow negative net book value** options are both set to **No**, and the settings can be changed independently. 
    * To calculate positive depreciation, set the **Calculate positive depreciation** option to **Yes**. This setting indicates the depreciation will debit the fixed asset book. When the **Calculate positive depreciation** option is set to **Yes**, the **Allow net book value higher than acquisition price** and **Allow negative net book value** options will automatically be set to **Yes**, and they will be locked. This lock helps ensure that positive depreciation will be applied only to fixed assets that were acquired with negative book value (credit). 

10. In the **Calendar** field, enter or select a value.

    Derived books will post transactions to different books at the same time. You create the transactions with the primary book and during posting, an exact copy of the transaction is posted to the derived book. There is no recalculation with derived book transactions, so it should not be used for depreciation transactions.

## Associate the book with a fixed asset group

1. Select **Fixed asset groups**.
2. In the **Fixed asset group** field, enter or select a value.
3. In the **Service life** field, enter a number.

    * Depreciation periods are calculated after the service life of the asset is entered.
    * The depreciation convention can be set as required for tax purposes.
    * For fixed assets that are associated with leases, the value of the **Service life** field will be overridden by the lesser of the lease term in the asset book and asset's useful life. If the **Transfer of ownership** option is set to **Yes** for the lease book, the value of the **Service life** field will always be the asset's useful life.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
