--- 
# required metadata 
 
title: Validate a production flow and version
description: This procedure shows how to create a new production flow and a first version for lean manufacturing. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LeanProductionFlow   
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
# Validate a production flow and version

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a new production flow and a first version for lean manufacturing. Prerequisites: The production parameters for Lean manufacturing and the units of measure for class time must be defined. You need to define a Value stream and a Production group. Refer to the white papers on Lean manufacturing to familiarize yourself with the concepts of production flows and activities. This procedure refers to the legal entity USMF in demo data. However, assuming that the legal entity is configured for Lean manufacturing, other legal entities can be used.


## Create a production flow
1. Go to Production control > Setup > Lean production flow > Production flows.
2. Click New.
3. In the Name field, type a value.
4. In the Description field, type a value.
5. In the Name field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
    * A value stream is an operating unit that spans over all activities and flows of the value stream.   At this stage, operating units are limited to a legal entity and have no further functionality.  
7. In the Production group field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
    * Production groups allow the definition of material, labor, and WIP accounts for a production process. To associate the accounting context to a production flow, a production group must be selected.  
9. Click Save.

## Create a production flow version
1. Click Add.
2. In the Expiration date field, enter a date and time.
    * You can update the Expiration date of the version at any given time, even for active versions. Use the expiration of the version to plan for a phase out of a version.  
3. Click OK.
4. In the list, mark the selected row.
5. In the Unit field, type a value.
6. Select the Takt unit.
7. In the Average takt time field, enter a number.
    * For the takt control of the production flow version, define a targeted average takt time.   The takt is defined as quantity  per time period.  In the given example, the takt time is 0.2 hours per 10 pieces. For a working time of 8 hours, this corresponds to a daily throughput capacity of 400 pieces.  
8. In the Quantity per cycle field, enter a number.
9. Expand or collapse the Version details section.
10. In the Minimum takt time field, enter a number.
    * The minimum takt time must be less than or equal to the average takt time.  
11. In the Maximum takt time field, enter a number.
    * The maximum takt time must be higher than or equal to the Average takt time.  
12. Enter a number of days in the Period for actual cycle time
    * The period for actual cycle time is the number of days that jobs are aggregated from the actual minute backwards to calculate the actual cycle time. The value can be changed at any time and is only used for the calculation of the actual cycle times.  
13. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]