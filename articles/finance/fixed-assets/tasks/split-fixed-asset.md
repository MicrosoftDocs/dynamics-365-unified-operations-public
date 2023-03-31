--- 
# required metadata 
 
title: Split a fixed asset
description: This article explains how to split a percentage of one asset book to a new asset book.
author: moaamer
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetTable, AssetBook, AssetSplit, AssetBookLookup, LedgerJournalTable, LedgerJournalTransAsset   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Split a fixed asset

[!include [banner](../../includes/banner.md)]

This article explains how to split a percentage of one asset book to a new asset book. 

## Create a new fixed asset

1. Go to **Fixed assets \> Fixed assets \> Fixed assets**.
2. Select **New**.
3. In the **Fixed asset group** field, enter or select a value. Note the fixed asset number to use in the split process later.
4. In the **Name** field, enter a value.
5. Close the page.

## Split a fixed asset

Before a fully depreciated asset is split, the asset book status should be manually changed from **Closed** to **Open**. This step is required because the book status has to be **Open** if you must post transactions for the asset (for example, for a disposal sale). You must also turn on the **Allow multiple transactions within one voucher** parameter on the **General** tab of the **General ledger parameters** page. After the asset book status is changed and multiple transactions within one voucher have been allowed, complete the following steps to split the asset.

1. In the list, find and select the link of the fixed asset to split.
2. Select **Books**. Select the book to split to the new asset.
3. Select **Functions**.
4. Select **Split fixed asset**.
5. In the **To fixed asset** field, enter or select a value.
6. In the **To book** field, select the drop-down button to open the lookup.
7. In the **Transaction date** field, enter a date.
8. In the **Percent** field, enter a number.
9. In the **Journal name** field, enter or select a value.
10. Select **OK**.

## Post the journal transaction

1. Go to **Fixed assets \> Journal entries \> Fixed assets journal**.
2. In the list, select the journal created with the split process.
3. Select **Lines**.

    - Verify the journal lines created.
    - An Acquisition adjustment transaction is created for the original asset to decrease the value by the percentage specified during the split process.
    - An Acquisition transaction is created for the new asset for the same amount.

4. Select **Post**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
