---
title: Create and confirm recognition test
description: For Japan, impairment is conducted in two main steps.
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
ms.search.form: AssetImpairmentManageTestResult_JP, AssetImpairmentRecognition_JP
---
# Create and confirm recognition test

[!include [banner](../../includes/banner.md)]

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



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
