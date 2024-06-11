---
title: Use assemble list of a fixed asset
description: In Japan, you can transfer an inventory item to a fixed asset. Learn about assigning components in an assemply list, including a step-by-step process.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 08/29/2018
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetComponentList_JP, LedgerJournalTable, LedgerJournalTransAsset
ms.dyn365.ops.version: Version 7.0.0
---

# Use assemble list of a fixed asset

[!include [banner](../../includes/banner.md)]

In Japan, you can transfer an inventory item to a fixed asset. 



This task walks you through using the assembly list to consume inventory items and create the fixed asset at the same time.



This task was created using the demo data company JPMF.


## Assign component in an assembly list
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. In the list, mark the selected row.
    * Select the fixed asset that you want to assign the assembly list to.  
3. On the Action Pane, click Fixed asset.
4. Click Components.
5. Click Add.
6. In the Item number field, type a value.
    * For example: enter 'D0001'  
7. Click Save.

## Use the assembly list to post a fixed asset write-up transaction
1. Go to Fixed assets > .. > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Lines.
5. In the Date field, enter a date.
6. In the Transaction type field, select 'Write up adjustment'.
7. In the Account field, specify the desired values.
    * Select the fixed asset number that you have assigned to the assembly list.  
8. In the Debit field, enter a number.
    * Enter the cost of the inventory item.  
9. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
