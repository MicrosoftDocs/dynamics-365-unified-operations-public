---
title: Acquire a fixed asset with asset retirement obligations
description: For Japan, the asset retirement obligation (ARO) is discounted to present value, and added to the acquisition cost of the fixed asset.
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
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset
---
# Acquire a fixed asset with asset retirement obligations

[!include [banner](../../includes/banner.md)]

For Japan, the asset retirement obligation (ARO) is discounted to present value, and added to the acquisition cost of the fixed asset. 



Use this task to learn how to acquire a fixed asset with ARO. 



In order to complete this task, the Fixed Assets configuration key must be selected.



This task uses the JPMF demo company data.

1. Go to Fixed assets > Asset retirement obligations > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. In the Date field, enter a date.
7. In the Account field, specify the desired values.
8. In the Book field, type a value.
9. In the Debit field, enter a number.
10. Click Functions.
11. Click Generate asset retirement obligation transactions.
    * The menu at Functions > Generate asset retirement obligation transactions is used when the fixed asset is in the same journal.     You can also use the menu at Proposals > Capitalized asset retirement obligation for already acquired fixed assets.  
    * Confirm that a new record with Document type of Asset retirement obligation is created.  
12. In the list, mark the selected row.
    * The proposed amount is discounted to present value.  
13. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
