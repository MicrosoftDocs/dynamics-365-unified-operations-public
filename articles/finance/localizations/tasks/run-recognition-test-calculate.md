---
title: Run the recognition test and calculate the impairment amount on individual assets
description: This task walks you through running the recognition test and calculating the impairment amount on individual assets.
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
ms.search.form: AssetImpairmentRecognitionTest_JP, SysQueryForm, AssetImpairmentCreateTest_JP, AssetImpairmentRecognitionTestResult_JP
---
# Run the recognition test and calculate the impairment amount on individual assets

[!include [banner](../../includes/banner.md)]

This task walks you through running the recognition test and calculating the impairment amount on individual assets.



Before you can complete this task, you must maintain impairment indicators on individual assets.



This task was created using the demo data company JPMF.


## Impairment recognition test
1. Go to Fixed assets > Periodic tasks > Impairment on individual assets > Impairment recognition test.
2. Click Query.
3. In the list, find and select the desired record.
    * For this example, select the Fixed asset group row.  
4. In the Criteria field, type a value.
    * Example: TOOL-M  
5. Click OK.
    * Confirm that three fixed assets with impairment indicators configured will be displayed.  
    * TOOLM-000006 does not have any impairment adjustment, whereas TOOLM-000007 and TOOLM-000008 have -1,750,000.00 and -2,250,000.00 respectively.  
6. Click Save impairment to open the drop dialog.
7. In the Description field, type a value.
8. In the Date field, enter a date.
9. Click OK.
    * The Confirmation form of the impaired fixed assets is displayed.  
    * The Impairment test ID is issued.     Remember the Impairment_test_ID for later use in Propose and post.   



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
