--- 
# required metadata 
 
title: Create and confirm a recognition test (Japan)
description: For Japan, impairment is conducted in two main steps. 
author: ShylaThompson
manager: AnnBe 
ms.date: 02/26/2016
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
# Create and confirm a recognition test (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

For Japan, impairment is conducted in two main steps. The first step is to test whether an impairment is needed. The second step is to calculate the impairment amount if needed. 



Use this task to learn how to run the two step process in a recognition test and get it ready for posting. 



In order to complete this procedure, the Fixed Asset configuration key must be selected.



This procedure was created using the demo data company JPMF.

1. Go to Fixed assets > Periodic tasks > Impairment recognition (Method I: on a bigger group than CGU).
    * For method 2, go to Fixed assets > Periodic tasks > Impairment recognition (Method II: Allocate carrying amount of shared asset / goodwill to CGUs).  
2. Click New.
3. In the CGU group field, type a value.
4. In the Date field, enter a date.
    * Enter the date on which to post the impairment transaction.  
5. In the Description field, type a value.
6. Click Save.
7. Click Recognition test.
8. Click Run test.
    * The recognition test will compare the sum of the net book value with the undiscounted cash flow of each cash generating unit to determine if calculation of the impairment amount is needed.  
9. Click Calculate.
    * If the test result is 'Yes', then the recognition test will subtract the recoverable amount from the net book value to determine the impairment adjustment amount. The impairment adjustment amount is distributed to each of the fixed assets for posting.  
10. Click Confirm.
    * You only can post confirmed recognition tests.  
11. Click Yes.

