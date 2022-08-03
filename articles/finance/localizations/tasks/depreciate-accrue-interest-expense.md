--- 
# required metadata 
 
title: Depreciate and accrue the interest expense for asset retirement obligations
description: For Japan, the depreciation of the asset retirement obligations (ARO) is processed along with the fixed asset. 
author: ShylaThompson
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Depreciate and accrue the interest expense for asset retirement obligations

[!include [banner](../../includes/banner.md)]

For Japan, the depreciation of the asset retirement obligations (ARO) is processed along with the fixed asset. In addition, interest expenses need to be accrued to recognize the full amount of the ARO.



Use this task to depreciate the ARO and accrue the interest expense. 



In order to complete this task, the Fixed Assets configuration key must be selected.



This task was completed using the JPMF demo company data.


## Depreciate a fixed asset with asset retirement obligation
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, select a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Depreciation proposal.
8. In the To date field, enter a date.
9. Click Filter.
10. In the Criteria field, type a value.
11. Click OK.
12. Click OK.
    * The depreciation of asset retirement obligation is indicated by Document type field.  
13. Click Post.

## Accrue the interest expense
1. Close the page.
2. Go to Fixed assets > Journal entries > Fixed assets journal.
3. Click New.
4. In the Name field, select a value.
5. Click Save.
6. Click Lines.
7. Click Proposals.
8. Click Asset retirement obligation - accretion expense.
9. In the To date field, enter a date.
10. Click Filter.
11. In the Criteria field, type a value.
12. Click OK.
13. Click OK.
    * Confirm that the records for interest expenses are proposed.  
    * The interest expenses are indicated by Transaction type  
14. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]