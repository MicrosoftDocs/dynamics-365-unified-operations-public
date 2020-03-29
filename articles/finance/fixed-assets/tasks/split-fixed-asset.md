--- 
# required metadata 
 
title: Split a fixed asset
description: This topic explains how to split a percentage of one asset book to a new asset book. 
author: saraschi2
manager: AnnBe 
ms.date: 08/06/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetTable, AssetBook, AssetSplit, AssetBookLookup, LedgerJournalTable, LedgerJournalTransAsset   
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
# Split a fixed asset

[!include [banner](../../includes/banner.md)]

This topic explains how to split a percentage of one asset book to a new asset book. It uses the Accountant role and USMF demo data.


## Create a new fixed asset
1. In the navigation pane, go to **Modules > Fixed assets > Fixed assets > Fixed assets**.
2. Select **New**.
3. In the **Fixed asset group** field, enter or select a value. Note the fixed asset number to use in the split process later.  
4. In the **Name** field, type a value.
5. Close the form.

## Split a fixed asset
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
1. In the navigation pane, go to **Modules > Fixed assets > Journal entries > Fixed assets journal**.
2. In the list, select the journal created with the split process.
3. Select **Lines**.

    - Verify the journal lines created.  
    - An Acquisition adjustment transaction is created for the original asset to decrease the value by the percentage specified during the split process.  
    - An Acquisition transaction is created for the new asset for the same amount.  

4. Select **Post**.

