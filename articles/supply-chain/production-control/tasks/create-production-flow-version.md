--- 
# required metadata 
 
title: Create a production flow version
description: This procedure focuses on creating a new production flow version. 
author: johanhoffmann
ms.date: 11/03/2017
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a production flow version

[!include [banner](../../includes/banner.md)]

This procedure focuses on creating a new production flow version. For this procedure, the production parameters for lean manufacturing and the units of measurement for class time must be defined. You also need to define a value stream and a production group. To learn more about production flows and activities in lean manufacturing, see the white papers on Lean manufacturing for Microsoft Dynamics AX. The demo data company used to create this procedure is USMF.


## Create a production flow
1. Go to Production control > Setup > Lean production flow > Production flows.
2. Click New.
3. In the Name field, type a value.
4. In the Description field, type a value.
5. In the Name field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
    * Select an operating unit of type value stream. A value stream is an operating unit that spans all activities and flows of the value stream. At this stage, operating units are limited to a legal entity and have no further functionality.  
7. In the Production group field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
    * Select a production group for the production flow. Production groups allow the definition of material, labor, and WIP accounts for a production process. To associate the accounting context to a production flow, a production group must be selected.  
9. Click Save.

## Create a production flow version
1. Click Add.
2. In the Expiration date field, enter a date and time.
    * If required, define an Expiration date for the version. You can update it at any given time, even for active versions. You can use it to plan to phase out a version.  
3. Click OK.
4. In the list, mark the selected row.
5. In the Unit field, type a value.
6. ResolveChanges the Takt unit.
7. In the Average takt time field, enter a number.
    * Define the Average takt time of the version. For the takt control of the production flow version, define a targeted average takt time. The takt is defined as quantity per time period. In the example, the takt time is 0.2 hours per 10 pieces. For a working time of 8 hours, this corresponds to a daily throughput capacity of 400 pieces.  
8. In the Quantity per cycle field, enter a number.
    * Define the quantity per cycle related to the Average takt time.  
9. Toggle the expansion of the Version details section.
10. In the Minimum takt time field, enter a number.
    * Define the minimum takt time. The minimum takt time must be less than or equal to the average takt time.  
11. In the Maximum takt time field, enter a number.
    * The maximum takt time must be higher than or equal to the Average takt time.  
12. In the Period for actual cycle time (days) field, enter a number.
    * Enter the number of days in the Period for actual cycle time. The period for actual cycle time is the number of days that jobs are aggregated from the actual minute backwards to calculate the actual cycle time. The value can be changed at any time and is only used for the calculation of the actual cycle times.  
13. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]