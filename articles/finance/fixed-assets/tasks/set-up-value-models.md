--- 
# required metadata 
 
title: Set up value models
description: This procedure shows you to how create a new fixed asset book and associate it with a fixed asset group. 
author: saraschi2
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetBookTable, AssetGroupBookSetup   
audience: Application User 
# ms.devlang:  
ms.reviewer: roschlom
ms.search.scope: Core, Operations 
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

This procedure shows you to how create a new fixed asset book and associate it with a fixed asset group. It uses the accountant role and demo data for the USMF legal entity.


## Create a book
1. Go to Fixed assets > Setup > Books.
2. Click New.
3. In the Book field, type a value.
4. In the Description field, type a value.
    * If Calculate depreciation is selected, the associated asset book will be included in depreciation proposals. If it is not selected, the asset book will not be automatically depreciated.  
5. Select Yes in the Calculate depreciation field.
6. In the Depreciation profile field, enter or select a value.
    * An alternative depreciation profile is also known as a switchover method of depreciation. The depreciation proposal will switch to this profile when the alternative profile calculates a depreciation amount that is equal to or greater than the default depreciation profile.  
    * The Extraordinary depreciation profile is used for additional depreciation of an asset in unusual circumstances. For example, you might use this to record depreciation that results from a natural disaster.  
    * If Create depreciation adjustments with basis adjustments is selected, depreciation adjustments will be automatically created when the value of the asset is updated. If it is not selected, the updated asset value will only affect depreciation calculations going forward.  
7. Select Yes in the Create depreciation adjustments with basis adjustments field.
    * By default, fixed asset book transactions will post to the general ledger. You can disable posting to the general ledger for the book by setting the Post to general ledger field to No. Books that do not post to the general ledger are typically used for tax reporting purposes. This gives you additional flexibility to delete historical transactions for the asset book because they have not been committed to the general ledger.  
    * The Posting layer defaults to the Current layer if the book posts to general ledger, and None if it does not post to general ledger. Update Posting layer if you need transactions for this book to be posted to a different layer.  
8. In the Calendar field, enter or select a value.
    * Derived books will post transactions to different books at the same time. You create the transactions with the primary book and during posting, an exact copy of the transaction is posted to the derived book. There is no recalculation with derived book transactions, so it should not be used for depreciation transactions.  

## Associate the book with a fixed asset group
1. Click Fixed asset groups.
2. In the Fixed asset group field, enter or select a value.
3. In the Service life field, enter a number.
    * Note that Depreciation periods is calculated after setting the Service life.  
    * You are able to set the depreciation convention as required for tax purposes.  

