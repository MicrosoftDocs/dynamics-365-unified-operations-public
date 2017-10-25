--- 
# required metadata 
 
title: Define loyalty reward points
description: This procedure walks through defining loyalty reward points. 
author: scott-tucker
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: scotttuc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Define loyalty reward points

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure walks through defining loyalty reward points. You should set up loyalty reward points before you set up a loyalty program. This procedure uses the USRT demo data company.

1. Go to Retail and commerce > Customers > Loyalty > Loyalty reward points.
2. Click New.
3. In the Reward point ID field, type a value.
4. In the Description field, type a value.
5. In the Reward point type field, select an option.
    * Select Quantity if you want the reward points to be rounded to the nearest integer. Select Amount if you want the reward points to be rounded according to currency rounding rules. If you select Quantity, skip the next step of this procedure..  
6. In the Currency field, type a value.
    * For Amount type reward points, all points issued will have the selected currency. For Quantity type reward points, this field doesn't apply—skip this step.  
7. Check or uncheck the Redeemable checkbox.
8. In the Redeem ranking field, enter a number.
    * Redeem ranking is used when two or more redeemable reward points can be used to pay for products. If the two reward points have the same redeem ranking, then the one that needs to lower number of points will be used.  
9. In the Expiration time value field, enter a number.
    * The reward points will expire the specified number of days, months, or years after when the points are issued. A value of ‘0’ means the loyalty reward points will never expire.  
10. In the Expiration time unit field, select an option.
11. Click Save.

