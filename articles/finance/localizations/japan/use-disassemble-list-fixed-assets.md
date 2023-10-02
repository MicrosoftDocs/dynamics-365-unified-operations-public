---
title: Use disassemble list for fixed assets
description: In Japan, you can transfer a component of a fixed asset to inventory.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: AssetTable, AssetComponentList_JP, AssetComponentPriceCalcDropDialog_JP, LedgerJournalTable, LedgerJournalTransAsset
---
# Use disassemble list for fixed assets

[!include [banner](../../includes/banner.md)]

In Japan, you can transfer a component of a fixed asset to inventory. 



This task walks you through using the disassembly list to write down the fixed asset, and create the inventory at the same time.



Before you can complete this task, you must complete the tasks in "Use assemble list of a fixed asset" first. 



This task was created using the demo data company JPMF.


## Enter the disassembly list
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. In the list, mark the selected row.
3. On the Action Pane, click Fixed asset.
4. Click Components.
5. In the list, mark the selected row.
6. Click Add to disassembly list.
7. In the Add field, enter a number.
8. Click OK.
9. Click the Disassembly list tab.
    * Verify that the record was added to the disassembly list.  
    * Optional: You can also choose to add the item to disassembly list by clicking on the add button.  
10. Click Calculate prices to open the drop dialog.
11. Click Calculate.
    * Verify that the costs are updated.  
    * You can modify the market value. It will be entered in the journal as the credit amount for the write down of the fixed asset.  

## Post the disassembly list
1. Go to Fixed assets > .. > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Lines.
5. In the Date field, enter a date.
6. In the Transaction type field, select 'Write down adjustment'.
7. In the Account field, specify the desired values.
    * Verify that the credit amount is automatically retrieved as the cost from the disassembly list.  
    * You can modify the credit amount.  
8. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
