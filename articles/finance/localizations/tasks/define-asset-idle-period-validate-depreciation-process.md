---
title: Define asset idle period and validate depreciation process
description: Use this task to learn how to define fixed asset idle period.
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
ms.search.form: AssetParameters, AssetIdlePeriodAssign_JP, AssetTable, AssetBook, AssetIdlePeriodUpdate_JP, AssetProfile, LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm
---
# Define asset idle period and validate depreciation process

[!include [banner](../../includes/banner.md)]

Use this task to learn how to define fixed asset idle period. 

Validate profile and proposal.



In order to complete this task, the Fixed Assets configuration key must be selected.



This task uses the JPMF demo company data.


## Assign number sequence in FA parameter form
1. Go to Fixed assets > Setup > Fixed assets parameters.
2. Click the Number sequences tab.
3. In the list, find and select the desired record.
    * Reference = Fixed asset idle period  
4. In the Number sequence code field, enter or select a value.
5. Click Save.
6. Close the page.

## Assign idle period for a Fixed asset
1. Go to Fixed assets > Periodic tasks > Assign idle period to a fixed asset.
2. Click New.
3. In the Description field, type a value.
4. Expand the General section.
5. In the From date field, enter a date.
    * From date = 01/01/2016  
6. In the To date field, enter a date.
    * To date = 12/31/2017  
7. In the Reason field, type a value.
8. Expand the Idle Periods section.
9. Click New.
10. In the Fixed asset group field, enter or select a value.
    * EQUP-M  
11. In the Fixed asset number field, enter or select a value.
    * EQUPM-000024  
12. In the Book field, enter or select a value.
    * 200NDB_CUR  
13. Click Save.
14. Click Confirm.
15. Close the page.

## Validate Fixed asset book
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. In the list, find and select the desired record.
    * EQUPM-000024  
3. Click Books.
4. In the list, find and select the desired record.
    * 200NDB_CUR  
5. Click Functions.
6. Click Update idle periods.
    * Validate the idle period created for the fixed asset book is listed  
7. Close the page.
8. Click Profile.
    * Validate the profile displays zero depreciation for the idle period  
9. Close the page.
10. Close the page.
11. Close the page.

## Execute depreciation proposal
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, enter or select a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Depreciation proposal.
8. In the To date field, enter a date.
    * To date = 12/31/2017  
9. Expand the Records to include section.
10. Click Filter.
11. Click Reset.
12. In the list, mark the selected row.
    * Field = Fixed asset number  
13. In the Criteria field, enter or select a value.
    * EQUPM-000024  
14. In the list, find and select the desired record.
    * Field = Book  
15. In the Criteria field, enter or select a value.
    * 200NDB_CUR  
16. Click OK.
17. Click OK.
    * Validate no depreciation journal is created for the idle period  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
