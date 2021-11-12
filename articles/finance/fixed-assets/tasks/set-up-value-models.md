--- 
# required metadata 
 
title: Set up value models
description: This procedure shows you to how create a new fixed asset book and associate it with a fixed asset group. 
author: moaamer
ms.date: 11/15/2021
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetBookTable, AssetGroupBookSetup   
audience: Application User 
# ms.devlang:  
ms.reviewer: roschlom
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up value models

[!include [banner](../../includes/banner.md)]
[!include [preview banner](../../includes/preview-banner.md)]


This procedure shows you to how create a new fixed asset book and associate it with a fixed asset group. It uses the accountant role and demo data for the USMF legal entity.

## Create a book
1. Go to Fixed assets > Setup > Books.
2. Click **New**.
3. In the **Book** field, type a value.
4. In the **Description** field, type a value.
    * If **Calculate depreciation** is selected, the associated asset book will be included in depreciation proposals. If it is not selected, the asset book will not be automatically depreciated.  
5. Select Yes in the **Calculate depreciation** field.
6. In the **Depreciation profile** field, enter or select a value.
    * An alternative depreciation profile is also known as a switchover method of depreciation. The depreciation proposal will switch to this profile when the alternative profile calculates a depreciation amount that is equal to or greater than the default depreciation profile.  
    * The Extraordinary depreciation profile is used for additional depreciation of an asset in unusual circumstances. For example, you might use this to record depreciation that results from a natural disaster.  
    * If **Create depreciation adjustments with basis adjustments** is selected, depreciation adjustments will be automatically created when the value of the asset is updated. If you don't select that option, the updated asset value will only affect depreciation calculations going forward.  
7. Select **Yes** in the **Create depreciation adjustments with basis adjustments** field.
    * By default, fixed asset book transactions will post to the general ledger. You can disable posting to the general ledger for the book by setting the **Post to general ledger** field to **No**. Books that don't post to General ledger are typically used for tax reporting. This option gives you additional flexibility to delete historical transactions for the asset book because they have not been committed to General ledger.  
    * The **Posting layer** is set to the **Current layer** by default if the book posts to General ledger, and **None** if it doesn't post to General ledger. Update the **Posting layer** setting if you need transactions for this book to be posted to a different layer.  
8. Calculate positive depreciation.
   * By default, the **Calculate positive depreciation** option is set to **No**. This setting indicates that depreciation will credit the selected asset book. In addition, the options **Allow net book value higher than acquisition price** and **Allow negative net book value** options are both set to **No**, and they can be changed independently. 
   * To calculate positive depreciation, set the **Calculate positive depreciation** field to **Yes**. This selection indicates the depreciation will debit the fixed asset book. When the **Calculate positive depreciation** is set to Yes, the **Allow net book value higher than acquisition price** and **Allow negative net book value** options will be set to **Yes** automatically, and will be locked. Locking these options helps ensure that positive depreciation will only applied to fixed assets that were acquired with negative book value (credit). 
10. In the **Calendar** field, enter or select a value.
    * Derived books will post transactions to different books at the same time. You create the transactions with the primary book and during posting, an exact copy of the transaction is posted to the derived book. There is no recalculation with derived book transactions, so it should not be used for depreciation transactions.  

## Associate the book with a fixed asset group
1. Click **Fixed asset groups**.
2. In the **Fixed asset group** field, enter or select a value.
3. In the **Service life** field, enter a number.

  * Depreciation periods are calculated after the service life of the asset is entered.  
  * The depreciation convention can be set as required for tax purposes.
  * For fixed assets that are associated with leases, the value in the **Service life** field will be overridden by the lesser of either the lease term in the asset book or asset’s useful life. If the **Transfer of ownership** field is set to **Yes** for the lease book, the value in the **Service life** field will always be the asset’s useful life.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
