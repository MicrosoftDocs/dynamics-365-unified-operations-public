--- 
# required metadata 
 
title: Create an accelerated depreciation document and enter usage data (Japan)
description: For Japan, Accelerated depreciation is declared on a per document basis. 
author: ShylaThompson
manager: AnnBe 
ms.date: 09/22/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create an accelerated depreciation document and enter usage data (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

For Japan, Accelerated depreciation is declared on a per document basis. Each document can contain multiple fixed assets. You must calculate an overuse rate on the accelerated depreciation document and multiply it by the ordinary depreciation amount to get the amount for the accelerated depreciation. 



The details of the accelerated depreciation declaration are listed on the document. Only a confirmed accelerated depreciation document can be used at accelerated depreciation proposal for posting. 



This procedure walks you through creating a fixed asset with an accelerated depreciation profile and then creating an accelerated depreciation document and assigning the fixed asset to it. Finally, you can enter the overuse hours for the fixed asset and calculate overuse rate on the document.



In order to complete this procedure, the Fixed asset configuration key must be selected.



This procedure was created using the demo data company JPMF.


## Create a fixed asset with accelerated depreciation
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. Click New.
3. In the Fixed asset group field, type a value.
    * Example: VEHI-M  
4. Note the fixed asset number for later reference
5. In the Name field, type a value.
6. Click Save.
7. Click Books.
8. Expand the Depreciation section.
    * Confirm that the Accelerated depreciation profile field is configured properly.  
    * For the existing fixed assets, you can also manually enter this value to apply accelerated depreciation profile to it.  

## Acquire the fixed asset
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. In the Date field, enter a date.
7. Use the previously noted fixed asset number
8. In the Debit field, enter a number.
9. Click Save.
10. Click Post.

## Enter overuse information in the accelerated depreciation document
1. Go to Fixed assets > Periodic tasks > Accelerated depreciation > Accelerated depreciation document.
2. Click New.
3. In the Description field, type a value.
4. In the Fixed asset equipment group field, type a value.
5. In the From date field, enter a date.
    * The From date and To date are used to define the declaration period during which to apply and to declare the accelerated depreciation.  
6. In the To date field, enter a date.
    * The From date and To date are used to define the declaration period during which to apply and to declare the accelerated depreciation.  
7. Expand the Fixed assets and working hours detail section.
    * It is recommended to enter working hours by fixed assets so that the data is accurate and complete.  
8. Click Add by query.
9. In the Criteria field, Filter the proper fixed assets.
10. Click OK.
11. In the Planned field, enter a number.
    * Other than Planned hours, you can also choose to enter Reserved or Actual hours if they apply.  
12. Click Save.
13. Click Calculate daily average hour.
    * Confirm that the Overuse rate is calculated and updated.  
    * If you have already calculated the Overuse rate you can choose to skip the calculate step and directly enter the Overuse rate and confirm the document for proposal purpose.  
14. Click Confirm.
    * Only confirmed Accelerated depreciation documents can be used for the proposal.  

