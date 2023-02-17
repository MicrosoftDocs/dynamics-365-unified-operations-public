--- 
# required metadata 
 
title: Define continuity schedules
description: This article walks through setting up a continuity program (otherwise known as reoccurring orders). 
author: josaw1
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: MCRContinuitySchedule, EcoResProductDetailsExtended   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Define continuity schedules

[!include [banner](../includes/banner.md)]

This article walks through setting up a continuity program (otherwise known as reoccurring orders). This article uses company USRT in the demo data.


## Create continuity program
1. Go to Retail and Commerce > Continuity > Continuity programs.
2. Click New.
3. In the Schedule ID field, type the continuity schedule ID.
4. In the Order start field, select 'First event'.
    * If a customer places a new order for the continuity program, there are two options for which product will be shipped:  1. First event: the first product in the continuity program will be shipped.  2. Current event: the current product will be shipped. For example. three months into the program, the customer will receive the third in the program.  
5. Select 'Yes' to prompt for the order start date.
6. Click Add line.
7. In the Item number field, type the item number for the first product ('0013').
8. Type 'CP'.
9. Enter the date when the first product will be available for order.
10. Click Add line.
11. In the Item number field, type '0014'.
12. In the Date interval code field, clear the value so the field is empty.
    * For this procedure, clear the date interval. You'll set the date as incremental from the start date of the first item.  
13. Here you'll enter the interval at which the products are shipped. Type '30'.
    * For a monthly program, you'll enter 30 days for the interval.  
14. Click Add line.
15. In the Item number field, type '0015'.
16. Type 'End'.
17. Click Save.

## Assign to continuity item
1. Go to Product information management > Products > Released products.
2. Select item '0016'.
    * For this procedure, you'll select item number 0016. Normally, you'll have created a released product that has additional continuity business logic applied when it's placed on a sales order in call center.  
3. In the list, click the link in the selected row.
4. Click Edit.
5. Expand or collapse the Sell section.
6. Here you'll enter the continuity program that this item represents. Type the Schedule ID you created earlier.
    * When this item is sold in a call center, additional business logic is applied from the selected continuity program.  
7. Click Save.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]