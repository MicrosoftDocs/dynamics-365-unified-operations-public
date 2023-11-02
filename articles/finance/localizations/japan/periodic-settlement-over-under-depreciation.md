---
title: Periodic settlement of over and under depreciation
description: Use this task to learn how to calculate and record depreciation expense for deductible expense.
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
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm, AssetDepPreTaxDedProcess_JP, AssetDepPreTaxDedProcessDetail_JP
---
# Periodic settlement of over and under depreciation

[!include [banner](../../includes/banner.md)]

Use this task to learn how to calculate and record depreciation expense for deductible expense.



This task uses the JPMF demo company data.




## Fixed asset depreciation
1. Go to Fixed assets > .. > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
    * Example: FAD  
4. Click Lines.
5. Click Proposals.
6. Click Depreciation proposal.
7. In the To date field, enter a date.
    * Example: 3/31/2016  
8. Click Filter.
9. In the Criteria field, type a value.
    * For example, set Fixed asset number = BUILM-000005  
10. Click OK.
11. Click OK.
    * Verify that the depreciation journal  was created.  
12. Click Post.

## Over and under depr settlements
1. Go to Fixed assets > Periodic tasks > Settlement of over depreciation or under depreciation amount.
2. Click New.
3. In the To date field, enter a date.
    * Example: 03/31/2016  
4. In the Journal name field, type a value.
    * Example: FAD_TAX  
5. Expand the Records to include section.
6. Click Filter.
7. In the Criteria field, type a value.
    * For example, set the Fixed asset number = BUILM-000005  
8. Click OK.
9. Click OK.
10. Refresh the page.
    * The results may not appear instantly. Click refresh to see if the result is created.  
11. In the list, find and select the desired record.
    * Click the new result with Status = Draft.  
12. Click View settlement results.
    * Verify that the correct result is created.  
13. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
