---
title: Maintain impairment indicators on individual assets
description: Use this task to learn how to maintain impairment indicators on individual assets.
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
ms.search.form: AssetTable, AssetBook, AssetImpairmentIndicator_JP, AssetImpairmentReview_JP, SysQueryForm
---
# Maintain impairment indicators on individual assets

[!include [banner](../../includes/banner.md)]

Use this task to learn how to maintain impairment indicators on individual assets.



Run the task 'Setup impairment accounting common parameters' prior to this running this procedure. 



This task uses the JPMF demo company data.


## Update impairment indicator on a single fixed asset
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. In the list, find and select the desired record.
    * Example: TOOLM-000006  
3. Click Books.
4. Click Functions.
5. Click Update impairment indicators.
6. Click New.
7. In the Modify date field, enter a date.
    * Example: 2013-04-01  
8. In the Description field, type a value.
9. In the Undiscounted cash flow field, enter a number.
    * In this example, enter field '3900000.'  
10. In the Recoverable amount field, enter a number.
    * In this example, enter field '3350226.'  
11. Click Save.

## Update impairment indicator on the impairment management form
1. Go to Fixed assets > .. > .. > Impairment management.
2. Click Query.
3. In the Criteria field for the fixed asset group row, click the drop-down button to open the lookup.
4. Click OK.
5. In the list, find and select the desired record.
    * TOOLM-000007  
6. In the list, find and select the desired record.
    * TOOLM-000008  
7. Click Update impairment indicators.
8. In the list, mark the selected row.
    * Select the record with Fixed asset number 'TOOLM-000007.'  
9. In the Modify date field, enter a date.
    * Define date = 2013-04-01  
10. In the Description field, type a value.
11. In the Undiscounted cash flow field, enter a number.
    * Enter 2500000.00.  
12. In the Recoverable amount field, enter a number.
    * Enter = 2000000.00.  
13. In the list, find and select the desired record.
    * Select the row with Fixed asset number 'TOOLM-000008.'  
14. In the Modify date field, enter a date.
15. In the Description field, type a value.
16. In the Undiscounted cash flow field, enter a number.
    * Enter 2000000.00.  
17. In the Recoverable amount field, enter a number.
    * Enter 1500000.00.  
18. Click Update indicator.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
