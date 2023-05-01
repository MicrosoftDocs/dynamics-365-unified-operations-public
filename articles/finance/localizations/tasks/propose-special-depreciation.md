---
title: Propose special depreciation
description: In Japan, a special depreciation is permitted under certain conditions.
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
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm
---
# Propose special depreciation

[!include [banner](../../includes/banner.md)]

In Japan, a special depreciation is permitted under certain conditions. For Reserve method, this is a two step task: post reserve, and then post reserve allocation. For Direct-off method, only one step is needed, which is the same procedure as post reserve. 



Use this procedure to learn how to propose special depreciation under Reserve method.

Make sure that the fixed asset has been acquired before following this procedure. Also, be sure that the Fixed Assets configuration key is selected.



This procedure uses the JPMF demo company data.


## Post Reserve
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Extraordinary depreciation proposal.
8. In the To date field, enter a date.
9. Click Filter.
10. In the Criteria field, type a value.
11. Click OK.
12. Click OK.
13. Click Post.

## Post Reserve allocation
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Extraordinary depreciation proposal.
8. In the To date field, enter a date.
    * Depending on the Allocation start convention, the Reserve allocation start date is different.  
9. Click Filter.
10. In the Criteria field, type a value.
11. Click OK.
12. Click OK.
13. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
